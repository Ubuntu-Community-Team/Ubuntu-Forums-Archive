---
title: "Lenovo x100e won't boot (Network?)"
date: 2010-05-21
forum: Hardware
---

### Post by frioux on 2010-05-21
Hey guys,

I just got a lenovo x100e and installed ubuntu on it with the usb-creator.  Booting into the installer works fine, but when I actually try to boot it up after install it crashes/freezes.  I think it's a kernel panic but I don't even know what logs to look at to see what's going on.  I'm pretty sure that it's a network issue because when I booted it at work where I have no wifi it worked until I plugged into a wired socket.  After that it immediately froze.  Then at home where I have wifi all over the house I can't even got it to the login screen.

Any help at all would be appreciated.

---

### Post by frioux on 2010-05-22
No one?  No ideas?

---

### Post by crunchfighter on 2010-07-24
Just tried to install Ubuntu and Fedora on my x100e.  It keeps freezing for me too.  Did you ever find a solution?

---

### Post by jerrykenny on 2010-07-25
Hard to see whats wrong here . . .  .two suggestions

One . . . look into your BIOS and make sure your boot device priority is set to boot into your dvd drive, AND your hard drive . . . 

Two . . . If you do ever get the thing to boot successfully, edit (as root) the file /boot/grub/menu.lst     look at your kernel entry and delete the word "splash" . . . your next bootup will then display the bootup feedback.

Mad partitioning schemes might make the thing unbootable. Mad BIOS settings can also be a problem eg turning off the Sata controller chip, albeit this is unlikely to be the case on a laptop.

---

### Post by crunchfighter on 2010-07-25
> **jerrykenny said:**
> Hard to see whats wrong here . . .  .two suggestions

One . . . look into your BIOS and make sure your boot device priority is set to boot into your dvd drive, AND your hard drive . . . 

Two . . . If you do ever get the thing to boot successfully, edit (as root) the file /boot/grub/menu.lst     look at your kernel entry and delete the word "splash" . . . your next bootup will then display the bootup feedback.

Mad partitioning schemes might make the thing unbootable. Mad BIOS settings can also be a problem eg turning off the Sata controller chip, albeit this is unlikely to be the case on a laptop.

Thanks for the feedback.  I found the bug report talking about how this happens to the x100e laptop when booting on battery power.  Solution was to interrupt boot and set "radeon.modeset=0" in grub.  I can't find the thread that solved it now.  If I do, I'll edit the post and link it here.

How do I mark this as "Solved"?

Edit: [http://ubuntuforums.org/showthread.php?t=1415792&highlight=x100e](http://ubuntuforums.org/showthread.php?t=1415792&highlight=x100e)
[http://swiss.ubuntuforums.org/showthread.php?p=9210552](http://swiss.ubuntuforums.org/showthread.php?p=9210552)

---

