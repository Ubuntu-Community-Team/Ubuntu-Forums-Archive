---
title: "Black screen on startup after upgrade from 9.04 to 9.10 RC"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by TC!! on 2009-10-24
I've read through lots of threads with black screen problems but so far nothing has fixed my issue.

My upgrade went fine with no errors, on my first boot up I saw the white Ubuntu logo on a black background followed by some text and then it went to a blank screen.

After reading I decided to try to update things to make sure there weren't any fixes. So I booted up and then used grub to go to recovery mode and ran sudo apt-get update which did install some updates.

After that instead of seeing text it goes straight from the white logo to a blank screen. I get the same if I boot into recovery and use startx, immediate black screen.

I had tried the other advice of editing the boot line in grub including removing quiet and splash and adding nomodeset but still the same problem.

Finally I tried using this command:
sudo apt-get remove --purge fglrx*

As this had helped some other people, now it stays on the white logo and says it's checking the disk, if I press escape to cancel it goes straight to the black screen. (Right now I've left it running and it is up to 15% so I'll leave this running.)

Finally I'm running on a Dell SC440 which has integrated graphics but I use an nvidia card.

---

### Post by TC!! on 2009-10-25
Bump. Am I posting in the wrong place or does no one want to help?

---

### Post by motsteve on 2009-10-25
That is what my upgrade was doing.  It gets to the end of the hardware check and then tries to start the x server, but the xorg.conf is hosed and I haven't gotten one that cures this.  Are you upgrading 64 bit?

---

### Post by pbrane on 2009-10-25
have you tried running

**sudo dpkg-reconfigure -phigh xserver-xorg**

in a terminal? This will reset /etc/X11/xorg.conf. If you are using the nvidia you'll probably have to re-install it. I did anyway. You can also try setting your driver to vesa in your xorg.conf like this:

[I]Section "Device"
    Identifier	"Configured Video Device"
#    Option    "NoLogo" "True"
#    Driver    "nvidia"
    Driver    "vesa"
EndSection
[/I]

---

### Post by TC!! on 2009-10-26
No it's a 32 bit install, I used to have problems with XBMC so chose 32 bit.

Thanks for the tips I'll try those out later, one other question though, what's the best way to install the nvidia drivers, I normally use envy.

---

### Post by motsteve on 2009-10-26
> **pbrane said:**
> have you tried running

**sudo dpkg-reconfigure -phigh xserver-xorg**

in a terminal? This will reset /etc/X11/xorg.conf. If you are using the nvidia you'll probably have to re-install it. I did anyway. You can also try setting your driver to vesa in your xorg.conf like this:

[I]Section "Device"
    Identifier	"Configured Video Device"
#    Option    "NoLogo" "True"
#    Driver    "nvidia"
    Driver    "vesa"
EndSection
[/I]

I'm guessing you would do this in the terminal you have if you boot recovery, right?  My clean install (64bit) has a xorg.conf file that is only one section.  Why the hey would the installer do this?  There is no way my install could even get into a stumbling gui.  It'll take a lot now to convince me to go to Karmic, but I'll try the above suggestion and thanks for the info.  I hope it works for the 32 bit install also.

---

### Post by pbrane on 2009-10-26
> **TC!! said:**
> No it's a 32 bit install, I used to have problems with XBMC so chose 32 bit.

Thanks for the tips I'll try those out later, one other question though, what's the best way to install the nvidia drivers, I normally use envy.

I used this forum thread to install nvidia 185.18.36 on my machine. I run 64-bit Ubuntu but all of this will work on a 32-bit machine as well.

