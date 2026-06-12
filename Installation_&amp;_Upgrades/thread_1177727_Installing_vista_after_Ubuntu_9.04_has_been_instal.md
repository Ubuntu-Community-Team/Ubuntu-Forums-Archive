---
title: "Installing vista after Ubuntu 9.04 has been installed"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by jackstoner on 2009-06-03
I have Ubuntu 9.04 installed on a family's pc but they want to use the iTunes store which I assume can only be used in windows. 

Is it possible to install Windows Vista 32bit Home Premium without having to install Vista first then ubuntu again? 

Thanks:p

---

### Post by merlinus on 2009-06-03
vista will probably need to go in a primary partition which is first on the disk.  if you can create this, all well and good.  otherwise, best to backup data and start fresh.

---

### Post by coffeecat on 2009-06-03
Windows needs to be in a primary partition, but not necessarily the first partition. Having said that, the Vista installer might not like the presence of a non-NTFS partition as the first one - I don't know. Backup all your data in case the installer does something unpredictable, I guess is good advice. And you might be better to prepare an NTFS partition before you start the Vista installer, so you can point it at that.

One problem is that Vista will overwrite the mbr so you won't be able to boot into Ubuntu until you've reinstalled grub to the mbr. And then you'll have to edit the grub menu.lst so that you'll be able to boot into Vista.

---

### Post by jackstoner on 2009-06-03
Looks like it'll be easier to install Vista first then use Vista's disk manager to make a partition for Ubunutu. 
 
Nothing really crazy to backup except for my sisters school projects.

---

### Post by VastOne on 2009-06-03
> **jackstoner said:**
> Looks like it'll be easier to install Vista first then use Vista's disk manager to make a partition for Ubunutu. 
 
Nothing really crazy to backup except for my sisters school projects.

There is nothing more sacred than a sisters school projects!

:cool:

---

### Post by Steelmourne on 2009-06-04
Before going back to Vista, try looking at this guide to getting itunes store support in ubuntu:

[http://ubuntuforums.org/showthread.php?t=79231](http://ubuntuforums.org/showthread.php?t=79231)

---

### Post by zman58 on 2009-06-04
Instead of dealing with itunes music store, you could opt for Limewire on Ubuntu Linux. It is very good at finding tunes to play. You can manage ipods using Rhythmbox, which comes on Linux. Just add the codecs you need to manage it.

Limwire basic is free:
[http://www.limewire.com/](http://www.limewire.com/)

---

