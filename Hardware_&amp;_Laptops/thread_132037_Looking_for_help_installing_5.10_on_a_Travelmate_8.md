---
title: "Looking for help installing 5.10 on a Travelmate 8104"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by Jim Link on 2006-02-17
Hello,  I just purchased a Travelmate 8104 and have been trying to both install or run a live cd with no luck what so ever.  I have tried the following commands with no luck:

vga=771 noapic
noapic
noapic nolapic
noacpi
acpi=off

If anyone has gotten Ubuntu or Kubuntu to work I would love a quick how to for 5.10.  Thanks for any help in advance.

---

### Post by K.Mandla on 2006-02-17
Can you tell us more about what happens? If you're getting error messages, that will help. Does it freeze at a particular point? Are you using any unusual addons?

I'm guessing you've seen these threads already. ...

[http://ubuntuforums.org/showthread.php?t=80800](http://ubuntuforums.org/showthread.php?t=80800)
[http://ubuntuforums.org/showthread.php?t=46536](http://ubuntuforums.org/showthread.php?t=46536)

---

### Post by DerekRom on 2006-03-09
[QUOTE=Jim Link]Hello,  I just purchased a Travelmate 8104 and have been trying to both install or run a live cd with no luck what so ever.  I have tried the following commands with no luck:

vga=771 noapic
noapic
noapic nolapic
noacpi
acpi=off

If anyone has gotten Ubuntu or Kubuntu to work I would love a quick how to for 5.10.  Thanks for any help in advance.[/QUOTE]

Added line

Option "MonitorLayout" "LVDS,AUTO"

to file /etc/X11/xorg.conf

as recommended by dorris in existing tip: Acer Travelmate 8103 8100 8104.

Then I typed line

sudo/etc/init.d/gdm restart

and Graphical Mode started and I could explore.

I saved my changes when prompted on logout.

This was all done from recovery mode boot.

---

