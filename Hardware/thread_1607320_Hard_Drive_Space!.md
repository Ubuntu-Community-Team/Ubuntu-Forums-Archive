---
title: "Hard Drive Space!???"
date: 2010-10-27
forum: Hardware
---

### Post by Cool Boy963 on 2010-10-27
Ok, so today i installed ubuntu 10.10 (im loving itt!!!!) I partitioned my drive so i have 60gb free for ubuntu (ps my dual boot is windows 7 (C) ubuntu (U) (C | U)) and now i go into windows 7 and it tells me on drive U: (ubuntu) i have 60 gb of free space. but when i launch ubuntu and click: Places > Computer > Right-click on File System > Click properties. it tells me i have 13 gb free space? i really need my 60gb of space. PLEASE HELP ME!! :mad:

My Setup is:
Ubuntu 32-Bit 10.10
Packard Bell Laptop

Just to let you know I have 64-bit windows 7 and 32-bit ubuntu this might be the problem...? Anyway, leave answers below!


EDIT--
I now have 64bit ubuntu and i realised my space was different becuase when i installed it i put it at the normal 17gb i later realised this is not how much space you want the setup to fill, but how much space is on your partition! thanks for the help anyway guys ;)

---

### Post by sikander3786 on 2010-10-27
I doubt if Windows 7 will be unable to calculate the exact disk space on an ext3/ext4 filesystem as it doesn't support any of them natively.

You need to post more details. Please post the output of

```
sudo fdisk -l
```

```
df -h
```

32-bit, 64-bit conflict is not considered as both the OS run independent of each other :-)

---

### Post by Cool Boy963 on 2010-10-28
> **sikander3786 said:**
> I doubt if Windows 7 will be unable to calculate the exact disk space on an ext3/ext4 filesystem as it doesn't support any of them natively.

You need to post more details. Please post the output of

```
sudo fdisk -l
```

```
df -h
```

32-bit, 64-bit conflict is not considered as both the OS run independent of each other :-)

Sorry, i dont get all this "code" stuff and what to do with it could you explain it to me? and i tried uninstalling ubuntu and remaking the partition to have 70gb but ubuntu still says 13gb!

---

### Post by krishnandu.sarkar on 2010-10-28
go to terminal from Application > Accessories > Terminal

And then run those two commands one by one. Copy the output from terminal and paste in [http://paste.ubuntu.com](http://paste.ubuntu.com) and share the link here.

---

### Post by sikander3786 on 2010-10-28
> Copy the output from terminal and paste in [http://paste.ubuntu.com](http://paste.ubuntu.com) and share the link here.

No need to paste it somewhere else. Just paste the output here directly in your post.

---

### Post by Cool Boy963 on 2010-10-29
> **sikander3786 said:**
> I doubt if Windows 7 will be unable to calculate the exact disk space on an ext3/ext4 filesystem as it doesn't support any of them natively.

You need to post more details. Please post the output of

```
sudo fdisk -l
```

```
df -h
```

32-bit, 64-bit conflict is not considered as both the OS run independent of each other :-)

outcome:

sudo fdisk -l = hussain@ubuntu:~$ sudo fdisk -l
[sudo] password for hussain: 

df -h = hussain@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  2.9G   13G  19% /
none                  1.5G  284K  1.5G   1% /dev
none                  1.5G  1.5M  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda5              69G   18G   51G  26% /host
hussain@ubuntu:~$ 

whats this for?

---

### Post by Cool Boy963 on 2010-10-29
WAIT! I go to Apps > Accessories > Disk Usage Analyser. And it says i have 64.1 gb left! but i go back to computer right click file system and it still says 13gb. WTF? whats wrong with my ubuntu. i love linux and need more space could anyone explain whats going on and which ones right. remember i said before i dual-boot to windows 7 and it tell me i have 64.1gb so.... is the file system wrong. or is the disk usage space app wrong? im so confused! :(

---

