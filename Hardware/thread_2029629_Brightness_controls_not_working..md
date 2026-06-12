---
title: "Brightness controls not working."
date: 2012-07-19
forum: Hardware
---

### Post by pato wlmc on 2012-07-19
My distro is Ubuntu 12.04, Laptop: Toshina Satellite P775D.

Ok, so my laptop brightness controls aren't working. I've searched for several solutions, yet none seems to work for me.

Any help would bne apreciated. I'll keep searching, and if I find anything I'll let you know :)

P.D. I foun a solution, or at least a work-around the issue. See the last post for details.

---

### Post by NikTh on 2012-07-19
Hi , 
Try to set a parm in Grub . 

Open a terminal (ctrl+alt+t) and copy-paste this command 
```
gksudo gedit /etc/default/grub
``` it will prompt you for your password , write it and a window will open. Search for this line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
and make it exactly like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" **
Save the file and close window 
At terminal run this command 
```
sudo update-grub
```After finish , reboot you pc and see if brightness controls work.
Thanks

---

### Post by Toz on 2012-07-19
What video card do you have? Open a terminal window, type in the following command and post back the results:
```
sudo lspci -vnn | grep -A10 VGA
```

If its an ATI or nvidia card, have you installed the proprietary drivers?

---

### Post by pato wlmc on 2012-07-19
> **NikTh said:**
> Hi , 
Try to set a parm in Grub . 

Open a terminal (ctrl+alt+t) and copy-paste this command 
```
gksudo gedit /etc/default/grub
``` it will prompt you for your password , write it and a window will open. Search for this line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
and make it exactly like this 
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" **
Save the file and close window 
At terminal run this command 
```
sudo update-grub
```After finish , reboot you pc and see if brightness controls work.
Thanks

Gonna Try this. Also, here's the results of "sudo lspci -vnn | grep -A10 VGA"
```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G] [1002:9641] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device [1179:fc00]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=256]
	Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>


```

And, curious, I thought I had propietary drviers enabled, but somehow seems like they disabled themselves. I'll enable them and reboot. Back to you in a few minutes..

---

### Post by pato wlmc on 2012-07-19
Ok, activated propietary drivers, nothing. Added that line to xorg.conf, and nothing. I'll keep searching.

---

### Post by pato wlmc on 2012-07-20
Ok, so here's an update. When I press f6 or f7, the brightness Icon DOES appear on the screen, though, nothing actually changes. But when I edit "/sys/class/backlight/acpi_video0/brightness" It does changes the brightness level. What the freak does this mean?
I'll try to find a solution and post it here, if it gets to be of some hel to anyone.

---

### Post by pato wlmc on 2012-07-20
Ok, so here's the solution I found. This command is the only way in which I can change my Laptop brightness. 
```

echo X |sudo tee /sys/class/backlight/acpi_video0/brightness 
```

Where "X" is any number between 1 and your laptop max_brightness capacity. Here's How you can find that number:

```

cat /sys/class/backlight/acpi_video0/max_brightness

```

In my case, is a range bettween 1 and 7. So I just created an alias for every level of brightness. In a way that 
```

echo 3 |sudo tee /sys/class/backlight/acpi_video0/brightness 

```

Is now:
```
zbright3
```

Note: I added the 'z' so I can just write 'zb' and then press tab, to make things faster.

Anyway, Is probably not the most effective solution, but It sure works well for me. If you're not afraid of the terminal, it should work just fine for you as well.

---

### Post by Toz on 2012-07-20
Does using the **acpi_backlight=vendor** kernel parameter make your function keys work properly?

---

