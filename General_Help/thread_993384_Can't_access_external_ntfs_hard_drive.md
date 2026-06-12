---
title: "Can't access external ntfs hard drive"
date: 2008-11-25
forum: General Help
---

### Post by ozguitarplayer on 2008-11-25
Hi,
I have a Ubuntu on one hard drive and windows (ntfs) on another, I can access the windows hard drive from Ubuntu.
However I have an external usb connected hard drive (ntfs) I can't get into that one and I need to (I have run the ntfs configuration tool and set it for internal and external drives)

This is the message I get when I try to access the drive;
An error occured while accessing "New Volume", the system responded: org.freedesktop.Hal.Device.Volume.UnknownFalure:$LogFile indicates unclean shutdown (0, 0) Failed to mount /dev/sdc1': Operation not supported Mount is denied because NTFS is marked to be in use.

it then goes on to explain how to safely disconnect the drive...

Any suggestions on how I may get into the external hard drive?

---

### Post by logos34 on 2008-11-25
> **ozguitarplayer said:**
> 
it then goes on to explain how to safely disconnect the drive...

well, have you tried to boot back into windows and do just that? Mass storage devices (usb) must be shut down/removed in windows properly, otherwise you often can't mount them in linux

---

### Post by ozguitarplayer on 2008-11-25
thanks, no I haven't tried that, as I've never had to do any 'correctly shut done' before with the external drive as I has never been mentioned before and there just the switch on the back that I use...

I don't often use that drive it's my back so I open it once a month.... 

If is was  in windows how do I go through the 'correctly shut down' procedure when it's never appeared as an instruction
.....somewhat confused....:)

---

### Post by Zaraphrax on 2008-11-25
> **ozguitarplayer said:**
> thanks, no I haven't tried that, as I've never had to do any 'correctly shut done' before with the external drive as I has never been mentioned before and there just the switch on the back that I use...

I don't often use that drive it's my back so I open it once a month.... 

If is was  in windows how do I go through the 'correctly shut down' procedure when it's never appeared as an instruction
.....somewhat confused....:)

I have this problem, and I find it easiest to actually shutdown (or restart) my machine with the External drive connected and powered up. That way, I don't even have to touch it and it mounts as soon as Linux boots up.

---

### Post by ozguitarplayer on 2008-11-25
thanks I now see the reasoning.....won't be able reboot for a few few hours...I'll let you know...

---

### Post by john183 on 2008-11-25
If you don't have the time to shutdown your windows machine, connect the usb hard drive and let windows recognize it and access it and all. Then in the system tray look for an icon that when you hove over it gives a tool tip of "safely remove hardware". it looks like a gray box with a green arrow coming out of it. right click that icon and select the drive that you want to "properly" remove. DO NOT pull out the usb cord until you get a little bubble that says "[xyz] drive can now be safely removed." At that point you can completely remove the drive from the computer and connect it to a linux machine without any issues.

---

### Post by ozguitarplayer on 2008-11-25
I restarted with the external hard drive already on and I got the same error message..is the idea of the ntfs config that it allows me to access ntfs files?
I could already access the ntfs files on the windows hard drive before installing the ntfs config I only install the config when I found that I couldn't get into the usb external hard drive.....
maybe I'll reinstall the congig....

---

