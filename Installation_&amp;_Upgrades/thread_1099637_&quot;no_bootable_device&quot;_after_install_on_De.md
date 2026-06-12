---
title: "&quot;no bootable device&quot; after install on Dell laptop"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by jackwarr on 2009-03-18
I just loaded 8.10 to a Dell latitude laptop.  All appeared to go well.  I ejected the CD and rebooted, but the laptop is telling me that no bootable device is detected.  Any ideas?

---

### Post by Sanus Compleo on 2009-03-18
Chances are you still have your computer set to boot to cd, change that back to boot to your first hard-drive and it should boot.

---

### Post by jackwarr on 2009-03-18
It is set to try to boot in the following order:

1. floppy
2. CD
3. hard drive

Shouldn't it go right down the list?

---

### Post by Mark Phelps on 2009-03-18
Yes ... it should.

You should boot from a liveCD and confirm that Ubuntu exists on your machine.

Did you install over an existing MS Windows OS (Vista?), did you install for dual-boot, or did you install to a clean drive?

---

### Post by lykwydchykyn on 2009-03-18
I don't know if you chose manual partitioning, but if you did, check in GParted from the liveCD and make sure at least one partition (either the root partition, or a Windows or /boot partition if you have one) is marked active (or bootable).

I've forgotten to do this before.

You also might try reinstalling GRUB from the liveCD.  I believe the command is just "grub-install".

---

### Post by jackwarr on 2009-03-18
This is a fresh install on a clean drive.  I will try the last couple of suggestions.

---

### Post by jackwarr on 2009-03-18
I tried installing once again and it didn't appear to work.  I'm still getting the message "no bootable devices"

I'm not sure how exactly to do the grub-install command.  It looks like it needs a variable like a location or something.

---

### Post by lykwydchykyn on 2009-03-19
> **jackwarr said:**
> I tried installing once again and it didn't appear to work.  I'm still getting the message "no bootable devices"

I'm not sure how exactly to do the grub-install command.  It looks like it needs a variable like a location or something.

Sorry, yes, it needs a device name.  If you only have the one drive, it'd probably be:
```

grub-install /dev/sda

```

---

### Post by meierfra. on 2009-03-19
> make sure at least one partition (either the root partition, or a Windows or /boot partition if you have one) is marked active (or bootable).

It does not matter what partition you mark as active, but it needs to be primary partition (/dev/sda1,/dev/sda2,/dev/sda3 or /dev/sda4) 

If you have more than one hard drive, see what happens if you change the boot order in  the bios.


In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

