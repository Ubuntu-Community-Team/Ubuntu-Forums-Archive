---
title: "Intel HDA Realtek ALC268"
date: 2009-04-05
forum: Hardware
---

### Post by toobukume on 2009-04-05
I just recently tried loading up Ubuntu on my HP Pavilion tx2510us laptop.

I first installed Ubuntu 8.10 x64. The first thing I noticed is that I don't have any sound. So, I figured, I'd give the new beta (9.04 x64) a shot. Still no sound.

I was sick today so I spent the entire day searching forums trying to get sound working (nothing better to do, lol). I have tried recompiling alsa libs and drivers with no luck. I have made the appropriate aditional configuration option in /etc/modprobe.d/alsa-base.conf. No matter what I do, I can't get sound to work (thru the built-in speakers, or any of the headphone jacks).

I am a COMPLETE noob to Ubuntu (and linux in general) so keep that in mind when replying. Thank you for your support!

---

### Post by bertolo on 2009-04-05
[http://ubuntuforums.org/showthread.php?t=1117215](http://ubuntuforums.org/showthread.php?t=1117215) look to my very first post
i have the same audio card. =P
good luck

---

### Post by Favux on 2009-04-05
Hi toobukume,

If bertolo's fix doesn't work then there is a well known (sorry) fix.  This is assuming you have the same sound chip as other TX2500's.

To the bottom of the file /etc/modprobe.d/alsa-base you add the following line:
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
To edit the file you would use:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Since you have to be root when you edit it gksudo will do that.  It will ask for your password.  Gedit is gnome-edit.  If you want to know why this works (which hopefully it will) I have some details I can give you.

Good luck.

---

### Post by toobukume on 2009-04-05
Thank you both for your quick responses!

I tried Favux's fix first (because it was a quick fix) and it actually worked!

I had: 
options snd-hda-intel model=hp

Instead of Favux's:
options snd-hda-intel index=0 model=toshiba position_fix=1

I made the change, rebooted, and heard the login sound for the first time. Thank you very much!

I will be posting about getting a few other hardware issues fixed shortly (tablet stylus functions, aircard).

---

### Post by Favux on 2009-04-05
Hi toobukume,

You are welcome.  I can help you get your Wacom stuff working if you want.  Are you back on Intrepid?

---

### Post by toobukume on 2009-04-06
That would be awesome if you could help get my tablet functions working!

Yes, I had trouble getting the proprietary video card drivers working in Jaunty so I backed down to Intrepid about half an hour ago. I'm back online, doing my fresh-install routine (Updates)

I don't even know where to start to get my tablet working.

UPDATE:
Out of the box, all I needed to do was add your line to my alsa-conf and sound works. I've not got the proprietary video drivers working and compiz is running smooth.

The only two hardware things I have left to get working is now my tablet and aircard (doubt i'll get the aircard working).

---

### Post by Favux on 2009-04-06
Hi toobukume,

Ok, the bad news is that you will have to disable Compiz and go back to Metacity.  Make sure your visual affects tab in Appearance is checked at say Normal.  Compiz interferes with rotation.  The linuxwacom drivers native to Intrepid are 0.8.1-4.  We'll want to upgrade them to 0.8.1-6.  First go to 

[http://ubuntuforums.org/showthread.php?t=1038949&page=7](http://ubuntuforums.org/showthread.php?t=1038949&page=7)

Download the TX2500 xorg.conf at the bottom of the first post.  Notice near the top the link to Loic2's Wacom wiki:

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

There you should download the 0.8.1-6 amd64 deb.s that are near the top and install them.  Now backup your xorg.conf and then compare it to the one from the HOW TO.  Basically you should replace yours with it (notice "radeon" not "fglrx").  If you want to change it piecemeal study it carefully.  Notice that some of the sections also have to be reflected in the "ServerLayout".  When you're done with that and have rebooted you should have Wacom.  Be sure to follow section 3 on the HOW TO to use wacomcpl and get your .xinitrc set up.  Then go to the Rotation HOW TO (also linked):

[http://ubuntuforums.org/showthread.php?t=996830&page=9](http://ubuntuforums.org/showthread.php?t=996830&page=9)

Notice the stuff about "fglrx".  It now does support rotation, but not with Compiz.

Good luck!

Edit:  I just noticed your other post about an external monitor.  I'd strongly advise not doing that until you get Wacom and rotation set up first.

---

### Post by matera.ttp on 2009-09-10
> **Favux said:**
> 
```
options snd-hda-intel index=0 model=toshiba position_fix=1

```
To edit the file you would use:
```
gksudo gedit /etc/modprobe.d/alsa-base
```


it works for me too. thanks a lot

---

### Post by markackerman8@gmail.com on 2009-11-01
Hey Guys I am having real problems with sound too after a clean install of karmic and with grug2. ARghhhhhh I have looked everywhere and tried all the troubleshooting guides with no success double arghhhhh

Everything that points to an output device only shows the"dummy" (WITH PADEVICECHOOSER or system/preferences/sound_preferences),

but when I:

ack@Titan:~$ gnome-alsamixer ... it shows "Realtec ALC268"

or
ack@Titan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 0/1
Subdevice #0: subdevic

or
ack@Titan:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Hewlett-Packard Company Device 30cc
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

ANY SUGGESTIONS?????

---

### Post by Favux on 2009-11-01
Hi markackerman8,

Do you have a TX2500 too?

You might want to check Hardware Drivers and see if Software Modem driver is installed.  If so try uninstalling it and rebooting.

---

