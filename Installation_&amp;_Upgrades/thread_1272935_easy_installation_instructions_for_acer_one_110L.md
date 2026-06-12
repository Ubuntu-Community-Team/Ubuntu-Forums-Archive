---
title: "easy installation instructions for acer one 110L"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by WhiteHorse007 on 2009-09-22
Does anyone know a link to an easy installation of unbuntu 9.04 on an Acer One 110L (the one with two separate mini drives of 8GB and no CD).

I've tried so many things. Ended up with two installations, one on each drive, the second drive only has the boot folder with grub.

I can never boot.

What is the best thing to do?

I was fed up with Windows on my Acer, but really the ubuntu 9.04  installation so far does not look like it's for a novice Linux user like me. 

Please prove me that I am wrong and that I was right to switch to ubuntu!!! ;)

Thanks!

---

### Post by tgeer43 on 2009-09-22
I don't see anything about your Acer that would prevent you from running Ubuntu and many folks are running the Netbook Remix without difficulty. So what are these "so many things" that you've tried and what exactly is the problem when you do try an install? "I can never boot" is a bit too vague for us to help. Provide a little info and we'll see what we can do but before you do try a google search for "Ubuntu Acer One 110L" and you'll see what others' experiences have been.

tgeer

---

### Post by WhiteHorse007 on 2009-09-23
I'm sorry, I can't write the whole process down. I did not take notes. As you wrote, many have made the installation successfully.

This is not my case.

I can only tell you what is the current status of my Acer One.

[IMG]file:///tmp/moz-screenshot-3.jpg[/IMG]BTW, I am using the flashdrive with ubuntu image to run as "demo". Forgive me if my terms are not exactly right, I'm French speaking and totally unfamiliar to Linux.

I can see my first drive and here is the list of folders (I tried screenshots, but there is no way I can save to files, so I have to write text instead!):
bin, games, include, lib, local, lost+found, sbin, share, src, X11R6.

My second drive contains the following folders:
bin, boot, cdrom, dev, etc, home, lib, lost+found, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var. It has the following files: initrd.img, vmlinuz.

The boot folder contains: folders grub and initrd.img-2.6.28-11-generic and the following files:
/media/disk-1/boot/abi-2.6.28-11-generic
/media/disk-1/boot/config-2.6.28-11-generic
/media/disk-1/boot/initrd.img-2.6.28-11-generic
/media/disk-1/boot/memtest86+.bin
/media/disk-1/boot/System.map-2.6.28-11-generic
/media/disk-1/boot/vmcoreinfo-2.6.28-11-generic
/media/disk-1/boot/vmlinuz-2.6.28-11-generic

In my posting I asked for links to easy installation procedures, I add to this is there any link to help for my case?

As you see, it looks like ubuntu installed properly on my secoond drive but when I boot, it does not start. No bootable or something message... Is there a way to boot from the second drive. I tried intercepting and change drive with F2 at startup, it still recognize no bootable information.

Thanks for taking the time to look at my case. Please don't be offended by my lack of knowledge of ubuntu.

---

### Post by tgeer43 on 2009-09-26
I had prepared a somewhat lenghty reply yesterday but apparently neglected to hit the 'Submit' button. :(

Since you don't have anything of value on either drive I think your best bet at this point is to just wipe both drives and try another installation on the first drive. I'm not sure why you got a partial installation the first time around but the second attempt (one the 2nd HD) did look to be complete judging by the directories that were created. Since you were able to do this then I see no reason why you should have any major difficulty getting Ubuntu installed to the first drive.

If you can get the basic installation done then we can deal with any further issues as they arise.

Give it another shot and let me know how it turns out. If you run into problems during the installation then take note of what was going on just prior to the error and write down any error messages that are generated.

Good luck,

tgeer

---

### Post by WhiteHorse007 on 2009-09-29
Hi Thanks for your encouragement to try again. This time it worked.

I had probably messed up at the stage where disk space was prepared.

This time I used the entire disk: SCSI2 (0,0,0) (sda) - 8.1 GB ATA.

I still have to install software for reading wav and mp3 files, I guess that should be easy.

Thanks again! :)

---

