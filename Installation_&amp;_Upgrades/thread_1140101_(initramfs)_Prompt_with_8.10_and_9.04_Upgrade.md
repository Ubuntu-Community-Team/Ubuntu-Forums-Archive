---
title: "(initramfs) Prompt with 8.10 and 9.04 Upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by nixguru on 2009-04-27
Before anyone says this is the same error as in other posts, the circumstances may be somewhat different.  Also, just so people know my technical level, I am a lead linux/unix administrator and have cross-compiled linux from scratch for embedded systems and such.

After upgrading from Ubuntu 8.04 (worked good) to 8.10 on my father's PC, using the provided kernel, I was getting dropped to the (initramfs) prompt on boot complaining about the UUID not being found.  Booting using the old kernel worked fine.  I decided maybe it was a fluke with the version of the kernel, and decided to make the leap to 9.04, since that was my goal anyway.  Same thing with 9.04.

Apparently the IDE disk devices are not showing up under /dev.  sdXX, hdXX, etc, are not there.  Nor is the path for accessing file systems by UUID.  It is as if the kernel module necessary for accessing the IDE devices is not present in the newer kernels.  This is a slightly older system with an XP1800+ and no SATA.  No RAID or anything setup here.

While I have him running to some extent with the old kernel from 8.04, this is not how I want to leave him.  I had read many posts from varios people with similar issues, but all seemed to have a different root cause.

Things I have tried:

1. Tried pathing root= to /dev/sdb1 (his boot partition) rather than UUID, but this was before I realized it didn't see the disk at all.
2. Setting rootdelay=60 in grub.
3. Installing the server version of the Ubuntu linux kernel, as someone suggested worked for them.  This didn't help.
4. Installed additional kernel module packages, after which the initrd image was recreated.  Didn't help.

I'm suspecting I will have to tell it to add an IDE kernel module that seems to be missing from the initrd image, but I first wanted to ask if anyone had experienced this exact cause -- disk was not seen at all.  If so, what did you do to fix it?

I could recompile the kernel and make it work, but I'd rather get this to work using the provided kernels to ensure upgrades to the kernel in the future go more smoothly.

---

### Post by nixguru on 2009-04-27
I just "fixed" it, so to speak.  Apparently the new kernels used in 8.10 and 9.04 have an issue with the MS-6390 motherboard chipset.  The 8.04 kernel never required this, but I simply set:

acpi=off

 ... on the kernel line in grub for the new kernels, and it worked like a champ.  Unfortunately this does mean there is some new bug with how the kernel is handling ACPI that did not exist in the older kernel used with 8.04.  I'm not sure I'm ambitious enough (or care enough) to submit a bug report unless someone wants/needs me to.  Since it isn't my computer, I didn't really want to spend the time to compile all of the necessary information unless someone thinks it could be fixed.

If anyone is having the initramfs issues where it drops you to the busybox prompt on boot, after installing a new version of Ubuntu and having verified no other fixes work, try this setting.  It may well work for you.

---

### Post by toastermm on 2009-04-27
> acpi=off

... on the kernel line in grub for the new kernels...

Sorry, how is this done?

I believe I have a very similar problem, just booting to a initramfs prompt.

---

### Post by nixguru on 2009-04-27
There were some other suggestions you can try, as well, based on another thread in the forums.  One or a combination of these might work for you, if acpi=off doesn't.  The way the problem manifested itself to me was by not seeing the disk drive devices at all.  If that is the same, and the below doesn't help, try that.

all_generic_ide
all_generic_ide irqpoll
all_generic_ide pci=nomsi
pci=nomsi
irqpoll
all_generic_ide floppy=off irqpoll pci=nomsi

All you have to do is add the acpi=off (or any of the other options) to your kernel boot string on boot when in the grub boot loader.  This allows you to test it for one time boots just to see if it works.  Best choice is to highlight recovery mode, press 'e', select the kernel line, then press 'e' again.

```
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah ro quiet splash
```Insert acpi=off at the end or after the root=UUID=blah-blah-blah statement, to look something like this:
```

kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah acpi=off ro quiet splash 

```

Press [enter] to commit your change, then 'b' to boot with it.

Recovery mode will allow you to see the boot process and where it could hang, but normal or single (recovery) mode would work fine to test.

---

### Post by bsmith1051 on 2009-04-28
Good detective work!  Is this a good solution for others?  It seems like a common problem, i.e., change in ATA compatibility with the new kernel.  I'm not nearly as technical as you but do you think you could report this in Launchpad?  It seems like there should be better auto-detection or auto compatibility testing or something.

---

### Post by toastermm on 2009-04-28
> There were some other suggestions you can try, as well, based on another thread in the forums. One or a combination of these might work for you, if acpi=off doesn't. The way the problem manifested itself to me was by not seeing the disk drive devices at all. If that is the same, and the below doesn't help, try that.

all_generic_ide
all_generic_ide irqpoll
all_generic_ide pci=nomsi
pci=nomsi
irqpoll
all_generic_ide floppy=off irqpoll pci=nomsi

All you have to do is add the acpi=off (or any of the other options) to your kernel boot string on boot when in the grub boot loader. This allows you to test it for one time boots just to see if it works. Best choice is to highlight recovery mode, press 'e', select the kernel line, then press 'e' again.


So I booted to the bash command, and here's the following output from the above commands:

