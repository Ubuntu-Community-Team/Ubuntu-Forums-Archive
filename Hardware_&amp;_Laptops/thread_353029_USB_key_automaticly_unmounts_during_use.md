---
title: "USB key automaticly unmounts during use"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by 7ofAnn on 2007-02-04
Hi All

First of all, I'm a total Linux/Ubuntu newbie, so excuse me if I post this at the wrong forum, or if this is a stupid question.

I have a USB disk key (512 MB - does not matter I guess), which automatically mounts when I plug it in (so far so good).  It functions, I can read files from it, and modify files on it, but after a while it is automatically unmounted.  It then reconnects, and unmounts again.  And so on and on and on.  Needless to say I can not work on the files anymore then.  Plus it is irritating, since I'm being notified that it unmounts, and that I should've clicked the icon to unmount it, and then that it mounts again.

I'm using Ubunty 6.10 on a MEDION laptop.  Everything else is working fine.  This is the only thing that really bugs me, since I make extensive use of USB disk keys.

I hope someone can help with this.

Thanks a lot
Ann

---

### Post by diskotek on 2007-05-13
hi all,

i have sam eproblem with feisty fawn 7.04. i have sony dsc-t3 camera. it's plugs itself as usb harddisk. but it unmounts itself aoutomatically, i can't copy any data from/to it. and also it warns "unsafe removal of usb device".. what can i do?

---

### Post by mssever on 2007-05-15
> **7ofAnn said:**
> I have a USB disk key (512 MB - does not matter I guess), which automatically mounts when I plug it in (so far so good).  It functions, I can read files from it, and modify files on it, but after a while it is automatically unmounted.  It then reconnects, and unmounts again.  And so on and on and on.  Needless to say I can not work on the files anymore then.  Plus it is irritating, since I'm being notified that it unmounts, and that I should've clicked the icon to unmount it, and then that it mounts again.
Sounds like a bad USB connection. What happens when you jiggle the key? You might have better luck plugging in into a different port. Or, you might not.
> **diskotek said:**
> i have sam eproblem with feisty fawn 7.04. i have sony dsc-t3 camera. it's plugs itself as usb harddisk. but it unmounts itself aoutomatically, i can't copy any data from/to it. and also it warns "unsafe removal of usb device".. what can i do?

Your problem might be the same as Ann's, but I really don't think its identical. You might wany to try mounting the camera manually, and see if that changes anything.

*For both of you*: You might want to monitor /var/log/messages to see if the system is recording the device rapidly connecting and disconnecting. If it is, you've probably had a bad connection (read: hardware problem). To monitor that log, type ```
less /var/log/messages
``` then hit <Shift>F.

---

### Post by Cornald on 2007-05-15
Same here,

under Edgy I made a backup to an external disk and can´t get it back after cleaning harddisk and new install of Feisty.
All external (USB-) Devices keep on unplugging, replugging, if not, they just make my desktop freeze without a chance of switching to a different workspace.

If I use a LiveCD (Knoppix, Feisty) everything works great. /var/log/messages doesn´t create any output during hangups....

I tested copying of a 680MB File from my desktop to a USB-Stick or an external Harddisk.
I used as well onboard USB and USB2.0 from an PCI-extension card plugged into my mainboard.

Board: ASUS A7N8X del. Rev. 2.0
AMD Athlon@2400

Any ideas?

[dmesg]("http://www.ubuntuusers.de/paste/10746/")

---

### Post by Cornald on 2007-05-15
[http://ubuntuforums.org/showthread.php?t=403725&page=6&highlight=usb+harddisk](http://ubuntuforums.org/showthread.php?t=403725&page=6&highlight=usb+harddisk)

similar problem

---