[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

---

### Post by bsntech on 2009-10-26
Something else you can try -

When you get to that black screen, hit Ctrl + F1 on your keyboard.  This will take you to a login prompt in just text-only mode.  Enter your username/password that you first entered when installing Ubuntu.

When you get a typical terminal prompt, enter:

sudo X -configure

This will automatically have X check your video card and create a xorg.conf file.  It will first save it to your home folder as xorg.conf.new.  Copy this to the /etc/X11 folder like such:

sudo cp ~/xorg.conf.new /etc/X11/xorg.conf

See if that corrects the video problems.

---

### Post by TC!! on 2009-10-26
OK, finally got something.

I tried the command to fix the xorg.conf file but I was still getting a black screen. In the end I just moved the xorg.conf out of the way and then I was able to boot to my desktop with no problem. Obviously I now have poor graphics and need to get that fixed. (But it also gave me vnc again which makes things much easier since I use my ubuntu setup for XBMC and it's attached to a TV.)

I'll try envy again to see if that will get me the latest nvidia drivers and configure things for me, or do you think it's better for me to follow the instructions on the link that was posted?

---

### Post by pbrane on 2009-10-26
Envy has worked for me in the past just fine. I wanted to install the lastest 185 drivers and envy wasn't seeing them. So I used the link posted above to install it. Either way is up to you, if envy has the latest driver then I would use envy.

---

### Post by TC!! on 2009-10-27
Envy gives me 185.18.36-0ubuntu9 which I think is the latest stable. I uninstalled and then reinstalled using envy but I can still only get to a desktop if I have no xorg.conf file.

I saw in the X11 directory that ubuntu backs up my old xorg.conf files when it performs an upgrade so I'm going to try rolling back to the one I had working before my upgrade to 9.10 RC.

I tried that but still no joy no matter what xorg.conf file I use I always get stuck with a black screen. Do you think it could be linked to my setup of having onboard Intel graphics and an Nvidia card or just purely linked to the Nvidia setup?

Is there anything else I can check on to see why this is happening? I looked at the /var/log/Xorg.0.log file but it looks like it is only written when the desktop runs successfully as I tried to read it after a failure but the dates where linked to the last time it ran successfully.

---

### Post by pbrane on 2009-10-27
I'm beginning to think that your onboard intel video is causing this. I assume you have disabled the onboard video in the BIOS? You might look at dmesg to see if the intel driver is being loaded. I'm not sure what to do if you can not disable your onboard video in the BIOS. Perhaps you can blacklist the intel video driver. Look in /etc/modprobe.d to see if one of the blacklist files will work.

Hopefully someone who has had to deal with this can help.

Try **lsmod** in a terminal to see if you have both nvidia and intel video drivers loaded.

---

### Post by TC!! on 2009-10-27
Not sure about the bios, will have to check.

lsmod has the following at the bottom, but this is when I run without the xorg.conf, does that make any difference?

radeon                636000  0 
ttm                    36212  1 radeon
drm                   159584  2 radeon,ttm
agpgart                34988  3 nvidia,ttm,drm
i2c_algo_bit            5760  1 radeon
tg3                   109600  0 

I believe the onboard graphics are similar to a radeon.

I also tried going back to the previous version of Nvidia drivers but still nothing.

---

### Post by pbrane on 2009-10-27
If you have an Intel graphics on board you shouldn't be running a radeon video driver. How about looking at **lspci** output and see if you can spot your onboard video.
Mine for instance:

[B][I]...
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
...[/I][/B]

I have a laptop with intel graphics and I don't have a radeon driver running. I also have a laptop with nvidia 8600M GT (I'm on it now) and I only have an nvidia driver loaded. I initially ran **dpkg-reconfigure** before I upgraded to Karmic and then installed the nvidia driver after the upgrade was complete. I had no issues.

---

### Post by TC!! on 2009-10-28
Here are the interesting bits of lspci:
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
05:07.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)

On Ubuntu the ES1000 uses the radeon driver. Any ideas what to try next?

---

### Post by pbrane on 2009-10-28
After looking at the ES1000 specs online I see why you use the nvidia card. I'm assuming there is no way to disable the onboard ATI in your BIOS, so, I would try blacklisting the radeon driver. I've never had to do that before so I'm not 100% sure if it will work or not. To blacklist that driver go to /etc/modprobe.d/blacklist.conf and add a "blacklist radeon" at the end of the file. Without the quotes of course. You may even want to make a backup of the original first. You'll have to do this as root.
**sudo gedit /etc/modprobe.d/blacklist.conf**
 in a terminal should do it. Or if you prefer you can type
**ALT+F2 **and enter **gksu gedit /etc/modprobe.d/blacklist.conf**

Let us know if this works.

---

### Post by fbroce on 2009-10-28
> **TC!! said:**
> OK, finally got something.

