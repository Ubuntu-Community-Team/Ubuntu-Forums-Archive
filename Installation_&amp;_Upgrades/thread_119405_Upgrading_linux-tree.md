---
title: "Upgrading linux-tree"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2006-01-19
Did the latest upgrade really just overwrite my /boot/grub/menu.lst???

I can't even find a backup of my old menu.lst from which I can copy the boot parameters for Windows and Gentoo.  I believe the upgrade overwrote menu.lst~ as well, which happened to be my backup.  I'm quite a bit displeased about this -- that was rather inconsiderate seeing that now I have to research again what lines I have to put in to boot those two OS's.  Am I hallucinating???

If I'm not hallucinating, this needs to be fixed immediately.  I was starting to feel like Ubuntu was a good Windows alternative, but it can't be with something like that -- if this happened to my mom she'd be upset because the computer wouldn't even boot since it changed all the (hd0,4) statements to (hd2,4).  There is *not* a simple and fast solution for fixing this problem if you're not computer savy.

On a side note, a comment should be added to the Ubuntu guide to explain grub a bit better.  When I first started with Ubuntu, I had serious booting problem because my device.map didn't agree with the boot order of my hard drives, which is how grub interprets them.  It wrote (hd2,4) when all of them should've been (hd0,4).  It took me a few days to figure that out.

Casper...

---

### Post by citronmg on 2006-01-19
Hey, I just saw your post after posting a similar problem...

---

### Post by lha on 2006-01-19
[QUOTE=casperlingus]Did the latest upgrade really just overwrite my /boot/grub/menu.lst???

I can't even find a backup of my old menu.lst from which I can copy the boot parameters for Windows and Gentoo.  I believe the upgrade overwrote menu.lst~ as well, which happened to be my backup.  I'm quite a bit displeased about this -- that was rather inconsiderate seeing that now I have to research again what lines I have to put in to boot those two OS's.  Am I hallucinating???

If I'm not hallucinating, this needs to be fixed immediately.  I was starting to feel like Ubuntu was a good Windows alternative, but it can't be with something like that -- if this happened to my mom she'd be upset because the computer wouldn't even boot since it changed all the (hd0,4) statements to (hd2,4).  There is *not* a simple and fast solution for fixing this problem if you're not computer savy.

On a side note, a comment should be added to the Ubuntu guide to explain grub a bit better.  When I first started with Ubuntu, I had serious booting problem because my device.map didn't agree with the boot order of my hard drives, which is how grub interprets them.  It wrote (hd2,4) when all of them should've been (hd0,4).  It took me a few days to figure that out.

Casper...[/QUOTE]

Yes it did overwrite **a part** of your menu.lst. There is no reason to alter this behaviour as this exactly as it is supposed to do.

Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=119512"). citronmg has the same problem as you. Instructions to fix your problem are there. The reason your Windows entry vanished is also described there. If you need further help, post output of
```
cat /boot/grub/menu.lst
``` here.

Further info on "the cause of this issue" can be found with
```
man grub-update
```

---

### Post by casperlingus on 2006-01-19
Okay, well that is unfortunate.  I did not realize that what falls between 

*### BEGIN AUTOMAGIC KERNELS LIST*

and 

*### END DEBIAN AUTOMAGIC KERNELS LIST*

is fair game for grub-update to erase.  I thought those tags were for *users* to identify where it has been automatically created.  I didn't realize that an upgrade will automatically delete what's between them.  

Of course, it's written right there in the comments.  Still, a warning would've been nice.  Or perhaps a time-stamped backup instead of overwriting the backup already in that directory....

It's going to be a pain to recall how to write the gentoo boot line...

Casper...

---

### Post by lha on 2006-01-19
[QUOTE=casperlingus]Okay, well that is unfortunate.  I did not realize that what falls between 

*### BEGIN AUTOMAGIC KERNELS LIST*

and 

*### END DEBIAN AUTOMAGIC KERNELS LIST*

is fair game for grub-update to erase.  I thought those tags were for *users* to identify where it has been automatically created.  I didn't realize that an upgrade will automatically delete what's between them.  

Of course, it's written right there in the comments.  Still, a warning would've been nice.  Or perhaps a time-stamped backup instead of overwriting the backup already in that directory....

It's going to be a pain to recall how to write the gentoo boot line...

Casper...[/QUOTE]

About your "backup". It is common for programs to make temporary backups of files you are editing and save them as filename~. So when opened that menu.lst for editing, your text editor probably overwrote menu.lst~ with menu.lst to protect your hard work on menu.lst in case the process should be terminated unexpectedly.

Does your Gentoo has a menu.lst? You could look there...

---

### Post by casperlingus on 2006-01-19
Heh, no it doesn't.  When I installed Gentoo I just skipped over dealing with grub, and configured Ubuntu's bootloader to deal with Gentoo.  It's not *that big of a deal,* just inconvenient.  

I store my backups as file.whatever~ because I've seen Ubuntu do it before and I figured that was a common convention I should use.  Apparently non-conformist was the way to go in this case.  Oh well.

Casper...

---

### Post by matrooswolf on 2006-01-20
Hi, I have the same problem.  Updating the kernel changed the grub menu.lst from root(HD 1,5) to (HD 1,6) and kernel /vmlinuz-2.6.12-10-386 root=/dev/hdb6 to hdb7.  I have no idea why.  This is the second time this happened.  The first time I was in panic, I couldn't boot, didn't know what was happening, got a Error 17: cannot mount selected partition.  It took me days to figure out that the partition numbers in grub had changed (who would think of that?) and how to change it back.  Second time, I updated the kernel, but changed the grub menu.lst back before rebooting ;) and everything worked fine.  But I am feeling the same as casperlingus: - if this happened to my mom she'd be upset!!!!  I cannot recommend Ubuntu to my students if things like this happen ...
(I am quite new to Linux)

---

### Post by matrooswolf on 2006-01-20
Hi, I have read the citronmg thread, and I hope it fixed my problems for the next upgrade.  But a question remains, why did my grub list get messed up in the first place?
What I think could be at the root of the problem, (but I have no idea), some time ago, I changed a partition on my first harddisk from linux to FAT32, to exchange files between my Windows setup and Ubuntu, I had a lot of problems doing that, tried it in Windows, tried it in Ubuntu, (unfortunatly, I don't remember exactly how I fixed it).
Anyhow, it is a very strange and annoying problem, very easy to repair, very difficult to find.  It reminds me too much of Windows :( 
Thank God for these threads!

---

### Post by lha on 2006-01-20
[QUOTE=matrooswolf]Hi, I have read the citronmg thread, and I hope it fixed my problems for the next upgrade.  But a question remains, why did my grub list get messed up in the first place?
What I think could be at the root of the problem, (but I have no idea), some time ago, I changed a partition on my first harddisk from linux to FAT32, to exchange files between my Windows setup and Ubuntu, I had a lot of problems doing that, tried it in Windows, tried it in Ubuntu, (unfortunatly, I don't remember exactly how I fixed it).
Anyhow, it is a very strange and annoying problem, very easy to repair, very difficult to find.  It reminds me too much of Windows :( 
Thank God for these threads![/QUOTE]

This repartitioning must be the cause of your problems. Some partitioners change the numbering of logical partitions when repartitioning. This is because Windows gets confused if logical partitions are not in order.

---

