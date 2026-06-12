---
title: "BOOT FROM KUBUNTU or does NOT needed to install kubuntu on external hdd ?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by lse123 on 2009-11-09
wubi installer for windows exist and for kubuntu 9.10 ? If I want to install kubuntu on external hdd I must first BOOT FROM KUBUNTU or does NOT needed ?

---

### Post by kio_http on 2009-11-09
Wubi is an installer within windows. It will create a virtual disk in a Windows partition and you will not be able to access your hard drive contents of the windows system.

If you want to install to your external hard disk boot the CD. Follow steps of install and select your external HDD. then restart and boot the external hard disk

---

### Post by catco_designs on 2009-11-09
wubi makes ubuntu?kubuntu a program inside windows. Go to this [page]("http://www.ubuntu.com/getubuntu/download") it will explain more about how to install ubuntu.

---

### Post by lse123 on 2009-11-09
WUBI is only for ubuntu or and for kubuntu?
where I understand if my pc supports boot from (the bios) extHDD OR USB-STICK ?
"and you will not be able to access your hard drive contents of the windows system." What you mean? from linux no access windows ? and from windows no access linux ? it will create two partitions (kubuntu+vista) ?

---

### Post by catco_designs on 2009-11-09
Wubi is a windows program. It is so you can run ?buntu inside Windows. 
Wubi does not create a partition on a disk. It creates a file. 
Just like a document or an image does but it contains ?buntu in that file and uses vfs(virtual file system) to emulate an actual install.

Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) click on [B]

[Alternative download options, including Ubuntu installer for Windows  ]("http://www.ubuntu.com/getubuntu/download#")

you can then download and burn the disk for your system depending on architecture 

or did you download the full version?

[/B][CENTER][LEFT][B][FONT=Franklin Gothic Medium]The way that I install is I download the cd or dvd image
 check md5
 burn to disc and then install[/FONT][/B]

I have never followed the wubi method I see on that link 
I thought that wubi was just the ubuntu windows program

this is what I am speaking of when I mention wubi 

[http://wubi-installer.org/](http://wubi-installer.org/)
[/LEFT]
[/CENTER]

---

### Post by catco_designs on 2009-11-09
To think about it another way the Windows partition is on your hard drive and the flash drive contains the Ubuntu files. So accessing ubuntu from Windows may be possible but to mount a location (the flash drive) and look backwards I don't really know. because I believe it is not changing the MBR to do this it is simply mounting from bios.

Another way to see if it has a separate partion is to simply go to Add Remove Programs and see if Wubi has an entry there. If it has an entry there that would mean it is acting as a program and not an operating system.

I am sorry but I wish that I could be more help..

---

