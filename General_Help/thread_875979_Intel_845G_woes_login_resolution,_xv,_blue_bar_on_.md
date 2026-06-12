---
title: "Intel 845G woes: login resolution, xv, blue bar on video playback"
date: 2008-07-31
forum: General Help
---

### Post by Zorael on 2008-07-31
I thought I knew my way around xorg.conf but here I am, stumped and out of ideas. I bought a Compaq Evo (something) cheap and I figured I'd put Kubuntu on it.
```
$ lshw -C video
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810
```


First of all; the monitor supports resolutions up to 1600x1200, but X *refuses* to make 1280x1024 the default. The login screen is *always* in 1024x768, though upon having logged in it properly switches to my user-specifically chosen 1280x1024. I've tried what first sprung to mind, defining the resolutions in xorg.conf and putting 1280x1024 first, but that didn't help.
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
                Depth   24
                Modes   **"1280x1024"** "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```
```
(II) intel(0): EDID vendor "DEL", prod id 28673
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA "1280x1024"**using initial mode 1024x768**
```


Secondly, I'm having some serious issues with xv. Mplayer refuses to play some/all files, spouting the following to a terminal.
```
VO: [xv] 1280x720 => 1280x720 Planar YV12  [zoom]
Source image dimensions are too high: 1280x720 (maximum is 1024x1088)
FATAL: Cannot initialize video driver.
```
Kaffeine (and xine) plays the same files, but a sizeable part of the output is just a blue field. I imagine this is the "overlay color", at a lack of better words? The field scales if I scale the video. To boot, Kaffeine always crashes upon closing it after having played anything using xv.

So far, I've made some modifications to xorg.conf as per [the Compiz-Fusion wiki](http://wiki.compiz-fusion.org/Intel%20with%20AiGLX) to enable AiGLX. That did, of course, speed up drawing speeds, but not much else.


Any ideas? Thanks.

---

### Post by jonno on 2009-01-22
> **Zorael said:**
> 
Secondly, I'm having some serious issues with xv. Mplayer refuses to play some/all files, spouting the following to a terminal.
```
VO: [xv] 1280x720 => 1280x720 Planar YV12  [zoom]
Source image dimensions are too high: 1280x720 (maximum is 1024x1088)
FATAL: Cannot initialize video driver.
```

Any ideas? Thanks.

I've just noticed the same problem trying to playing hi-def video (same Intel 845G). [Thread started here]("http://ubuntuforums.org/showthread.php?p=6595142#post6595142").
Did you ever figure out a solution?

---

### Post by bigbrovar on 2009-01-22
for the resolution problem have you tried installing 915resolution from synpatic or geekly via terminal ```
sudo apt-get install 915resolution
```

---

