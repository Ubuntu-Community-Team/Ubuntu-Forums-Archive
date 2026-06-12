---
title: "Suggestion for replacing a secondary hard drive"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by Jaymoon on 2006-12-13
Ok, here's my situation.  I had Suse installed on my computer, then I switched to Xubuntu.

Not thinking that it would make any difference, I kept the Suse hard drive (master) hooked up, as I installed Xubuntu to the slave drive.

When the system is turned on, I can boot either Xubuntu, or Suse.  That's fine.

But now I want to take out the Suse drive, and stick in a blank drive for Windows.  But when I take out the Suse drive (master), and make the Xubuntu drive the new master, I get the Error 21 with Grub.

I assume that Grub is installed onto the Suse drive.  Now my question is, how exactly would I go about taking out the Suse drive, making the Xubuntu drive the new master, and being able to install Windows to the new slave?

Thanks in advance. ;)

---

### Post by thelocust on 2006-12-13
[SIZE="2"]**Make your self a grub floppy disk. The easiest way is to get the alternitive install cd use the rescue broken system option and reinstall grub to (fd0).**[/SIZE]

---

### Post by Jaymoon on 2006-12-13
> **thelocust said:**
> [SIZE="2"]**Make your self a grub floppy disk. The easiest way is to get the alternitive install cd use the rescue broken system option and reinstall grub to (fd0).**[/SIZE]

Thank you very much.  Seems to have worked, so I can at least fall back to that floppy, in case something goes wrong.

---

### Post by Jaymoon on 2006-12-13
Well if anyone is interested in how it went...

I install Grub to the floppy, thinking that I could just edit the .conf file to tell it where the install of Xubuntu and Windows was.

Unfortunately, that's not the case.

In the end, I wiped all 3 drives, installed Windows, then installed Xubuntu.

I hate you Grub. :mad:

---

### Post by thelocust on 2006-12-13
**Sorry it didn't help you. Grub doesn't really play well with others. For future grub interaction you should check out [GrubEd]("http://ubuntuforums.org/showthread.php?t=228104&highlight=grubed") make sure you have zenity installed or it won't work. :cool:**

---

