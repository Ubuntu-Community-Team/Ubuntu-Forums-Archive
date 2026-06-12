---
title: "64 Bit Processor and RAM"
date: 2010-02-02
forum: Hardware
---

### Post by XanTrax on 2010-02-02
Hi everyone.  Any help on this would be much appreciated.

I have recently purchased the new ASUS 1201N Netbook.  The specs are:

- Intel Atom 330 @ 1.60 Ghz, 64-bit processor
- Nvidia ION Graphics Card
- 2GB of RAM upgraded to 5GB (at this time 5GB, will be 8GB)

Now, my question is this...The max memory allowed is 8GB and I have currently upgraded it to 5GB.  The stick is correct and the BIOS reads 5GB of RAM.  I have installed 64-bit Ubuntu and confirmed in multiple ways that I have a 64 bit processor and that I am (obviously) operating a 64-bit operating system.

If I execute "cat /proc/meminfo | grep -i total" and view the line "MemTotal:" it seems to only read 3.25GB.  I thought this was a bit odd because I thought 32-bit is what read a max of 3.25 or 3.5 GB or what not...I have also installed Windows 7 and Windows 7 reports "5GB (3.25GB Usable)".  This, again, is very odd to me because everywhere is reporting 5GB of RAM but only 3.25GB usable.

Does anyone know why this is?

As another side note, when it came with 2GB of RAM Ubuntu and Windows 7 BOTH said only 732MB of RAM was usable...I dont understand where I am losing/missing almost ~1.5GB of RAM somewhere in the operating system.  

Any ideas?

---

### Post by XanTrax on 2010-02-02
Nevermind, just found this quip of a post on ASUS

[http://vip.asus.com/forum/view.aspx?id=20100119175615203&SLanguage=en-us&page=3&board_id=20&model=Eee%20PC%201201N](http://vip.asus.com/forum/view.aspx?id=20100119175615203&SLanguage=en-us&page=3&board_id=20&model=Eee%20PC%201201N)

Just in case anyone else is wondering.  Apparently the 1201N can not actually support 8GB of RAM and NewEgg and Amazon quietly changed their descriptions after this was brought to light; naturally, after I bought it.

---

