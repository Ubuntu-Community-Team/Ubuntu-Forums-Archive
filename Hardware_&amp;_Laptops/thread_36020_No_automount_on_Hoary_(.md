---
title: "No automount on Hoary :("
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by fjleal on 2005-05-21
Greetings, everyone!

I just finished installing Hoary on an Asus L5900 (PIV 2.8GHz, 512 MB, Ati Radeon 9K 64MB). After installing Java, flash, VLC, etc., I realized that, unlike previous Hoary installations I did on other machines, automount simply doesn't work. No USB devices (pens, removable HDDs, cameras), no CDROM, no DVD... Automounting is selected in Preferences, but nothing happens when I plugin a device, or insert a CD. If I access the CD via Nautilus (Computer > CD-Rom drive), it then gets mounted, but _only_ then.

Can anyone think of a reason for this behaviour? Thanks in advance!

P.S.: hald is running, I can see it on a "ps -ef" list.

---

### Post by stevanhe on 2005-05-22
Hi, you should edit your /etc/fstab configuration file, doing that you can change the ways the filesistems are mounted automatically, at system start or after and other various options...

For a sharp help file go to this link...

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)


Bye, Stevanhe

---

### Post by fjleal on 2005-05-22
[QUOTE=stevanhe]Hi, you should edit your /etc/fstab configuration file, doing that you can change the ways the filesistems are mounted automatically, at system start or after and other various options...

For a sharp help file go to this link...

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)


Bye, Stevanhe[/QUOTE]
 Hi, Stevanhe. There's nothing unusual with /etc/fstab, it is set up the way it should be such that devices like the CD-Rom should automount. Also the services are running. But nothing gets recognized when plugged-in, may it be a USB device or a CD or DVD. This happens only on this particular machine, and that's the weird part... Fedora Core 3, running on the same machine (on another partition), mounts everything with no problems at all. :(

---

### Post by shof2k on 2005-05-23
Auto mount can be set up via the gui.  System-Removable media I think.  See if the automount options are checked.

---

### Post by fjleal on 2005-05-23
Every single one of them! It is the automount system that somehow doesn't work.  ](*,)

---

### Post by Ali_Baba on 2005-05-23
Hi,i had this same problem before.I heard that its dbus/hal bug.I updated to breezy and its ok now.There is a thread about this problem on the forums.I think you might have the same problem too. Here is the thread [http://www.ubuntuforums.org/showthread.php?t=27087&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=27087&page=1&pp=10) 
Hope this helps :)

---

### Post by fjleal on 2005-05-23
Thanks for the link! Yes, it may be the same problem. It's strange because the LiveCD works perfectly, but a lot of people is complaining about that same issue. Still, upgrading to Breezy in such an early stage of development may bring other problems... Hum...  :???:

---

