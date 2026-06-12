---
title: "DVD-ROM writer not recognized (lshw does, though)"
date: 2008-08-05
forum: Hardware
---

### Post by kc600 on 2008-08-05
Hi,

Sometime after installation of Gutsy, i want to mount a new CD burner instead of the old slow one. Problem is, when i insert a CD, nothing happens.

BIOS does recognize it: Although BIOS says "No conductor cable for secondary IDE channel", i can boot from a CD on it (although no Ubuntu 8.04, because i get buffer I/O errors, but a Knoppix 4.0 live CD seems to work). And it does get detected:

$ lshw
           *-cdrom
                description: DVD-RAM writer
                product: DVDRRW GSA-4166B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                serial: [HL-DT-STDVDRRW GSA-4166B1.0205/11/14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1

I tried to mount it manually (mount /cdrom) but it says "dev/scd0: no such device" (even though the file is there). 

Any clues, things to try, questions, would be appreciated.

PS This is on an old Athlon XP 1100 machine, not any of the machines below.

---

### Post by Qchan on 2008-08-05
> **kc600 said:**
> Hi,

Sometime after installation of Gutsy, i want to mount a new CD burner instead of the old slow one. Problem is, when i insert a CD, nothing happens.

BIOS does recognize it: Although BIOS says "No conductor cable for secondary IDE channel", i can boot from a CD on it (although no Ubuntu 8.04, because i get buffer I/O errors, but a Knoppix 4.0 live CD seems to work). And it does get detected:

$ lshw
           *-cdrom
                description: DVD-RAM writer
                product: DVDRRW GSA-4166B
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                serial: [HL-DT-STDVDRRW GSA-4166B1.0205/11/14
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1

I tried to mount it manually (mount /cdrom) but it says "dev/scd0: no such device" (even though the file is there). 

Any clues, things to try, questions, would be appreciated.

PS This is on an old Athlon XP 1100 machine, not any of the machines below.

[b][color=darkred]
I wouldn't be surprised if your BIOS was suffering from Foxconn'itcis

To fix this, try adding "acpi=off" without the quotations to your kernel boot options.

To do that, once your PC boots, you'll see either the Grub boot menu or a timer counting down to 0. If you see the timer, press ESC. That'll take you to the Grub boot menu.

Once at the boot menu, highlight the kernel version you wish to choose (if you can't decide, it'll be the one on the top) and press the e key. Once there, press the "END" button on your keyboard or simply use the arrow keys to scroll all the way to the right. Press the spacebar to add a little space. Now type in acpi=off   

After that, press enter and press b to boot from those options. 

That should fix your issue. If it doesn't come back here.
[/b][/color]

---

### Post by kc600 on 2008-08-08
You are so right! Thanks!

---

