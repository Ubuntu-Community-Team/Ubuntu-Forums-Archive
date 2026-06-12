---
title: "Dual boot install onto multiple-disc XP system"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Wlodek_T on 2008-12-18
Dear All,

Bear with me, as this is my first post here.

After several sad no-Linux years I decided to make my multi-HD, 64-bit AMD system a dual boot.

Ubuntu 8.10 (64-bit) CD starts fine, the installation process takes off, but when I get to the manual partitioning the installer only sees 2 discs, when I have 3. Windows see them correctly. They are all SATA drives. 

I guess I don't have awkward needs: make it dual boot, install on what Windows call Disk 2. 

At the moment 
- Disk 0 is NTFS (single partition) with the Windows system and "My Programs"; 
- Disk 1 is my NTFS drive with My Documents, Matlab stuff, photos etc. 
- Disk 2 has a FAT32 "communication partition" and room for Ubuntu installation. Lots of it.  

I would like the installation not to do anything to Disk 0 (except perhaps for installing the multi-boot bits there), ignore Disk 1 (perhaps mount it just to see it), and install Ubuntu on Disk 2, partitioning the remaining space as needed (preferably separating /, swap and /home, but that's the easy bit)

I am surprised that the installer won't see all the installed discs. 

And also a question (yes, I backed all my documents up, and I have a full XP system backup too for this machine). The question is, will the installation pick up my Windows installation on Disk 1 and add it to the boot menu? Do I need to do anything about it, apart perhaps from RTFM?

My worry is that if the installer can't (sometimes) see all the drives, then it might (sometimes) do something unspeakable to the system ... and with my luck, this "sometimes" will happen to me with probability 1.

Any reassurance from the (well) seasoned Ubuntians?

Many thanks in advance,

W.

---

### Post by logos34 on 2008-12-18
Open a terminal and post the output of this:

sudo fdisk -l

Also, on the desktop go to System>admin>partition editor.  DOes gprated see the other disk?

---

### Post by ajgreeny on 2008-12-18
If this seems like a silly question, please forgive me, but are your three disks actually disks and not perhaps partitions on a disk, or perhaps on two disks.  I ask this because windows will see partitions as disks named C: D: and perhaps E: when you look in Windows Explorer.  They may not actually be separate disks.

However, as logos34 says, from the live CD run that command ```
sudo fdisk -l
``` and post the output back here.

---

### Post by Wlodek_T on 2008-12-18
Logos: thanks for this. I can't do it right now, something (a long calc.) is running on that machine in Windows and will do for the next 2h, but I'll do that tomorrow morning and post the output. Should have thought about that myself ... ](*,)

AJ: thanks too, not a silly question at all. There are three physical discs (or disks). Windows view is not in Explorer but in diskmgmt.msc and Ubuntu did see three yesterday ... :( 

W.

---

### Post by Wlodek_T on 2008-12-19
Many thanks.  When I booted directly into installation I could see all the physical drives and all went swimmingly.
I can now play!:guitar:  (sorry, could not resist)

In fact I am writing this from the newly installed ...

I have other questions now, but that's in another forum.

All the best,
W.

---

