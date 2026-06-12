---
title: "USB hard drive is read-only"
date: 2009-05-07
forum: Hardware
---

### Post by SomeHobo on 2009-05-07
Hi all,

I did all the googling I could and tried everything yet my USB connected hard drive just refuses to delete files or add more onto it.

here's what I tried:

$ sudo chmod 777 Crapodisko/
chmod: changing permissions of `Crapodisko/': Read-only file system

someone suggested this - it didn't work either:
$ sudo dosfsck -a /media/Crapodisko
[sudo] password for watachichi: 
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
open /media/Crapodisko:Is a directory

I tried changing the owner and permissions through Nautilus - it doesn't work: it says either Read-only file system or "you are not the owner" 

the owner listed is #99 (which google says means "nobody")

I also tried simply formating the disk with gparted - same read-only thing again.

So far the disk seems to be totally sudo-and-chmod-proof I'm out of ideas and out of google results to click.

A little history on this disk, we had the same problem before and I couldn't do anything with it but to format it with my mac. When mounted on my mac, the permissions are read&write for everyone and I can delete, copy or whatever...

I need this disk for backing up my ubuntu desktop and it just wouldn't be practical to transfer all the files to my laptop and then to the disk - also, obviously that would be equivalent to declaring defeat and I love ubuntu too much for that.

please help!

---

### Post by taurus on 2009-05-07
Is it /dev/sdb1?

```
sudo umount /dev/sdb1
sudo mkdir /media/Crapodisko
sudo mount -t vfat /dev/sdb1 /media/Crapodisko **[COLOR="Blue"]-o umask=000[/COLOR]**
df -h
```

---

### Post by SomeHobo on 2009-05-07
Hi Taurus, thanks for the help. I tried your commands but got an error on the 3rd one.

I'm not sure what you mean by "is it sdb1" - I tried googling sdb1 but didn't get much at my level of knowledge. here's the error I got:

```


$ sudo mount -t vfat /dev/sdb1 /media/Crapodisko -o umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```



I had a look under /dev/ and I do have a sdb1, I don't know if the rest is of any use to you but I'm pasting the condents of /dev/ right here.

```

adsp             network_throughput  sr0     tty48           usbdev6.2_ep07
adsp1            null                stderr  tty49           usbdev6.2_ep81
agpgart          nvidia0             stdin   tty5            usbdev6.2_ep82
audio            nvidiactl           stdout  tty50           usbdev6.2_ep83
audio1           oldmem              tty     tty51           usbdev6.2_ep87
block            pktcdvd             tty0    tty52           usbdev6.3_ep00
bus              port                tty1    tty53           usbdev6.3_ep81
cdrom            ppp                 tty10   tty54           usbdev7.1_ep00
cdrw             psaux               tty11   tty55           usbdev7.1_ep81
char             ptmx                tty12   tty56           usbdev8.1_ep00
console          pts                 tty13   tty57           usbdev8.1_ep81
core             ram0                tty14   tty58           usbdev8.2_ep00
cpu_dma_latency  ram1                tty15   tty59           usbdev8.2_ep02
disk             ram10               tty16   tty6            usbdev8.2_ep83
dmmidi           ram11               tty17   tty60           usblp0
dsp              ram12               tty18   tty61           usblp1
dsp1             ram13               tty19   tty62           usbmon0
dvd              ram14               tty2    tty63           usbmon1
dvdrw            ram15               tty20   tty7            usbmon2
ecryptfs         ram2                tty21   tty8            usbmon3
fd               ram3                tty22   tty9            usbmon4
full             ram4                tty23   ttyS0           usbmon5
fuse             ram5                tty24   ttyS1           usbmon6
hidraw0          ram6                tty25   ttyS2           usbmon7
hidraw1          ram7                tty26   ttyS3           usbmon8
hidraw2          ram8                tty27   urandom         vcs
hidraw3          ram9                tty28   usb             vcs1
initctl          random              tty29   usbdev1.1_ep00  vcs2
input            rtc                 tty3    usbdev1.1_ep81  vcs3
kmem             rtc0                tty30   usbdev2.1_ep00  vcs4
kmsg             scd0                tty31   usbdev2.1_ep81  vcs5
log              sda                 tty32   usbdev2.8_ep00  vcs6
loop0            sda1                tty33   usbdev2.8_ep02  vcs7
loop1            sda2                tty34   usbdev2.8_ep81  vcs8
loop2            sda5                tty35   usbdev3.1_ep00  vcsa
loop3            sda6                tty36   usbdev3.1_ep81  vcsa1
loop4            sda7                tty37   usbdev4.1_ep00  vcsa2
loop5            sdb                 tty38   usbdev4.1_ep81  vcsa3
loop6            sdb1                tty39   usbdev5.1_ep00  vcsa4
loop7            sequencer           tty4    usbdev5.1_ep81  vcsa5
MAKEDEV          sequencer2          tty40   usbdev5.2_ep00  vcsa6
mapper           sg0                 tty41   usbdev5.2_ep81  vcsa7
mem              sg1                 tty42   usbdev5.2_ep82  vcsa8
midi             sg2                 tty43   usbdev6.1_ep00  xconsole
mixer            shm                 tty44   usbdev6.1_ep81  zero
mixer1           snapshot            tty45   usbdev6.2_ep00
net              snd                 tty46   usbdev6.2_ep01
network_latency  sndstat             tty47   usbdev6.2_ep02

