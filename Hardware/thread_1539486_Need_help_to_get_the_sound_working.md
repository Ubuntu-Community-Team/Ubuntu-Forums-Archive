---
title: "Need help to get the sound working"
date: 2010-07-26
forum: Hardware
---

### Post by mastablasta on 2010-07-26
Hello I just switched the motherboard. I don't know do i need to do anything else in Linux to register this, because sound is not working (everything else works really nice). Let me give a better description of what is going on.

i need help with my sound card. i already asked on local IRC channel and got some help using alsamixer, but nothing changed. i thought this sound card is not compatible with linux (though it should be) so i tried Mint Live 8 - and SOUND WORKS. Don't have the 9 version, appart from LXDE. i will try that one as well, just to see if there is some Kernel issue. 

Anyway my card is:

According to alsamixer

 chip realtek ALC662 rev1
 card HDA VIA VT82XX

according to preferences: VT 1708/A Azalia HDAC (VIA High definition Audio Controler)

Only this one dissapears after some time from the preferences. And then they behave like i do not have any sound card, so i can't change any settings. I am suspecting this is the old sound "card".

Please help.

EDIT> I just tested MInt 9 LXDE live session / sound works OK though it is a bit quiet and i cant really increase it much.

---

### Post by dabl on 2010-07-26
Audio How-To: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by mastablasta on 2010-07-26
OK this is strange Live session Ubuntu 10.04 sound work OK.

When i type aplay -l

It says the list of cards and the shows up nothing.

lspcv show it normally.
-------
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: ASRock Incorporation Device 0662
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

------

like i said card seems to be installed ok at the start but then it dissapears.

alsa mixer is showing master volume as 0. and i can't increase it!!!

There must be just a wrong setting somewhere in the system.

---

### Post by lidex on 2010-07-26
Do you have an add on card or just onboard audio? Is it a new install? Using old /home partition?
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by mastablasta on 2010-07-27
> **lidex said:**
> Do you have an add on card or just onboard audio? Is it a new install? Using old /home partition?


Onboard audio. itsa new install (as in hardware install) using old home partition.

oh and here is the link the scrip gave me:
[http://www.alsa-project.org/db/?f=e4b2a5c59a4438fd710cf71e2b13707176388e82](http://www.alsa-project.org/db/?f=e4b2a5c59a4438fd710cf71e2b13707176388e82)

---

### Post by lidex on 2010-07-27
So this is a new asrock board? What's the model number?
Remove old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
If you've installed alsa-backports, uninstall it. 
Now reboot and follow the alsa-upgrade link in my sig
to get v 1.0.23

---

### Post by mastablasta on 2010-07-27
> **lidex said:**
> So this is a new asrock board? What's the model number?

Yes it's a "new" motherboad withold components. It's 4CoreDual-SATA R2.0. Has both AGP and PCIe ports as well as DDR and DDR2 ra slots. but can only hold max 2 GB ram. but perfect for upgrading.
> 


rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
"says cannot remove, no such file or directory." is this ok? should i just continue with next command?

---

### Post by mastablasta on 2010-07-27
Problem solved by a helpful ubuntu member on IRC channel.:

First i had to set the cvolume properly with this command:
> sudo alsamixer -c0And then save it:
> sudo alsactl store

---

