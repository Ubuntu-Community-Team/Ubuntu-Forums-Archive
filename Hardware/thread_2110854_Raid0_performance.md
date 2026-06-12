---
title: "Raid0 performance"
date: 2013-01-31
forum: Hardware
---

### Post by Mascarade on 2013-01-31
Hi All :p

I,m using kubuntu 12.10...

using mdadm
I get a raid1 for /boot...ext4
and raid0 for /system, /swap, /home...... ext4
I get p4p800 deluxe motherboard, 1,2 gigaheartz, 4 gig ram, radeon 1950 video card....

I saw a lot of documentation on raid partitionning but not for the performance.......
My raid device work well, but if i transfert a movie, mp3, a bunch of text documents from my home to a ntfs device, my transfer rate is at 15 to 17 m/sec....
Now if i transfert the same example from my home to an external device, i goes up to 20 m/sec.....

My question is : the performance for a raid0 device is not suppose goes faster than whit a usb drive??

Using usb2...... In windowshit my raid performance was very faster whit 2 internal (raid0) drive then whit an internal (raid0) drive and a usb drive!!

So how come?

I don't go crazy whit that like 20m/sec, it ok for me, but i just don't understand!!!

Thanks for your reply :o)

Louis

---

### Post by SlugSlug on 2013-01-31
so your home is on raid and difference in speed is what your writing to NTFS drive / USB drive?

you can benchmark speed with hdparm

```
sudo hdparm -Tt /dev/sda
```


depends where your raid is?

```
sudo hdparm -Tt /dev/md0
```
 in my case

---

### Post by Mascarade on 2013-01-31
Hi thank i wasn't know this command :p

The /sdb1 is my data ntfs, and /md3 my home folder in raid0....

/dev/sdb1:
 Timing cached reads:   1862 MB in  2.00 seconds = 930.68 MB/sec
 Timing buffered disk reads: 200 MB in  3.02 seconds =  66.19 MB/s

/dev/md3:
 Timing cached reads:   1860 MB in  2.00 seconds = 929.45 MB/sec
 Timing buffered disk reads: 224 MB in  3.01 seconds =  74.52 MB/s

Is not a big deal... :o)
and there is a prob for benchmark writting? because my result in all case resume to be the same performance whit a raid0 or not.....? That is not strange?

Thank for your response amigo :0)

---

### Post by SlugSlug on 2013-01-31
Thats not a good raid0 speed

Is it onboard raid or a PCI card?

my 4 disk motherboard raid0:

```
 sudo hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   3614 MB in  2.00 seconds = 1807.58 MB/sec
 Timing buffered disk reads: 1134 MB in  3.00 seconds = 377.63 MB/sec
```
for write speed you can 

SSD:
```
dd if=/dev/zero of=/tmp/output bs=8k count=100k;
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 1.04223 s, 805 MB/s

```
RAID0:
 ```
dd if=/dev/zero of=/mnt/raid0/output bs=8k count=100k;
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 1.34461 s, 624 MB/s
```

---

### Post by Mascarade on 2013-01-31
mascarade@Kubuntu:~$ dd if=/dev/zero of=/tmp/output bs=8k count=100k
102400+0 records in
102400+0 records out
838860800 bytes (839 MB) copied, 5.92882 s, 141 MB/s

and the other command doesn't work...

It a onboard raid controller, but when i was looking to create a raid device in kubuntu all the people was saying that desactivate all onboard controller in bios and to don't create the raid device in bios seting...So i desactive all in bios and i didn't see the raid device before booting an Os...(like ctrl + i).... and i got 2 device for the raid setup...

And i got sata 1 for the 2 devices......Raptor disk.....And i think i can't go more 150 m/sec per disk...

On board intel ich5r

---

### Post by tgalati4 on 2013-01-31
RAID0 should theoretically be 2X faster than single-drive speeds, but since you have split the operating system between different RAID schemes (RAID0 and RAID1) you may have an internal bottleneck.  For instance where is root?  (/)

I get a raid1 for /boot...ext4
and raid0 for /system, /swap, /home...... ext4

Is that the same as /system?  It's generally not a good idea to run /home on RAID0 since data errors will immediately trash your personal data, in a way that is not recoverable.

[http://en.wikipedia.org/wiki/RAID0](http://en.wikipedia.org/wiki/RAID0)

Additionally, /swap should be on its own partition and not on a RAID0.  If you have enough RAM then you won't use swap, but regardless, it doesn't make sense to speed up swap with RAID0 when you want to avoid swap in the first place with enough RAM.

---

### Post by Mascarade on 2013-01-31
HI tgalati4 :)

i know it not usefull for the swap...it just because i'm knew under gnu/linux and in winshit, you don't have to make partition like this....so i was confused and decide to split everything on my raid array egual..... that why! :)

So if i understand you i just have to create a raid 0 on /root? (the /system is my root)
butif i want want a swap on one drive, then the 2 drive for raid0 not gonna be the same gig!?!?!?

Do i make raid0 on /root and leave the /home install in the same partition then /root?
and i can create on one drive the /boot and on the other the /swap and put the same gig on both of them? so my 2 disk gonna have the same space...??...

And i got an external drive to backup everything, so i Don't care about loosing data....

/dev/mdo = /boot (raid1) ext4
/dev/md1 = / (raid0) ext4
/dev/md2 = /swap (raid0)
/dev/md3 = /home (raid0) ext4

and do i need to activate my raid controller in motherboard?
or should i re-install whitout raid1?
Or, i make a raid array for my 2 disk an make an standard install?

Thanks!
Louis

---

### Post by tgalati4 on 2013-01-31
If you are new to linux, then I would do a standard installation without any RAID.  Just make a swap partition that exceeds your RAM slightly and do a normal install.  If you have two disks, you can put /home on a separate disk and that may give some performance improvement and make backups and migration a little easier.  I would spend 6 months to a year using linux in the standard configuration before messing with performance.  

Otherwise, you will be constantly questioning why things are not working right when you don't have a standard installation to compare to.  But that is my opinion.  It's your machine and if you can do what you want.  If you break it, you get to keep the pieces.

You need a standard setup and collect some benchmarks on the standard setup so you know what your machine is capable of in standard configuration.  No BIOS RAID, no software RAID, just simple installation so you can learn linux on a stable platform.

---

### Post by Mascarade on 2013-01-31
Yeah i understand your point but i'm learning a lot!!!!

And i was able alone to create this raid array and it work axept for the performance.....

and a was able to switch from the kubuntu 12.04 to 12.10.......

i  able to understand it..... i configureit well for the rest like in option and other thing...all my system work fine exept this thing for speed that escape from me..... i'm new, but i'm playing whit that for 4 month whit a several number of hour in a day....... but i want to experiment the debian squeeze distro, so i can put on an another drive and see what performance i have..... and keep kubuntu like this.....
Everyone in post that i read say that the raid controller is **** in linux......Cuz the mdadm can't recognize it?
I read your info in wiki... And for the disk that is not same equality i know that it work.....
So if a make a install whit /swap and /boot one one drive and make a raid0 array for /root and /home it sould be work?
Thank :)

---

### Post by tgalati4 on 2013-01-31
If your hardware/motherboard RAID is considered "fakeRAID", then yes, they are generally crappy.  If it is a dedicated, hardware RAID controller with a separate battery for cache writes, and separate, RAID BIOS, then you might get better performance with hardware RAID and hot-swap capability.  Software RAID is convenient, but not necessarily faster than single-drive performance.  It depends on a lot of factors and testing in your environment.

---

