---
title: "How can I skip memtest86+ during boot"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by abhint on 2008-12-21
Hi All

I just installed Xubuntu on my old thinkpad (dual with XP). The installation went fine but during boot I get the option as "ubuntu 8.10, memtest86+" along with windows XP.  

I let it run the test thinking it was just one time but I get the same option everytime I boot. If I let the test comeplete it says something like "no errors found, press ESC to exit" and I press esc, it says halting... but the screen just freezes.  I reinstalled Xubuntu but the same thing.

Is there anyway I can skip this and boot Xubuntu.  I am very new to this and I would really appreciate some help.

Regards

Abhi

---

### Post by Partyboi2 on 2008-12-21
Select ubuntu 8.10 at boot to load ubuntu, the mentest86+ is an option you can choose if you are wanting to check your memory, and will remain in the menu unless you remove it.

---

### Post by abhint on 2008-12-22
Thanks for your messgage
I am not sure how to just select ubuntu 8.10, the memtest86 test is in the same line.. during the start up its something like..

ubuntu 8.10, memtest86+
other operatiing system:
windows XP

How do I remove it from the memory.

---

### Post by dakiro on 2009-02-18
I have the same problem. The only option for boot after install is the damn memorytest.. 

I am very disappointed since I really wanted to have xubuntu on my pc. After fighting with the faulty install (I had to manually unmount one drive for the partitioner to work) I can't boot it.
the only usable entry in grub is 

title		Ubuntu 8.10, memtest86+
uuid		40f83cb8-4eb3-487f-b72f-2f8cfd9f9761
kernel		/memtest86+.bin
quiet
, I made a separate boot partition as well, and there is only a initrd.img-2.6.27-7-generic file, again with no reference to it in the menu.lst. Despite looking everywhere, I can't find the vmlinuz file though... 
What the heck is that supposed to be??? Should I copy a vmlinuz from a different ubuntu install or what? 
I would appreciate it if you could help me with this.
Regards

---

### Post by dakiro on 2009-02-22
open the cd or iso file, copy the vmlinuz and initrd.gz files from /casper, copy them to /boot in /boot.
Add a stanza to menu.lst (in /boot/grub) 

[CENTER][B]title Xubuntu
rootnoverify (hd0,5)
kernel (hd0,0)/boot/vmlinuz root=/dev/sda6 keyb=us ro
initrd (hd0,0)/boot/initrd.gz[/B][/CENTER]
(just an example of mine - with grub for dos on the windows partition)

---

