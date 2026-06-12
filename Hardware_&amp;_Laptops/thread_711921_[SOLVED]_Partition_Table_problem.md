---
title: "[SOLVED] Partition Table problem"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by cd7 on 2008-03-01
Hi all,
the system does not boot anymore: GRUB error 17.
I thought it as a grub problem so 've tried to fix GRUB with SUPERGRUBDISK but it didn't work.
So i thought about the disk, this is the output of fdisk:
```

ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x962b of partition table 5 will be corrected by w(rite)

```

So the problem is obviously in the partition table...

Now what shall I do if i don't want to loose my data?
Is option "w" (write partition table) of fdisk safe?

Thanks

cd7

---

### Post by seshomaru samma on 2008-03-01
I'm not sure what you can do but you can use the Live-Cd to backup your data
also you can use Gparted on the liveCd to create a /home partition copy your /home partition there and if you need to reinstall you will keep your settings and data
(more about /home [here]("http://www.psychocats.net/ubuntu/separatehome"))

---

### Post by cd7 on 2008-03-01
The problem is that I've already got a separate home partition but i can't see it. The previous partition (root) overlaps my home partition. I can only see my root partition at the moment.
Googling around i found that gpart could guess the correct partition table configuration, This is the output of gpart:
```

ubuntu@ubuntu:~$ sudo gpart /dev/sda -W /dev/sda

** Error: invalid extended ptbl found at sector(147926581).

Begin scan...
Possible partition(Linux ext2), size(10001mb), offset(0mb)
Possible partition(Linux ext2), size(101535mb), offset(10001mb)
Possible extended partition at offset(111537mb)
   Possible partition(Linux swap), size(2933mb), offset(111537mb)
End scan.

Checking partitions...
Partition(Linux ext2 filesystem): primary 
Partition(Linux ext2 filesystem): primary 
Partition(Linux swap or Solaris/x86): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 10001mb #s(20482808) s(63-20482870)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(1274/254/59)r

Primary partition(2)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 101535mb #s(207945360) s(20482875-228428234)
   chs:  (1023/254/63)-(1023/254/63)d (1275/0/1)-(14218/254/63)r

Primary partition(3)
   type: 130(0x82)(Linux swap or Solaris/x86)
   size: 2933mb #s(6008240) s(228428298-234436537)
   chs:  (1023/254/63)-(1023/254/63)d (14219/1/1)-(14592/254/56)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Edit this table (y,n) : y  
```

Shall I trust gpart and write the partitions?

cd7

---

### Post by cd7 on 2008-03-01
I took the risk and changed the partition table as suggested by gpart (actually i did it incounsciously with the command "sudo gpart /dev/sda -W /dev/sda").

With luck the parameters were correct and I've been able to reboot in my system with no data loss.

Problem solved

My question now is how could I ruin my partition table in this way? I only have ubuntu installed and it is mainly used by my sister to surfs the web...

Thanks

cd7

---

