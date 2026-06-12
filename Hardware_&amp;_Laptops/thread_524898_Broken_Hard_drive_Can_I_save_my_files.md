---
title: "Broken Hard drive? Can I save my files?"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by t1m on 2007-08-13
A while ago I had a few problems with my hard drive, but running fsck  seemed to fix everything. Ubuntu ran fine for a while, then I started getting grub errors (number 18, and a few others).
Now I get various Grub errors when I turn the computer on or I get some Intel error message telling me to reboot or insert the correct type of media. Is there a way I can mount my hard drive so I can move my files over my network (I don't mind having to re-install Ubuntu if my files are safe)?
I have a fair number of important files and it would be very disappointing to loose them.
Please help.
Thank you.

---

### Post by dyous87 on 2007-08-13
Yes if you use the Ubuntu live cd you should be able to mount the hard drive and then save whatever is still intact on it. Good luck.

---

### Post by t1m on 2007-08-15
I actually did try to mount my hard drive from the live cd, but I wasn't  sure how to do that. I don't know the name (i.e. /dev/<somename>) of my hard disk. Is there a way to find that out?
Tnx

---

### Post by dyous87 on 2007-08-15
I believe it should be located under Places>Computer if not then after you load the live cd do:

```
sudo apt-get install gparted
```

then run gparted and see if your computer is picking it up at all. if it is not it is most likely completely dead.

---

### Post by t1m on 2007-08-18
After my first attempt to mount my hard drive from the live cd (before I wrote this thread) I turned the computer on, it seemed to boot (without showing anything on the screen), I assume that it did fsck and needed to reboot and then... it rebooted properly!!! I did a backup to another computer of */etc* and
 */home*.
I'm planning to reinstall ubuntu because I don't really fell like the hassle of trying to fix the problem another way. Are there any other files I need to backup so that I don't have to re-configure all of my programs with a new ubuntu?

---

### Post by dyous87 on 2007-08-20
all of your program options and configurations should for the most part me saved in your home folder. you can do ctrl h to view hidden files and they should all be there. for example, firefox stuff will be in the .mozilla folder and your gaim preferences and logs would be in the .gaim folder

---

### Post by t1m on 2007-08-20
Thanks.
Actually, I already re-installed Ubuntu, but I did have a backup of my home dir. I tried putting all of my old files (including the hidden ones) in my home dir, but somthing went wrong with the permissions. I had to delete my user and add it back. Now I just have my documents etc. and a few of the hidden files that weren't messed up.

Thanks again for your help! :KS

---

### Post by dyous87 on 2007-08-20
anytime, hope all goes well from now.

david

---

### Post by chickendude on 2007-10-25
When I load up the LiveCD and try to mount my old hard drive, it says that it is unable to mount it:
-device /dev/sda1 is not removable
-could not execute pmount

The drive is indeed detected, though... My computer isn't loading up (I have been getting [this](http://ubuntuforums.org/showthread.php?t=292533) error as it attempts to load) and I figure if I can just get some of my files off I don't have any issue just re-installing Ubuntu, however I haven't been able to figure out how to get these files off my hard drive!

Any help would be great :)

---

### Post by t1m on 2007-11-04
*Update:*

   I had forgotten about this post, so I should have written this earlier. I had tried re-installing ubuntu several times, but every time somthing would seem to get screwed up. I remembered that one time my mom had watered a plant on the computer desk (yes, that was not the best place to put it!), and the screen had gotten water inside of it. The screen made some pretty scary sounds, and the colors/size etc. got messed up! Thankfully we were able to let it "dry out" over night, and I'm using the same screen now. Anyhow, we came to the conclusion that the hard drive had been damaged then, which would make sense of all my troubbles with it. Thankfully, we had another harddirve availible which we re-installed ubuntu on, and the compueter has been running fine! Yipee!

The moral of the story is: don't put a flower pot above your computer!

---

### Post by dyous87 on 2007-11-04
hmm I see yes that is probably what happened then. Glad you got everything running well :)

---

