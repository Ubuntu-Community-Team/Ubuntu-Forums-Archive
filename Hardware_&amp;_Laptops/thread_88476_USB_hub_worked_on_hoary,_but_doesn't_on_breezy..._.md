---
title: "USB hub worked on hoary, but doesn't on breezy... what happened?"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by melissawm on 2005-11-10
I had posted this in another forum but i just think this one is more appropriate.

I've been reading a lot of posts about problems with USB hubs and i can see they're problematic some times, but my hub worked just fine under hoary, and now that i've upgraded to breezy it suddenly disappeared. Individual devices are working if connected directly to the ports, but not in the hub. I have a Belkin 4 port 2.0 high-speed hub and it's not powered.

---

### Post by ranf on 2005-11-10
You can try selecting the 2.6.10 Kernel from Hoary in the bootup menu, if you still have it and see if it works then.

---

### Post by melissawm on 2005-11-11
In fact i had some problems during the installation - it wouldn't let me upgrade without formatting the whole linux partition, so i don't have it anymore... I just don't get it, upgrades are supposed to be better, not worse :(

---

### Post by ranf on 2005-11-11
[QUOTE=melissawm]In fact i had some problems during the installation - it wouldn't let me upgrade without formatting the whole linux partition, so i don't have it anymore...[/QUOTE]
That would have been a good test if your problem is kernel related.

Do you see the hub listed when you type this (in a terminal)?
```
lsusb
```

---

### Post by melissawm on 2005-11-11
Ok, this is what happened. I was having some problems with the usb modem also, so i decided to make a fresh installation and voila, everything works fine (after 3 complete installations however, because i was having some freaky display errors)

So thanks anyway! ;)

---

### Post by Mustard on 2005-11-11
Hmmm..be nice to have a better option to solve this issue than a clean install or going back to an old kernel.

(I'm on a powered hub)

I've just been chatting with multiple people in IRC support channel with the same issue.  It would be nice to have some answers for them.  Unplugging the usb drive and plugging it in again works for me, but thats a pretty clumsy solution.

lsusb output;
```
Bus 002 Device 004: ID 03f0:2f11 Hewlett-Packard
Bus 002 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 001 Device 001: ID 0000:0000

```

mount output;
```
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /lib/modules/2.6.12-9-686/volatile type tmpfs (rw,mode=0755)
/dev/hdb9 on /home type ext3 (rw)
/dev/hdb8 on /tmp type ext3 (rw)
/dev/hdb5 on /usr type ext3 (rw)
/dev/hdb6 on /var type ext3 (rw)
/dev/hda9 on /mnt/hda9 type ext3 (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```

---

