---
title: "Need a program to help me mount NTFS partitions"
date: 2008-07-28
forum: General Help
---

### Post by gotix on 2008-07-28
I need a program to help me mount the NTFS partitions I have on the hard disk. A nice graphic interface with a wizard would be awesome

---

### Post by leito666 on 2008-07-28
You could try

sudo apt-get install disk-manager

---

### Post by gotix on 2008-07-28
> **leito666 said:**
> You could try

sudo apt-get install disk-manager

I get this result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package disk-manager

---

### Post by hyper_ch on 2008-07-28
install ntfs-3g (I think there's another package with a manager)... search synaptic for it. with it you can mount existing ntfs drives as read/write upon boot.

---

### Post by WRDN on 2008-07-28
Ubuntu already includes NTFS Drivers (ntfs-3G) to allow it to read/ write to NTFS drivers and partitions. If you click Places > Computer, the drive/ partition should already be listed, so just double click it to mount it. 
Incase you don't have the packages, you need to install "ntfs-3g" and "libntfs-3g23".

---

### Post by hyper_ch on 2008-07-28
you don't know what version of ubuntu he's using ;)

---

### Post by gotix on 2008-07-28
> **hyper_ch said:**
> you don't know what version of ubuntu he's using ;)

I have the latest, 8.04. At this very moment I'm in Windows so can't try the above advices. Anyways I have 3 hard disks in total, all have ntfs partitions on them

---

### Post by jonian_g on 2008-07-28
Check this post:

[http://ubuntuforums.org/showthread.php?p=5473592#post5473592](http://ubuntuforums.org/showthread.php?p=5473592#post5473592)

---

### Post by michlt on 2008-07-28
I have a dual boot Ubuntu (Hardy Heron 8.04) / WindowsXp. 

In Gnome & KDE the Windows partition is visible as an icon and easily mountable with just a click. From there I have full read/write access. 

My aggravation: I have started using Xfce4 (and I like it) but from Xfce4 I cannot locate the Windows partition with the file manager (Thunar) at all to mount it. (Same with Fluxbox - which I am also trying out).

Since I clearly have all necessary utilities already loaded to access an NTFS partition, how do I make it visible in Xfce4 and Fluxbox? Thanks.

---

### Post by michlt on 2008-08-04
Jonian_g is pointing to 

[http://ubuntuforums.org/showthread.php?p=5473592#post5473592]("http://ubuntuforums.org/showthread.php?p=5473592#post5473592")

and mentions **PySDM** in post #5 from that thread.

That was an excellent suggestion. PySDM made my WinXP partition visible in Xfce4 and Fluxbox without me having to edit the fstab file.

[It was already/automatically visible from Gnome and KDE 3. I'm still curious why it would not have been from Xfces4 and Fluxbox. If anyone knows you can continue this thread or just drop me a message. Many Thanks.]

Thanks for the great tip, Jonian_g.

---

