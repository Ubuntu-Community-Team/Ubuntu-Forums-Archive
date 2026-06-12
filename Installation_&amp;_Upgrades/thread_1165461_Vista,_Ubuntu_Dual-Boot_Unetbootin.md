---
title: "Vista, Ubuntu Dual-Boot: Unetbootin"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by juice43 on 2009-05-20
Just joining the forums, so hello everybody.

I have Vista installed on my computer as my primary OS. I have used Ubuntu for some time now in Wubi, but I feel like I want to take it to the next step apart from Windows, because last time that my Windows partition got messed up so did my Ubuntu. I don't want to burn a cd or dvd, but instead I want to install from the harddrive. I've heard about Unetbootin which could be done without any cd. The issue is that any guides on the internet all refer to using a USB (which I have but only 512 mb), but I don't know the exact procedure for hard drive install. I know what I'm doing but I just don't have the exact resources for this kind of thing.

My questions are whether I can keep the ISO (I already have one on disk) in my windows partition for the install and just need to create a partition for Ubuntu, or if I should have three partitions: one for the ISO, the Vista one, and for Ubuntu? Also does the Unetbootin installer allow me to choose option like regular Ubuntu install (I would like to set up a few things, esp. Colemak, which I use as my keyboard layout)

Thanks in advance guys

---

### Post by Mark Phelps on 2009-05-21
Using the info in the link below, you can "move" your Ubuntu installation into its own partition without having to remove and reinstall it:

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by juice43 on 2009-05-21
Well, my issue is that I didn't know that this was possible and thus removed my Wubi install, while just backing up any of my documents there to Windows. So as of now I don't have Wubi installed. Is there any way to install without CD or USB easily? Or should I just reinstall Ubuntu in Wubi and then use LVPM to make it a real partition?

---

### Post by snowpine on 2009-05-21
Have you considered reading the instructions on the Unetbootin web page?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by juice43 on 2009-05-21
Yes, but I don't exactly the procedure for harddrive install, because mostly gives detail for a USB install. I don't know if I need a different partition for the ISO, or just the one for Ubuntu...and also I want to know if there is a during install customization?

I really don't want to just wing it, because I do not want to mess with my Vista configuration which is doing fine. I just want to have a dual-boot, to get the best of both worlds.

---

### Post by snowpine on 2009-05-21
You would typically customize your system (for example installing Colemak) once Ubuntu is installed.

> **juice43 said:**
> Yes, but I don't exactly the procedure for harddrive install, because mostly gives detail for a USB install. I don't know if I need a different partition for the ISO, or just the one for Ubuntu...and also I want to know if there is a during install customization?

I really don't want to just wing it, because I do not want to mess with my Vista configuration which is doing fine. I just want to have a dual-boot, to get the best of both worlds.

The best advice I can give you is don't do anything until you have carefully read and understood the instructions at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) They have an FAQ, they have a wiki, they have a forum. I am not trying to be a smart aleck, but are you going to follow instructions from a random stranger  (me) or from the official website? What if I leave out an important step and your system gets hosed?

For example, if the official instructions do not tell you to make a new partition for the ISO, then don't do it, no matter what I tell you. ;)

A word to the wise, though... back up everything important on your Vista partition first! I cannot stress how important that is. If you still are not sure what to do after reading the Unetbootin documentation, Wubi is safer. Good luck!

---

### Post by juice43 on 2009-05-21
I guess I'll continue to take Wubi for a spin, and then upgrade with LVPM (which with the documentation, I understand quite well), if I have the chance over the Memorial Day weekend. That should be a bit safer for me, since I understand it. 

Thanks for the help guys.

---

### Post by juice43 on 2009-05-24
More problems in UbuntuLand. 

Well, I installed Wubi, and configured everything the way I wanted it to be, using it all day yesterday. Then at night, I used the Partition Manager tool, to create a swap and ext3 partition. Then using LVPM I transferred the Wubi, to those partitions. It worked flawlessly, except for the fact that I got an error 17, which I quickly fixed by changing the root in the GRUB from () /ubuntu/disks to root (hd0,1) which I found using find /boot/grub/stage1.

The real issues came this morning after I removed Wubi on Windows. I got the error 17 again. I figured that it would be fixed, just by changing the root again, but it seems that the kernel and initrd are still trying to be detected in Wubi, because I get an error 15: file not found. I am getting a /host/ubuntu/disks/root.disk does not exist. I don't know what to edit at GRUB, and I've tried Super Grub on my USB, using Fix GRUB/Linux (it didn't work). I really had everything working on Ubuntu, is there any way to fix this (and remember that I can't burn any CD's and am limited to a 512 MB USB). 

How should I go about doing this?
Any advice is welcome, thanks in advance. (Ugh, I have to use Vista in the meanwhile...)

EDIT: I fixed the problem simply by editing the menu.lst at boot time. All I had to was change the kernel root directory to root=/dev/sda2. It worked perfectly. And I get to keep all my settings. Thanks for all the help, guys.

---

