---
title: "Hard Drive root folder not displayed. fstab output"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by klittzzer on 2007-01-10
Hello all,

I have been running Ubuntu&Kubuntu Edgy on a Fujitsu Siemens Amilo L7310G notebook for a couple of months now and finally ditched Windows completely a couple of weeks ago and have the above solely occupying my HD (~80GiB).

I have a problem. When I was dual booting with Windows Gnome displayed the contents of my file system no probs. KDE and Konqueror have never displayed a folder through which I can gain access to my file sytem. If I type '/' in the search bar of Konqueror (minus the apostrophe), the various folders, 'etc', 'dev' and so on drop down and I am able to access the files.

I would like to have the same access that Ubuntu gave me, however. When I bring up fstab in a terminal I get the following output:

[B]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=10fe8008-d8bb-4164-a9d1-5f97cd05964b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6c3f209a-7dfe-474d-8cda-e46d59332897 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

[/B]
It looks as though /dev/hda1 and /dev/hda5 are not being picked up because of the # in front of them.

Am I correct in thinking that if I edit fstab as root and delete the # in front of them my HD will then be accessible through a root folder. At the moment, when I click on 'media' I only have a path to CD rom. 

I am still fairly new to this OS so any help will be appreciated. I am tempted to go ahead and edit fstab but don't want to cause any fatal errors. If it was a piece of software I would jump in and learn from my mistakes. This could effect my system though??

Thanks, this forum has helped me so much every time.

Peace

klittzzer

---

### Post by raul_ on 2007-01-10
The # in front of them is just to say that the UUID's are from the devices...it has nothing to do with it. I don't work with Konqueror but have you tried accessing "/" from the search bar and then bookmarking it and adding it to the places tab?

---

### Post by contadinoste on 2007-01-21
It's a new security feature in Konqueror ( maybe also in Nautilus). Open "root folder" tab and activate "show hidden files" then you will see them in the main window, but not in the tree. Or type in konsole: 
cd /
ls

---

