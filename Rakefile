# -*- coding: utf-8 -*-
$:.unshift("/Library/RubyMotion/lib")
require "motion/project/template/ios"

begin
  require "bundler"
  Bundler.require
rescue LoadError
end

Motion::Project::App.setup do |app|
  app.name = "tunein"

  # development configurations for running on a physical iOS device
  app.identifier = "com.pachun.tunein"
  app.codesign_certificate = "iPhone Developer: Nicholas Pachulski (GM8PL5BLV7)"
  app.provisioning_profile = "/Users/pachun/code/tunein/.provisioning_profiles/tunein_development_provisioning_profile.mobileprovision"

  # spotify sdk dependencies:
  app.libs << "-ObjC" # sneaks in a linker flag
  app.frameworks += ["AVFoundation"]
  app.vendor_project("vendor/Spotify.framework", :static, products: ["Spotify"])

  # the following silences a warning which displays no details and
  # whose significance nobody seems to understand
  #
  # http://stackoverflow.com/questions/21150223/ld-warning-too-many-personality-routines-for-compact-unwind-to-encode
  app.libs << "-Wl,-no_compact_unwind"
end
