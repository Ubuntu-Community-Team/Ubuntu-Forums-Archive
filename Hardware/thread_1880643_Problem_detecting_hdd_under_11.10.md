---
title: "Problem detecting hdd under 11.10"
date: 2011-11-14
forum: Hardware
---

### Post by wmdvanzyl on 2011-11-14
This thread is a spin-off from another thread found [here]("http://ubuntuforums.org/showthread.php?t=1879017"). I am not going to rehash how i got to this position as that was all covered in the previous thread. Point is, i have a working a 11.10 and i can access my NTFS drive which contains Win7. I **cannot**, however, access the other drive (ntfs i think - or fat - not sure now) that contains a bunch of data. I used to be able to before i swapped out the sata hdd's to this machine. The hdd is detected in the BIOS, but i can't see it under Ubuntu.

What info can i provide to begin this troubleshoot? :-)

---

### Post by wmdvanzyl on 2011-11-15
Anybody?

---

### Post by dabl on 2011-11-15
I looked at the other thread, but I'm not sure I understand how many variables have changed since the last time an OS was able to see all your drives and partitions.

For starters, can you boot a Live CD -- preferably a version other than the one you have installed. Any Linux will do -- I like [[COLOR="SeaGreen"]**Parted Magic**[/COLOR]](http://sourceforge.net/projects/partedmagic/) and [[COLOR="SeaGreen"]**aptosid**[/COLOR]](http://aptosid.com/index.php?module=News&func=display&sid=28) for these types of tests. Open a terminal and issue (as root, or with "sudo" prefix):

```
fdisk -lu
```

and see how many drives and partitions are reported. If another Live CD cannot see the drive you are having trouble with, then we can probably focus on your hardware, and not point at Ubuntu.  If another Linux Live CD can see the drive/partition, but Ubuntu cannot, then we can work on Ubuntu.

---

