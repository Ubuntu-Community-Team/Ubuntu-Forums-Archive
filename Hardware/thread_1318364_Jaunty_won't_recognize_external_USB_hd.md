---
title: "Jaunty won't recognize external USB hd"
date: 2009-11-07
forum: Hardware
---

### Post by supdewds on 2009-11-07
I have two external drives, both seagate, both usb interface.  They both have been detected and mounted before on the Dell 4700C I'm using as a media box, however, when I try to boot I sometimes have an error which says something about the usb device (I have tried to replicate it but can't seem to, so far) and when I unplug the usb cable, it will continue to boot normally. 

The weird thing is that the one with the on/off switch will mount every time, but the one without it won't, in either windows or ubuntu.  

I am dual booting tinyxp and jaunty on a Dell 4700C with 2gb of RAM and 2.6 Ghz pentium.  Is there a preferred way to get both operating systems to recognize the drive?  When one does it, both will, but never will one do it and the other won't.  I have read that there are sometimes problems with things being "cold-plugged", i.e., plugged in on boot, so maybe I could modify my boot procedure?  

The unpredictable behavior has me really confused.

---

### Post by gillmt on 2009-11-07
I think that if you leave a CD in the drive or a USB device plugged in when you boot your PC and your BIOS is set to boot from anything other than the HD first, it will be looking for an operating system.

No expert but I always start the PC before plugging anything in unless I want to boot from a CD or USB device.

---

### Post by supdewds on 2009-11-07
Fair enough, I guess.  It's just weird that I used to be able to boot with them plugged in on my other pc and have no troubles.  Maybe it's because of the dual boot?

edit: okay, booting with them turned off and then plugging them in when boot has finished worked, but that's kind of a pain in the ***.  If I want to restart into windows or vice versa I have to shut down, unplug the drives, boot, and plug the drives back in.  I don't really want to have to do that if there's a way around it.

---

