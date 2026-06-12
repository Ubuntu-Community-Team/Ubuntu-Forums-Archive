---
title: "how to uninstall ubuntu????"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by pranavgoyal40341 on 2008-12-21
Can anyone please explain me the whole procedure to uninstall ubuntu 8.04
I m using side by side windows XPS..
please tell me...

---

### Post by overdrank on 2008-12-21
> **pranavgoyal40341 said:**
> Can anyone please explain me the whole procedure to uninstall ubuntu 8.04
I m using side by side windows XPS..
please tell me...

Hi and this  can [_help_]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by pranavgoyal40341 on 2008-12-21
it's too big to understand....actually i m a begginer of ubuntu..can anyone tell some easy way to uninstall it...

---

### Post by infamous-online on 2008-12-21
Personally, I would never install the two on the same harddrive to avoid this conflict altogether. Actually the link that was provided seemed straight-forward, so perhaps you should take another look. ;)

---

### Post by caljohnsmith on 2008-12-21
> **pranavgoyal40341 said:**
> it's too big to understand....actually i m a begginer of ubuntu..can anyone tell some easy way to uninstall it...
In order to uninstall Ubuntu, the main thing is just to restore a Windows MBR (Master Boot Record) so that you can boot directly into Windows again. Once you can boot directly into Windows, you can use a partition editor to delete the Ubuntu partitions, or format them to use the Windows NTFS file system so you can use the partitions in Windows. To restore a Windows MBR, if you have your Windows Install CD, boot that, go to the "recovery console" and run:
```
fixmbr
```
Or if you don't have a Windows Install CD, you could boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo lilo -M  /dev/sda mbr
```
And that will install a Windows equivalent MBR to your internal drive. Let me know how it goes.

---

