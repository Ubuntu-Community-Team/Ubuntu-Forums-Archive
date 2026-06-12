---
title: "on boot &quot;ACPI: Unable to lacate RSDP&quot;"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by benanderson on 2007-05-12
I have Ubuntu 7.04 (used 6.10 to install and upgraded from there) on an old computer (around 7 years old, y2k). On boot with both 6.1 and 7.04 I get an error saying "[     000000] ACPI: Unable to locate RSDP". (Not sure how many zeros are in the brackets, so bare with me)
After that the system runs fine with no worries. But when I try to shut down it doesn't power off, the system itself shuts down and then hangs waiting for the power to cut out so I have to press and hold the button on the front of the tower for a while (about 15 to 30 seconds, it fluctuates). Any ideas?
It's not a major problem, it's just a pain in the ***.

---

### Post by chili555 on 2007-05-12
Perhaps your oldie doesn't support ACPI? If you press ESC as the machine is booting, you can edit your boot parameters. I would edit the line that looks something like this:```
/boot/vmlinuz-2.6.20-15-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
```to add the following:```
pci=noacpi acpi=off
```Boot up and see if your problem is fixed. If so, you can *sudo gedit /boot/grub/menu.lst* to add these items permanently.

---

### Post by benanderson on 2007-05-12
> **chili555 said:**
> Perhaps your oldie doesn't support ACPI? If you press ESC as the machine is booting, you can edit your boot parameters. I would edit the line that looks something like this:```
/boot/vmlinuz-2.6.20-15-generic root=UUID=4b70eff7-c255-4e38-9af6-1a9d9af90fe3 ro quiet splash
```to add the following:```
pci=noacpi acpi=off
```Boot up and see if your problem is fixed. If so, you can *sudo gedit /boot/grub/menu.lst* to add these items permanently.

So is using the "pci=noacpi acpi=off" the same as activating the legacy power interface under windows? Just checking. =]

---

### Post by chili555 on 2007-05-12
I dunno, I haven't used Windows for many years. They still have viruses and BSOD?

---

### Post by benanderson on 2007-05-15
why yes they do! not so much the BSOD with xp now... i think it's red in vista too ... hmmm RSOD.... not as catchy =P

---

