---
title: "Full install to USB Flash Drive but hold writes until shutdown"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Meson on 2009-02-02
I'd like to do a full install to a USB Key, but to avoid killing the key, I want to hold all writes until I shutdown the computer.  I'll be mounting /tmp to ram of course.

The reason I don't want to install the live distro to the key is because I want to be able to update the kernel, etc.

---

### Post by dabl on 2009-02-02
Format it FAT32, or ext2, and it will not be subjected to journalling writes.  Ext2 is the same as ext3, but without journalling.

:)

---

### Post by snowpine on 2009-02-02
Get a good quality USB drive and don't worry about it (except for making regular backups, of course), is my advice. Rumors of exploding flash drives are greatly overexaggerated...

---

### Post by Meson on 2009-02-02
> **dabl said:**
> Format it FAT32, or ext2, and it will not be subjected to journalling writes.  Ext2 is the same as ext3, but without journalling.

:)


I think I actually want the journalling though.  Just have it stored in RAM and written on shutdown.  I think it's the synchronous writing that could cause problems, especially in /var

---

### Post by dabl on 2009-02-03
If you want to use ext3 and tweak the tuneable parameters to reduce the number and frequency of writes to the media, there are a considerable number of things that you can do.  The default "commit" cycle is every 5 seconds (500 centisecs) -- you can run it up as high as you want.  Don't forget to add to the "rootflags=" line in defoptions in your /boot/grub/menu.lst and run grub-update to enable the options at boot time and keep them after kernel upgrades.  Also there are parameters in /proc/sys/vm that you can adjust. Here are some links to get you started:

[http://www.westnet.com/~gsmith/content/linux-pdflush.htm](http://www.westnet.com/~gsmith/content/linux-pdflush.htm)

[http://www.cs.rochester.edu/~kshen/csc573-spring2008/assignments/assignment3.html](http://www.cs.rochester.edu/~kshen/csc573-spring2008/assignments/assignment3.html)

[http://kerneltrap.org/index.php?q=mailarchive/linux-kernel/2007/4/6/74301/thread](http://kerneltrap.org/index.php?q=mailarchive/linux-kernel/2007/4/6/74301/thread)

---

### Post by Meson on 2009-02-03
Thanks for the great resources, dabl.  After I get around to going through them and research some more, I'll post my findings.  It would be nice if projects like unetbootin and portablelinux would configure devices like this to give users a much more complete portable installation.

---

### Post by theozzlives on 2009-02-03
As close as I can see you want to boot off it, boot the live 8.10 CD and try:
```
wget pendrivelinux.com/downloads/u810.sh
```
then
```
chmod +x u810.sh && sh u810.sh
```
just follow the prompts.

---

### Post by dox_drum on 2009-02-03
> **theozzlives said:**
> As close as I can see you want to boot off it, boot the live 8.10 CD and try:
```
wget pendrivelinux.com/downloads/u810.sh
```
then
```
chmod +x u810.sh && sh u810.sh
```
just follow the prompts.

Sorry. I got a laptop without OS, could Ubuntu be installed to it using this method?

Because I've tried with the installation CD and always got an error when installing the kernel (for Intrepid Ibex).

Thanks.

---

### Post by Meson on 2009-02-03
> **theozzlives said:**
> As close as I can see you want to boot off it, boot the live 8.10 CD and try:
```
wget pendrivelinux.com/downloads/u810.sh
```
then
```
chmod +x u810.sh && sh u810.sh
```
just follow the prompts.

I want to do more than that.  I want a fully blown installation that's flash drive friendly.  I've been able to manually partition my current key, copy the live cd to a small partition, and set up persistence with casper.  The reason I don't like this is because it's difficult to update the kernel as well as some other components with security updates available.

---

