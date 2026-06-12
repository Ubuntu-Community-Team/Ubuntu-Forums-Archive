---
title: "Worm/trojan infected USB pendrive, is now write protected"
date: 2011-09-04
forum: Hardware
---

### Post by Muiske on 2011-09-04
Hi all,


Since this is a pesky problem and I have found no solution on the net, I will try explaining the issue here to see if anyone can come up with an adequate solution.

The case. 

My wife is currently writing her PhD dissertation and has to use the Windows PC's at her work (that, although the IT guys claim otherwise, are totally unprotected against viruses). She uses a lot of media to back-up her work, among which a USB pendrive (16G, Kingston Datatraveller). Due to the faulty antivirus policy, the drive is now infected with a worm. It installed itself under the name "explorer.exe" on the drive. I scanned it with Clam AV and have quarantined the file (I do not know if that worked, however... which I will explain later). 

It seems that this worm has changed the USB drive to 'read-only' modus. I tried removing the files, but to no avail. I tried changing the permissions with *chmod* but that also did nothing. 

The next stop was Gparted, but it could not remove the partition and install a new one, due to the same error. 

So now, I am at a loss here. I might try a low-level formatting, but I do not know how or with what program. 

Note: this is the second time such a thing has happened. I discarded the previous USB pendrive, but if this continues, it is going to be costly. So I REALLY would like a solution this time, so the drive can still be used.

Is there anyone that has a proven solution for this? 

Thank you.

/ Muiske.

---

### Post by fdrake on 2011-09-04
first: if you really care about the data in the usb first make a copy with dd in your desktop, otherwise, never mind. 

second: such a cool virus!:P ! can you post here   your :
```
sudo fdisk -l
```

---

### Post by iponeverything on 2011-09-04
some usb drives have write protect tab. This is the only way to write protect a drive, as any software method would be pointless. 

Can other things be written and removed from drive, just not virus?

If that is the case the file was given a read-only attribute that is being honored. -- If it does have the attribute, it can be removed -- allowing the removal of the file.

---

### Post by shaneo1 on 2011-10-15
I too have the same issue, I have a 500GB Maxtor usb drive which form some reason unknown to me is now ready only, this has only happened in the last couple of days I have ubuntu 11.10.  

I have run this drive in a Vbox on win xp and it can be accessed as normal, so there seems to be nothing wrong with the drive itself, but Nautilus seems to be the issue.  I have installed Gnome Sushi yesterday, but I am unsure if this would be the cause.

set on /dev/sdb1

Any ideas would be welcomed.

---

### Post by diasf on 2011-10-15
afaik, drives with filesystem problems are automatically remounted as read-only.... 


boot the system, wait a bit, then see the last lines of dmesg... that might shed some light on it

---

### Post by fdrake on 2011-10-15
> **shaneo1 said:**
> I too have the same issue, I have a 500GB Maxtor usb drive which form some reason unknown to me is now ready only, this has only happened in the last couple of days I have ubuntu 11.10.  

I have run this drive in a Vbox on win xp and it can be accessed as normal, so there seems to be nothing wrong with the drive itself, but Nautilus seems to be the issue.  I have installed Gnome Sushi yesterday, but I am unsure if this would be the cause.

set on /dev/sdb1

Any ideas would be welcomed.
after you have mounted your druve can you post the output of mount nd your /etc/fstab? maybe your driver is configured to be run as read-only.
try also
```
sudo mount -w /dev/sdb1 /media/disk(or whatever dir you use)
```

---