> 
root@owner:~# all_generic_ide
bash: all_generic_ide: command not found
root@owner:~# all_generic_ide irqpoll
bash: all_generic_ide: command not found
root@owner:~# all_generic_ide pci=nomsi
bash: all_generic_ide: command not found
root@owner:~# pci=nomsi
root@owner:~# irqpoll
bash: irqpoll: command not found
root@owner:~# e
bash: e: command not found


> I'm not sure this is what should happen, the bash command does not recognize most of these commands.

```
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah ro quiet splash
```
Insert acpi=off at the end or after the root=UUID=blah-blah-blah statement, to look something like this:

```
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah acpi=off ro quiet splash
```
Press [enter] to commit your change, then 'b' to boot with it.

Recovery mode will allow you to see the boot process and where it could hang, but normal or single (recovery) mode would work fine to test. 

So here is that output:

> 
root@owner:~# kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah ro quiet splash
bash: kernel: command not found
root@owner:~# kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah acpi=off ro quiet splash
bash: kernel: command not found
root@owner:~# b
bash: b: command not found


Hmm... it doesn't even recognize the boot command, b.


---------------------

I also tried to put in a live cd to see if it would boot off of that- it did not even read the cd.  I checked the boot order, and USB and CD/DVD are above hard drive, so I'm not sure what to do now.

---

### Post by RainKap on 2009-07-08
Thanks for a useful post. I had two problems:

1. An oldish machine (Athlon XP1600 with Via chipset, 512MB, 20GB & 40GB IDE HD, IDE DVD-ROM and DVD writer) in which I'd replaced the HDDs (the Maxtor ones died) and wanted to install Jaunty; the direct install of Jaunty using the alternate CD wouldn't work, 'cos the installer couldn't see the DVD drive it had just booted from(!) so I installed from the 8.04 alternate CD and upgraded with the Jaunty alternate CD. However the machine refused to boot into the 2.6.28-13 kernel. After much scratching around, I tried putting "acpi=off" in the kernel line of /boot/grub/menu.lst, and it booted OK *but* wouldn't power down :( I've decided to drop back to a plain 8.04 install, because the PC is for someone else who wants to use it as an appliance, rather than doing esoteric things at the command line.

2. A rather newer machine (2 x dual core Opteron with nvidia chipset, 2 x 4GB RAM, 150GB and 4x320GB (RAID5 array) SATA HDD, 2xIDE DVD writer) which I updated to Jaunty a while back - it frequently hung during startup while trying to do HT MSI mapping. The "pci=nomsi" addition to the kernel line of /boot/grub/menu.lst seems to have cured this :)

Thanks again

Ian

---

### Post by junksortie on 2009-11-12
i,

i have the same problem. After i tried updating to 9.04 from 8.10, all I'm being greeted by is the initramfs.

as per the above discussion i tried the GRUB edit and inserted the "ACP=OFF and booted, still getting dropped to "INITRAMFS"

here's what appears when i boot.

MP-BIOS Bug: 8254 timer not connected to IO-APIC
FATAL: Error inserting fan: /dev/<BLAH> :No such device
FATAL: Error inserting thermal: <BLAH> : No such device

Gave up waiting for root device

ALERT! /dev/disk/by-uuid/<BLAH> does not exist

some one please let me know if there's a way out.

you can also contact me @ 

[email]ooliganism@gmail.com[/email]

---

### Post by junksortie on 2009-11-12
there's a quick .. howto page on this link . migh not solve the issue for most ... but jsut gives a intro on the subject

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

---

### Post by qneill on 2009-12-14
I'm fighting a similar problem, except it's a "General error mounting filesystems", e.g. [http://ubuntuforums.org/showthread.php?t=1336988](http://ubuntuforums.org/showthread.php?t=1336988)

> **toastermm said:**
> So I booted to the bash command, and here's the following output from the above commands

@toastermm, @nixguru is listing kernel parameters to try (gathered from some other threads).

These would need to be added to the grub menu item that is booting your kernel.

When booting, hit "esc" to interrupt grub, highlight the kernel you are booting (most likely the top item), hit 'e' to edit, then select 'kernel /boot...' and hit 'e' again to edit the boot parameters.

I deleted "splash" and "quiet" from the boot params to see what is going on at boot time.

-- 
Quentin

---

### Post by dobbod on 2009-12-17
> **nixguru said:**
> There were some other suggestions you can try, as well, based on another thread in the forums.  One or a combination of these might work for you, if acpi=off doesn't.  The way the problem manifested itself to me was by not seeing the disk drive devices at all.  If that is the same, and the below doesn't help, try that.

all_generic_ide
all_generic_ide irqpoll
all_generic_ide pci=nomsi
pci=nomsi
irqpoll
all_generic_ide floppy=off irqpoll pci=nomsi

All you have to do is add the acpi=off (or any of the other options) to your kernel boot string on boot when in the grub boot loader.  This allows you to test it for one time boots just to see if it works.  Best choice is to highlight recovery mode, press 'e', select the kernel line, then press 'e' again.

```
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah ro quiet splash
```Insert acpi=off at the end or after the root=UUID=blah-blah-blah statement, to look something like this:
```

kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=blah-blah-blah acpi=off ro quiet splash 

```Press [enter] to commit your change, then 'b' to boot with it.

Recovery mode will allow you to see the boot process and where it could hang, but normal or single (recovery) mode would work fine to test.

Thanks nixguru, this post really helped me. I managed to boot into Ubuntu at last. Thank you.

---

