---
title: "Problem transferring files between HDDs"
date: 2009-03-13
forum: Hardware
---

### Post by Squall117 on 2009-03-13
Hello, I recently bought a new HDD and in Windows XP I can't get it to run DMA so it's a real pain to transfer files because the PIO mode takes a lot of the processor.

So I rebooted to Ubuntu and everything went great, I transfer files at 20Mb/s speed. So I decided to disable the new drive in windows and do the file transfers when I'm using Ubuntu. But today I started having problems... The transfer just froze in 1.2 Gb of 2.6 Gb - 1 minute left (20.4Ms/s) and now when I try to access it, I get this message: "Transport endpoint is not connected"

I wrote this in terminal, though I don't know what it does but I just read that in some other threads people asked for the output of this command **df -h**

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             6.2G  3.7G  2.2G  63% /
varrun                377M  104K  376M   1% /var/run
varlock               377M     0  377M   0% /var/lock
udev                  377M   64K  377M   1% /dev
devshm                377M  132K  376M   1% /dev/shm
lrm                   377M   44M  333M  12% /lib/modules/2.6.24-23-generic/volatile
/dev/sdb1              68G   35G   34G  52% /media/Lionheart
df: `/media/Lionheart II': Transport endpoint is not connected

```

Some additional information:
-My motherboard is capable of SATA 1.5 but not 3.0 and the HDD is 3.0 but with a jumper setting it goes to 1.5 which is what I'm doing since I installed the HDD.
-This SATA HDD is meant for a new computer I'm building but right now I'm using it as backup/storage unit. My boot HDD is an old 80Gb IDE HDD with Ubuntu and Windows XP.
-I have two RAMs one with 512Mb and the other with 256Mb. The one with 512Mb is not working good. When I use Memtest86+ it goes crazy with errors. Sometimes 16000+ and sometimes even 300000+
-I know my poor hardware is dying, I'm just trying to make it work until I finish buying all the stuff for my new system.

Thanks in advance.

---

