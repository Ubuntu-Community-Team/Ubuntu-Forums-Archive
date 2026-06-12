---
title: "Problem!. installing Jaunty on laptop"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by xkuruma on 2009-05-15
Hello everyone!,  well here's the deal.   i have a Compaq Presario laptop ( a bit old) ( AMD Sempron @ 1,8ghz,   512mb RAM  )   and I'm trying to install Ubuntu Jaunty on it. 
Well i insert the Live cd, i choose install ubuntu, it starts to load, and after a few minutes it starts to show a huge list with errors and stuff, here's a picture of what's happening:





[IMG]http://s3.subirimagenes.com/fotos/2545069img0011.jpg[/IMG]







Any suggestions i could try ??
thanks!!

bye :P

---

### Post by abn91c on 2009-05-15
you cdrom drive may need a good cleaning, the cd itself may be a bad burn, try burning on a scratch free cdrom at slow speed, also use the "try ubuntu" option first if you go straight into install you get those kind of problems, the live cd option will give you a change to test ubuntu, then if all hardware works click on the install button.

---

### Post by grungedoobie on 2009-05-15
The optical drive is a good place to check, but if you have another bootable disk, try that one also to see if the drive really is the problem.

Another place I've seen a problem like this is with Windows XP.  Microsoft never put effort into adopting proper 64 bit device drivers for their 32 bit XP operating system.

Thus, there was an option placed in bios for 32/64 bit compatibility.  Sometimes the 32/64 switch is hidden as a drive option like IDE/SATA.  I Worked on a Dell dual core true 64 bit and the 32/64 switch was hidden there.  I've run into this problem with XP on numerous occasions even with today's machines.

If you're already running XP on the drive and are wishing to make it dual boot, I'd suggest the x86 alternate install for your laptop.  With as little RAM as you have available, I'd stay away from 8.10.  8.04 is the most stable and most mature.  9.04 is highly reliable, but may need to mature a little more if this is your first time.

These suggestions are not a guaranteed work for your hardware.  Just suggestions.

Other tips:

If your laptop has a high speed hard drive (anything faster than IDE) with XP as the current or prior install, then you may have a very hard time.  Microsoft and their buddies never fixed the HDD and bus drivers to run properly with XP on anything faster than IDE.  In this case, the hard drive is forced to use a format which is useless to any other operating system.  I've run in to that problem on several occasions as well.

If the laptop had crashed and burned unexpectedly or unanswerably (or if you got it really cheap or as a freebee), I've also seen that error when the RAM has been partially cooked.  Use the memtest if you are able.  You usually don't have to wait long as in most cases, when something is wrong with RAM, you'll see errors in short order.

The live cd does not touch the hard drive until you prepare to make the install.  Therefore, while it is booting up, it runs the entire linux operating system from RAM.  If RAM is partially cooked, it ends up looking like a drive problem and spits out a bunch of I.O. errors.  (Also check the hard ware requirements for running the live cd of the distro you're working with.  An I.O. error report will occur when the operating system has run out of RAM.)

Luck to you, I hope you find the answers your looking for,


The Grunge.

---

### Post by xkuruma on 2009-05-17
thank you everyone ! :D

well, i was installing jaunty to have a dual boot, with a prior install of windows XP, and the disc i was using was  a DVD, into which i burned the Ubuntu image, (i had used that same disc for several installations on my desktop pc), and for some odd reason, it was giving me a hard time on the laptop,    i just burned the image into a cd and it worked immediately. :P


Thanks again ! :D

bye :P

---

