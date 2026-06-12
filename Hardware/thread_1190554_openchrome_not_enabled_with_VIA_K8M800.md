---
title: "openchrome not enabled with VIA K8M800"
date: 2009-06-18
forum: Hardware
---

### Post by dpenndorf on 2009-06-18
Hi, I recently installed Ubuntu 9.04 - first linux install.  I can't get my display to do any better than 800x600, even though it has many higher resolution options with Windows.

I've spent many hours trying to properly install openchrome driver, with no success.  I have not found any known bugs to keeping Jaunty from installing this driver.  3d rendering has bugs, sure, but I'm not trying to do anything fancy - just have a normal resolution.

As you can see, my video card is detected (I have the K8M800 chipset):
dp@dp:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

But I can't for the darn life of me do anything to get the details properly into my xorg.conf.  This is the entire output, and I personally added the Driver "openchrome" line:
________________________________________
Section "Device"
    Identifier    "Configured Video Device"
        Driver          "openchrome"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
--------------------------------------------------------------

Any clear instructions (remember: first time with linux!) to follow?  Thanks for any help!
Dave

---

### Post by dpenndorf on 2009-07-06
any ideas?

---

### Post by X-BANE on 2009-07-06
What kind of driver is it? a Run file or a Tar.gz?

---

### Post by dpenndorf on 2009-07-06
openchrome is the video driver for my chipset: [http://www.openchrome.org/](http://www.openchrome.org/)

from all accounts that I can find, it should be automatically installed, but since it's not, I tried half a dozen different manual install methods.  What I posted was my xorg.conf without any of my attempts to manually update it or have any version of openchrome try to install itself.

thanks for any hints/advise!

---

### Post by zepita on 2009-07-06
try adding
Modes  "1024x768"

in the screen section

change it to look like this:

```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
   Subsection "Display"
   Modes "1024x768"
   EndSubsection
EndSection
```



Remember to backup your xorg.conf first so you can restore it from the console. If something goes bad and you mess up the X server you can install links2 by typing sudo apt-get install links2 and view the forum from the console :D

---

### Post by dpenndorf on 2009-07-07
Thanks Zepita, but unfortunately nothing is different.  Unless I'm forgetting to do something to reset the display or something.  I added the text you suggested to my xorg.conf after backing it up, then restarted, and went to Preferences > Display but still only have 800x600 as max resolution.

---

### Post by zepita on 2009-07-07
> **dpenndorf said:**
> Thanks Zepita, but unfortunately nothing is different.  Unless I'm forgetting to do something to reset the display or something.  I added the text you suggested to my xorg.conf after backing it up, then restarted, and went to Preferences > Display but still only have 800x600 as max resolution.

If you see 800X600 as max resolution, there may be a place where that 800X600 is stored and may be edited to 1024x768..

I'll do a quick search to see if I can give you a better advise.

Please try this first:

sudo dpkg-reconfigure -phigh xserver-xorg

Can you paste your xorg.conf file as it looks now using [CODE]?

---

### Post by tommcd on 2009-07-07
The OpenChrome driver should be installed by default in Ubuntu 9.04. Open a terminal and run:
```
aptitude search chrome
```
You should see **xserver-xorg-video-openchrome** in the output with the letters **i** and **A** in front of it. The "i" means installed and the "A" means automatically installed.

Try booting to recovery mode and choose the option **xfix fix video** then reboot and see if you can get the proper resolutions.

---

### Post by dpenndorf on 2009-07-07
Still no luck; but please, keep the suggestions coming!

Both after zepita's sudo dpkg-reconfigure -phigh xserver-xorg and tommcd's recovery mode xfix, my xorg.conf is at the generic state of affairs:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by zepita on 2009-07-07
check here

[http://ubuntuforums.org/showthread.php?p=7573895](http://ubuntuforums.org/showthread.php?p=7573895)

---

### Post by dpenndorf on 2009-07-07
The link you provided sounds like the exact same issue!  I'll have to monitor and see if shail00 gets to a resolution.

When I tried messing with xrandr, I couldn't get my new resolution to take.  I did added the resolution, and it's there, but I can't figure out what --addmode output to call to actually update my resolution.  Here's my relevant outputs:

```

dp@dp:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
dp@dp:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
dp@dp:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768_60.00 (0x80)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz

```[note: prior to 'cvt' command, only the 800x600 and 640x480 resolutions were listed]

---

### Post by zepita on 2009-07-07
check this guide

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I hope it helps and you can enjoy your big screen :P

---

### Post by dpenndorf on 2009-11-12
Solved, Finally!

In xorg.conf, modified to have:

Section "Monitor"
   Identifier "Configured Monitor"
   HorizSync 30-70
   VertRefresh 50-150
EndSection

---

