---
title: "Problem with Hard Disk Partitioning Detection @ Jaunty Installation"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by tamer_radi on 2009-04-24
Hi all , Just Downloaded / Checked MD5 / Burned  the Jaunty ISO Image
Then I booted / checked media / started to Install  from the CD

(( I have XP 64-bit Pre Installed , and the Jaunty is 64 bit too ))

When I reached "Starting the Partitioner" 
I found this ...
"This computer has no operating systems on it."  !!!!
any way I choose to Specify Partitions manually , but I couldn't find any partition at all , only /dev/sda
the whole hard-disk !!
Seems that Jaunty can't detect the partition table ??

But when closed Installation and returned to Live CD 
I opened Nautilus ... partitions are visible
and I mounted them and opened some files too .

any help ??

---

### Post by tamer_radi on 2009-04-24
I've tested something 

System > Administration > Partition Editor
GParted can't detect partition table 
It just Detect the Hard Disk size , and that is Unallocated

but..

Fdisk has another opinion 

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc56e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2738    21992953+   7  HPFS/NTFS
/dev/sda2            2739        5476    21992985   83  Linux
/dev/sda3            5477       38913   268582702+   f  W95 Ext'd (LBA)
/dev/sda4           15676       25993    82879335    7  HPFS/NTFS
/dev/sda5            5477        5737     2096419+  82  Linux swap / Solaris
/dev/sda6            5738       15675    79826953+   7  HPFS/NTFS
/dev/sda7           25994       38913   103779868+   7  HPFS/NTFS

```

---

### Post by Steveire on 2009-04-24
I've hit the same issue and reported it:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/366282](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/366282)

---

### Post by Thomas_SD on 2009-04-24
I am having the same problem. Downloaded the .iso yesterday for 32-bit x86. Installing on an HP TX2500 laptop with hard drive WD2500BEVS-6. When I run 'sudo fdisk -l' from the LiveCD it shows my Windows partitions on /dev/sda1 and /dev/sda2 and gives a warning that the partitions do not end on cylinder boundary. I have Windows Vista Recovery partition installed on /dev/sda1 (HPFS/NTFS filesystem) and Windows XP installed on /dev/sda2 (FAT16 filesystem).

---

### Post by jncs12 on 2009-04-24
Problem solved!

Please see the post [http://ubuntuforums.org/showthread.php?p=7138024#post7138024](http://ubuntuforums.org/showthread.php?p=7138024#post7138024)

---

### Post by tamer_radi on 2009-04-25
Trick didn't work with me :(

---

### Post by sloppyc on 2009-04-25
I noticed that too, but didn't pay much attention to it as I generally go the manual route when it comes to partitioning.

---

### Post by tamer_radi on 2009-04-25
> **sloppyc said:**
> I noticed that too, but didn't pay much attention to it as I generally go the manual route when it comes to partitioning.

In my case  , Manual Partitioning too sees that harddisk as one unpartitioned space



any one knows a way to bypass the partitioner stage
could I just use Fdisk and mk2fs to make the required partitions

then Just tell the installation where to install

---

### Post by jncs12 on 2009-04-25
> **tamer_radi said:**
> In my case  , Manual Partitioning too sees that harddisk as one unpartitioned space



any one knows a way to bypass the partitioner stage
could I just use Fdisk and mk2fs to make the required partitions

then Just tell the installation where to install

How many **primary **partitions do you have? What type of partitions do you have?
Is there any unallocated space?

Could you dump here the output of **sudo fdisk -l**?

---

### Post by pjeeanah on 2009-04-25
I have the same problem. I want to install on the first hard disk. The installer only shows /dev/sda as a whole and no partitions. The second hard disk shows partitions ok. I have installed temporarily on the second hard disk.

fdisk -l gives

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x020f020f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3039    24410736   83  Linux
/dev/sda2            3040       19301   130624515    5  Extended
/dev/sda3   *       11529       14715    25599577+   7  HPFS/NTFS
/dev/sda5            3040        3161      979933+  82  Linux swap / Solaris
/dev/sda6            3162        5073    15358108+  83  Linux
/dev/sda7            5074        8260    25599546   83  Linux
/dev/sda8            8261       11528    26250178+   e  W95 FAT16 (LBA)
/dev/sda9           14716       19301    36837013+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9da480c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sdb2            9562       10777     9767520   83  Linux
/dev/sdb3           10778       16492    45905737+   5  Extended
/dev/sdb5           10778       12601    14651248+  83  Linux
/dev/sdb6           12602       14425    14651248+  83  Linux
/dev/sdb7           14426       14668     1951866   82  Linux swap / Solaris
/dev/sdb8           14669       16492    14651248+  83  Linux

---

### Post by jncs12 on 2009-04-25
pjeeanah and tamer_radi:

Your partitions are not in correct order.
**You must correct this with some other Partition Manager (like Paragon, Symantec or other one).**
Try to move or resize your partitions to correct the order when you apply the changes.

Just to see:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc56e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2738    21992953+   7  HPFS/NTFS
/dev/sda2            2739        5476    21992985   83  Linux
/dev/sda3            5477       38913   268582702+   f  W95 Ext'd (LBA)
/dev/sda4           15676       25993    82879335    7  HPFS/NTFS
/dev/sda5            5477        5737     2096419+  82  Linux swap / Solaris
/dev/sda6            5738       15675    79826953+   7  HPFS/NTFS
/dev/sda7           25994       38913   103779868+   7  HPFS/NTFS
/dev/sda4 is first than /dev/sda5 and /dev/sda6.

```Correct order should be:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc56e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2738    21992953+   7  HPFS/NTFS
/dev/sda2            2739        5476    21992985   83  Linux
/dev/sda3            5477       38913   268582702+   f  W95 Ext'd (LBA)
/dev/sda4            5477        5737     2096419+  82  Linux swap / Solaris
/dev/sda5            5738       15675    79826953+   7  HPFS/NTFS
/dev/sda6           15676       25993    82879335    7  HPFS/NTFS
/dev/sda7           25994       38913   103779868+   7  HPFS/NTFS
```In pjeeanah first disk that should be:

```
/dev/sda1 1        3039    24410736   83  Linux
/dev/sda2            3040       19301   130624515    5  Extended
/dev/sda3            3040        3161      979933+  82  Linux swap / Solaris
/dev/sda5            3162        5073    15358108+  83  Linux
/dev/sda6            5074        8260    25599546   83  Linux
/dev/sda7            8261       11528    26250178+   e  W95 FAT16 (LBA)
/dev/sda8   *       11529       14715    25599577+   7  HPFS/NTFS
/dev/sda9           14716       19301    36837013+   7  HPFS/NTFS
```
Notice that pjeeanah second disk it's all ok:

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9da480c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sdb2            9562       10777     9767520   83  Linux
/dev/sdb3           10778       16492    45905737+   5  Extended
/dev/sdb5           10778       12601    14651248+  83  Linux
/dev/sdb6           12602       14425    14651248+  83  Linux
/dev/sdb7           14426       14668     1951866   82  Linux swap / Solaris
/dev/sdb8           14669       16492    14651248+  83  Linux     

```I hope that helps you.
Some feedback will be appreciate!

