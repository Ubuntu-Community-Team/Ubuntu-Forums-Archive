---
title: "GRUB Problems"
date: 2008-11-17
forum: General Help
---

### Post by techsupportnerd on 2008-11-17
Hi, I recently moved my partitions around to make a bit more space for ubuntu.

When I rebooted, I came to find that GRUB was giving me an Error 17! So immediately I booted off a live CD, and followed the instructions to fix grub after installing windows.

Here's the problem. Windows work, Ubuntu doesn't.

Is there a way I can reset grub to it's defaults without reinstalling ubuntu?

---

### Post by Marius Derekus on 2008-11-17
1.)Boot from a liveCd again.  
2.)Eneter into your ubuntu hardrive, 
3.)find folder called boot.  Enter into it, 
4.)then find a folder called grub and enter into it. 
  There should be a file called menu.lst. 
5.)Open that file and post it on this thread. 

(If i have my directories wrong, you can Follow the first 2 commands then click the "search command at the top of the screen and search "menu.lst)

---

### Post by Marius Derekus on 2008-11-17
Btw, even if you find the file and post it, I can't gaurentee  that i can fix the problem

---

### Post by lavinog on 2008-11-17
you should post your /boot/grub/menu.lst

if you can also post an image of your partitions or output of:
```
sudo parted /dev/sda print all
```
(assuming sda is your harddrive)

---

### Post by techsupportnerd on 2008-11-17
ahhhh I just messed it up beyond repair.

Sorry for the trouble, and thanks for the responses. I'm definitely going to have to reinstall everything now.

---

### Post by Marius Derekus on 2008-11-17
The boor folder might be located in a folder called disks

---

