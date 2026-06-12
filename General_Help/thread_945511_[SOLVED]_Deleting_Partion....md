---
title: "[SOLVED] Deleting Partion..."
date: 2008-10-12
forum: General Help
---

### Post by Fxy on 2008-10-12
Hi

A while ago i installed ubuntu along side vista on my laptop....  Noq im getting a new laptop n am passing my current laptop onto another family member.  My problem is they want me to delete ubuntu n only have vista installed on the computer.  Within vista i can view the vvista n ubuntu partions but im unable to touch the ubuntu partion.  i have tried gparted but the cd wont load "any ideas"...  Thnx in advanced...

---

### Post by mikedep333 on 2008-10-12
Try re-downloading and burning an ubuntu desktop CD to use gparted.

BTW: It is spelled "partition."

---

### Post by Fxy on 2008-10-13
> **mikedep333 said:**
> Try re-downloading and burning an ubuntu desktop CD to use gparted.

BTW: It is spelled "partition."

I have an official Ubuntu cd, how do i get into or use gparted from the cd.  Im a complete Linux noob and i can't seem to find it :(...

---

### Post by ago on 2008-10-13
If you used Wubi, there is no partition created, only files. If you didn't use Wubi, this is not the right forum ;)

In any case if you didn't use Wubi you can simply delete the partition using any partitioning tool.

---

### Post by Fxy on 2008-10-13
> **ago said:**
> If you used Wubi, there is no partition created, only files. If you didn't use Wubi, this is not the right forum ;)

In any case if you didn't use Wubi you can simply delete the partition using any partitioning tool.

Hi ago

Yes i did use Wubi to install ubuntu and my problem is that when i view my partitions in windows the one that ubuntu excited on cannot be deleted or edited :?...  I have downloaded gparted but i cannot get it to run from dvd...

---

### Post by ago on 2008-10-13
Can't you uninstall Ubuntu from add/remove programs?
Wubi uses files that are all in the ubuntu directory, partitioning programs will not help since there is no partition... You could also delete the files manually, see the WubiGuide for more info.

---

### Post by Fxy on 2008-10-13
> **ago said:**
> Can't you uninstall Ubuntu from add/remove programs?
Wubi uses files that are all in the ubuntu directory, partitioning programs will not help since there is no partition... You could also delete the files manually, see the WubiGuide for more info.

Since i installed ubuntu via wubi a separate partion has appeared along side my vista 1.  My problem is that when i view it inside vista i cannot delete it n i cant seem to get gparted to run from cd...  See my attached screenshots below...

This is the screenshot of what is available when i right click on my vista partition
[IMG]http://img522.imageshack.us/my.php?image=screeni1eg3.jpg[/IMG][IMG]http://img511.imageshack.us/img511/1517/screeni1ze2.jpg[/IMG]


This second screenshot is of what is available when i click on the partition im trying to delete
[IMG]http://img521.imageshack.us/img521/4264/screeni2nh1.jpg[/IMG]

---

### Post by ago on 2008-10-13
I am 100% sure that wubi does not create any partition. That is either the recovery partition of your machine or some partition you created using other tools.

---

### Post by Fxy on 2008-10-13
Oh kool im startin to understand lol...  Any way i can join this partition back onto my vista one :?...

---

### Post by ago on 2008-10-13
If you boot in wubi you should be able to mount that partition manually and see what is in there... One of the advantages of having Linux around...

---

### Post by Fxy on 2008-10-13
Kool ill try that and report back if im successful or unsuccessful ;)

---

