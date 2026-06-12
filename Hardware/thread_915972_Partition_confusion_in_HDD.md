---
title: "Partition confusion in HDD"
date: 2008-09-10
forum: Hardware
---

### Post by mailtwogopal on 2008-09-10
Hi all,

  I am running Ubuntu hardy only in my machine for past 4 months. When i was eradicating dual boot and opting for linux OS alone and while installing Ubuntu i gave the option "Use entire disk" or similar option to install. Mine is the 80GB SATA HDD. I did no partition at all while installing and not till now. I am sure that my HDD is unpartitioned. I today executed command "sudo fdisk -l" n below is the output:

```

gopal@gopal-desktop:~$ sudo fdisk -l
[sudo] password for gopal:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9e3f9e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
gopal@gopal-desktop:~$

```

But here in output can see sda1, sda2 and sda5. What these are all and how it is showing three items. Also tell me whether using the unpartitioned HDD makes any difference in performance of the computer when compared to partitioned one. If it is so, how can i make the partition in this case? Please help.

---

### Post by fenrir12 on 2008-09-10
I would try booting from a live cd and try to erase/edit any erroneous partitions.

---

### Post by mailtwogopal on 2008-09-11
Hi fen,

  Are you sure that it is the correct way to do that and do u agree that those are erroneous  partitions?

---

### Post by mailtwogopal on 2008-09-18
Hi all,

 Can anyone please help me in this and i wanna get rid of this confusion. How i can partition the 80GB HDD which i made option "Entire disc" while i was installing ubuntu some 4 months before. please help.

---

### Post by rraj.be on 2008-09-19
> **mailtwogopal said:**
> Hi all,

```


/dev/sda1   *           1        9566    76838863+  83  Linux


```

This will eb the default ' / ' partition  created for system usage.
> 
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris
gopal@gopal-desktop:~$
[/code]

This is swap created as default by  system.


Nothing is wrong untill this.

> 
```

/dev/sda2            9567        9729     1309297+   5  Extended
```


This is somewhat messed up thing.

Is it mounted in any mount point. [I.E could u access this partition. . . .could u see this partition in browser?


Try this command to check disk usage. . 

```
df
```

If you cant access this one means . .  .it should be some erroneousness partition and just give me the size of that partition.

I will surely help you . . .:) bye bye

---

### Post by mailtwogopal on 2008-09-19
Hi raj,

  i ran the command "df" and here is the result:

```

gopal@gopal-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76232764   5419876  66970948   8% /
varrun                  224408       104    224304   1% /var/run
varlock                 224408         0    224408   0% /var/lock
udev                    224408        44    224364   1% /dev
devshm                  224408        12    224396   1% /dev/shm
lrm                     224408     37632    186776  17% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      76232764   5419876  66970948   8% /home/gopal/.gvfs
gopal@gopal-desktop:~$

```

In browser i can see it, am not sure whether what i attached is right or wrong. it is been displayed as a file and not a drive. While i click "Computer" in browser, i can see "CDROM" and "Filesystem" and not others.
i am really confused of it, if it is erroneous how it was formed.

---

### Post by rraj.be on 2008-09-19
In /dev  all partition and devices will be handled as files.

Try this command.

```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
```

If it gets mounted then, Try with  system monitor and view the mounted partitions properties.


**Edit :** I too think that the #8 by IntuitiveNipple is a correct answer for your question. . 

Is ur problem solved? ?

---

### Post by IntuitiveNipple on 2008-09-19
/dev/sda2 is an **extended partition** that contains /dev/sda5. You can see from the output of fdisk that they have the same start and end cylinders.

The swap partition (sda5) is in it. Assuming the PC is using that partition for 'swap' nothing is wrong. Here's an example:
```

cat /proc/swaps 

Filename				Type		Size	Used	Priority
/dev/sda3                               partition	4000176	0	-1

```

---

### Post by mailtwogopal on 2008-09-21
Hi intuitive and raj,

  i tried to executed mkdir and sda2 is created inside media but i can't mount that rather i got an error that "specify file type to mount". Shall i take it as nothing harmful in it as /dev/sda2 exists. Can you confirm me? and why is it so happens?

---

