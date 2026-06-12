---
title: "2 hard drives installation"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by RxBandit256 on 2009-09-24
New to Ubuntu here, I recently installed through wubi n like what i saw, now i want to install it for good but still keep windows for games etc...my question is, i hav 2 hard drives, the main drive has windows on it, the second one basically has all my music, pics n a few programs but thats the drive where i want to install ubuntu to...will i run into a problem trying to install there? is there a chance of losing data?
thanks in advance for the help

---

### Post by raymondh on 2009-09-24
> **RxBandit256 said:**
> New to Ubuntu here, I recently installed through wubi n like what i saw, now i want to install it for good but still keep windows for games etc...my question is, i hav 2 hard drives, the main drive has windows on it, the second one basically has all my music, pics n a few programs but thats the drive where i want to install ubuntu to...will i run into a problem trying to install there? is there a chance of losing data?
thanks in advance for the help

Welcome to the forums and Ubuntu :)

You can install Ubuntu in your 2nd HD. When you get to the partition stage (step 4), you choose the appropriate HD.  Note that linux/Ubuntu does not differentiate using letters (C, D, E....) but rather sdX,Y or hdX,Y where X is the HD so double-check before installing.

Ubuntu does not require much to run.  I have made an install as low as 8GB ... but realizing/remembering that my music, data, pictures, videos (those heavy stuff) have to be placed elsewhere.  My current install (in this netbook)only has an allocation of 20GB and even with all the applications I have downloaded, I only have used up 12 GB. That said, I wouldn't hesitate to load ubuntu in the 1st drive ... if I could spare space from windows.... thus keeping your 2nd HD as your data/media drive. Ubuntu can read/write into NTFS.... and I'm hoping that is the file format of your 2nd HD.

There is always a risk of losing data when doing work on the HD.  Back-up please.

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

Good luck.  Post back for clarifications or requests.

---

### Post by RxBandit256 on 2009-09-24
thanks for ur help, my problem is that my first drive (in which windows is installed) is only a 40 GB drive n thats about half full although im sure i could probably send some stuff to my other drive to open up space, my second drive which i bought somewhat recently has about 400GB of space so space there wouldnt b a problem, i was gonna install there n give ubuntu about 150GB of space...any suggestions?

---

### Post by RxBandit256 on 2009-09-25
bueller? bueller? anyone out there with any ideas?

---

### Post by Juha Hjulgre on 2009-09-25
> **RxBandit256 said:**
> bueller? bueller? anyone out there with any ideas?
Should'nt be a problem, it's been a while from my last installation but if i'm not entirely wrong installation asks you which disc to use and offers to use the existing empty space on the disc. So just fiddle with the installation until u get to the point where it will start making actual changes to the hard drive.

There should be a radio button selection for the desired hard drive and it should offer u to either make the existing partitions smaller, to use the entire disc or manually enter partitions...

Make sure to backup as was mentioned before...

---

### Post by raymondh on 2009-09-25
> **RxBandit256 said:**
> bueller? bueller? anyone out there with any ideas?

LOL

LiveCD ok, tested on your system and running well?

If it were me .... I'd 

- defrag the target HD (2nd)
- boot into the liveCD and in live session (try ubuntu without changes)
- access gparted (system > admin > partition editor)
- select the appropriate HD (2nd)
- ensure that it is unmounted (highlight the 2nd HD and rt. click. If given the option to unmount, do so.
- Shrink the existing HD.  I'd allocate at least 20GB (more is better, say 30-50GB).  When OK, click apply to shrink ... leaving the freed up space unallocated
- Exit gparted and select install
- when you get to step 4, highlight the 2nd HD and install in largest/continuous free space (the space you left unallocated when you shrank previously
- Now you have to decide......
a.  If you want to control which OS to boot by selecting in BIOS, in step 7, you click "advanced" and **install GRUB in the MBR of the 2nd HD** which will be referred to as hd1.  This means that if you want to boot Ubuntu, you need to set the 2nd HD as "first to boot" in BIOS.
b.  Or, if you don't want to mess with changing BIOS and just have the option which OS to boot when you start your computer ... when you get to step 7, you click "advanced" and **install GRUB in the MBR of the 1st HD** (where windows is) which will be referred to as hd0.  This will overwrite the windows bootloader and GRUB will be your bootloader.

As always, back up.  Also, post back if unsure ... need clarifications, need a second opinion, etc.

Here are reference/reading guides for you to digest prior to installing.

[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Good luck.

---

### Post by RxBandit256 on 2009-09-26
believe it or not i got it all done b4 i saw this post, n then of course somehow my internet connection (and cable tv as a matter of fact) got disconnected for 24 hrs...but yeah i did almost all that u mentione raymondhenson...the only things i didnt do anythin with hav to do with the GRUB settings...i went into the BIOS n told the computer to look at my 2nd HD first in order to boot OS n i get all the right options, the only thing i guess is if i choose to boot windows it takes me to the boot menu from my 1st HD n i hav an option there to start Ubuntu (the old wubi installation which has been uninstalled already), how do i get rid of that?
thanks in advance

---

### Post by raymondh on 2009-09-26
> **RxBandit256 said:**
> believe it or not i got it all done b4 i saw this post, n then of course somehow my internet connection (and cable tv as a matter of fact) got disconnected for 24 hrs...but yeah i did almost all that u mentione raymondhenson...the only things i didnt do anythin with hav to do with the GRUB settings...i went into the BIOS n told the computer to look at my 2nd HD first in order to boot OS n i get all the right options, the only thing i guess is if i choose to boot windows it takes me to the boot menu from my 1st HD n i hav an option there to start Ubuntu (the old wubi installation which has been uninstalled already), how do i get rid of that?
thanks in advance

WUBI:

Boot into the 1st HD, windows, and manually edit the boot.ini file (c:/drive).  Depending on which windows version ... here's the guide linked below.  Remember ... **ONLY THE WUBI RELATED LINE **OR YOU LOSE THE OPTION TO BOOT WINDOWS AS WELL.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

GRUB:

Once you are settled and comfortable ... you can always re-install GRUB to suit your needs.  In fact, you can also edit the /boot/grub/menu.lst to "chainload" windows.  That way, you have the option to boot either OS at start-up without the need to BIOS select.  Post back if you wish to do so.  Here's a brief guide about "chainloading"

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Congratulations on your install and well done :)

---

### Post by RxBandit256 on 2009-09-27
aaaah very nice thank u, i removed the wubi thing as the guide said n its perfect, now when i select windows it just goes straight into it...thank u very much for ur help, now i hope to get very well acquainted with ubuntu n linux in general, got a lot to learn!
thanks again for all ur help

---

### Post by raymondh on 2009-09-27
> **RxBandit256 said:**
> aaaah very nice thank u, i removed the wubi thing as the guide said n its perfect, now when i select windows it just goes straight into it...thank u very much for ur help, now i hope to get very well acquainted with ubuntu n linux in general, got a lot to learn!
thanks again for all ur help

You're welcome and happy ubuntu-ing.  Oh, if you want, mark this thread solved (use "thread tools") to help others as they search for solutions.

---

### Post by cradom on 2009-09-27
I installed onto my second drive and mistakenly put the bootloader on that drive.
Now whenever I do a restart I have to do the ESC thing, select the Ubuntu drive and get grub.
Is there an easy way to put the bootloader on the first drive so I can just select which OS to boot from?
HD0 - Vista - sda
HD1 - Ubuntu - sdb

Thanks

---

