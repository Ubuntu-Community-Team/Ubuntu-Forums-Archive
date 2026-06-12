---
title: "acpi problems"
date: 2008-10-13
forum: Hardware
---

### Post by woodenbrick on 2008-10-13
Hopefully someone can help me with this, it's been a long term problem for me..

I have been using Debian Lenny for about 6 months now, and recently installed Ubuntu on a seperate partition.  I prefer Ubuntu, but there is some hardware issue I cant figure out.  The only way I can boot it is if i append acpi=off to the boot line.  If I don't, it will freeze halfway through.  I can boot the Debian install with acpi so i'm wondering what the issue could be.

Some hopefully useful information:

grub menu.lst
```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6e3f4e7a-3186-4021-bb67-52fce272eb32 ro quiet splash acpi=off xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Debian Lenny amd64 (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.25-2-amd64 root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.25-2-amd64
savedefault
boot

```

---

### Post by cariboo on 2008-10-13
The difference may be the kernel. Your Debian install is running 2.6.25-2 while your Ubuntu install is using 2.6.24-9. You may want to upgrade your kernel to a newer version.

Jim

---

### Post by Patrick793 on 2008-10-13
I don't know if this is your problem, but I was having something like that. For me, I would wait and it would eventually boot.

Then I noticed that if I have something plugged into a usb drive (in my case, a usb mouse), it will not stall or anything, and boot smoothly.

---

### Post by woodenbrick on 2008-10-13
@cariboo: I'll give it a try and see how it works out.  How easy is it to upgrade the kernel? I haven't tried before
edit: do you also think the 64bit kernel has something to do with it?

@pat: It wont boot even if all USB ports are empty, however the Bios does make a second short beep if the usb mouse is plugged in.

---

### Post by akshay.sulakhe on 2008-10-13
i faced same problem on my machine...i updated my kernel and removed that noacpi line...i also used noapic..worst hardware...

---

### Post by woodenbrick on 2008-10-14
Ok I tried installing a new kernel: 2.6.27-7-generic
It freezes at this point:
```

Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init/bottom...
Done.
_

```
Then it freezes.

I tried copying over the kernel from my debian install and it seems to get a lot further, in fact gdm starts up, but then it freezes there at some point just as the panels are loading.

---

### Post by WWSmith36 on 2008-10-14
These tend to be related to bios / kernel.

I have solved this on different machines.  On one machine a bios update solved the problem and on another, I just waited for the new kernel and then I was able to remove acpi=off.

I hope one of these options will help

---

### Post by woodenbrick on 2008-10-18
Well I've kinda given up on this, I think there is something special in the Debian kernel that isn't in Ubuntu's which allows  computer to boot with the acpi on.  I tried adding the lenny repo and installing a kernel but I got kernel panic when I tried to boot up so maybe they aren't compatible.  Thanks everyone for the tips.

---

