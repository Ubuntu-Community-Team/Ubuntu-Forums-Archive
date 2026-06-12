---
title: "can't revert to grub legacy"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by n00b512 on 2009-11-03
Ok, so I'm totally new to Linux making my first jump from Windoze.  So far an incredibly painful experience!!  I'm trying to dual boot with XP, using truecrypt.  There are instructions for this with the old grub, but no one knows enough about new grub to do it and after 4 days of trying I'm giving up.  If I can just get back to old grub the instructions should work fine, only I can't get the old grub.  I followed the instructions here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) But when I get to the part about apt-get install grub it says the package grub can't be found!  Yes I am connected to the internet.  What gives???  I'm so sick of this mess I'm ready to give Bill Gates all my money to provide with a slightly less awful experience.  I've posted 2 other threads and gotten 0 responses.

---

### Post by sliketymo on 2009-11-03
I used the forum search feature,and found this thread:

[http://ubuntuforums.org/showthread.php?t=1247994&highlight=revert+grub2+legacy+grub](http://ubuntuforums.org/showthread.php?t=1247994&highlight=revert+grub2+legacy+grub)

The search features are located at  the top of each page.Comes in handy sometimes.

---

### Post by n00b512 on 2009-11-03
> **sliketymo said:**
> I used the forum search feature,and found this thread:

[http://ubuntuforums.org/showthread.php?t=1247994&highlight=revert+grub2+legacy+grub](http://ubuntuforums.org/showthread.php?t=1247994&highlight=revert+grub2+legacy+grub)

The search features are located at  the top of each page.Comes in handy sometimes.

 Thanks.  I'd seen that previously, but it lists pretty much the same commands.  In any case apt-get is required for both and that is what's not working.  For some reason I'm able to do the apt-get from the live cd but not from the hd install of ubuntu, but even then it won't let me install grub onto sda.  I've pretty much run out of ideas and patience.  I'm going back to an OS I can understand.  Maybe ubuntu will get all the grub2 problems worked out and/or decent documentation so those of us who do have problems can work them out.

---

### Post by dazer26 on 2009-11-04
I followed these instructions to put grub legacy back on my laptop (grub2 would freeze).

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

As far as apt-get install grub not working, that is kind of strange.  Have you done a "sudo apt-get update"?  If your using wireless to connect to the internet, maybe try with an ethernet cord instead.  If your able to get into a graphical desktop, can you install grub using the package manager?  

edit: If you type "ifconfig" in a terminal does it show your network device as connected (with proper ip ect.)?  I just saw that you get internet on the live cd, if all else fails you can try to install grub from the live cd.  First you have to loginto you ubuntu install on your HD  the following link will tell you how to do it.
[http://ubuntuforums.org/showpost.php...2&postcount=10](http://ubuntuforums.org/showpost.php...2&postcount=10)

edit2: I have often had trouble with ubuntu not setting up grub properly, I dual-boot with XP and I have 3 sata hard drives (ubuntu on one, windows on another and music/video on third).  9.10 actually almost got it right, except I had my windows drive as the first to boot in my bios and ubuntu installed grub2 on my ubuntu drive, so after switching the boot order in the bios it actually dual booted perfectly.  Long story short, long ago I made a windows boot floppy just incase I couldn't dual boot or grub got completely messed up.  I have used it a lot over the years too lol.  Is this your first time trying Ubuntu?  IF so, i'd stick with it, as once you get things ironed out, it's well worth it.  Also i'd try ubuntu 9.04 as that seems to be a lot more stable at the moment and it still uses the old grub.  9.10 just came out so it will take a couple of months to patch all the bugs.  As well if you manage to upgrade from9.04 to 9.10 you will still be using the old grub with 9.10.  Good luck :)

---

### Post by wkulecz on 2009-11-04
Details of what went wrong are lacking, but my 9.10 install used ext4 by default which means if your install was to an ext4 filesystem you can't use legacy grub unless you setup a seperate ext3 /boot partition during the install.

Can you boot the live CD to poke around your installed partition and maybe try re-installing grub from there?

Dual boot with encrypted filesystems is not a great place to start.  I don't think Bill Gates supports Truecrypt either.

--wally.

---

### Post by dazer26 on 2009-11-04
> **wkulecz said:**
> Details of what went wrong are lacking, but my 9.10 install used ext4 by default which means if your install was to an ext4 filesystem you can't use legacy grub unless you setup a seperate ext3 /boot partition during the install.


My 9.10 install on my laptop is using ext4, and I downgraded to legacy grub with no problem (less problems actually).

---

### Post by n00b512 on 2009-11-04
> **dazer26 said:**
>  edit2: I have often had trouble with ubuntu not setting up grub properly, I dual-boot with XP and I have 3 sata hard drives (ubuntu on one, windows on another and music/video on third).  9.10 actually almost got it right, except I had my windows drive as the first to boot in my bios and ubuntu installed grub2 on my ubuntu drive, so after switching the boot order in the bios it actually dual booted perfectly.  Long story short, long ago I made a windows boot floppy just incase I couldn't dual boot or grub got completely messed up.  I have used it a lot over the years too lol.  Is this your first time trying Ubuntu?  IF so, i'd stick with it, as once you get things ironed out, it's well worth it.  Also i'd try ubuntu 9.04 as that seems to be a lot more stable at the moment and it still uses the old grub.  9.10 just came out so it will take a couple of months to patch all the bugs.  As well if you manage to upgrade from9.04 to 9.10 you will still be using the old grub with 9.10.  Good luck :)

  I think I like your idea best of all.  Just use the old 9.04.  Cuts out a lot of headache for me.  I have better things to do with my time than wrestle with an overcomplicated bootloader.

---

### Post by kansasnoob on 2009-11-05
> **dazer26 said:**
> My 9.10 install on my laptop is using ext4, and I downgraded to legacy grub with no problem (less problems actually).

+1! That's a misconception.

From the grub changelog:

> grub (0.97-29ubuntu51) jaunty; urgency=low

  [ Colin Watson ]
  * more_scsi_disks.diff: Add support for up to 256 SCSI disk devices on
    Linux (LP: #335174). Due to BIOS disk numbering only at most 128 can be
    bootable, so ensure we don't crash if there are more.

  [ Colin King ]
  *** ext4_fix_variable_sized_inodes.diff: Add support for ext4 variable**
    sized inodes (LP: #345488). This is backwardly compatible with ext2
    ext3 fixed sized inodes.

 -- Colin Watson <cjwatson@ubuntu.com>  Fri, 20 Mar 2009 16:12:22 +0000

The current version of grub in both Jaunty and Karmic will work with ext 4.

As to the OP's problem, if apt was not working something else must be borked. 

If it's simply a network issue, but networking works from the live CD, the Karmic /root partition can be mounted and chroot can be used to carry out the same procedure. I link to a brief description of how to mount and chroot in Appendix #1 of that guide.

---