I tried the command to fix the xorg.conf file but I was still getting a black screen. In the end I just moved the xorg.conf out of the way and then I was able to boot to my desktop with no problem. Obviously I now have poor graphics and need to get that fixed. (But it also gave me vnc again which makes things much easier since I use my ubuntu setup for XBMC and it's attached to a TV.)

I'll try envy again to see if that will get me the latest nvidia drivers and configure things for me, or do you think it's better for me to follow the instructions on the link that was posted?

With the latest kernels, you don't have to have an xorg.conf. You could make a copy of your located in /etc/X11 and then try it without xorg.conf. 

Fred B-

---

### Post by TC!! on 2009-10-28
> **fbroce said:**
> With the latest kernels, you don't have to have an xorg.conf. You could make a copy of your located in /etc/X11 and then try it without xorg.conf. 

Fred B-

I have been running without the xorg.conf but then when I try to set my screen resolution through the Nvidia app it tells me the nvidia driver isn't being used. So how do I turn on the nvidia driver without an xorg.conf file?

---

### Post by TC!! on 2009-10-29
> **pbrane said:**
> After looking at the ES1000 specs online I see why you use the nvidia card. I'm assuming there is no way to disable the onboard ATI in your BIOS, so, I would try blacklisting the radeon driver. I've never had to do that before so I'm not 100% sure if it will work or not. To blacklist that driver go to /etc/modprobe.d/blacklist.conf and add a "blacklist radeon" at the end of the file. Without the quotes of course. You may even want to make a backup of the original first. You'll have to do this as root.
**sudo gedit /etc/modprobe.d/blacklist.conf**
 in a terminal should do it. Or if you prefer you can type
**ALT+F2 **and enter **gksu gedit /etc/modprobe.d/blacklist.conf**

Let us know if this works.

Hey, that did it!!!

I blacklisted as you suggested and tried a few different xorg.conf files (including failsafe which failed), I then tried the backup xorg.conf from the last time it was working and it came up with full resolution!!

Looks like the new xserver in 9.10 isn't happy with the dual graphics setup I had to force the onboard to be disabled. What's even more confusing for me is that the xorg.conf has loads of stuff in it related to the card we just disabled but the system seems happy about that.

---

### Post by pbrane on 2009-10-29
Cool! I guess with xorg being more "automatic" these days it got confused about which driver to use. I think it should have dropped you back into the vesa driver. That would have been the sane thing to do. You may be able to remove (or comment out) the radeon stuff in xorg.conf. I bet your xorg.log has some clues in it. You should be running the nvidia driver only.

---

### Post by ufo123 on 2009-12-14
TC, can you please list your xorg.conf file. I also have an SC440 with a Nvidia 8500GT graphics card and also get the black screen if I leave the xorg.conf file on /etc/X11. Can't try using an other xorg.conf file since I reinstalled 9.10 hoping to resolve the graphics card issue, don't have a previously working xorg.conf to try
Thanks

---

### Post by TC!! on 2009-12-20
Here is my xorg.conf but remember to blacklist as well.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Generic Keyboard"
#       Driver          "kbd"
#       Option          "XkbRules"      "xorg"
#       Option          "XkbModel"      "pc105"
#       Option          "XkbLayout"     "us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#EndSection

Section "Monitor"
        Identifier     "Configured Monitor"
EndSection

Section "Monitor"
        Identifier     "monitor1"
        VendorName     "Generic LCD Display"
        ModelName      "LCD Panel 1360x768"
        HorizSync       31.5 - 48.0
        VertRefresh     56.0 - 65.0
        Gamma           1
        ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine       "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
        ModeLine       "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
EndSection

Section "Monitor"
        Identifier     "monitor2"
        Gamma           1
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Device         "Configured Video Device"
        Monitor        "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes      "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "screen1"
        Device         "device1"
        Monitor        "monitor1"
        DefaultDepth    24
        Option         "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth       24
                Modes      "1280x768@60" "1280x720@60" "800x600@60" "800x600@56"
        EndSubSection
EndSection

Section "Screen"
        Identifier     "screen2"
        Device         "device2"
        Monitor        "monitor2"
        DefaultDepth    24
        Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
        Load           "v4l"
        Load    "glx"
        Disable "dri2"
EndSection

Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "keyboard"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
        # generated from default
EndSection

Section "Extensions"
EndSection

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "screen1" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier     "Configured Video Device"
        Driver  "nvidia"
EndSection

Section "Device"
        Identifier     "device1"
        VendorName     "NVIDIA"
        BoardName      "NVIDIA GeForce 7 Series"
        BusID          "PCI:2:0:0"
        Screen          0
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection

Section "Device"
        Identifier     "device2"
        VendorName     "ATI"
        BoardName      "ATI Radeon"
        Option         "MergedFB" "off"
        BusID          "PCI:5:7:0"
        Screen          0
        Driver  "nvidia"
EndSection

```

---

### Post by ufo123 on 2010-01-10
Thanks TC,
Couldn't resolve by problem using the xorg.conf file you included, but,
was able to resolve the black screen issue and problems with the system not 
recognizing the nvidia graphics card by following instruction of this link
[ http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400") and also had to blacklist 
my mother board radeon graphics card by adding 'blacklist radeon' (don't include quotes) to /etc/modprobe.d/blacklist.conf

---

