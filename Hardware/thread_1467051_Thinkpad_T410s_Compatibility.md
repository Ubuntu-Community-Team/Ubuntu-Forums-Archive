---
title: "Thinkpad T410s Compatibility"
date: 2010-04-30
forum: Hardware
---

### Post by ming0 on 2010-04-30
Just wanted to kick a new thread out for all you thinkpad T410s owners and potential owners. I just got one and it's nice. 

 To start, there's a pre-release lucid thread that is pretty much accurate for the official 10.04 lucid release. undoIT reports:
> I'm testing out Kubuntu 10.04 and have the latest bios installed (1.11).  Here's a list of the issues I'm having:

1. Sound card not detected, easy fix as mentioned: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538383)
2. Suspend to RAM not working properly, second time causes system to  reboot.
3. TrackPoint sensitivity cannot be permanently adjusted, as mentioned  here: [http://ubuntuforums.org/showthread.php?t=1454452](http://ubuntuforums.org/showthread.php?t=1454452)
4. Most function keys seem to be working. The only one that doesn't  appear to be working properly is the key to switch between laptop screen  and external monitor.
5. Multi-touch is not working for TrackPad :sad:  I was really hoping for two  finger scroll and right click. Perhaps there is a hack, but this seems  to be an issue with the T400s as well. Hopefully a Synaptic driver  update is coming.

I do not have the issue where left mouse button stops working. Tested  several times. Also, the wireless hasn't given me any trouble (Intel  Ultimate-N 6300) although I haven't tested it for an extended period of  time yet.

Another issue which may just be figuring out how to configure, is that  the brightness setting is not remembered between reboots. The power  daemon always sets the brightness to the profile level, rather than  remembering the level I had adjusted using the Fn keysAlso, if you're interested in using the trackpoint middle button for scrolling, this worked for me (and middle button scrolling is awesome!): [http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html](http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html)

---

### Post by peepingtom on 2010-05-01
The suspend to ram issue will be solved by a BIOS update that's due in early May. Gpointing device settings is the best way to control trackpoint/trackpad for most users because it uses udev. There may be a bug in gpointing-device-settings that prevents settings from persisting. 

[https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754](https://bugs.launchpad.net/ubuntu/+source/gpointing-device-settings/+bug/508754)

[https://bugzilla.kernel.org/show_bug.cgi?id=15407](https://bugzilla.kernel.org/show_bug.cgi?id=15407)

---

### Post by ming0 on 2010-05-04
> **peepingtom said:**
> The suspend to ram issue will be solved by a BIOS update that's due in early May.
That's great news. If anyone hears any more about that being rolled into an easy-to-install update (or automatic update), please post here!

Also would like to report that I'm using the dock (Mini *Dock* Plus Series 3) w/ port replicators and it's working great for: VGA out, sound out, wired ethernet/network, and USB.

There are some minor annoyances w/ the display settings not being remembered when I pop it in/out, but generally speaking it is a good experience.

---

### Post by pbateman on 2010-05-06
One thing I wish would work with Linux is the powered USB port. I've never been able to use it but would come in handy when the laptop is off and I want to charge my phone. Anyone gotten it to work
Also I remember in Karmic, the mute volume would light up when pressed (at least im pretty sure it did) now it doesn't.


Edit. I just noticed this is a t410s thread, i have a t400s...but hopefully the power USB issue applies.

---

### Post by ming0 on 2010-05-10
Quick update:

I get occasional lockups. Can't switch virtual terminals or anything... basically everything is 100% frozen. I'm assuming this is because of some random kernel issue (that will hopefully be fixed in time).

Sleep issue hasn't been resolved yet, but still hoping for that kernel update soon.

I'm running XP in virtualbox (w/ 8 gigs of RAM) and it works flawlessly. No delay in switching windows or performing any function... it's awesome. This is a necessity for me (I use adobe graphics programs professionally).

I know the above user is on a T400, but I can report that my mute button light does work properly on my T410s.

---

### Post by pbateman on 2010-05-12
Thanks I think i'll try doing  reinstall just for kicks and see if it gets resolved...

---

### Post by ming0 on 2010-05-18
New firmware **(**BIOS: 1.14 / ECP: 1.09) fixes the sleep issue (link to iso boot disk w/ firmware upgrade): [http://www-307.ibm.com/pc/support/site.wss/MIGR-74944.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-74944.html)

Note: the USB ports on my laptop stop responding when I come back up from sleep (USB ports on the dock work fine).

---

### Post by ming0 on 2010-05-27
Wanted to report that I have full sleep/wake-up functionality and live USB ports all the time.

The fully functional USB ports will be coming with kernel 2.6.34, but I was impatient and used an ubuntu deb of the early version, using these instructions for amd64: [URL="https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Workaround%20D:%20Use%20a%20kernel%20other%20than%202.6.32"]https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#Workaround%20D:%20Use%20a%20kernel%20other%20than%202.6.32
[/URL]

---

### Post by cayhorstmann on 2010-06-03
Did that new kernel help you with suspend/resume? I just installed the 2.6.34 kernel, and now suspend and hibernate simply fail with an error message that a USB device wasn't cooperating. (I unplugged all external devices, so it must be something internal.)

---

### Post by ming0 on 2010-06-03
I haven't had any problems w/ suspend/resume (I never hibernate tho), ever since I updated the firmware. Seemed to work w/ both versions of the kernel, and the more recent one gives me the added bonus of working USB.

---

### Post by cayhorstmann on 2010-06-04
Thanks for letting me know that it works for you. Unfortunately, I get a message 

usbhid 2-1.8:1.1: suspend error -5
pm_op(): usb_dev_suspend+0x0/0x20 returns -5
Device 2-1.8 failed to suspend async: error -5
Some devices failed to suspend

in the kernel log.

I am not sure what 2-1.8 would be. lsusb identifies 

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If anyone stumbles on this and can give some debugging hints, I would be much obliged.

Thanks,

Cay

---

### Post by nxmehta on 2010-07-29
ming0, can you tell us what it's like to run a mainline kernel?  The wiki says that restricted drivers won't work, but that should be easy to bypass by downloading binary drivers directly from manufacturers (nvidia, etc.).  It does say that ubuntu specific patches will be lost though, but who knows what those patches are for... have you noticed any major differences?

---

### Post by ming0 on 2010-08-06
I just tried switching back to the official Ubuntu kernel (2.6.32-24) and it seems to have solved the last problem I was having with USB (on resume from sleep, USB wasn't working). 

For the most part, things work well on the computer (and generally did with the mainline kernel too). Have recently been noticing some kind of weird wifi instability (I connect to an AP, networking works for a minute, then stops working -- must switch to different AP to get it working), but I haven't seen that often or established any patterns.

How are other T410s lucid users doing? Any major complaints or problems?

---

### Post by ming0 on 2010-10-12
I just updated to 10.10 (saved my /home/ folder) and everything seems to be working pretty well so far.

---

### Post by cpbl on 2010-11-07
Thinkpad T410s and Ubuntu 10.10:

installs perfectly, but I'm disappointed, given Lenovo's assurance that this machine is Ubuntu-ready, about the lack of multi-touch mousepad scrolling and fingerprint reading.

[note on cpbl.wordpress.com]("http://cpbl.wordpress.com/2010/10/29/lenovo-thinkpad-t410s-and-ubuntu-10-10/")

I'd love to hear of anyone's success (preferably simple) with this/these..

c

---

### Post by cpbl on 2010-11-07
Touchpad and Two-finger scrolling...

Adapting instructions from:

[http://www.thinkwiki.org/wiki/Installing_OpenSUSE_11.3_on_a_ThinkPad_T410s](http://www.thinkwiki.org/wiki/Installing_OpenSUSE_11.3_on_a_ThinkPad_T410s)

I tried:

```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 20
```

This works instantly to make two-finger scrolling work.
To make this permanent, I tried putting

```
Section "InputClass"
       Identifier "touchpad catchall"
       Driver  "synaptics"
       MatchIsTouchpad "on"
       MatchDevicePath "/dev/input/event*"
       Option  "HorizScrollDelta"      "99"         # enable horizontal scrolling
       Option  "VertTwoFingerScroll"   "True"       # enable vertical two-finger scrolling
       Option  "VertScrollDelta"       "99"
       Option  "TapButton1"            "1"          # 1-finger tap = left mouse click
       Option  "TapButton2"            "3"          # 2-finger tap = right mouse click
EndSection
```

into /usr/share/X11/xorg.conf.d/20-synaptics.conf 

But this did nothing.  Any suggestions, based on the xorg log that results after next restarting X?

Also, there's another annoying problem with the touchpad on T410s under Ubuntu 10.10: the bottom area of the touchpad has no effect, and turning on horizontal edge scrolling in the mouse preferences has no effect.  Any fixes?

I've submitted a note about the lack of two-fingered scroll in the mouse gui: [https://bugs.launchpad.net/bugs/672650](https://bugs.launchpad.net/bugs/672650)

---

### Post by cpbl on 2010-11-07
Lenovo t410s and fingerprint scanner:

Tried instructions for installing thinkfinger, but I get 
"Initializing...USB device not found" when I try 

```
sudo tf-tool --acquire

```

Instead, then, tried fprint rather than thinkfinger:

```
sudo apt-get install fprint-demo 
```

Then, running

```
sudo fprint_demo
```

brings up the GUI without error, but scanning a finger does not work.

help?

---

### Post by fhsm on 2010-11-22
Does anyone have a T410s with the switchable graphics? If so how does that work? It sounds like it may not ([https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)), is that the case?

Do you have any switching ability, manual or otherwise? Are you able to install and run successfully with one of the two chips?

---

### Post by ming0 on 2010-11-22
> **fhsm said:**
> Does anyone have a T410s with the switchable graphics? If so how does that work? It sounds like it may not ([https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")), is that the case?

Do you have any switching ability, manual or otherwise? Are you able to install and run successfully with one of the two chips?

I don't have switchable gfx

---

### Post by Paerez on 2011-01-14
I just got mine today. I have the switchable graphics. Intel works but it doesn't switch to nvidia. Seems like that support is not going to happen.

If you go into the bios you can force it to nvidia and ubuntu will install the drivers for you w/ Additional Drivers. But then you are on nvidia and can't switch to intel.

Also, seems that the brightness controls don't work w/ nvidia graphics, but I'm still working on that. Everything else has worked great.

---

### Post by Paerez on 2011-01-15
Instructions for switching from intel to nvidia:

1) install "nvidia-current"
2) Use the following /etc/X11/xorg.conf:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```

3) Reboot. At boot, press the ThinkVantage button, then when you get to the boot menu, press F1 to go into Bios. Choose "Config" then "Display". Set the graphics to "Discrete Graphics", forcing nvidia.
4) F10 to Save and Exit

To switch from nvidia back to intel
1) remove "nvidia-current"
2) remove /etc/X11/xorg.conf
3) Perform steps 3 and 4 above, but just "Integrated Graphics"


To allow brightness control when in NVIDIA, see the above xorg.conf.

I know that nvidia is working because Starcraft 2 plays flawlessly under wine. :-)


EDIT: I changed the intel steps to "Integrated Graphics". If you set it to "OPTIMUS" then the nvidia chip doesn't turn off. I saw an 80% increase in power draw when I set it to optimus. So make sure you turn off optimus in ubuntu!

---

### Post by ming0 on 2011-04-15
Hey fellow T410s users, just wondering how your battery life is with Ubuntu?

Mine seems to be rather terrible — roughly 1.5-1.75 hours web surfing, with the display turned to the lowest brightness setting. Closer to 1-1.25 if I've got the brightness up and am doing anything intensive (playing video, graphics editing, etc).

I could only stand to run windows for two days before I uninstalled it, but people report getting 3-4 hours of battery life when they have their display turned down.

I've looked at some of the "improve your battery life" threads and the suggested options seem to be already turned on, or somewhat impractical.

Are other people experiencing the same thing? Anyone found any solutions?

---

### Post by ming0 on 2011-07-05
Just want to report that 11.04 is terrible with the T410s — multiple people have reported it and unfortunately, I didn't check their posts ahead of time. I'm having trouble with a blank screen: [http://ubuntuforums.org/showthread.php?t=1750567&highlight=external+monitor+black+switch+resolution](http://ubuntuforums.org/showthread.php?t=1750567&highlight=external+monitor+black+switch+resolution)

---

