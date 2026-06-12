---
title: "DVD R/W Read error"
date: 2008-11-16
forum: Hardware
---

### Post by aazamansari on 2008-11-16
Hi All,

I am able to write DVD and CD using my DVD R/W. But I am unable to read files from using the DVD R/W.

I can browse the CD but I cannot play or read any file.

It gives following error.

VFS: busy inodes on changed media.
[  783.217380] VFS: busy inodes on changed media.
[  783.247024] VFS: busy inodes on changed media.
[  783.257256] VFS: busy inodes on changed media.
[  783.272615] VFS: busy inodes on changed media.
[  783.282270] VFS: busy inodes on changed media.
[  783.559358] VFS: busy inodes on changed media.
[  783.567797] VFS: busy inodes on changed media.
[  784.646838] VFS: busy inodes on changed media.
[  784.654601] VFS: busy inodes on changed media.
[  784.861791] end_request: I/O error, dev sr0, sector 19656
[  784.861802] printk: 32 messages suppressed.
[  784.861807] Buffer I/O error on device sr0, logical block 4914
[  784.861814] Buffer I/O error on device sr0, logical block 4915
[  784.869272] end_request: I/O error, dev sr0, sector 19656
[  784.869284] Buffer I/O error on device sr0, logical block 4914
[  784.885292] end_request: I/O error, dev sr0, sector 19660
[  784.885304] Buffer I/O error on device sr0, logical block 4915
[  784.908050] end_request: I/O error, dev sr0, sector 19672
[  784.908062] Buffer I/O error on device sr0, logical block 4918
[  784.908070] Buffer I/O error on device sr0, logical block 4919
[  784.925600] end_request: I/O error, dev sr0, sector 19672
[  784.925612] Buffer I/O error on device sr0, logical block 4918
[  784.946225] end_request: I/O error, dev sr0, sector 19676
[  784.946237] Buffer I/O error on device sr0, logical block 4919
[  784.958513] end_request: I/O error, dev sr0, sector 19680
[  784.958525] Buffer I/O error on device sr0, logical block 4920
[  784.958533] Buffer I/O error on device sr0, logical block 4921
[  784.969142] end_request: I/O error, dev sr0, sector 19680
[  784.990446] end_request: I/O error, dev sr0, sector 19684
[  785.004694] end_request: I/O error, dev sr0, sector 19672
[  785.017455] end_request: I/O error, dev sr0, sector 19672
[  785.034168] end_request: I/O error, dev sr0, sector 19676
[  785.045102] end_request: I/O error, dev sr0, sector 19680
[  785.064531] end_request: I/O error, dev sr0, sector 19672
[  785.081028] end_request: I/O error, dev sr0, sector 19676
[  785.088618] end_request: I/O error, dev sr0, sector 19672
[  785.104620] end_request: I/O error, dev sr0, sector 19672
[  785.123314] end_request: I/O error, dev sr0, sector 19676
[  785.134596] end_request: I/O error, dev sr0, sector 19672
[  785.147998] end_request: I/O error, dev sr0, sector 19672
[  785.159447] end_request: I/O error, dev sr0, sector 19676
[  785.174961] end_request: I/O error, dev sr0, sector 19800
[  785.185963] end_request: I/O error, dev sr0, sector 19736
[  785.215756] end_request: I/O error, dev sr0, sector 19740
[  785.233930] end_request: I/O error, dev sr0, sector 19736
[  785.249604] end_request: I/O error, dev sr0, sector 19736
[  785.267508] end_request: I/O error, dev sr0, sector 19740
[  785.280913] end_request: I/O error, dev sr0, sector 19672
[  785.299279] end_request: I/O error, dev sr0, sector 19672
[  785.307124] end_request: I/O error, dev sr0, sector 19676
[  785.329037] end_request: I/O error, dev sr0, sector 19672
[  785.338681] end_request: I/O error, dev sr0, sector 19672
[  785.356295] end_request: I/O error, dev sr0, sector 19676
[  785.375741] end_request: I/O error, dev sr0, sector 19672
[  785.386444] end_request: I/O error, dev sr0, sector 19688
[  785.401376] end_request: I/O error, dev sr0, sector 19692
[  785.413396] end_request: I/O error, dev sr0, sector 19672
[  785.423936] end_request: I/O error, dev sr0, sector 19672
[  785.443034] end_request: I/O error, dev sr0, sector 19676
[  785.463080] end_request: I/O error, dev sr0, sector 19672
[  785.479309] end_request: I/O error, dev sr0, sector 19672
[  785.493199] end_request: I/O error, dev sr0, sector 19676
[  785.504004] end_request: I/O error, dev sr0, sector 19672
[  785.514977] end_request: I/O error, dev sr0, sector 19672
[  785.536178] end_request: I/O error, dev sr0, sector 19676
[  785.550878] end_request: I/O error, dev sr0, sector 19680

Please can anyone suggest what should I do. The DVD R/W works fine on the same machine using Windows XP.

---

### Post by Xikkub on 2008-11-16
The disc drive may just be broken. I have a few drives that can write data but not read it and vice-versa. Maybe put another CD drive in your computer and see if that one works?

