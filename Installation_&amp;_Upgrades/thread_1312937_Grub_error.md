---
title: "Grub error"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by RndmGuy06 on 2009-11-03
I'll start with the problem. Dual boot XP and Netbook-remix 9.10. Worked 
well except I am using on a ASUS netbook (No cd/drive) with the 1.33 ghz
proc. Remix was just way too slow and lagged. Hopped back into XP 
reformatted my Ubuntu Drive thinking all would be well. Had to restart XP 
due to an upgrade for IE. Now this...

GRUB loading.
error: unknown filesytem
grub rescue>

The only command I can get to do anything is ls. My XP drive is fully 
intact but not backed up in the past week. So there is a lot of 
assignments I would really not like to lose. And I wanted to try out 
Moblin.


So I made a huge mistake yesterday. I have been using Ubuntu for a few 
years now and have converted a few :) but as a student I can't convert 
fully yet. I have a little c++ and networking experience but a terminal 
window still can get me nervous. 

I have a desktop running Ubuntu fulltime and virtual box XP. I love it! 

Anyway, anything that you guys can help with would be so appreciated!

---

### Post by dstew on 2009-11-03
Probably the grub boot loader will not work because the grub.cfg file was removed when you reformatted the Ubuntu partition. Do you want to remove Ubuntu completely, and just boot XP? If so, you can use an XP CD "Recovery Console" and replace the grub boot loader with the XP boot loader. I think the command is FIXMBR.

If you want to keep using grub to boot XP, I am not sure you can do that. The grub boot loader needs to get the bulk of its code from a filesystem somewhere on the disk. The grub 2 manual gives an example of installing grub 2 into a Linux filesystem, using a Linux package manager, but no example of installing it into an NTFS. You might be able to create a small ext3 partition, use a Live CD to install grub into it, and then use that to boot XP.

---

### Post by RndmGuy06 on 2009-11-03
Thanks for the info. I am trying that now but without a cd-drive I am attempting to find iso and converting to boot to a usb. I just finished making an XP system recovery drive and I'll see if it works right now.

If this doesn't work then I would love for you explain the last part of what you just said about a small partition for a linux grub.  

I'll be right back...

{Added}
I can't get the computer to recognize anything else ie usb. It goes straight to the GRUB loading....blah blah blah.  Is there a way I can have it boot from a usb without having a grub loaded?

---

### Post by ajgreeny on 2009-11-03
If needed after your attempt to get windows back again, try reinstalling ubuntu again, but choose manual at the partitioning stage, and as dstew says, make a small (100MB) partition and mount it as boot in the dropdown list.  Install as normal from that point, and then you can if needed delete the ubuntu partition and the boot partition will still be there and allow you to boot into windows.

If your repair of the win MBR is successful, just ignore all this as you won't really need it.

I've just noted you used 9.10, which has grub2 and not all tye files needed for grub are in the /boot/grub folder, as they were in legacy grub (9.04 and earlier), so my idea may still not work, I'm afraid, though my knowledge of grub2 is very limited, and I can't say it will not work with any certainty.  The old menu.lst file is now replaced with a grub.cfg file, which needs other files located in /etc to be produced in the first place, but once there it may be fine for the windows boot, even though the other files are no longer present (if you remove the ubuntu partition).

---

### Post by RndmGuy06 on 2009-11-03
That sounds easy enough :) I have been making my 9.10 start-up drive right now...done in 1 min. 

I think my issue is I can't get the usb to boot. Could grub be causing that? or would that strictly be BOIS settings?

---

### Post by JBAlaska on 2009-11-03
Not sure about your netbook, but most computers need to have "allow to boot from usb" (Or some such) and usb before the HD in the boot order set in the BIOS.

---

### Post by ajgreeny on 2009-11-03
I would think it is a bios setting; the system is going to the partition where grub is installed, instead of the usb where you have the (live?) ubuntu.

---

### Post by RndmGuy06 on 2009-11-03
> **JBAlaska said:**
> Not sure about your netbook, but most computers need to have "allow to boot from usb" (Or some such) and usb before the HD in the boot order set in the BIOS.

Thanks I had done that and those are still my settings in the BOIS. But it would not recoginze any boot usb drive ie, Ubuntu, Moblin, or a Windows repair disk.  

I have a built in card reader so I just created a "Boot Card" lol or whatever you want to call it. It finally recognized it. So I am going to reinstall Ubuntu and then go from there...so far so good.

---

### Post by RndmGuy06 on 2009-11-03
> **ajgreeny said:**
> 

I've just noted you used 9.10, which has grub2 and not all tye files needed for grub are in the /boot/grub folder, as they were in legacy grub (9.04 and earlier), so my idea may still not work, I'm afraid, though my knowledge of grub2 is very limited, and I can't say it will not work with any certainty.  The old menu.lst file is now replaced with a grub.cfg file, which needs other files located in /etc to be produced in the first place, but once there it may be fine for the windows boot, even though the other files are no longer present (if you remove the ubuntu partition).

K I finally got a boot device to recognize and I am going to reinstall Ubuntu. 

What exactly did you want me to do? Create a another partition ~500 mb that is /boot and the rest as normal on my larger 60gb section?

---

### Post by HandLotion on 2009-11-03
Go into your system's bios and remove the hard drive as a boot from device.  I've never booted from a usb device, but six months ago when I first installed ubuntu (and then deleted that partition) I had to do this to allow me to boot from the cd/dvd device.  For whatever reason the bios always read the MBR from the hard drive which contained the grub loader - even when I told it to try the cd/dvd device first.

---

### Post by RndmGuy06 on 2009-11-03
> **HandLotion said:**
> Go into your system's bios and remove the hard drive as a boot from device.  I've never booted from a usb device, but six months ago when I first installed ubuntu (and then deleted that partition) I had to do this to allow me to boot from the cd/dvd device.  For whatever reason the bios always read the MBR from the hard drive which contained the grub loader - even when I told it to try the cd/dvd device first.

Thank you. I had tried that earlier but it gave weird errors. I actually have two sets of options in BOIS. One that is boot order (like every other computer I have ever used) and then a hard drive order. The only two options in the hard drive order section is my flash reader and my hd.

I was able to get the ubuntu live cd to run via the built in memory card reader.

---

### Post by RndmGuy06 on 2009-11-03
I was able to get Ubuntu reinstalled with the help of everyone! Now I get to figure out to remove it...sad I know but I am still full time Ubuntu on my Desktop!  Another day I'll tackle that project, I have had too much fun troubleshooting for one week...

[sigh of relief]

---

### Post by ajgreeny on 2009-11-03
You will only be able to remove the ubuntu partition using a live usb system, ie your card reader.  You can not do it from ubuntu that is installed.  I suppose you could do it from windows, but to be honest, I have forgotten how to do almost everything on that now, so can't tell you exactly how.

---

### Post by RndmGuy06 on 2009-11-04
Thanks, I appreciate everyone's prompt advice!  It helped the whole process along :)

---

