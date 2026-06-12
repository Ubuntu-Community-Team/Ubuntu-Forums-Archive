---
title: "Problem Installing from Hard Disk"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by delabel on 2009-10-14
Hi everyone, I'm trying to install Ubuntu Hardy from the hard disk. I've followed the instructions in the installation guide and so I copied the files initrd.gz and vmlinuz in the directory /boot/newinstall of my current Ubuntu Dapper system. I also put there the iso file because that's worked for me on Debian, although as fas as I can tell, the guide doesn't mention anything. The installer starts fine, but after I set up the keyboard it is unable to find the iso image. I've got a copy on Ubuntu dapper, another on Windows, and also a CD with Ubuntu Hardy in an external, USB CD-drive. It gets mounted but the program can't find a valid image or CD.

If I start up the computer with the CD-drive off, then something slightly different occurs. First it says that a quick search in what it calls typical locations has found nothing. Then it asks me if I want a search through all the hard disk. I say yes and it starts with the first partition but soon gives up, even before reaching the second partition, and the same message about the CD comes up. 

What could I be doing wrong?
Thanks.

---

### Post by MelDJ on 2009-10-14
could you give the guide you are following? and why not do a clean install with the cd?

---

### Post by delabel on 2009-10-14
> **MelDJ said:**
> could you give the guide you are following? and why not do a clean install with the cd?

Hi Mel, it is the official guide of Ubuntu 8.04 LTS. These are the relevant sections:

[https://help.ubuntu.com/8.04/installation-guide/i386/boot-drive-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-drive-files.html)
[https://help.ubuntu.com/8.04/installation-guide/i386/ch05s01.html](https://help.ubuntu.com/8.04/installation-guide/i386/ch05s01.html)

This is the Debian guide I mentioned earlier that worked for me:

[http://www.debian.org/releases/stable/i386/ch04s04.html.en](http://www.debian.org/releases/stable/i386/ch04s04.html.en)
[http://www.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd](http://www.debian.org/releases/stable/i386/ch05s01.html.en#boot-initrd)

The only difference I see between both guides is that the Debian one says that you can put the iso image along with the other two files.

I've got an Intel Mac Mini with the CD-drive broken and the only way I can boot is from the hard disk. I've tried with an USB stick and an external CD without success.

---

