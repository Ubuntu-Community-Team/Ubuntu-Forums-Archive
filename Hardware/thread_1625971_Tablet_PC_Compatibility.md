---
title: "Tablet PC Compatibility?"
date: 2010-11-19
forum: Hardware
---

### Post by pjrandall on 2010-11-19
I'm  getting a tablet notebook from one of my friends, and I'm planning on installing Ubuntu. The question is, will I be able to use the pen-sensitive screen with Ubuntu? Does it natively support it, or will I need a specific distro or program? Thanks.:p

---

### Post by Favux on 2010-11-19
Hi pjrandall,

It depends a little on who makes the digitizer or touchscreen in the tablet pc but most either work out of the box or only require a little configuration.  So to answer your question we need to know who makes the tablet pc and what model is it?

---

### Post by pjrandall on 2010-11-20
OK, I'll get the make and manufacturer as soon as I can :)

---

### Post by pjrandall on 2010-11-20
OK, I called him and it is an HP Compaq TC4200. I actually had him install Ubuntu and it's working great with the pen input!

---

### Post by Favux on 2010-11-20
Hi pjrandall,

Great.  :)

The HP Compaq TC4200 has a Wacom digitizer.  I believe the internal connection to the digitizer is serial not usb.

The Wacom drivers in Maverick (10.10) work well.  You should be set.

---

### Post by pjrandall on 2010-11-20
> **Favux said:**
> Hi pjrandall,

Great.  :)

The HP Compaq TC4200 has a Wacom digitizer.  I believe the internal connection to the digitizer is serial not usb.

The Wacom drivers in Maverick (10.10) work well.  You should be set.

Thanks very much! Cheers!:D

---

### Post by pjrandall on 2010-11-20
Really quick question: When I rotate the screen into portrait orientation, will the desktop rotate like it does in WinXP Tablet Edition?

Edit: Would Ubuntu Netbook edition work with the Tablet input? It is a bit old, and I've heard that Netbook ed. is a bit easier on older and smaller comps.

---

### Post by Favux on 2010-11-20
Probably not unless the swivel hinge has a switch that uses ACPI and the old ACPI rotation script is still in there.

If there is a swivel hinge switch and it uses hp-wmi you'd be able to use Magick Rotation.  Linked in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Otherwise you can use one of the scripts there in a launcher or bind one to a key.

You might like a Netbook edition.  I haven't ever installed one so I don't know much about them.  You might want to go with a standard Ubuntu gnome desktop install and get comfortable before you try it though.

---

### Post by pjrandall on 2010-11-20
> **Favux said:**
> Probably not unless the swivel hinge has a switch that uses ACPI and the old ACPI rotation script is still in there.

If there is a swivel hinge switch and it uses hp-wmi you'd be able to use Magick Rotation.  Linked in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Otherwise you can use one of the scripts there in a launcher or bind one to a key.

You might like a Netbook edition.  I haven't ever installed one so I don't know much about them.  You might want to go with a standard Ubuntu gnome desktop install and get comfortable before you try it though.

Thanks for all the advice, although I already use Ubuntu on my main machine.You've been really helpful. :biggrin:

---

### Post by pjrandall on 2010-11-23
I tried reinstalling 10.10, and it's loading straight into a GRUB Rescue screen with an message saying 
ERROR: out of disk.
GRUB RESCUE:

---

