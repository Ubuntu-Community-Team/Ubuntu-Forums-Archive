---
title: "Ubuntu not appearing on boot screen"
date: 2008-11-12
forum: General Help
---

### Post by Mason Whitaker on 2008-11-12
Installed Ubuntu in Windows Vista, using Wubi, and its not showing up on the boot screen. 
Already uninstalled and reinstalled 2 times now.
Help?

---

### Post by iNaitvad on 2008-11-12
Me acuerdo que me paso lo mismo una vez, creo que se puede solucionar con el StartupManager, cambie la resolucion del bootsplash y listo.

---

### Post by Mason Whitaker on 2008-11-12
He intentado ya, y no funcionó  :(
Can we speak in English please?

---

### Post by Aistina on 2008-11-12
It's not working here either. Possibly there's something wrong with the download of the ubuntu iso? Wubi told me it was finished in under a minute, while I only have a 1.5 Mbps internet connection, so it couldn't have finished downloading that quickly. Or does Wubi check if said iso exists in the dir it's run from? (I happen to have the iso there.)

---

### Post by Aistina on 2008-11-12
Ok, just read in another thread that Wubi outputs a log file to %temp%, so I verified that it does indeed grab the .iso from the folder Wubi.exe is in.

Just had a second though. Is the disk you're installing Ubuntu on  "Dynamic"? (Check in Computer Management -> Storage -> Disk Management). I just remembered mine is, but I'm not sure if it'll be a problem or not.

---

### Post by Mason Whitaker on 2008-11-12
Yeah, it is

The weird thing is, when I used Wubi to install Hardy Heron, it automatically put it on the boot screen, same computer and same settings.

---

### Post by Aistina on 2008-11-12
I see. Well, I am pretty sure the problem lies with the dynamic disks, as I uninstalled Ubuntu and then reinstalled it on another disk, which is not dynamic (yay for plenty of hard drive space). I was then able to boot into Ubuntu without problems.

It is also worth mentioning that Ubuntu recognizes all my NTFS partitions and puts them into the Places menu, except the ones that are on the dynamic disk.

---

### Post by Mason Whitaker on 2008-11-12
Just got of the phone with my cousin ( has tons of experience with OpenSUSE )
He told me that there is a certain setting in Windows Vista which can load the Boot Screen on startup.
Anyone happen to know how to do that?

---

### Post by Markopolo123 on 2008-11-14
I too am having this problem with vista 32bit. The first wubi install appeared in the boot options, then I uninstalled Ubuntu in Windows and tried to reinstall. Ubuntu no longer shows up in the boot options.

---

### Post by ago on 2008-11-14
You can use EasyBCD to check the vista boot menu

---