---

### Post by aazamansari on 2008-11-16
> **Xikkub said:**
> The disc drive may just be broken. I have a few drives that can write data but not read it and vice-versa. Maybe put another CD drive in your computer and see if that one works?

Thanks Xikkub for your suggestion. But the drive that I am using is new and it works fine on Windows XP. Actually I am using a Lenovo Laptop which I have just bought and I see this problem on my laptop.

I have read different threads related to this problem but it seems that there is no solution yet for this problem.

I need a solution or atleast a workaround which helps me read a DVD/CD. It doesn't matters if disk write doesn't work on my system since it is not of much importance to me right now.

---

### Post by apollyon0810 on 2008-11-17
I guess I'm having the same problem.  But it is specifically with LiveCD's.  It errors after loading "busybox".  Same error though.  I have a Samsung SATA DVD R/W.

---

### Post by aazamansari on 2008-11-21
Thanks Xikkub for your suggestion. But the drive that I am using is new and it works fine on Windows XP. Actually I am using a Lenovo Laptop which I have just bought and I see this problem on my laptop.

I have read different threads related to this problem but it seems that there is no solution yet for this problem.

I need a solution or atleast a workaround which helps me read a DVD/CD. It doesn't matters if disk write doesn't work on my system since it is not of much importance to me right now.

---

### Post by capsel on 2008-11-22
I have the same problem. I have it under 8.04 and 8.10 (ubuntu/kubuntu if there is a difference).

CDRW woks under my XP and GENTOO (linux) on every dvd I have, but not ubuntu (same machine).

DVD discs I've tested works on every other computer that I have.

I connected old ide dvd-reader via usb and I have same results.

Strange thing is that when I started ubuntu with kernel from my gentoo-backup the problem persists. And I did not forgot about modules.

Setting options for libata (atapi_enabled, dma=7) did not worked (/sys/modules/libata/parameters/* showed correct results).

I've also tried some other options for kernel cmdline that I do not remember right now...

Compiling into kernel libata, cdrom, scsi subsystem didn't help.

gmplayer dvd://
starts buffering but it goes very slowly, and after buffering it still reads something...

What are my other options?

sorry for syntax errors :)

---

### Post by Yezinki on 2008-11-22
Poor quality media or dirty lens.

Regards,

Yezinki.

---

### Post by capsel on 2008-11-22
> **Yezinki said:**
> Poor quality media or dirty lens.

Regards,

Yezinki.

I checked every combination (disk/drive/computer/system) I thought of, and it's not:

- broken dvd drive
- broken dvd disk

Or...

all my dvd disks are "poor" and every dvd drive of my friends, and mine, are dirty.

I don't know how this is possible but under windows and gentoo all my dvd disks, dvd drives works fine.

---

### Post by capsel on 2008-11-22
I'm back on gentoo right now, and all my dvd works fine. No errors in dmesg.

---

### Post by Yezinki on 2008-11-23
> **capsel said:**
> I checked every combination (disk/drive/computer/system) I thought of, and it's not:

- broken dvd drive
- broken dvd disk

Or...

all my dvd disks are "poor" and every dvd drive of my friends, and mine, are dirty.

I don't know how this is possible but under windows and gentoo all my dvd disks, dvd drives works fine.



Well I agree with you.......hard ware mismatch/ incompatibility with Ubuntu 8.10....that's the only thing left.

Regards,

Yezinki.

---

### Post by capsel on 2008-11-23
Thank you for your reply, that was very helpfull.

Is there any way I can help to solve this bug or you just going to write obvious, but not very helpfull, things, driving me mad?

The fact is - ubuntu does not handle my dvds. I think this is called entry point (or exit point).

--
I've checked that after disabling "laptop-mode" from starting at boot time helped, at least it (mplayer) started to "play". I haven't seen any images on screen but it did say that it plays something.

I've got to laptop-mode by grepping "proc" out of /etc.

Is there anyone that can help here?

---

### Post by DMBryant on 2008-12-16
I think I have the same problem.

I've just moved an internal DVD R/W (ide) into an external USB enclosure.  I can navigate discs and burn discs but cannot read any of the files on the disc.  I know it's not the drive as it worked before (plugged directly into IDE cable) and also works fine in XP.

In dmesg I get:

[sr0] unaligned transfer

and lots of:

buffer i/o error on device sr0

Anyone got any ideas?

---

### Post by DMBryant on 2008-12-16
Sorry, I cant give any more detail than that at the moment as I am at work :-)

---

### Post by Yezinki on 2008-12-16
[http://ubuntuforums.org/showthread.php?t=978408](http://ubuntuforums.org/showthread.php?t=978408)

---

### Post by aazamansari on 2008-12-16
Please try following:

mount -t iso9660 /dev/sr0 /media/cdrom

You need to be administrator for this.

Replace /dev/sr0 by the device in you system and replace /media/cdrom by the folder where you want to mount the DVD/CD.

If the CD/DVD is already mounted then you will have to unmount it first and then try the above command.

---

### Post by DMBryant on 2008-12-17
Nope, sorry, didn't make any difference :(

---