```

---

### Post by taurus on 2009-05-07
Post the output of this command then.

```
sudo fdisk -l
```

---

### Post by SomeHobo on 2009-05-07
I get this:
note that the 320 gig one is the internal one and is fine, it's the 500 gig one that's giving me trouble.

```


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42972524

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12352    99217408+   7  HPFS/NTFS
/dev/sda2           12353       38912   213343200    f  W95 Ext'd (LBA)
/dev/sda5           25497       38912   107763988+   7  HPFS/NTFS
/dev/sda6           12353       25309   104077039+  83  Linux
/dev/sda7           25310       25496     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386552+  af  Unknown




```

---

### Post by SomeHobo on 2009-05-08
I have some interesting news:

I closed my computer yesterday night but forgot to shut down the external drive, now this morning when I booted my desktop the external drive was mounted right away and everything seemed to work fine, I could copy, delete and everything.

So I started my backup of 96 .rar files (of roughly 500mb each) 

I sent the files through terminal with a "mv" command but at file 37-8 I got an error that there is no more space on device (the drive is empty and should have 500gb free) file 39-96 each says 

```

mv: cannot create regular file  '(file name and path here)': Input/output error

```

Basically now, my disk was unmounted - I had to physically unplug and re-plug the USB - and now I have the same "read-only filesystem" problem.

I tried to reset the desktop, reset the drive, anything it seems stuck in read only again. 

Could it be that the disk is bad? Or is there a program that doesn't care about permissions and just plows through formatting the whole thing no matter what?

---

### Post by DJYoshaBYD on 2009-05-08
try this

open synaptic, and search for NTFS

there should be something called the ntfs configuration tool.. its simply a lil program with 2 check boxes... they will give you read/write access..

I have been doing this for external drives, but they really should be just PnP...

also, if you had the ntfs drive mounted to a windows system, and didnt shut down or remove the rive properly, then it may stay read only until you put it back into a windows machine and properly unmount it.. i have only had this problem a few times on my dualbooted pc, but it fixed it every time it happened..

you could also just format the drive to NTFS again (since its empty, right?) and try to mount it again..

hope it helps..

---

### Post by t0cableguy on 2009-05-08
I'm having this same issue but with an internal drive. it is that same exact size, with the same number of heads and sectors, probably the same make and model drive.

---

### Post by SomeHobo on 2009-05-09
Thanks for the tip Yosha, unfortuatly the NTFS configuration tool didn't do the trick...

So I decided to give another try to gparted and this time it worked out just fine and stuff is transfering right now on it, seems to be doing great so far.

Just in case other people are having the same problem here's what I did:

I used gparted to create a new partition on the disk and to then format it (I used ext4). 
The one thing to watch out for is to make sure the disk is connected but unmounted 
(mine was mounted and for the longest time I couldn't figure out why gparted gave me an error when trying to format). 

Once that was done, the disk was still read-only but I changed that by changing the disk owner to root.

```

$ chown root /media/disk/

```

and then giving all the permissions to everyone:
```

$ chmod 777 /media/disk/

```

And then everything works just fine. 

In retrospect the solution seems so easy but when you don't know what the problem is....

I believe my problem was that the formatting type that I did with OSX might not have been compatible with linux somehow - I don't know enough about those things though...

---

### Post by soberrover on 2009-12-08
it worked! thanks very much for posting the solution.
for me, it was my SD cards in a USB reader, but it's really the same problem. It happened to both my 1gb and my 8gb cards at pretty much the same time, after they had both been working normally the day before. creepy... it's gotta be some sort of bug.
when I formatted the disks, I kept them as FAT32 just in case my digital camera would have problems with an ext file system

---

### Post by grahams on 2009-12-13
Having the same issue with an 1G Ipod shuffle on 9.10. Had to reformat.

Had worked fine on 9.04

---

