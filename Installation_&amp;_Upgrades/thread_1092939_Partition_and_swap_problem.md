---
title: "Partition and swap problem"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by metalaarif on 2009-03-10
I have installed Windows and Ubuntu. Windows use 2 partition Primary and Extended partition, where as Ubuntu uses 2 primary partion. Root and swap has primary partition. 
Now i want 2 install another OS but no partition left and  i dont want to format windows. 

Can i remove Swap from primary partion then put it in extended partion.

can any1 help me please

---

### Post by Neo_The_User on 2009-03-10
Not extended but you can put it in a logical partition.

---

### Post by metalaarif on 2009-03-10
Yes yes i understand about Logical partion but 
how do i do it .. please please can you help me 

i tried deleting the swap and creating a new one but i couldn't do it.

---

### Post by Neo_The_User on 2009-03-11
Yes you can. Your hard drive /dev/sda correct?

---

### Post by metalaarif on 2009-03-11
Yes your right it is /dev/sda

---

### Post by Neo_The_User on 2009-03-11
OK. You got Ubuntu livecd?

---

### Post by metalaarif on 2009-03-11
yes i got it it's right here

---

### Post by Neo_The_User on 2009-03-11
M'kay lets get started. 

Boot off of the livecd, open a terminal, type in sudo fdisk -l (its a lowercase L) and post all the output so I can see. Then I could be of further help.

---

### Post by metalaarif on 2009-03-11
you mean
 
1) i gotta boot with my live CD then
2) open terminal then type fdisk -l
 fdisk means to format and then what is l

anyway ok i will do it .. if output comes out i will post it

---

### Post by Neo_The_User on 2009-03-11
fdisk doesn't have to format if you don't tell it to.

```

sudo fdisk -l

```

It lists all your hard drive info that I'll need and your partitions. now the d command in fdisk is what erases / formats things which is WHAT YOU DO NOT WANT ATM.

---

### Post by metalaarif on 2009-03-11
Ok thanx i will be back in few minutes please don go
 
i'm gone boot now

---

### Post by Neo_The_User on 2009-03-11
I'm not leaving until... 45 minutes then its my bed time.

---

### Post by metalaarif on 2009-03-11
hey sorry bit problem with connection
and my cdrom was not working

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04f404f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15137   121587921    7  HPFS/NTFS
/dev/sda2           19371       56420   297604125    f  W95 Ext'd (LBA)
/dev/sda3           56421       60801    35190382+  83  Linux
/dev/sda5           19371       42868   188747653+   7  HPFS/NTFS
/dev/sda6           42869       55922   104856223+   7  HPFS/NTFS
/dev/sda7           55923       56420     4000153+  82  Linux swap / Solaris

i hope you help

---

