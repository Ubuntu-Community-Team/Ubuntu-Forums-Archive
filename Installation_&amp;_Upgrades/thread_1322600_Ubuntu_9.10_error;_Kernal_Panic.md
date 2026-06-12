---
title: "Ubuntu 9.10 error; Kernal Panic"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Christopher8827 on 2009-11-11
After updating Ubuntu and rebooting, a error occurred while booting up: 

```

[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x37864000, size=0x78b7af]
[1.430898] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (8,1)

```

Please help me to fix this problem.

---

### Post by ninja togo on 2009-11-11
that same thing happened to me I can't reinstall or I will lose my school projects:icon_frown:. Please someone help us[-o<

---

### Post by janwillemk on 2009-11-11
hm, I have the same problem.:(

I'm using a 32bit Wubi installation and the recovery mode results in a kernel panic as well.

---

### Post by garikgarik on 2009-11-11
> **janwillemk said:**
> hm, I have the same problem.:(

I'm using a 32bit Wubi installation and the recovery mode results in a kernel panic as well.
same problem

---

### Post by Schobs on 2009-11-12
exactly the same issue here!....

---

### Post by Christopher8827 on 2009-11-12
any fixes found yet?

---

### Post by Christopher8827 on 2009-11-15
I hope I don't have to a reinstall...

---

### Post by iainmellis on 2009-11-16
Exactly the same problem. Is there anyway to report this directly to ubuntu.

---

### Post by tino.st on 2009-11-16
same same same error!!!

anyone could fix it?

---

### Post by Dale61 on 2009-11-17
Add another to the ever growing list.

I only had 9.10 installed, via WUBI, for a couple of days, so deleting it was any concern.  Fortunately, I still have 9.04 installed on the main desktop, so I still have at least one flavour.

---

### Post by mr.hope on 2009-11-21
I also got the same problem , too , is there anyone to help me out of this ? i dont want to lose my data !!! :(:(:(:(:(

---

### Post by Dale61 on 2009-11-21
Apparently, you can roll back to the previous kernel, and it should all work fine.

I just re-installed 9.10 via WUBI, and when the updates came up, the 'problem' kernel was marked as a new install, so the problem may have been fixed as I am now using the kernel that crashed.

---

### Post by ian_gary_price on 2009-11-22
I have the same problem. Error mesages while trying to start Ubuntu are:

1.444602 RAMDISK : Couldn't find valid RAMDISK image starting at 0

1.530541 No filesystem could mount root, tried : ext3 ext 2 ext 4 fuseblk

1.530766 Kermel panic - not syncing : vfs Unable to mount root fs on unknown block (8,2)

This has happened to me twice. First time I reinstalled, but this time I will loose files, so I really want to fix it. 

Does anybody know how to "rolll back the kernel"?

Gary

---

### Post by rad_rich on 2009-11-22
I've only recently installed Ubuntu as duel boot up with Vista on to my laptop and during an upgrade yesterday the laptop froze.

When i rebooted I have the same problem that people have listed here. I've seen a few solutions on other pages, but most of them go way over my head.

Can some one provide an idiot proof way to resolve this?

Thanks....

---

### Post by Christopher8827 on 2009-11-24
> **Dale61 said:**
> Apparently, you can roll back to the previous kernel, and it should all work fine.

I just re-installed 9.10 via WUBI, and when the updates came up, the 'problem' kernel was marked as a new install, so the problem may have been fixed as I am now using the kernel that crashed.

How do I roll back to the previous kernel? This is getting frustrating. :o

---

### Post by l_fonseca on 2009-11-24
> **Dale61 said:**
> Apparently, you can roll back to the previous kernel, and it should all work fine.

I just re-installed 9.10 via WUBI, and when the updates came up, the 'problem' kernel was marked as a new install, so the problem may have been fixed as I am now using the kernel that crashed.

So, for those who don't have a previuous kernel installed (like me), the only available solution is re-install wubi. Hope the problem have been fixed. I'm re-installing wubi.

---

### Post by Dale61 on 2009-11-24
To both of the above:

When you initially install 9.10, it has the 'original' kernel as a starter.  The first 'major' update installs the next kernel in line.

When you start your pc, you should be given an option of which kernel you want to boot into.  The 'newest' kernel is at the top, so you just choose the lower one.

---

### Post by grndnl on 2009-11-25
Ok, the info in this thread still does not help...
I have seen a LOT of people all over the internet with this same problem, all linked to the latest update (of, apparently, the kernel). There has to be an easier way than reinstalling it, thus the "boot with another kernel option" came in. Too bad people do not explain with enough detail WHEN:
> you should be given an option of which kernel you want to boot into. The 'newest' kernel is at the top, so you just choose the lower one.
that happens...

---

### Post by Dale61 on 2009-11-26
When you first boot up, you are greeted with a GRUB menu, giving you choices of how you want to boot up.

Linux kernel (newest)
Linux kernel (newest safe mode)
Linux kernel (oldest)
Linux kernel (oldest safe mode)
Memory test
Windows whatever.

If you can't boot into the 'newest' kernel, you then try the 'oldest'.  How difficult is that?

This is also why you should ALWAYS have at least two Linux kernel options in your GRUB.

My install is now running fine, but as I'm only a 'user', not a 'tech', I hope someone who knows what caused the problem can help you.

---

### Post by GraFfiX420 on 2009-12-14
I have the same issue, after the rc3 kernel update. I only have one kernel listed in grub so can't do that. I haven't been using my ubuntu install because im trying to wait for a way to recover. If we are missing something obvious here please some super user step in and shed some light.

---

### Post by Dale61 on 2009-12-14
I had an update download on Friday, and GRUB imploded again.

After some searching, I found this fix, which did work for me.

```
sh:grub linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro

sh:grub initrd /boot/initrd.img-2.6.31-17-generic

sh:grub boot
```

The 2.6.31-17-generic kernel is the latest one I have, and the sda2 points to the WUBI installation on the Windows partition.

If it all goes as planned, you should now be looking at Ubuntu.  If so, you now need to open a terminal, and type in:

```
sudo update-grub2
```

You should now be able to boot into Ubuntu as you normally would.

I also had four GRUB kernel entries, so to get rid of the two oldest ones, I went into Synaptic and marked for complete removal both of the oldest kernels (-14 and -15).

GRUB then recompiled itself, and now I only have kernels -16 and -17 to choose from (other than Vista).

If none of the above helps, replace the sda2 entry with sda1, or change the kernel version to -14, -15 or -16.

It did take me some time to get my head around it as I was trying the sda1 route, but once I tried it with sda2, all was sweet.

---