---

### Post by tamer_radi on 2009-04-25
mmm , I'll give a try , hope this works

---

### Post by karth83 on 2009-04-26
anyone found a solution?

Ubutnu 7.10 installed properly with the same partition for me before...

Now i hve deleted the Ubnutu partition and swap from windows and tried still it is not detecting the partitions..

---

### Post by meierfra. on 2009-04-26
**tamer_radi:**  The problem is not really  the order of the partition, but the fact that primary partition "/dev/sda4" sits inside the extended partition /dev/sda3.  


To solve your problem, you need to rewrite your partition table. Please post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

and I can show you how to do that.

---

### Post by meierfra. on 2009-04-26
**pjeeanah and karth83:**
Post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```

But please start your own thread. Trying to solve more than one problem in one thread can be pretty confusing. Thanks.

---

### Post by karth83 on 2009-04-26
> **meierfra. said:**
> **pjeeanah and karth83:**
Post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```

But please start your own thread. Trying to solve more than one problem in one thread can be pretty confusing. Thanks.

Pls see my post:
[http://ubuntuforums.org/showthread.php?p=7149125#post7149125](http://ubuntuforums.org/showthread.php?p=7149125#post7149125)

thank u

---

### Post by tamer_radi on 2009-04-28
Problem Solved

I used Partition Magic which detected and fixed the Problem at Start up
but caused deletion of another Partition :D:D so I used another partition and file recovery program .

And now I am Posting from my new Ubuntu 
Thanks all for help

---

### Post by lefontiy on 2009-04-28
I have the same issue, the installer won't see any of my other partitions!
My thread with full information - [http://ubuntuforums.org/showthread.php?t=1140372](http://ubuntuforums.org/showthread.php?t=1140372)
What should I do? Do I have to download Partition Magic and follow steps given in the previous page?

---

### Post by caljohnsmith on 2009-04-30
> **tamer_radi said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc56e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2738    21992953+   7  HPFS/NTFS
/dev/sda2            2739        5476    21992985   83  Linux
/dev/sda3            [COLOR="Red"]5477       38913[/COLOR]   268582702+   f  W95 Ext'd (LBA)
/dev/sda4           [COLOR="Red"]15676       25993[/COLOR]    82879335    7  HPFS/NTFS
/dev/sda5            5477        5737     2096419+  82  Linux swap / Solaris
/dev/sda6            5738       15675    79826953+   7  HPFS/NTFS
/dev/sda7           25994       38913   103779868+   7  HPFS/NTFS

```
The reason why the Ubuntu partitioner displays your sda HDD as unallocated is because your partition table is unfortunately corrupt. As shown highlighted in red above, your sda4 primary partition is inside your sda3 extended partition, so sda4 should be a logical partition instead. If you would like help fixing your partition table, how about posting:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want. :)
> **pjeeanah said:**
> ```

fdisk -l gives

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x020f020f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3039    24410736   83  Linux
/dev/sda2            [COLOR="Red"]3040       19301[/COLOR]   130624515    5  Extended
/dev/sda3   *       [COLOR="Red"]11529       14715[/COLOR]    25599577+   7  HPFS/NTFS
/dev/sda5            3040        3161      979933+  82  Linux swap / Solaris
/dev/sda6            3162        5073    15358108+  83  Linux
/dev/sda7            5074        8260    25599546   83  Linux
/dev/sda8            8261       11528    26250178+   e  W95 FAT16 (LBA)
/dev/sda9           14716       19301    36837013+   7  HPFS/NTFS

```
Pjeeanahou, you indeed have the same problem as tamer_radi; as shown highlighted in red, your sda3 primary partition is inside your sda2 extended partition. Therefore sda3 should be a logical partition instead. If you want help correcting your partition table, please post the output of the same commands I asked tamer_radi to post, and we can work from there.

Cheers,
John

---

