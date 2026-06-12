---
title: "unused disk space issue.."
date: 2009-02-04
forum: Hardware
---

### Post by vrv123 on 2009-02-04
Hi Experts,

This is a question long due, I have ubuntu 8.10 on my dell xps m1330, and thats the only OS on it, so entire partitioned disk is allocated to ubuntu.

I see that the available free/unused disk space is at variance when i compare properties of diskusage analyzer, system monitor & gparted/grub, respectively.

please have a look at the jpg attached to see the storage differences as marked in red.

the extended sda2 and swap sda5 have their own allocations of 8.69 gb each, I feel that is correct. so in reality, I would like to have the unused space of 217.58 in the system, as shown correctly in the gparted.

Can anyone tell me which property should i trust the most,
df command or diskusage analyzer or system monitor or gparted/grub

and why are these tools showing different sizes at the first place ?
is this normal or a bug ?

as a tech guy myself, I would like to see system memory and space allocations to be in sync across the board...

Thanks in advance!

---

### Post by dabl on 2009-02-04
I'm not 100% certain of the answer to your question, but I know for sure that you need to be very careful about the definitions of such terms as "used" and "available" when discussing disk capacity in Gigabytes, and filesystem characteristics. Note that Linux won't run at all if you actually use up 100% of the disk capacity on the filesystem where the OS is installed.  (OK, techies, YES you could still run it from a USB stick .....).

I think probably what this is telling you is that there is a little more than 206G of space available for you to use for saving data, after an allowance of 5% for the ext3 filesystem overhead is taken into consideration.  You can check my math on that.  ;)

---

### Post by vrv123 on 2009-02-04
dabl although your explanation seems reasonable, I still feel that ubuntu toolsets being used for memory/used/unused management purpose should calculate the "available" disk space that is directly proportional to the 'df' command return values.
not sure though.

---

### Post by mcduck on 2009-02-04
Gparted and Disk Usage Analyzer are giving the same value, only rounded with different amount of decimal digits. This is the value of available space on the filesystem.

System Monitor is telling how much *your current user* has available disks space. The rest, 5% of the disk space by default, is reserved for root user only (so it's not filesystem overhead, its usable disk space, only not available for regular users).

---

### Post by dabl on 2009-02-04
mcduck wins the "best answer" prize for today:

[http://www.ducea.com/2008/03/04/ext3-reserved-blocks-percentage/](http://www.ducea.com/2008/03/04/ext3-reserved-blocks-percentage/)

:)

---

### Post by vrv123 on 2009-02-04
absolutely! 1st prize goes to mcduck.
and dabl, I went through the url you posted(its very precise),

i did the math, 
I have unused space of 217.6 gb(this number shows up in gparted and dua) 
so, 217.6 - 5% of 217.6 = 206.7 gb (this is very close to what shows up in the system monitor properties)

(5% is ext3 partition reserved percentage)

bingo! this clarifies my doubt.

thanks for replying!

---

### Post by alphaniner on 2009-02-04
If you get the opportunity (ie. re-install), you can reduce or eliminate the reserved space by formatting the partition from the command line with
```
mkfs.ext3 -m # /dev/sdXX
```
where '#' is the percentage to reserve.

I'm no expert, but it seems to me that using % (as opposed directly specifying the amount in MB) is massively overkill with the size of disks these days.  I generally make a 15GB / partition with 1% reserved and for data partitions I reserve 0%.

---

### Post by mcduck on 2009-02-05
> **alphaniner said:**
> If you get the opportunity (ie. re-install), you can reduce or eliminate the reserved space by formatting the partition from the command line with
```
mkfs.ext3 -m # /dev/sdXX
```
where '#' is the percentage to reserve.

I'm no expert, but it seems to me that using % (as opposed directly specifying the amount in MB) is massively overkill with the size of disks these days.  I generally make a 15GB / partition with 1% reserved and for data partitions I reserve 0%.

You don't need to reinstall, or reformat, to change the amount of reserved space. It can be changed with the tune2fs command.

Anyway, I recommend leaving it as it is for the root partition, for others you can safely set it to zero if you want.

---

