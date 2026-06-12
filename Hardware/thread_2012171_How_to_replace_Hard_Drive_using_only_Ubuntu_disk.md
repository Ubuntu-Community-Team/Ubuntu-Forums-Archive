---
title: "How to replace Hard Drive using only Ubuntu disk"
date: 2012-06-28
forum: Hardware
---

### Post by irishshanna on 2012-06-28
Need to replace my internal SATA hard drive with a new one, and the instructions (I'm not a pro so I actually did read the instructions!) say to boot to a Windows disk after I swap the old drive for the new one. This is a problem, since I only have my Ubuntu disk. Is that going to work?

---

### Post by WTF_Shelley on 2012-06-28
If your migrating from a small drive to a large one then

[LIST=1]
[*]turn off pc
[*]plug in new drive
[*]switch on and boot from clonezilla cd
[*]clone old hdd to new hdd
[*]switch off again
[*]remove old hdd
[*]switch on and set bios to boot to new drive
[/LIST]

That should do it.

I know you only have a ubuntu cd but download clonezilla and save your self a bunch of aggro. You could use DD and update-grub2 and check /etc/fstab for uuid but clonezilla is easier.

Just BACKUP YOUR DATA!!!! and dont shoot me if you hose your install

---

