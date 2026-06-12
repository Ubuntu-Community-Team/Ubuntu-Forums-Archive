---
title: "partioning scheme for a first time user"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by ouchifell on 2009-07-28
first time ubuntu user here. burned a copy of ubuntu onto a dvd using my laptop and installing it in a computer built from scratch. i managed to boot from the installation dvd and trying to figure out the ideal partitioning scheme.

i have 1 250 gig hard drive.

how much should i allot for ubuntu? what file system should i use?
i plan on using my computer primarily for watching movies. should i make a separate partition for any that i download? 

i'm sorry if this question was asked already. i did try to find an answer to my question, but i can only find info on partitioning schemes with dual boot setups. 

thanks. any help would be appreciated.

---

### Post by merlinus on 2009-07-28
I have a 500G hdd, and it is partitioned this way:

10G primary /storage partition
all the rest is an extended partition with these logical partitions within it:
15G  /
20G /home
1.4G /swap
rest of space is /data

All are formatted as ext3.

---

### Post by ouchifell on 2009-07-28
ok 3 questions:

i am using the newest version of ubuntu (sorry should have mentioned that before). this may explain why i don't see the /data partition? 

i'm at the partition part of the installation right now. how do i turn something into an extended partition?

the ubuntu install guide states as follows: 

The root partition / must always physically contain /etc, /bin, /sbin, /lib and /dev, otherwise you won't be able to boot. Typically 150–250MB is needed for the root partition.

so should i allot 250 MB for the / partition? or does this depend on my HD space?

---

### Post by running_rabbit07 on 2009-07-28
> **ouchifell said:**
> ok 3 questions:

i am using the newest version of ubuntu (sorry should have mentioned that before). this may explain why i don't see the /data partition? 

i'm at the partition part of the installation right now. how do i turn something into an extended partition?

In the window it should have a clicker for primary and logical, tick logical

> **ouchifell said:**
> the ubuntu install guide states as follows: 

The root partition / must always physically contain /etc, /bin, /sbin, /lib and /dev, otherwise you won't be able to boot. Typically 150&#8211;250MB is needed for the root partition.

so should i allot 250 MB for the / partition? or does this depend on my HD space?

Make the / partition about 15 gigs or 15000 megabytes.

Make a swap about the size of 1.5 times your RAM size. 

Make the /home partition for the rest of the drive.

That will make for a happy system that can be easily upgraded in the future.
You can use EXT3 or EXT4 they both have worked fine for me.

---

### Post by ouchifell on 2009-07-28
ok ! last question ... should all of these partitions be primary? 

even the swap?

---

### Post by Shazaam on 2009-07-28
If the whole drive is for Ubuntu/linux might I suggest this since you are a new user?...
1. Boot the cd/dvd to the desktop.
2. Go to System>Administration>Partition Editor.
3. Go to Device>Create Partition Table- make it msdos.
4. Your first decision is "Am I ever going to install Windows on this drive?" If you are, now is the time to do that.
5. If not, make a PRIMARY partition roughly 1gig in size for swap.
6. Make an EXTENDED partition to fill up the rest of the drive.
7. INSIDE of that Extended partition make as many LOGICAL partitions (formatted ext3) as you think you will need. Ubuntu runs fine on a 10gig or larger partition (some say even on smaller partitions). A lot of users divide up the drive into separate /boot, /home etc. partitions. I have tried that, and for me only I see no advantages to it. Others will disagree.
8. When done, reboot with the cd/dvd and install. When you get to the partitioning stage choose MANUAL, point the installer at those new partitions.

The reasoning behind the Extended partitions is that you won't run into the 4 primary partition limit. Another thing to remember is if you decide to install other versions of linux alongside Ubuntu, the last distro installed will overwrite grub unless you specify otherwise. But thats for a later post :)

---

### Post by ouchifell on 2009-07-28
i don't plan on installing windows so i've just gone ahead and allocated my swap partition.

