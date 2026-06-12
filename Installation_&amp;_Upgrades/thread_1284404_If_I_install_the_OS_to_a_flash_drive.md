---
title: "If I install the OS to a flash drive"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by ki4jgt on 2009-10-06
If I install kubuntu directly to a flash drive, can I do it without messing up my boot proccess. I can't start the OS from the live cd, bc it keeps showing an error message.

---

### Post by mikewhatever on 2009-10-06
If Kubuntu doesn't run from cd, it probably won't run from usb too. You may need to deal with the errors first.

---

### Post by ki4jgt on 2009-10-06
After I get past the errors, then, if I install to USB, instead of the persistant install, will it mess with my boot proccesses? I wouldn't say they're errors, as much as the desktop stops loading after the little hard drive shows up on the splash screen and then three messages about crypto something display.

---

### Post by mikewhatever on 2009-10-06
There are two different thing that often get mixed up.
You can put an iso on the USB and then boot from it. That's not an installation and no, it will not mess with anything boot related.
You can also make a persistent installation on a USB stick, in which case, the boot loader is installed. If the boot loader is installed to a wrong place, it might cause boot problems.

---

### Post by bit mad on 2009-10-15
Can Ubuntu be installed on a harddisk partition, but with the bootloader on a USB stick?
I.e. no risk of messing up the usual boot process into Windows
and security : no-one can get into Ubuntu on the machine without the USB 'dongle' :)

?  :)

---

### Post by dabl on 2009-10-15
@bit mad, Yes, that will work.  You just need to do two things:

(a) -- be VERY certain that you know the /dev/sdx number of your USB stick, at the time that you click the "advanced" button on the installer, toward the end of the process, and tell it to install Grub to the MBR of the hard drive that you select, and

(b) set your PC BIOS to boot from USB first.

Kubuntu is no different than Ubuntu on this subject, but here's a reference from Kubuntu Forums:  [http://kubuntuforums.net/forums/index.php?topic=3089474.0](http://kubuntuforums.net/forums/index.php?topic=3089474.0)

---

### Post by bit mad on 2009-10-15
Thanks
I've done some research into partioning and I don't fully understand it, so I think I'd better leave it alone :)
I tried making sense of [http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-6.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-6.html) but maybe I'm just thick or something! The more I try to figure out what Primary/Logical means, and why you need to specify "do not use the partition" ?!!!
( [http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-4.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-4.html) )
... the more my eyes glaze over and I doubt I'll ever understand all this voodoo!

There's no way I'm meddling with anything like this without a clear understanding of what it's all about, so I'll have to keep looking for something that explains all these Ubuntu install options in language this moron can understand!

---

### Post by dreza on 2009-10-15
Heres a way to be sure you do not overwrite the MBR. SHutdown your system with the livecd already in. Open your computer case and unplug the harddrive, plugin your usb drive and start the computer. When it asks choose use entire drive as long as it only shows the usb drive. The OS and grub will both be on the stick, after its done reconect the harddrive and restart the computer. Change your boot priority so that it is CD< the usb drive, and then first HDD. The USB stick will show up as a harddrive by the way.


Yes this works great, there are other options but your worried about the MBR and this eliminates the issue. Also as long as you do not activate proprietary drivers you can use the stick on any computer simply by plugging it in, though you may have to open the boot menu to get it to do so.

---

### Post by bit mad on 2009-10-15
Thanks dreza, I'm going to have to do a fair bit more reading before I'm happy with all this, and I can't help wondering if I'll just give up :)

What is the point of this "do not use" option?! :confused:

[IMG]http://media.bestofmicro.com/Linux-Ubuntu-9-04,X-8-209852-13.png[/IMG]

---

### Post by ki4jgt on 2009-10-17
Thanks you guys this was very helpful. I've been wanting to do this ever since I heard about Ubuntu (2 years ago) but couldn't find a very good way of doing it. I was also wondering about how big a flash drive I would need. I have a 2 gig, and an another 2 gig sd card. I'm wanting to boot from the thumb drive, and then store my files on the sd card, while still being able to install ubuntu upgrades, as needed, and the persistant thing just wasn't working out. It kept forgetting my settings, so thanks.

---

