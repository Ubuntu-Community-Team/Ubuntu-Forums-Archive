---
title: "GRUB Error 17"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by Conspiritor on 2006-05-21
Hey there,
I've, until now, had a dual boot, one with Kubuntu Breezy Badger, and the other with Windows XP.

I decided to remove my linux install (yes I know.. it's heresy) because my Windows partition was starting to run out of space.

So in Windows I went Start>Control Panel>Administrative Tools>Computer Management>Disk Management and then I right clicked on the Linux partition and clicked Format and set it to quick format in NTFS with default allocation.

Now when I try to boot, normally I would have a GRUB boot option thing, but now I get:
GRUB Error 17

I've been reading around other forums and most people say that you should type a string of commands. But I have no prompt to type them in.

Any help would be appreciated.

EDIT: Clearly I don't search enough :/ I found the solution - and for future reference, You must "boot off your windows CD go to the recovery council and type fixmbr and it will return it to just booting windows" [thanks to markitect & sputnik.1956]

---

### Post by sputnik.1956 on 2006-05-21
Hi Conspiritor,

please start your PC with your Windows Install CD and select the Recovery Console, login and type fixmbr. For mor info about fixmbr have look at:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

After that step you should have a working Windows System again and you can install afterwards Ubuntu :-).

HTH
Sputnik

---

### Post by Conspiritor on 2006-05-21
Yep it works :D

Thanks :)

---

### Post by bigken on 2006-05-21
:rolleyes:

---

### Post by MSE on 2006-05-25
I have the same problem, and when I tried to run fixmbr, it just messed up my partition table, so now I can't boot Windows XP Pro. Does anyone have any tips how to solve it?

---

### Post by bigken on 2006-05-25
hi run fixmbr then fixboot in console if these dont  work try bootcfg /rebuild
in console you will also have to install the grub menu to do this run the ubuntu install and when it gets to the partion menu press escape then go to install grub  press yes and reboot hope this helps

---

### Post by MSE on 2006-05-25
I have tried fixmbr, fixboot and bootcfg. Bootcfg is unable to locate my Windows installation. I've run Ubuntu Live, and it tells me that my NTFS-partition is of an uknown type.

---

### Post by bigken on 2006-05-25
you could  do repair install of the win xp then rerun the grub install back up your data 1st if u can ;)

---

### Post by MSE on 2006-05-25
Actually, I would have reinstalled Windows, it's just that I will loose all my files if I do so. The Windows installation program doesn't recognize my NTFS-part. as a Windows-partition, rather an unknown partition, so if I ask it to reinstall Windows, I am told that I have to reformat the partition first.

---

### Post by bigken on 2006-05-25
do u have a second hdd so u could install windows on that and try and get your files from it im sure if u got to the install windows page it will give the option to do a repair install   (a repair install leaves all your files and folders intact)
the unknown partion is probablys the linux partion

---

### Post by MSE on 2006-05-25
I fixed it using TestDisk to restore my original MBR...

---

### Post by bigken on 2006-05-25
[QUOTE=MSE]I fixed it using TestDisk to restore my original MBR...[/QUOTE]

pleased you got it sorted (now back up your data) and start playing  with ubuntu

---

