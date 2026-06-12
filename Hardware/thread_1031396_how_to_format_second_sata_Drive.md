---
title: "how to format second sata Drive"
date: 2009-01-05
forum: Hardware
---

### Post by endacoz on 2009-01-05
I have a Dell DESKTOP optiplex 620.  4g RAM dual core etc.

I have ubuntu Intrepid installed on an 80 Gb sata HD

I was given a unformatted 250 GB sata drive.

I have tried using parition logic iso disk.  I can get the ap to load fully.  says error or hangs.  

When in ubuntu, it does not see the secondary hard drive, through the GUI.  
Can i format it through command line? and mount it or does it need to be formated 1st before linux can read it?

---

### Post by jocko on 2009-01-05
Just install gparted:
```
sudo apt-get install gparted
```(or find it in synaptic).

Then start gparted (System --> Administration --> gnome partition editor).
It should see all connected hard drives.

---

### Post by howefield on 2009-01-05
Install gparted with Synaptic package manager, (if you haven't already got it in your System > Administration menu, it would show up as Partition Editor.

Use that to format your drive, it will need to be unmounted before you can format.

Or load up the Intrepid Live cd and do it from there, (gparted is part of the live cd).

---

### Post by endacoz on 2009-01-05
My plan is this:

To use 200 of the 238gb  as a storage partition.  then the other 38 I will install ubuntu on.  I want to then have ubuntu manage it as I have the storage partition as a share drive on my LAN.  This LAN shared drive will need to be viewed and accessed from both PC and linux.  Possibly even password protect the drive so that I have to log into it etc.  This is a useful project I have given myself to finish as I know linux can do this well and I want to improve my skills in this area.

Are there better ways to do this?  does not look like Gparted will let me do NTFS.  what format is best for server conditions? or should I go about this whole idea differently?

---

### Post by egalvan on 2009-01-05
> **endacoz said:**
> My plan is this:

.. I want to then have ubuntu manage it as I have the storage partition as a share drive on my LAN.  This LAN shared drive will need to be viewed..accessed from both PC and linux.  Possibly even password protect the drive so that I have to log into it etc... I know linux can do this well and I want to improve my skills in this area.

Are there better ways to do this?  does not look like Gparted will let me do NTFS.  what format is best for server conditions? or should I go about this whole idea differently?

Can´t give an opinion on ´better ways´..

But I can say that GParted DOES do NTFS.}
I use it to prepare-repair Windows drives.

But having said that, let me also state that if drive is installed on a Linux machine that will not boot windows, then forget NTFS and go with a native *nix file system.

The linux OS will handle network requests for the drive, and you don´t need NTFS.

Even if you ARE dual-booting with windows, there are ext2-ext3  drivers you can use under windows...

---

### Post by howefield on 2009-01-05
> **endacoz said:**
> ....does not look like Gparted will let me do NTFS.  what format is best for server conditions? or should I go about this whole idea differently?

Install ntfsprogs from Synaptic Package Manager and you will find the gparted will allow to to do ntfs formats.

---

### Post by endacoz on 2009-01-07
worked great thank you howefield!

---

