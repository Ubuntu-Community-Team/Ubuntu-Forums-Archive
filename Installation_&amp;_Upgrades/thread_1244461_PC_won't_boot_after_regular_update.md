---
title: "PC won't boot after regular update"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by KneadToKnow on 2009-08-19
8.04 LTS on Dell OptiPlex GX260, Pentium 4 2.4 GHz, 256 MB RAM.

I ran an update this morning, a very common task. I think it updated 3 files with lib or xlib in the names (sorry, I didn't pay very close attention). The update required a reboot, and I obliged.

Now my computer won't boot. It POSTs, then I get the GRUB loader screen, then I get "Loading please wait" and it goes into never-never land.

Is there a way via booting from a live CD or some other way to undo the update or figure out what got broken?

---

### Post by Sam Lars on 2009-08-19
Does it give you the option to press Esc to get into the Grub menu? You should be able to try a different kernel, or safe mode from the list.

---

### Post by karx11erx on 2009-08-19
Are you able to tell the boot loader to stop after a certain run level and boot in a text console window? The update may have changed X server files and thus have broken graphics driver integration with it. If this is the case, reinstalling the gfx driver may help.

---

### Post by checoimg on 2009-08-19
...

---

### Post by Sam Lars on 2009-08-19
When you boot, it should show the BIOS screen, and directly after that it should go to something about Grub... you can try pressing Esc to get into it.
If you're sure Grub isn't coming up, then you should [reinstall Grub]("http://ubuntuforums.org/showpost.php?p=7815057&postcount=16") from the LiveCD.

---

### Post by checoimg on 2009-08-19
...

---

### Post by Sam Lars on 2009-08-19
I think it's just
```
setup (hd0)
```

---

### Post by checoimg on 2009-08-19
...

---

### Post by KneadToKnow on 2009-08-20
> **Sam Lars said:**
> Does it give you the option to press Esc to get into the Grub menu? You should be able to try a different kernel, or safe mode from the list.

I was able to access Grub and assuming the top-most listed one is the default, I booted to the next one down, **Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)**.

First time around, I got errors from fsck saying that sda1 needed to be checked, leading to a long series of messages starting

ata2.00: status: { DRDY ERR }
ata2.00: error { UNC }

Under the impression that I shouldn't try to use fsck on a mounted volume, I booted from a SysRescCD live CD and ran fsck from there against the drive.

After rebooting, I no longer get the error about fsck needing to be checked, but I'm still getting plenty of the ata2.00 errors.

---

### Post by Sam Lars on 2009-08-20
> **KneadToKnow said:**
> After rebooting, I no longer get the error about fsck needing to be checked, but I'm still getting plenty of the ata2.00 errors.

Is it possible that something is wrong with your drive?

---

### Post by Sam Lars on 2009-08-20
> **checoimg said:**
> When "setup (hd0)" I get error 17

What you said you got from
```
setup (hd0,0)
```
looks like what you want... still no Grub after that?
Also... have you tried Alt+F1 to get to a terminal when it boots?

---

### Post by checoimg on 2009-08-20
...

---

### Post by KneadToKnow on 2009-08-20
> **Sam Lars said:**
> Is it possible that something is wrong with your drive?

Anything's possible. :)

I'm going to try running fsck again.

---

### Post by checoimg on 2009-08-20
...

---

### Post by KneadToKnow on 2009-08-21
> **Sam Lars said:**
> Is it possible that something is wrong with your drive?

Well, I ran PowerMax against the drive (it's a Maxtor, obviously) and it certified the drive free of errors. Still getting tons of the DRDY ERR messages, though, after booting is to ESC to the GRUB menu and boot in recovery mode. I'm not sure if I understand the difference for Ubuntu between booting in recovery mode, so maybe I'm just getting the visual output here that I don't normally see when booting?

Anyway, I'm beginning to think it's time to reinstall the OS, barring other suggestions.

---

### Post by checoimg on 2009-08-26
...

---

### Post by Sam Lars on 2009-08-26
> Can I store the updates without installing them with this?
Yes, that's what that option is for.
> Anyway, I'm beginning to think it's time to reinstall the OS, barring other suggestions.
I agree, if you've tried fsck and are still getting errors, a reinstall might be be best bet.
> Is just that my system wont boot if I have any usb device polugged maybe cause of my bott sequence. 
I've noticed the same thing, sometimes I forget and leave some USB device plugged in and it sits there forever trying to boot from it. I think it's because USB is placed above the hard drive in the boot sequence.

---

