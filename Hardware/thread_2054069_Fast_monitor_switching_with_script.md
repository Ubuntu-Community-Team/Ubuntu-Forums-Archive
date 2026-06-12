---
title: "Fast monitor switching with script"
date: 2012-09-06
forum: Hardware
---

### Post by kovo1533 on 2012-09-06
Hello I need help with this: I have Lenovo S12 ion notebook and two external LCD monitors. One 22" connected trought VGA analog port (Samsung SyncMaster 2220LM) and second 17" trought HDMI port (HDMI to DVI)

All works fine, when i am @ home i am able to disable laptop screen and enable this two in twinwiew mode trought nvidia-settings BUT it takes LONG time to set all settings. I want to do it by ONE CLICK.

Few days ago, i have only samsung 22" monitor and i was using program in C that uses "disper" and depending on what screen was currently used, it switch to external or laptop and few other things like notification and conky restart

Now the problem is that i cannot find way to enable the 17" monitor with command. i must do it manually in nvidia-settings

---

### Post by kovo1533 on 2012-09-06
oh i forgot some data: 
laptop screen: 1280x800 60 Hz
22" monitor: 1680x1050 60 hz
17" monitor: 1280x1024 60 hz

when on external, use twinview and use 22" as primary,
in 17" properties disable option "force full GPU scaling" (otherwise monitor randomly shuts down and flicker)
positions of screens are absolute 

some data from terminal running "disper -l"

root@kovo-notebook:/home/kovo# disper -l
display DFP-0: AUO
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 640x350, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 1024x768, 1280x800
display CRT-0: Samsung SyncMaster
 resolutions: 320x240, 400x300, 512x384, 680x384, 640x480, 720x450, 700x525, 840x525, 800x600, 960x540, 832x624, 960x600, 1024x768, 1152x864, 1360x768, 1280x960, 1440x900, 1280x1024, 1400x1050, 1920x1080, 1680x1050
display DFP-1: Arnos Instruments M-17 DVI
 resolutions: 320x175, 320x200, 360x200, 320x240, 400x300, 416x312, 512x384, 576x432, 640x400, 680x384, 720x400, 640x480, 720x450, 640x512, 700x525, 800x512, 840x525, 800x600, 960x540, 832x624, 960x600, 896x672, 928x696, 960x720, 1024x768, 1152x864, 1280x960, 640x350, 1280x1024
root@kovo-notebook:/home/kovo#

---

### Post by Eromatic on 2012-09-08
_[Disper-indicator](https://code.launchpad.net/~nmellegard/disper/disper-indicator)_ *[_(PPA)_](https://launchpad.net/~nmellegard/+archive/disper-indicator-ppa)* could perhaps be useful for a quick point & click solution. Sometimes you'll need to select the monitor configuration from the drop-down menu a second time for the switch to be successful. Needs 2-4 clicks at most, but I believe it is the safest and easiest way to use disper, as it also auto detects the connected monitors.

For disper terminal commands, there is a guide that I have used with much success at [http://maketecheasier.com/change-linux-displays-on-the-fly-with-disper/2010/12/22](http://maketecheasier.com/change-linux-displays-on-the-fly-with-disper/2010/12/22)

One note however about disper is that it doesn't work with Nvidia's 300+ series drivers the last time I had checked, and only up to the 295 series should be used with disper.

---

