---
title: "Swap problem?"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by fred6633 on 2009-02-02
Hello,

I use 8.10. I don't know if my swap partition is ok.
I created Linux partitions in Bootit New Generation (BING). First I installed Mandriva but I got problems.

Then I installed Kubuntu 8.10 on the same partitions. I choosed manual partionering and there was no problems during the install.

Today when I resized my /home partition in BING, it reported that the swap partition not was formatted.

when I enter df -h there is no swap partiton listed.

When I enter top it reports a swap partition: Swap:  4088500k total, 
 0k used,  4088500k free 

fdisk -l reports a swap partition dev/sda7

In /etc/ fstab I have a swap partition, but in /etc/mstab I have not.

So I'm confused.

How do I find out if swap is formatted? and if not, how do I format?

I read I could use the live CD but I saw no such option when I booted with it.

Is it a problem at all? Everything works fine so far.

My Linux knowledge is limited.

Thanks

Fred

---

### Post by taurus on 2009-02-02
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by logos34 on 2009-02-02
> **fred6633 said:**
> 
when I enter df -h there is no swap partiton listed.


When I enter top it reports a swap partition: Swap:  4088500k total, 
 0k used,  4088500k free 

fdisk -l reports a swap partition dev/sda7

In /etc/ fstab I have a swap partition, but in /etc/mstab I have not.


df nor mtab will show it.

Looks like it's working and everything is fine, but the system doesn't need to cache anything there because you have plenty of ram.

---

### Post by fred6633 on 2009-02-03
Thanks for your replies. Here comes the outposts:

fredrik@Hem:~$ sudo fdisk -l
[sudo] password for fredrik:
Disk /dev/sda: 160,0 GB, 160041885696 byte
255 headers, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xc945c945

    Device Start     Begin        End     Block    Id  System
/dev/sda1               1        7648    61432528+   7  HPFS/NTFS
/dev/sda2   *        7649        8285     5116702+  83  Linux
/dev/sda3            8286       11808    28298497+   f  W95 Extended (LBA)
/dev/sda5            8286        9559    10233373+  83  Linux
/dev/sda6            9560       11299    13976518+  83  Linux
/dev/sda7           11300       11808     4088511   82  Linux swap / Solaris

fredrik@Hem:~$ sudo blkid
/dev/sda1: UUID="5CEC3D1BEC3CF0BE" LABEL="Toftered" TYPE="ntfs"
/dev/sda2: UUID="b80446f6-393c-4123-b9a1-43a555105931" TYPE="ext3"
/dev/sda5: UUID="08bd900e-0a26-4b0e-a18b-ea7128b85917" TYPE="ext3"
/dev/sda6: UUID="23cf5d59-2e3d-45a5-ac5e-1c6184244224" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="350d3080-c7c8-4670-adaa-6810bde555f7"

fredrik@Hem:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b80446f6-393c-4123-b9a1-43a555105931 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=23cf5d59-2e3d-45a5-ac5e-1c6184244224 /home           ext3    relatime     0       2
# /dev/sda5
UUID=08bd900e-0a26-4b0e-a18b-ea7128b85917 /usr            ext3    relatime     0       2
# /dev/sda7
UUID=350d3080-c7c8-4670-adaa-6810bde555f7 none            swap    sw     0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

fredrik@Hem:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1987        640       1346          0         20        337
-/+ buffers/cache:        282       1705
Swap:         3992          0       3992

Sorry that all words above are not english. I translated some of them.

Fred

---

