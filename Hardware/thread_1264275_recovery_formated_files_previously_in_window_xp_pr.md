---
title: "recovery formated files previously in window xp pro"
date: 2009-09-12
forum: Hardware
---

### Post by nuttynibbles on 2009-09-12
hi, i recently installed ubuntu netbook remix 9.04 onto window xp in my netbook. i understand we can migrate the files over during installation, but i accidentally formatted the entire hard disk. now if i wanna retrieve those files, what are the ways to do so?

1) attach the netbook hard disk to a *window xp* pc and use a recovery software?
2) try recoverying the files in ubuntu itself?

which is the better way?

thanks

---

### Post by hal10000 on 2009-09-12
> but i accidentally formatted the entire hard disk which partition of your harddisk did you format? The whole drive? The windows partition? The ubuntu partition?

To verify this, open a terminal window and post the output of the command
[COLOR="Red"]sudo fdisk -l[/COLOR]

If you're still able to boot ubuntu, then i guess your windows system partition is gone.
If you have another partition where you stored your own documents (e.g. Office-documents, Videos, music etc.) then you are lucky and can access them easily with ubuntu.
But if you have them all stored together in your windows partition, then they are gone together with your windows.

there's a linux command-line utility called [COLOR="Red"]sudo testdisk[/COLOR] and with a little luck it may recover your partition (but i don' know if you can run it from your live cd). If it's not installed you can get it with 
[COLOR="Red"]sudo apt-get install testdisk[/COLOR]
If testdisk does not work for you, then i guess the only chance to get your windows back is to boot your windows recovery disc (if you have one), but then your ubuntu and all your own files will be wiped out.

> i understand we can migrate the files over during installation
I can't imagine which files you mean here, your Office-files or what?
I've done a lot of linux/ubuntu installations, but i never migrated any files during installation.

---

### Post by nuttynibbles on 2009-09-17
hey hal10000, sorry for the late reply. well i finally got hold of the netbook.

well the netbook was initially installed with window xp pro. it has C and D drive. my friend decided to use ubuntu netbook remix and wanted to use the migrate settings which will migrate all files and documents from winxp pro to the new OS ubuntu netbook remix. sadly, a wrong option was chosen and the entire HD was formated n installed with the ubuntu netbook remix.

to recover the files, im gonna attached them2.5 sata HD to my desktop motherboard with IDE on it. 

my question is, can I run a recovery software like those found in [http://data-recovery-software-review.toptenreviews.com/?](http://data-recovery-software-review.toptenreviews.com/?)

any help will be appreciated.
tks

---

### Post by IcarusR on 2009-09-17
Linked software only any good if it can recover files that have been formatted to linux ext2 or ext3.
Might be worth trying [[COLOR="Red"]Testdisk[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk") which I believe is in the repositories.
Boot desktop from Ubuntu live CD, (with messed up dirve connected) install Testdisk to live CD ubuntu & run it & see what it finds.
If you are really paranoid unplug all drives except the one in question first. Avoid any more disasters !

Have never used Testdisk so I don't know if it will work or not.
Also could try [[COLOR="Red"]Photorec[/COLOR]]("http://www.cgsecurity.org/wiki/PhotoRec")

Good luck

---

### Post by nuttynibbles on 2009-09-17
hi IcarusR, would it be the same if i run testdrives on windows and trying to recover those files on the 2.5 sata harddisk(with ubuntu netbook remix installed) that is attached to the pc IDE? or shu i install testdrives on ubuntu as u suggested. any diff?

---

### Post by hal10000 on 2009-09-18
> 
sadly, a wrong option was chosen and the entire HD was formated n installed with the ubuntu netbook remix.

If you really formatted the entire harddisk then you are really sad, because the data on this disk will be gone forever. You may take the drive to a specialist, but i guess you then will have to pay up to several thousand dollars to get your data back.
To verify if you really formatted the whole drive, you can post the output of the following command:
[COLOR="Red"]sudo fdisk -l[/COLOR]

---

### Post by nuttynibbles on 2009-09-18
hi, tks for the reply. will try it and get back to you. tks again

---

