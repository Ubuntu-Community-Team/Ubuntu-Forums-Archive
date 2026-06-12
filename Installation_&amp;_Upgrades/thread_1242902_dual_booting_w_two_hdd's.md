---
title: "dual booting w/ two hdd's"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by shanecy on 2009-08-17
Hi.

later today i was planning on rebooting windows on my computer because its way to slow. and i was thinking about dual booting it with ubuntu 9.04. i have two SATA hdd's, one 80gb and one 500gb. i was originally planning on putting windows and linux on the 80gb hdd, and using the 500gb hdd for storage, but im wary of issues that might occur from having windows and ubuntu using the same hdd for storage. i would hope to have shared document, video, and picture folders, as well as programs etc on the 500gb.

are there any problems with this? any suggestions for better configs? id appreciate some input here :D


EDIT: what about wubi? are there any disadvantages using that instead of the whole grub/partition manager process?

---

### Post by serpantman on 2009-08-17
You can install both on the same HD no problem as long as you install windows first as it overwrites grub. Up to you though.

---

### Post by stlsaint on 2009-08-17
you should install xp first then install ubuntu...now for the sharing of hdd space windows will not see a ext3/4 formatted hdd...but ubuntu...being the great OS that it is can see a NTFS filesystem so all you have to do is make sure its hooked up after you install both OS and ensure that in your system tools under add/remove you have the ntfs tool installed( not sure if its 100% necessary but it cant hurt to have!!) Make sure that you install the operating systems on that 80GB and i recommend you unplug the 500gb from the MOBO...just as a cautious step not really needed!! then plug back in and format as ntfs and ubuntu will see it under places tab!

---

### Post by stlsaint on 2009-08-17
> **stlsaint said:**
> you should install xp first then install ubuntu...now for the sharing of hdd space windows will not see a ext3/4 formatted hdd...but ubuntu...being the great OS that it is can see a NTFS filesystem so all you have to do is make sure its hooked up after you install both OS and ensure that in your system tools under add/remove you have the ntfs tool installed( not sure if its 100% necessary but it cant hurt to have!!) Make sure that you install the operating systems on that 80GB and i recommend you unplug the 500gb from the MOBO...just as a cautious step not really needed!! then plug back in and format as ntfs and ubuntu will see it under places tab!

correction...format the 500GB as fat32! i understand that ubuntu and vista will be able to write to it better this way!!

---

### Post by presence1960 on 2009-08-17
> **serpantman said:**
> You can install both on the same HD no problem as long as you install windows first as it overwrites grub. Up to you though.

You can install Ubuntu first if you wish. When you install windows it will overwrite GRUB, but a simple 30 second process will restore GRUB:
```

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


```

In # 6 use setup (hdx) where x is the number of hard drive you want to put GRUB on the MBR. Just remember counting starts at 0. Thus sda = (hd0), sdb = (hd1), etc

---

### Post by raymondh on 2009-08-17
> **presence1960 said:**
> you can install ubuntu first if you wish. When you install windows it will overwrite grub, but a simple 30 second process will restore grub:
```

1. Boot your computer up with ubuntu cd
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for ubuntu.
6. Type "setup (hd0)", to install grub to mbr, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install grub to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable cd.


```

in # 6 use setup (hdx) where x is the number of hard drive you want to put grub on the mbr. Just remember counting starts at 0. Thus sda = (hd0), sdb = (hd1), etc

+1 ....

---

### Post by stinger30au on 2009-08-18
or if the manual suggestion fails try this

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

i have been playing round with this for a few hours now, very good bit of gear this for grub/lilo issues

---

### Post by shaneecy on 2009-08-19
stlsaint, presence1960, thank you very much for your insightful replies. i have decided to start with ubuntu, then format the 80gb into two partitions, install windows, then use the advice that presence1960 gave me to un-overwrite grub. then ill format the 500gb fat32 and ill be set.

again, thanks a lot. :guitar::)

---

### Post by presence1960 on 2009-08-19
> **shaneecy said:**
> stlsaint, presence1960, thank you very much for your insightful replies. i have decided to start with ubuntu, then format the 80gb into two partitions, install windows, then use the advice that presence1960 gave me to un-overwrite grub. then ill format the 500gb fat32 and ill be set.

again, thanks a lot. :guitar::)

sounds like a plan! if you need any help come back here.

---

