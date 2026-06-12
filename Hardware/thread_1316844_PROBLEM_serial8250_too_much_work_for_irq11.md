---
title: "PROBLEM: serial8250: too much work for irq11"
date: 2009-11-06
forum: Hardware
---

### Post by clauber on 2009-11-06
People,

I need some help here. I have a desktop with intel dualcore processor and an ubuntu 64bits OS installed.

The thing is: when i start my computer, it gets too slow. The load avarage goes up to sky and sometimes my Ubuntu freezes. On screen i see this warning: serial8250: too much work for irq11 over and over...

After a while (if it don't freeze), my system goes back to the normal. But this problem is getting me nuts. :mad: I'd like to find some solution for it.

This is my dmesg | tail response:
clauber@clauber-desktop:~$ dmesg | tail
[  109.393160] serial8250: too much work for irq11
[  109.394290] serial8250: too much work for irq11
[  109.401194] serial8250: too much work for irq11
[  109.403715] serial8250: too much work for irq11
[  109.405024] serial8250: too much work for irq11
[  109.449875] serial8250: too much work for irq11
[  109.450970] serial8250: too much work for irq11
[  109.458237] serial8250: too much work for irq11
[  109.459346] serial8250: too much work for irq11
[  109.460559] serial8250: too much work for irq11

---

### Post by iponeverything on 2009-11-06
Are using pppoe? As a test, kill off pppd to see clears up the issue:

```
sudo killall -v pppd

```

Maybe too... try booting with these options:

```
noapic pci=routeirq
```

---

### Post by clauber on 2009-11-06
With this new grub2 i don't know anymore how to set those things up. I've disabled the ACPI in Bios, but the problem persisted.

I'm going to try your tips later and i'll give you a feedback. Now i have to work. :-P

Thanks.

---

### Post by mneish on 2009-11-06
I have a similar problem after upgrading from 9.04 to 9.10 (32-bit).  'dmesg' is filled with the line 'serial8250: too much work for irq16'.  I tried the boot options suggested by [https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems), but it didn't help.  If I look in the directory /proc/irq/16, I have 'nvidia' and 'ohci1394', which I'm guessing is my video card and the firewire from my sound card (is this even the right place to look?  I'm kind of a newb).  I'd be interested to see what hardware clauber was having conflicts with, if there's some kind of pattern.

FWIW, my first attempt at a workaround was to blacklist all the firewire modules in /etc/modprobe.d/blacklist-firewire.conf.  Unfortunately, I still get the same error messages whenever I boot.  If I check out /proc/irq/16, It looks like I'm conflicting with 'nvidia' and 'serial'.  The strange thing is, after a few minutes it seems to resolve itself, and the error messages stop.  Still very annoying, though.

---

### Post by clauber on 2009-11-07
Guys,


I still having problems. iponeverything, i tried your suggestions, but with no success. I need some more assistance, because this grub2 is much more complicated than the anterior one.

---

### Post by clauber on 2009-11-11
The problem persists.... :-(

---

### Post by lord_zerg on 2009-11-14
I'm having the exact same problem

---

### Post by mneish on 2009-11-16
I was getting extremely frustrated with all the "serial8250" messages, so I did a clean install of 9.10 (I wanted to move to 64-bit anyway).  The problem seemed to go away, but then as soon as I enabled ANY of the nvidia restricted drivers, *BAM* irq conflicts.  Removing the drivers seems to "fix" the problem, but then I don't have any 3d acceleration :(
Anyway, clauber do you have an nvidia card?  You could try disabling any proprietary drivers and see if that helps at all...

---

### Post by clauber on 2009-11-24
I don't have any proprietary drivers installed in my system, neither nvidia cards.

The problem persists. :(:(:(

---

### Post by mneish on 2010-01-01
Hi clauber,

You could try removing modem-manager

sudo apt-get purge modemmanager

This seemed to resolve the problem for me (although I don't know if we had the same problem to begin with).

---

### Post by clauber on 2010-01-07
I did what you suggested and restarted my system and i got these messages with dmesg | tail command:

```

[   11.831507]    groups: 0-1 (__cpu_power = 2048)
[   13.918026] CPU0 attaching NULL sched-domain.
[   13.918031] CPU1 attaching NULL sched-domain.
[   13.940156] CPU0 attaching sched-domain:
[   13.940161]  domain 0: span 0-1 level MC
[   13.940166]   groups: 0 1
[   13.940174] CPU1 attaching sched-domain:
[   13.940177]  domain 0: span 0-1 level MC
[   13.940181]   groups: 1 0
[   21.310005] eth0: no IPv6 routers present

```

Before those messages, there are still those "too much work" warnings:
```

[   11.049303] type=1505 audit(1262887557.934:20): operation="profile_replace" pid=1098 name=/usr/sbin/cupsd
[   11.050831] serial8250: too much work for irq19
[   11.053368] serial8250: too much work for irq19
[   11.053953] type=1505 audit(1262887557.944:21): operation="profile_replace" pid=1099 name=/usr/sbin/tcpdump
[   11.054248] serial8250: too much work for irq19
[   11.064532] serial8250: too much work for irq19
[   11.065404] serial8250: too much work for irq19
[   11.066246] serial8250: too much work for irq19
[   11.071917] serial8250: too much work for irq19

```

I tryed to know what device is located in irq19. With the "ls /proc/irq/19/" i got:
```

clauber@clauber-desktop:~$ ls /proc/irq/19/
ata_piix  smp_affinity  spurious  uhci_hcd:usb3

```

---

