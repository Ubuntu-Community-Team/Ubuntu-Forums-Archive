---
title: "Grub entries not displaying for boot choice"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2009-05-25
I just ran a kernel build using kernelcheck and it built fine.

In menu.lst the options for the new kernel are there but I do not have an option on bootup to choose it, they do not display.

Weird but true

Any thoughts?

---

### Post by taurus on 2009-05-25
Are you using GRUB?  Post your /boot/grub/menu.lst.

---

### Post by VastOne on 2009-05-25
> **taurus said:**
> Are you using GRUB?  Post your /boot/grub/menu.lst.

Yes

title		Ubuntu 9.04, kernel 2.6.29.4-candela
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.29.4-candela
quiet

title		Ubuntu 9.04, kernel 2.6.29.4-candela (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.29.4-candela root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.29.4-candela

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=428ae622-173c-4eb7-a1c1-5958387d6b46 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		428ae622-173c-4eb7-a1c1-5958387d6b46
kernel		/boot/memtest86+.bin
quiet

---

### Post by taurus on 2009-05-25
Is candela the one?  When you said no option to choose, are you talking about the GRUB menu?  Maybe you have **hiddenmenu** in /boot/grub/menu.lst so you wouldn't see the menu.  Try pressing Esc when you see the word GRUB on the screen or comment it out in /boot/grub/menu.lst.

---

### Post by VastOne on 2009-05-25
> **taurus said:**
> Is candela the one?  When you said no option to choose, are you talking about the GRUB menu?  Maybe you have **hiddenmenu** in /boot/grub/menu.lst so you wouldn't see the menu.  Try pressing Esc when you see the word GRUB on the screen or comment it out in /boot/grub/menu.lst.

Candela is what is missing.  From 2.6.28-12 down is my original menu.lst and is all that is showing up in grub.

I am hitting esc and there I am presented grub but instead of seeing Candela and all the options shown in menu.lst, all I see is my original grub with 2.6.28.-12 down.  It's as if there is another menu.lst/grub loading.

---

### Post by taurus on 2009-05-25
Install startupmanager and use it to configure your GRUB menu then.

---

### Post by VastOne on 2009-05-25
> **taurus said:**
> Install startupmanager and use it to configure your GRUB menu then.

I can do that, but why would an entry that is clearly in th emenu.lst not show up as a grub entry?

---

### Post by taurus on 2009-05-25
Did you set a limit number of kernels/entries you could have in /boot/grub/menu.lst?

---

### Post by VastOne on 2009-05-25
> **taurus said:**
> Did you set a limit number of kernels/entries you could have in /boot/grub/menu.lst?

No. And upon loading startupmanager that option is not ticked.

Rebooting now to see if there are any changes

---

### Post by VastOne on 2009-05-25
> **VastOne said:**
> No. And upon loading startupmanager that option is not ticked.

Rebooting now to see if there are any changes

Still a no go.

Startupmanager sees the menu.lst and all of it's options but does not display it as a grub entry.

I am going to switch to Candela as the default within startup manager to see if that triggers anything

---

### Post by VastOne on 2009-05-25
> **VastOne said:**
> Still a no go.

Startupmanager sees the menu.lst and all of it's options but does not display it as a grub entry.

I am going to switch to Candela as the default within startup manager to see if that triggers anything

When startupmanager starts the first line is

Grub2 not detected


I thought grub2 was the default in jaunty or ext4 installs or was it left out?

---

### Post by VastOne on 2009-05-25
Starting startupmanager displays the following:

Grub2 not detected
sh: convert: not found
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29.4-candela
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


It appears to be updating the menu.lst correctly and saves it when it is done.

Yet I still get original grub menu with only 2.2.28-12 and -11 as options

There must be something borked that is allowing another menu.lst to load and execute

Is grub2 the standard loader now in Jaunty and ext4 systems?

---

### Post by taurus on 2009-05-25
I don't know about your system but on my jaunty, it uses GRUB (0.97-29ubuntu53), not GRUB2.

---

### Post by VastOne on 2009-05-26
Solved! I had 2 drives with the same uuids :oops:

---

