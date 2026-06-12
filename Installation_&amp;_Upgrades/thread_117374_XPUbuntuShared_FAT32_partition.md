---
title: "XP/Ubuntu/Shared FAT32 partition"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by macluvjay on 2006-01-14
I have successfully setup an XP/Ubuntu dual botting machine.  Woo-Hoo, right.  During the Ubuntu install I also set aside a 16GB partition formatted FAT32 mounted @ /windows.  I see it, but the permissions are such that I cannot read to / write from the partition in the gui.  obviously I can sudo actions via Terminal, but I had hoped to use this partition to share files between the two OSes.  Any help would be greatly appreciated.

---

### Post by aysiu on 2006-01-14
[QUOTE=macluvjay]I have successfully setup an XP/Ubuntu dual botting machine.  Woo-Hoo, right.  During the Ubuntu install I also set aside a 16GB partition formatted FAT32 mounted @ /windows.  I see it, but the permissions are such that I cannot read to / write from the partition in the gui.  obviously I can sudo actions via Terminal, but I had hoped to use this partition to share files between the two OSes.  Any help would be greatly appreciated.[/QUOTE] See the fourth link of my signature or [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Omnios on 2006-01-14
Check out

 [http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")

 Personaly I use this in fstab for full access. Mainly to right click  and change permitions.

 ```
/dev/hda2       /media/Documents     vfat    rw,users,gid=users,umask=000,       0       0
```


 Also when making the media/windows directory you can call it anything you want for the file name and this will show up named as that. I also put a link in my home file called Documents to the My documents on my fat drive which saves me inputing 'My Documents in terminal. Lastly you can also set up your windows to use the fat partition as the My Documents folder and link the My Documents in windows to it.

---

### Post by macluvjay on 2006-01-14
Thanks everyone for the quick response!  This seems to be working.  I will reboot into windows and see how this goes.

---

### Post by macluvjay on 2006-01-14
Cool!  So XP see's the /dev/hda8 partition just fine.  I haven't gotten XP to redirect My Documents to the F:/ drive yet, but this is an awesome start.  Thanks again to everyone for your help!

---

