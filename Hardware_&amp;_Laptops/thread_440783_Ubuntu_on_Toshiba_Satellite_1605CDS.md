---
title: "Ubuntu on Toshiba Satellite 1605CDS"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by CocheseUGA on 2007-05-11
Hi. New to the forums, new to Linux.

Here's my situation, and I'll make the most important things stand out: I am trying to install Ubuntu to a 99-00(?) Toshiba Satellite 1605CDS. The memory is maxed at 160MB, and it's a K6-550 processor, IIRC. The **CDROM doesn't work**. The BIOS is also too old to have USB boot, and it only has a RJ45 port.

I finally got a working boot disc of 7.04, and proceeded to install it on the laptop's HDD via an external USB enclosure on my XP machine. First install went bad at 59% with a foometric/db error. Second try breezed through no problem.

Install the HDD back in the laptop, and it states 'Cannot load operating system'. HDD didn't show up on the XP machine for me to check it out after the install, I assumed that was normal.

I'm downloading Xubuntu right now, hoping that it's lower requirements will be more palatable to the laptop. Any other suggestions for me? I got this laptop dirt cheap (free), and I've only spent about $30 trying to get it up and running. I'd like to limit the damage if at all possible, or I'll just find something at a yard sale.

Thanks for the help, the OS looks OUTSTANDING.

---

### Post by CocheseUGA on 2007-05-12
Bumping this to the top.

From the Xubuntu Live CD, I can see the files on my target HDD, it has Grub installed on it. So, what else do I need to do to make the HDD boot? It won't boot on my XP machine (where I can boot from a USB HDD), and the Toshiba doesn't recognize it.

Any help would be GREATLY appreciated. I'm not sure what to do at this point.

---

### Post by nanonomic on 2007-05-12
first of all how old is this thing?

---

### Post by CocheseUGA on 2007-05-12
2000. I believe the problem is I need to edit the HDD record in GRUB, something I asked about in the beginner forum. If I can fix that, then it should work. (IE, it's pointing to a kernal on (2,0) when it is supposed to be (0,0)

---

### Post by oilchangeguy on 2007-05-12
found a cd drive for your computer:
[http://www.sparepartswarehouse.com/Toshiba,Laptop,Part,K000680200.aspx](http://www.sparepartswarehouse.com/Toshiba,Laptop,Part,K000680200.aspx)

---

### Post by CocheseUGA on 2007-05-13
> **oilchangeguy said:**
> found a cd drive for your computer:
[http://www.sparepartswarehouse.com/Toshiba,Laptop,Part,K000680200.aspx](http://www.sparepartswarehouse.com/Toshiba,Laptop,Part,K000680200.aspx)

Woof. Appreciate it, but there's no way in hell I'm spending that much to fix this POS. I'd much rather spend that money on a new one.

---

