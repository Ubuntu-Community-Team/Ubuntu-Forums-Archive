---
title: "Ubuntu: from portable to permanent"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by enzo2 on 2009-06-19
Hi all

I've done a fair bit of google / forum searching and can't find an answer to my question. I hope you can help me.

I've been using a usb portable* install of Jaunty for long enough to want to use it full time. The portable version is persistent, using a 3gb casper-rw file.

When booting from the usb, I am offered the option of installing Ubuntu to the host machine. If I go ahead and install, does anyone know if the settings / applications in the casper-rw file will make it across? And, if not, does anyone have any suggestions of how I might transfer all my settings?

This is my first post in a linux forum, so please forgive me if I've not presented my problem as well as I could have. 

Many thanks in advance,
Enzo

* installed as per [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

---

### Post by 22tape on 2009-06-19
i'm interested in exactly this too.  thanks!

---

### Post by ChristianMartel on 2009-07-16
Hello, newbe to Hardy Herron.  Initial install of 8.04 onto a HP Pavillion notebook, on an 80GB NTFS partition, in Win XP SP3 as a folder, "Portable Ubuntu".  Only requested 10GB of space and installed from CD image not DVD image.  

Got hungry and installed more and more and now machine does not startup on Ubuntu side of dual boot, but still ok on Win XP side.  

Currently following instructions to increase partition size from 10GB to 22GB based on posts at [http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/) , and hopefully this will resolve the startup problem.  But like 2 previous posts I'd like to migrate this installation to a permanent, separate EXT3 partition.  So here are a couple of questions that generates:

1) Can I copy my 10GB Ubuntu folder to my file server while I resize the NTFS partition to make space for a new EXT3 partition, and then copy the image back to my new EXT3 partition?  What changes need to be made in which files to make this work?

2) I'd like by notebook to boot up by default on Ubuntu side not Win XP side.  When I look at my Grub menu.lst file, changing the Default=0 to say 1, makes Ubuntu boot in safe mode, and Win is still default.

Thx for patience and help.

Regards,


xian

---

