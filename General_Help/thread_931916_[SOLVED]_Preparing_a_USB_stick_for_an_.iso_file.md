---
title: "[SOLVED] Preparing a USB stick for an .iso file"
date: 2008-09-27
forum: General Help
---

### Post by semitone36 on 2008-09-27
Hey all

Im hoping to tinker around with Arch linux on my other laptop and I would like to use a USB stick to install it (there is something wrong with my DVD burner so my only option is to use my 2GB flash drive).  But Im having trouble preparing the stick.

Im following this guide: [http://wiki.archlinux.org/index.php/Install_from_USB_stick](http://wiki.archlinux.org/index.php/Install_from_USB_stick) but I cant get past step one.  cfdisk returns a "FATAL ERROR: cannot open disk drive".  How do I get around this?

---

### Post by ear0wax on 2008-09-27
Give [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") a try, it can pull the isos off the net, or you can use a locally stored one.

also pull up gparted and format your stick.

---

### Post by semitone36 on 2008-09-27
> **ear0wax said:**
> 

also pull up gparted and format your stick.

Ive never had to used gparted since installing ubuntu.  How do I format with it?

---

### Post by ear0wax on 2008-09-27
Its GUI, so theres no santax no learn. just goto synaptic and install it or sudo apt-get install gparted

If you have any issue using UNetbootin make sure you set the executable flag.

---

### Post by semitone36 on 2008-09-27
I tried to get unetbootin to work for me but I didnt find it in Synaptic and I am terrible at compiling programs myself lol.  I appreciate the suggestion though

---

### Post by zzzzz1 on 2008-09-27
just download the .deb and run it
UNetbootin is the easiest way to get an iso on a USB stick or SD card

---

### Post by semitone36 on 2008-09-27
> **ear0wax said:**
> Its GUI, so theres no santax no learn. just goto synaptic and install it or sudo apt-get install gparted

If you have any issue using UNetbootin make sure you set the executable flag.

I alread have gparted installed I just am unfamiliar with it.  (I couldnt find a "format" button haha).  And even after chmod -x I still couldnt get unetbootin to run.

---

### Post by semitone36 on 2008-09-27
> **zzzzz1 said:**
> just download the .deb and run it


Unebootin wasnt in getdeb.com and google wasnt any help either...

---

### Post by zzzzz1 on 2008-09-27
ear0wax posted the link above 

[http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-282&use_mirror=garr](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-282&use_mirror=garr)

---

### Post by semitone36 on 2008-09-27
Ah. God Im dumb. I forgot to mark the program as executable...

---

