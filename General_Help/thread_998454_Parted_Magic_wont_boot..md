---
title: "Parted Magic wont boot."
date: 2008-11-30
forum: General Help
---

### Post by Flaffen on 2008-11-30
I have an issue, I installed Wubi like the instructions said, then partitioned and transferred Ubuntu to a seperate partition. Now I want to get rid of Windows and the Wubi install in Windows, problem is that I cant boot Parted Magic anymore, I just get error 17 or error 15 (cant mount partition or file not found).
So what can I do to get Parted Magic to boot again? So I can get rid of windows? And will this **** up Grub?
Btw, I'm a linux noob.

---

### Post by ago on 2008-12-01
Assuming you are booting linux from a dedicated partition (cat /proc/mounts), AND that grub is in the MBR (i.e. that grub is the default bootloader, started before ntldr), then you can simply delete the windows partition from within ubuntu with tools such as gparted.

---

