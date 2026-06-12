---
title: "Transfering my partition on a new HDD"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by ubuntuuser on 2005-09-26
Hi,

I am currently running my system (laptop) in a WinXP/ ubuntu dual-boot mode. I want to buy a new harddrive. Is it possible to simply install XP on the new disk and then copy my working and set-up ubuntu partition on a newly created partition?

If not, how could I transfer my configured ubuntu on my new harddrive without reinstalling an re-setting up all my programs? I have invested a lot of time in making my ubuntu just as I want it to be and I don't want to do it all over again (I would, if I had to, but hopefully I can somehow avoid it).

Btw, as I am using a laptop I don't have the possibility to install a second HDD, I definitely need a new and bigger harddisk.

Thank you very much for your help.

---

### Post by mlomker on 2005-09-26
> Btw, as I am using a laptop I don't have the possibility to install a second HDD, I definitely need a new and bigger harddisk.


Well, it isn't so easy if you don't have access to some other equipment.  

If you have access to a server or a USB hard disk then you could back it up to another machine (using Ghost or the linux-based [systemrescuecd]("http://www.sysresccd.org/")).

One option would be to just [back up]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") the main configuration directories (then burn the files to a CD or whatever).  That won't save everything, but it'll get most of it.

---

### Post by ubuntuuser on 2005-09-27
Hi.

[QUOTE=mlomker]Well, it isn't so easy if you don't have access to some other equipment. [/QUOTE]

That's no problem, I have an external 150 GB HDD I would use. I just wrote that because some friends already told me to simply install a second harddisk.

What I would really like to do is to copy all directories on the external disk, install the new drive, install Windows and ubuntu and then overwrite the new ubuntu installation with my old data. That sounds too easy so there must be some problems I don't think of. Maybe some directories I must not overwrite or maybe some highly important config files that ubuntu customized to fit my old hardware setup and which would refuse to let my computer boot because they expect file XX to be in sector YY...

Would that way of transfering my data work? Are there directories I must not, under no circumstances, overwrite (I am thinking of /dev, but I am sure there are more). I simply don't know enough of how Linux or ubuntu really works to estimate the damage I could cause with these actions.

---

### Post by mlomker on 2005-09-27
>  I simply don't know enough of how Linux or ubuntu really works to estimate the damage I could cause with these actions.

It'd probably work if you use the same version of Ubuntu.  Most of the items in /dev are created on boot-up anyway.  I've never tried it that way, though.

---

