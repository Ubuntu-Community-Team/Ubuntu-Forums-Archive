---
title: "Duel Boot TROUBLE.  XP Pro with Ubuntu 5.10."
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by ubuntuforums on 2006-02-06
Hey guys.  I just downloaded the i386 ISO for Ubuntu 5.10 and I want to make it duel boot on my XP Professional system.  Anyway I figured it would be easy, so I opened up Partition Magic, resized my XP partition and put aside 10gb for Ubuntu.  I poped in my burnt cd with the iso of ubuntu 5.10 and restarted my computer.   Then the computer automatically booted to CD and I chose my language, keyboard setup, and I let it automatically partition the free space.  Then I let it install, after a minute or two the screen turned red and I got an error, so I clicked continue to try again, this time the screen turned read again and gave me the selection of three kernals, something like,, ubuntu i386, ubuntu image i386, and ubuntu image 2.1 something...  So I chose the first kernal and it gave me an error after just a little bit, so then I did it over again,, and so on till I tried all three kernals, still got an error.

So I said whatever, restarted my computer and removed the cd.  Then it checks for boot record from CD drive, then the the IDE hardrive, after the hard drive it says "...OK" then nothing, so I started to set up windows on the partition I made for Ubuntu, but when it restarted it showed BOTH OSes so I selected my old one and i booted right in.  So its fine now I guess, but I dont know why Ubuntu wouldn't installl...  Please help, thank you...

Specs for the sysytem im installing ubuntu on...
Intel Celeron 1.7GHz
768MBs of ram
Radeon 9600XT 256DDR
SoundBlaster Live! 24-bit 7.1
300W PSU...
40GB Maxtor hard disk driver...
LG 12x 8x 32x Recordable/Rewritable disk drive...

i think thats it for that system,,,

All help/comments are appreciated,, THANKS...  I want to install Ubuntu asap.  :)

---

### Post by ubuntuforums on 2006-02-06
bump...  Could someone please explain to me how I can install Ubuntu as the second OS on another partition of the same HDD as my Windows partition...    (lol)...  I did it all and it should work, but I get an error...

I'll be here waiting...  Thanks...

---

### Post by skirkpatrick on 2006-02-07
What was the error message from the Ubuntu install?

---

### Post by wallijonn on 2006-02-07
What I find is that the partition has to be completely blank, especially the disk label. So you may have to throw in a CDLive (or Slackware 9.0 CD) and run Linux's [COLOR="Red"]fdisk[/COLOR] or [COLOR="Red"]cfdisk[/COLOR] to completely erase all data and label. 

Since you are working with just a 10GB partition, it might be better to find an old disk (or get one on rebate, like a 80GB for $25 at CompUSA, CircuitCity, BestBuy, FryElectronics, when they go on sale for rebate. You can also usually buy old disks at your local State College or University Computer Surplus Store,) and install Ubuntu unto just that disk and write the boot record to the disk rather than to the first disk's MBR. Then you can select the OS through the BIOS. (It's a little more cumbersome but a lot more secure.)

---

### Post by skirkpatrick on 2006-02-07
I just changed my daughter's machine around.  Win98 on the primary drive, normal install.  Switched it to the slave channel and put her Ubuntu drive on as master.  Re-installed grub on the MBR of the Ubuntu drive and changed the Windows info in menu.lst to map the drives so that 98 thinks it's the first drive.  She ran into a problem about a month ago when she had XP as the first drive where XP decided to screw-up the MBR and I had a heck of a time trying to get Ubuntu back up.

---

