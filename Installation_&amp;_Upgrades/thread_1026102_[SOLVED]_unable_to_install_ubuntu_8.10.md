---
title: "[SOLVED] unable to install ubuntu 8.10"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Jimi180 on 2008-12-30
Complete Linux novice btw. I'm currently running Vista and have just added a second SATA hd which I would like to install ubuntu on to. Downloaded the iso and installed it to my second clean hd via wubi, when I boot I get the option of vista or ubuntu, if I select ubunto I get the error code 0xc000000e and it says something about wubildr.mbr and won't boot, though vista is still fine.

I uninstalled it and reformatted the drive, burned the iso to a CD and booted from my DVD drive, I get a screen with the ubuntu logo, select english from the list and they select the install option, an orange bar goes back and forth for a bit then the screens go black and a load of white text starts scrolling up, most lines said something about "error" and "bad request" - I left this and it continued for about 45 mins before I gave up, on a couple of occasions I got one dark blue screen and the other had multi colour vertical lines. I've tried the first option (forget what it was called now, the option to just run ubuntu and then install from within there) and get the same problem. I've tried burning different discs at different speeds with different iso burner software and nothing works :( I d/l kubuntu and have exactly the same problem.

I've spent ages scouring google and forums for a resolution but can't find anything, is there any way I can install ubuntu on to my second hd and have the option of which OS to boot? PC specs are:

AMD Athlon64 X2 dual core 4400
2gb RAM
nvidia GeForce 6600GT

Dell PC

Thanks for any help :)

---

### Post by gettinoriginal on 2008-12-30
You might find this helpful:  :P

[http://ubuntuforums.org/archive/index.php/t-395150.html](http://ubuntuforums.org/archive/index.php/t-395150.html)

---

### Post by zaveloff on 2008-12-30
I am having a similar problem trying to install Ubuntu 8.04.1 desktop edition on a Dell Inspiron 530 Quad core with 3 GB of RAM and two 500 GB hard disks. I have Vista on one and am trying to install Ubuntu on the other. am using a CD that I ordered because I was having the problem using a downloaded version and thought that that might be the reason. I get the same result with either, however. I have tried installing clean, installing in Windows (Vista, although I had the same problem with XP), and running from the CD. In each case, I get the endless error messages.

---

### Post by zaveloff on 2008-12-30
> **gettinoriginal said:**
> You might find this helpful:  :P

[http://ubuntuforums.org/archive/index.php/t-395150.html](http://ubuntuforums.org/archive/index.php/t-395150.html)

Your link is useless with regard to this problem. You have to be able to install Ubuntu first!

---

### Post by Jimi180 on 2008-12-30
I've got a Dell Dimension, probably just Dell :rolleyes: I've read all the FAQ's I can find but can't seem to find a solution anywhere :confused:

---

### Post by gettinoriginal on 2008-12-30
As the first sentence says, install on disk with only one disk connected.  When you insert your disk, it is trying to install to the windows drive, not your external.

---

### Post by Jimi180 on 2008-12-31
success! I downloaded the AMD 64 alternate CD and it installed, only problem is it won't boot :( I've tried booting with just the Linux hd connected and with both after using EasyBCD but both times it fails and says to insert the CD. Couple of things, both hd's are connected but I can only see my Vista one under my computer, although it shows up under disk management. Any ideas? thanks.

---

### Post by Jimi180 on 2008-12-31
Cannot load from harddisk
insert systemdisk and press any key

^^ thats what it says when I try and boot ubuntu

---

### Post by zaveloff on 2008-12-31
> **gettinoriginal said:**
> As the first sentence says, install on disk with only one disk connected.  When you insert your disk, it is trying to install to the windows drive, not your external.

In my case, it doesn't try to install to the Windows disk (both of mine are internal by the way). It doesn't get that far. Even if it did, I have empty space to install on that disk too. Also, it won't install in Windows either.

---

### Post by Jimi180 on 2009-01-01
I managed to completely screw everything up and couldn't even get in to Windows :D but it's all fixed now, if I was to download an older version of ubuntu, can you upgrade to 8.10 from within the OS? and so bypass and possible problems installing this version from CD? (I don't know if an older version would even work anyway, only thing I can think of doing as I've tried everything else)

---

### Post by Jimi180 on 2009-01-02
fwiw, afraid this won't help you though zaveloff as you ordered a CD, I finally solved my problem by using my laptop to burn the iso and it worked perfectly, I guess the writer in my desktop must have been creating dodgy disks. I still had problems after that, but after removing my second monitor all was fine. Now marking this thread solved.

---

