---
title: "Gnome won't start after laptop has been to sleep and woken up (Thinkpad T21)"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Sleeper Service on 2005-07-26
This problem originally started because my on-board network card didn't work.  I'm using an IBM Thinkpad T21.

I followed advice on these forums and altered my /boot/grub/menu.lst file to include acpi=off noacpi.  I also added apm to my /etc/modules.

All of this means Ubuntu now recognises my on-board ethernet card, and for the first time the power-management stuff seems to be working.

But if the laptop has gone into standby/sleep mode, Gnome will not start once the laptop has woken up again.  When I log in and chose Gnome (as any of three users set up on this machine), I'm just presented with a brown background.  The only way to get out is to restart gdm.

Other window managers seem to be fine - even Xfce4 which is loading some Gnome components.

Can anyone suggest what might be happening?  I wondered if some Gnome components weren't starting properly when the laptop wakes up...  but I don't know where to start looking...


(And while we're about it, does anyone know how to switch automatic standby off?  I'd like to leave the laptop running but tucked out of the way with the lid down, where I can ssh into it from my desktop - but with apm, shutting the lid causes it to go into standby so ssh is impossible..)

---

### Post by netsyd on 2005-07-26
I haven't used apm (I'm new to Linux), but I know with ACPI there is /etc/acpi/events/lidbtn ---- which in turn calls the /etc/acpi/lid.sh script. I would assume there is something similar to this in apm that you could just go in and remove the lidbtn event...

---