for the extended partition, if i want to divide them into various logical partitions ... do i have to assign it a mount point? i want to allocate 100 gigs of the extended partition to movies ... mount point required?

---

### Post by ericab on 2009-07-28
personally id go with a

/boot
/root
/home
/tmp
and depending on if you have less then 4gb of ram:
/swap

4+ gb of ram, dont even bother making a swap partition, itll never be used.
just wasted space.

---

### Post by running_rabbit07 on 2009-07-28
> **ouchifell said:**
> i don't plan on installing windows so i've just gone ahead and allocated my swap partition.

for the extended partition, if i want to divide them into various logical partitions ... do i have to assign it a mount point? i want to allocate 100 gigs of the extended partition to movies ... mount point required?

The /home partition will contain your settings and all your stored files. If you make the / partition primary, you'll make the /home logical. The Swap doesn't give you any options for anything else. You will need swap if you plan to Hibernate. Being that you plan to be loading full sized movies, you may want to use EXT4 being that it has much less problem with fragmentation.

Edit: Here I have added a screenshot of my partitions to help give you a picture of what you may be aiming for. Obviously I have kept NTFS for Windows.

---

### Post by ouchifell on 2009-07-28
how much would you allocate to each with a 250 gig hard drive?

3 gigs for swap since i have 2 gigs of ram ...

how much for /boot, /root, and /home? and which ones do i assign as primary and which do i make as part of the extended?

i know some of these values depend on what type of user i am. 99% of use is surfing the net and using bit torrent ...

---

### Post by ouchifell on 2009-07-28
ok ... i think i got it ... so far, i've allocated 3 gigs for swap ... and 15 for /root ... both primary ... now i'm going to make 2 logical partition and call them both /home ... one of which will be for movies ... does that make sense?

---

### Post by Shazaam on 2009-07-28
> **ouchifell said:**
> i don't plan on installing windows so i've just gone ahead and allocated my swap partition.

for the extended partition, if i want to divide them into various logical partitions ... do i have to assign it a mount point? i want to allocate 100 gigs of the extended partition to movies ... mount point required?

Mmmmm, it's up to you. There are differing opinions on separate partitions. Some like them, some don't. The main advantage is if you decide to re-install or upgrade (9.04 to 9.10, etc) later you don't loose files that are not part of a Ubuntu install like movies and such.

---

### Post by running_rabbit07 on 2009-07-28
> **ouchifell said:**
> ok ... i think i got it ... so far, i've allocated 3 gigs for swap ... and 15 for /root ... both primary ... now i'm going to make 2 logical partition and call them both /home ... one of which will be for movies ... does that make sense?

If you make them both /home the system will get confused. If you want to make an extra partition you will be better off leaving whatever size you want the extra storage partition to be as unallocated for now and install Ubuntu. 

Once installed, go into Synaptic Package Manager under the System>Administration menu and install GParted. With this program you can create the extra partition as EXT3 or EXT4, doesn't matter and you can mount it and save folders and files to it.

---

### Post by ouchifell on 2009-07-28
ok ... i think i'm done messing with this ... i think i'm spending too much time on this hehe ... i decided to go with the 3 gigs of swap, 15 of /root, and the rest for /home ... thanks so much to all that replied

---

### Post by running_rabbit07 on 2009-07-28
> **ouchifell said:**
> ok ... i think i'm done messing with this ... i think i'm spending too much time on this hehe ... i decided to go with the 3 gigs of swap, 15 of /root, and the rest for /home ... thanks so much to all that replied

You are welcome. Happy Ubuntuing!

---

### Post by ericab on 2009-07-28
15 gigs for /root is a major waste.

---

### Post by running_rabbit07 on 2009-07-29
> **ericab said:**
> 15 gigs for /root is a major waste.

That is a good opinion. If you would like to write a thread on making a "perfect" partition table I am sure the Admins might even make it a sticky.:D

---

