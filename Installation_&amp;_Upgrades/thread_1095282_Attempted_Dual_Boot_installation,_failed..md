---
title: "Attempted Dual Boot installation, failed."
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by iarp on 2009-03-13
Ah Friday the 13th eh?

I've had windows installed on my desktop for months now and decided to install Xubuntu onto drive #3 (more on drives later). The installation went fine, but when i try to boot into linux i get error code 2 and when i try to boot to windows i get error code 17.

My current machine has 5 drives (1,2,3,5,6) all SATA. Slot #4 has nothing for the time being. 5 and 6 are in a mirrored raid and disk 1 has Windows XP Pro. I tried installing Xubuntu (been told the same thing as ubuntu) onto disk #3 which i had previously wiped and removed partitions.

As soon as i saw the error codes i googled and found SuperGrubDisk, downloaded and riped that. Used it to semi fix the MBR to at least windows load up(more error codes when tried booting ubuntu some files are missing). Now when i load XP Pro i get errors from other programs that ACL.DLL is missing somehow, but that i'm pretty sure i can fix myself.

I'd still like to dual boot Xubuntu with XP Pro and the guides i've read so far say that basically what i did last night should've worked fine. 

So what am i todo from here?

---

### Post by meierfra. on 2009-03-13
I suggest to install grub to the MBR  of the Ubuntu drive and boot from  Ubuntu drive:

Boot from the Ubuntu Live CD and open a terminal. Type

```
sudo grub 
```

and at the "grub>" prompt.


```
 find /boot/grub/stage2 
```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)

Still at the "grub>" prompt:


```
root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "/find /boot/grub/stage2")

Reboot, with the bios set to boot from the Ubuntu drive.

---

### Post by iarp on 2009-03-14
That works, thanks.

---

### Post by meierfra. on 2009-03-14
> That works, thanks.

Good news. Are you able to boot into XP from the Grub menu?  That should be possible, but   sometimes can be tricky.

---

### Post by tommcd on 2009-03-14
> **meierfra. said:**
> 

```
 
find /boot/grub/stage2
 
```


Just curious, but why did you suggest /boot/grub/stage2 instead of /boot/grub/stage1 as described here, and many other places:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
I tried it with both stage1 and stage2 and the output is the same.

---

### Post by meierfra. on 2009-03-14
> I tried it with both stage1 and stage2 and the output is the same. 

You are right. They give  the same output. But  in the Code tags is easy to mix up  the number one and the letter l:

```
/boot/grub/stage1
/boot/grub/stagel
```

So I prefer using "/boot/grub/stage2".

---

