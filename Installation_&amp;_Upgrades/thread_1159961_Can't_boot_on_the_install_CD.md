---
title: "Can't boot on the install CD"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by pieroxy on 2009-05-15
Hi,

I burned the install CD for Jaunty and whenever booting on the CD, I can see the menu and then select whichever options that I choose, I see the CD that starts booting (Ubuntu logo and the moving progressbar) and after a few seconds I get a BusyBox shell. Apparently it cannot mount the root fs because as soon as I leave the shell I get an error message saying that it cannot mount /newroot.

Whenever I try to mount the newroot myself in the busybox shell I get the error message "Invalid Argument"....

I also burned a SystemRescueCd (v1.2.0) and the CD reacts exactly the same. I tried to boot these CDs on three different machines just to get the same result...

Aditionnally my HDD-based install of Jaunty does the same since a couple of days, just after having installed the package fglrx for my ATI gc, I had to hard reset the machine... I checked the FS of my root partition but it is fine (ext2fs -f didn't report anything wrong)

I tried a CD with Ubuntu 8.04 and it boots perfectly fine on all three machines....


Is it something with the new kernels? Can anyone help over here? 

Thanks in advance!

---

### Post by 73ckn797 on 2009-05-15
Old question but what speed did you burn the disks at. Did you verify the md5sums for the downloaded files and run the disk check from the CD boot menu?

---

### Post by pieroxy on 2009-05-15
I don't know how to verify the md5sum from windows (that's my second machine, still up and running...). I tried to take all the files from the CD and copy them to a folder on my HDD with success though. That said, this cannot explain my HDD failure ;-)

Verifying the CD from the CD boot screen gives me the same BusyBox ...

I will try reburning the CD tonight though. Will keep you posted.

---

### Post by 73ckn797 on 2009-05-15
Burn the CD at the lowest speed.

Google doing the md5sum via Windows. You ought to be able to find something out.

Try this quick link I found: 
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

In Ubuntu terminal you would use this basic command adding the path to the iso file you are checking.
```
Terminal command:  md5sum ubuntu.iso 
```

[http://releases.ubuntu.com/9.04/MD5SUMS](http://releases.ubuntu.com/9.04/MD5SUMS)
```
3b5e9861910463374bb0d4ba9025bbb1 *ubuntu-9.04-alternate-amd64.iso
c564ae16dffb51a922aef74a07250473 *ubuntu-9.04-alternate-i386.iso
cace6ea9dde8dc158174e345aabe3fae *ubuntu-9.04-desktop-amd64.iso
66fa77789c7b8ff63130e5d5a272d67b *ubuntu-9.04-desktop-i386.iso
8f921e001aebc3e98e8e8e7d29ee1dd4 *ubuntu-9.04-netbook-remix-i386.img
78cf52114804f80576b0bfc8f5984339 *ubuntu-9.04-server-amd64.iso
20480057590ff8b80ad9094f40698030 *ubuntu-9.04-server-i386.iso
5e6f6acf2105c366db2f9727e2a65d03 *wubi.exe
```

---

### Post by pieroxy on 2009-05-16
Right on spot, thanks. I burned the image again with another burner and it now works like a charm. I took this opportunity to do a fresh Jaunty install, and goodbye problems with the ATI X drivers and my sound drivers.

Thanks a bunch. I'm still appalled that I thought of the content of the CD instead of the CD itself when I tried it on three computers with the same result...

Anyway, thanks a lot for the help.

Anyone knows how I can mark the thread as fixed? I used to know these things, bu I can't see the option anywhere anymore....

---

