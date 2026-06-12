---
title: "Trying to use Ubuntu on Asus PUNDIT-R"
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by Patinux on 2004-12-13
Hi !


Well I hope some one will spend few minutes to explain to me how to solve these little problems on my barbone (I'm not a Linux expert ;) )

So I've tried to install Ubuntu on my personnal barbone after successful tests at the office.
Unfortunately I'm having trouble with me Lan chip which is not correctly detected (3c920B-EMB-WNM) and with my video chipset ATI IGP 9100 (If I can access to the Lan  I should be able to solve this problem running "apt-get")
The Lan chipset driver doesn't seems to be available as a dedicate driver file.

The machine start to boot but after more than 5 minutes I'm still waiting on the "starting hotplug subsystem" screen

Does any one installed this great distribution on this Asus barbone ?
If you have any procedure to help me to solve these problems, I will appreciate. 
(deb files are not so familiar to me)

Regards.

---

### Post by mythagel on 2005-01-31
Hello,

I've just bought one of these Pundit-R's as well (i haven't got mine yet), and this link seems to say that debian sarge runs fine on it, mean that Hoary probably will too.

[http://sanguine.nothovel.net/cgi-bin/blosxom/2005/01/21#20050121-pundit](http://sanguine.nothovel.net/cgi-bin/blosxom/2005/01/21#20050121-pundit)

It seems that the lan chip is supported but not detected properly ( i read a post at [http://lists.debian.org/debian-boot/2004/11/msg01268.html](http://lists.debian.org/debian-boot/2004/11/msg01268.html) that suggests it should be fixed now).

You can load the ethernet module by typing

# modprobe 3c59x


-Nick

---

### Post by Patinux on 2005-02-06
Sorry for the delay !

I just discovered your answer .... THANKS !!!


Due to this problem I moved to Mandrake distribution (no problem with this one), waiting for the new Ubuntu's version (final one, because betas are working too).

I will read both links soon .... 
That really a good news !  :D  I hope, I will be able to succeed :D


Regards.


[EDIT] Yes I've done it once !

But I still have problems with the hardware detection FAT32 partition, USB hub, extra graphical card (ATI 9200se) ... etc.
Ubuntu telling me that my BIOS is configured as Plug&Play.... but it's not....  keep searching.

---

### Post by mythagel on 2005-03-16
If you're still interested as an update i am currently running Hoary on my Pundit-R right now and the only thing not working is the built in card reader!

let me know if you run into any troubles setting it up and i'll let you know how i've fixed it

cheers,

-nick

---

### Post by jang on 2005-08-15
I have this same unit, but I don't have audio.  Any advice?

---

