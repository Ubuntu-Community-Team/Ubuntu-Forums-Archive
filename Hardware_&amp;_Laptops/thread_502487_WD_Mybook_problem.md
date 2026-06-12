---
title: "WD Mybook problem"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by addman on 2007-07-16
ok so here is my problem i had no idea what i was doing so i installed ubuntu on my external hard drive. it was going too slow so i cancelled about half way and just put it on my computer. so now i don't have permission to access my drive and it has half of an operating system on it. i was wondering if someone could tell me how to reformat it so i can use it =) thanks for any help

---

### Post by EXCiD3 on 2007-07-16
I personally use Hiren's boot CD, Boot into it and run Partition Magic to format any drives i need. It requires no OS to use. If you have an OS, or a live CD you can use any partition manager to reformat the drives you need.

---

### Post by addman on 2007-07-19
thanks ill try that and post the results :)

---

### Post by addman on 2007-07-20
ok so that deletedeverything on the drive. but i still dont have full permissions because it says i am not the owner =/

---

### Post by EXCiD3 on 2007-07-22
Now you should try reinstalling ubuntu onto the drive, without interrupting the install.

---

### Post by addman on 2007-07-25
thats not what i want to do though. i have ubuntu running on my computers hard disk, i just want to gain permissions to that drive to put stuff on it.

---

### Post by EXCiD3 on 2007-07-26
Oh, sorry, i thought you wanted to install Ubuntu onto it. Reformat the drive, or convert it, to FAT32 or another linux friendly (ie. NOT NTFS because it is not natively supported). This should make it automatically writable. There is a script in Automatix that will automount NTFS and FAT32 drives for read/write permissions. You make check that out first: [http://www.getautomatix.com]("http://www.getautomatix.com")

---

### Post by addman on 2007-07-28
ok so heres wat i did so far. i put it on my windows comp and reformated it but as ntfs because there was no option. i figured for the time being it was better to be able to use it on somthing than nothing. but do u know a way to format it to fat 32 now like a program, one that works on windows or linux. thanks for helping =)

---

### Post by ugm6hr on 2007-07-28
> **addman said:**
> ok so heres wat i did so far. i put it on my windows comp and reformated it but as ntfs because there was no option. i figured for the time being it was better to be able to use it on somthing than nothing. but do u know a way to format it to fat 32 now like a program, one that works on windows or linux. thanks for helping =)

Easy way in Ubuntu:
Install GParted (find it in Synaptic) or run Ubuntu from LiveCD or use Gparted LiveCD.
Open GParted
With USB HD plugged in, select correct drive in GParted.
Delete existing partition & create new partition (fat32 format).
Apply.
Should now work.

As for accessing it - external drives should automatically be installed with read/write permission for all desktop users.  They certainly do in Xubuntu7.04.

For internal drives:
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

If you want to use the command line - I think it's something like this (but please check - and careful which device you are formatting!):
```
mkdosfs -n *volume-name* -F 32 /dev/sd*devicelabel*
```

---

### Post by addman on 2007-07-31
ok well i installed it but i cant find the executeable icon anywere, is there a command i can use?

---

### Post by llamakc on 2007-07-31
> **addman said:**
> ok well i installed it but i cant find the executeable icon anywere, is there a command i can use?

What did you install?

---

### Post by addman on 2007-08-01
gparted

---

### Post by llamakc on 2007-08-01
ken@llamakc 05:33:24:~$ which gparted
/usr/bin/gparted

---

### Post by addman on 2007-08-01
it says i need to give root privileges in order to run it because it said it may be a weapon of mass destruction????? anyway how do i give root privileges

---

### Post by ugm6hr on 2007-08-01
It is normally installed in the System Menu as "GNOME Partition Editor"

If not:
```
gksudo gparted
```

---

### Post by addman on 2007-08-27
im just about ready to blow this damn harddisk to hell. so basicly ... it dosent seem to work :) because it contains a mounted file system.  (asdfghjkl !!!!!!!!!!!!!!) why is this so hard, i mean when i converted it to ntfs i just clicked a button on windows and like magick it just happened, but no fat32 has no magic button.  this is too much work for 250 gigs
(sorry if i seem a little mad/frustrated ive had a bad day =) )  thanks for any help

---

