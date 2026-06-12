---
title: "Wubi install gets me to grub but not to linux"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by JacksonHarding on 2009-10-10
I've just decided to migrate from Windows to Ubuntu and as a first step decided to try using Wubi to set up a Linux installation and start finding my way around.

The Wubi installer had lots of errors all the way along saying "Drive not found" however after several attempts and clicking Continue a lot of times the installer started, all seemed well.  Ubuntu was installed in a large folder, the installer seemed to work very nicely.

Now I have the dual boot system and I can boot into Windows or Ubuntu.  Choosing Ubuntu and I end up at the command prompt within Grub.  I have tried loading the kernel with no joy, I get a variety of errors telling me that the file is not found or that the kernel needs to be a blockname.

How do I mount the kernel and get started?

Jackson

---

### Post by stlsaint on 2009-10-10
i would recommend you reinstall ubuntu via wubi and also how did you install it the first time?

---

### Post by JacksonHarding on 2009-10-11
Thanks for your help.  I'd removed and re-installed Ubuntu via Wubi twice already.  I've just done it a third time.

Removing Ubuntu this time proved to be something of a chore, with WinXP wanting to run CHKDSK multiple times, seems there were a few disk problems.

I installed the first time (and second, and third) by running Wubi within windows, rebooting and continuing the install.  Each time it has resulted in a "half install"  The GRUB bootloader is now installed and it offers me Linux as a choice, however when I choose it I find myself at the Grub command prompt, not in a Gnome desktop under linux (which is were I expected to be).

On the positive side a full Ubuntu install onto an old laptop (Toshiba P20) has given me a fully functional Ubuntu system which is running a dream.

Jackson

---

