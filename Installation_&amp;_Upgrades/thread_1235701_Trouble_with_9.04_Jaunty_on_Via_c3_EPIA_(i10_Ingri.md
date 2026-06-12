---
title: "Trouble with 9.04 Jaunty on Via c3 EPIA (i10 Ingrian EdgeSecure)"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by scprotz on 2009-08-09
Hi All,

I am trying to install Jaunty on a Via C3 EPIA - ITX mainboard in an Ingrian i10 EdgeSecure computer.  I am trying to start with a command-line only install first, and so tried both the Server and the Alternate CDs.  What happens is after installation and reboot, I can log into the system (if I'm fast enough) but after a while the whole system locks up/freezes/hangs.  If I try to run anything in apt-get, it will almost always hang (unless the apt-get is very small)

I have also noticed that when using the rescue CD, I've left it overnight, done tons of apt-get and have never once experienced any instability in the system.  I have never had it lock up once using the 'rescue' off the server or alternate CDs.

Things I have tried based on comments in the forum already:

1) create an aliases.conf file in /etc/modprobe.d and add "alias longhaul off".  Some have stated that this cures oddness with C3 systems - does nothing for me though.

2) apt-get install linux-386 (Some have stated that backing down the kernel such that cmov instruction isn't included may make this work better as well) - this also doesn't change the system and I still have instability (also, oddly enough, I do the *install linux-386*, and do a *remove linux-generic,* and yet a *uname-a* still shows the system as being a linux-generic i686 - is that correct? or does linux-386 not update uname?

Ideally, I'd love for someone who has this working on a similar system to show me how to get it working.  Also I installed Windows (yeah..I know..) just to see if the system would hang, but needless to say, Windows performed (in its windowy way) just as it was supposed to.

Other specs of the Via C3 EPIA box:
40 GB ATA hard drive
192 MB PC133 memory
Rhine 100MB ethernet
Sound card (unknown - but integrated on the board - currently turned off in bios, just in case)
Video ( unknown as well - integrated into mainboard)

Any help would be greatly appreciated.

Thanks so much.

---

### Post by phillw on 2009-08-09
Is it stable if you boot into live-cd and use that, as opposed to the install ?

Phill

---

### Post by scprotz on 2009-08-09
Yes, I can run from a live CD.  As a matter of fact, I think I may have gotten it fixed (running for 4 hours now and no crash).
 
So apparently my step #2 actually does work - BUT - I forgot to tell grub to use the linux-386 kernel (so it was still booting with the linux-generic kernel).  On reboot I took the time to tap ESC once, and lo-and-behold, there was my 386 kernel I installed (#3 on the list).  After testing the new kernel for a bit and a quick trip to /boot/grub/menu.lst and setting the default to '2' (since we are counting from 0), this let me boot right up into my new kernel all the time.
 
Now I have everything working, a lightweight X in place, Firefox running, apt-get working fine, and no lockups/crashes. (X is just a bonus for me to play around with..this thing is a set-top-box..heh..needed it more for running USB drivers and a web server..but hey..it has the horsepower and plenty of left over disk space..so why not...)
 
Hope this helps anyone else who runs across the Via C3 EPIA.
 
My steps:
 
1) install Server or Alternate
2) reboot and run rescue disk (choosing shell on hard drive)
3) apt-get install linux-386
4) boot with grub again, hitting ESC and choose the linux 386 kernel
5) go to /boot/grub/menu.lst and modify so that the 386 kernel is the default
6) have fun with new working system.

---

### Post by fookite on 2009-08-25
> **scprotz said:**
> Yes, I can run from a live CD.  As a matter of fact, I think I may have gotten it fixed (running for 4 hours now and no crash).
 
So apparently my step #2 actually does work - BUT - I forgot to tell grub to use the linux-386 kernel (so it was still booting with the linux-generic kernel).  On reboot I took the time to tap ESC once, and lo-and-behold, there was my 386 kernel I installed (#3 on the list).  After testing the new kernel for a bit and a quick trip to /boot/grub/menu.lst and setting the default to '2' (since we are counting from 0), this let me boot right up into my new kernel all the time.
 
Now I have everything working, a lightweight X in place, Firefox running, apt-get working fine, and no lockups/crashes. (X is just a bonus for me to play around with..this thing is a set-top-box..heh..needed it more for running USB drivers and a web server..but hey..it has the horsepower and plenty of left over disk space..so why not...)
 
Hope this helps anyone else who runs across the Via C3 EPIA.
 
My steps:
 
1) install Server or Alternate
2) reboot and run rescue disk (choosing shell on hard drive)
3) apt-get install linux-386
4) boot with grub again, hitting ESC and choose the linux 386 kernel
5) go to /boot/grub/menu.lst and modify so that the 386 kernel is the default
6) have fun with new working system.

Hey scprotz, how's that box working out for you? There's a bunch on ebay and I was thinking about picking one up to turn into a set top box. What kind or performance are you getting?

---

### Post by oziemike on 2009-08-29
OK I bought one of these to play around with and I can't for the life of me find out how to get into the BIOS?? Is there some trick at boot time to get in there?? Mike.

---

### Post by cdonjenkins on 2009-08-31
According to the manual available here.

[http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=21](http://www.via.com.tw/en/products/embedded/ProductDetail.jsp?id=21)

Hold down the <del> key during the boot process.

---

### Post by oziemike on 2009-08-31
Thanks for that and the url for the board data. I am trying to boot the box with an external USB DVD/CDROM. No luck there either. Same drive works off any other other PC. I do note that there really doesn't seem to be provision in the BIOS for an external USB DVD drive to boot from. Again appreciate any comments.

---

### Post by cdonjenkins on 2009-08-31
> **oziemike said:**
> Thanks for that and the url for the board data. I am trying to boot the box with an external USB DVD/CDROM. No luck there either. Same drive works off any other other PC. I do note that there really doesn't seem to be provision in the BIOS for an external USB DVD drive to boot from. Again appreciate any comments.

I have one on order from Ebay and my plan is to take the cover off and plug and old DVD drive into the extra IDE channel. Then after the install I have an USB powered DVD I can plug in as needed. Only drawback is the USB 1.1 ports. May Add a USB 2.0 PCI card via some kind of home made riser.

---

### Post by oziemike on 2009-09-02
Yep, using a desktop type DVD/CD did the trick. I now have the OS on the box.

Thanks for your help guys. Mike.

---

### Post by ronald.wigman on 2009-09-26
Hi,
This is great. 
It also is the solution for a VIA C3 Samuel2 with the VIA CLE266 chipset.
I have been looking for a solution for a few weeks now.
Cheers,
Ronald

---

