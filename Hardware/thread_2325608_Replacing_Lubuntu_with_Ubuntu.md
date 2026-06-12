---
title: "Replacing Lubuntu with Ubuntu"
date: 2016-05-23
forum: Hardware
---

### Post by dhaneku.b on 2016-05-23
[COLOR=#111111][FONT=Ubuntu]I installed Lubuntu 16.04, and noticed quite a few bugs. I want to remove this OS, and put Ubuntu 14.04 on instead.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When giving the Linux partition back to Windows, I understand that you need to put the Windows 10 .iso onto a flash drive, and repair Windows from there.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However, I don't want to give the partition back to Windows. I want to delete the Lubuntu volumes from disk manager, leave it unallocated, and put Ubuntu in it's place. Is this possible? Or do I have to give the partition back to Windows, then re-partition it for Ubuntu, and then install Ubuntu in the re-created unallocated disk space?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks![/FONT][/COLOR]

---

### Post by Dennis N on 2016-05-23
All you need to do is boot the Ubuntu live media, start the Installer, and use the "something else" option when you come to the "Installation Type" screen. Then on the next screen, select the existing Lubuntu partition, click on the "Change" button, and in the popup dialog, designate it as the / partition for Ubuntu. I would also mark it to be formatted. You can keep the same swap partition that you created for Lubuntu. You can then proceed with the installation.

---

