---
title: "PC random freeze issue"
date: 2015-05-21
forum: Hardware
---

### Post by rockwinder on 2015-05-21
Hello everyone,

I built a desktop system 1 year ago. I checked devices' compatibility with each other from forums before building. It freezes randomly. I thought it was software caused and tried linux also but no luck. I need help for debugging the problematic hardware. 

I checked cpu temp - it's around 20-40.

Also, it freezes even in idle state after running for hours. It usually freezes on desktop while a music is playing in a software or youtube. It freezes less in games and videos.

I have dual boot Ubuntu 15.04 32 bit and Windows 8.1 64 bit. So I can use both for debugging if you advice anything. I used Linux Mint 64 bit before Ubuntu and it freezed too.

It is so random that I can't reproduce when I wish.

Here is the PC specs:

CPU Type: OctalCore AMD FX-8320, 3800 MHz
CPU Fan: Xigmatek SD1283 GAIA II
Motherboard: Asus M5A97 Evo R2.0
Mobo Chipset: AMD 970, AMD K15
Memory: Corsair Vengeance LP CML4GX3M1A1600C9 4 GB DDR3-1333 DDR3 SDRAM 
Video Adapter: AMD Radeon HD7790 (2 GB)
Audio Adapter: Realtek ALC892 @ ATI SB900 (HDMI connected)
Disk Drive: Seagate ST1000DM003-1CH162 (1000 GB, 7200 RPM, SATA-III)
PSU:            650 watt 
Monitor: A Turkish branded 40" HDTV (Vestel)

Thank you in advance.

---

### Post by dino99 on 2015-05-21
Please post the output of > cat /etc/fstab and >  sudo blkid
Glancing at > sudo journalctl for warnings/errors might help a lot

---

### Post by weatherman2 on 2015-05-21
Try running Memtest overnight.

Your problem may be a faulty power supply, hard drive, video card, or even some motherboard defect.  Freezes that occur in multiple operating systems are usually hardware, and if they occur rarely and randomly, they can be difficult to identify.  Sometimes "replace one thing" (like a stick of RAM, etc.) is the easiest way to try to eliminate a problem.  Usually the motherboard itself is considered the problem if you've ruled out everything else.

---

### Post by rockwinder on 2015-05-22
> **dino99 said:**
> Please post the output of  and 
Glancing at  for warnings/errors might help a lot

cat /etc/fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=3a6e30b4-96c3-439b-99e4-d29d30c50656 /               ext4    errors=remount-ro 0       1
# /winC was on /dev/sda2 during installation
# UUID=3EF64D40F64CF9A3 /winC           ntfs    defaults,umask=007,gid=46 0       0
# /winE was on /dev/sda4 during installation
UUID=7A8A66228A65DB61 /winE           ntfs    defaults,umask=007,gid=46 0       0
```

sudo blkid:
```

/dev/sda1: LABEL="System Reserved" UUID="DC78461D7845F6B4" TYPE="ntfs" 
/dev/sda2: UUID="3EF64D40F64CF9A3" TYPE="ntfs" 
/dev/sda3: UUID="3a6e30b4-96c3-439b-99e4-d29d30c50656" TYPE="ext4" 
/dev/sda4: UUID="7A8A66228A65DB61" TYPE="ntfs" 
```

I just installed Linux Mint 32 bit now and there is no journalctl package as Mint doesn't replaced to systemd. Is there any equilavent command? If no I can change back to Ubuntu.

> **weatherman2 said:**
> Try running Memtest overnight.

Your problem may be a faulty power supply, hard drive, video card, or even some motherboard defect.  Freezes that occur in multiple operating systems are usually hardware, and if they occur rarely and randomly, they can be difficult to identify.  Sometimes "replace one thing" (like a stick of RAM, etc.) is the easiest way to try to eliminate a problem.  Usually the motherboard itself is considered the problem if you've ruled out everything else.

I'll try Memtest but is there any risk of freeze during the test? Could it freeze and start burning? :) Or freeze and display gone after long test?

And if it's really the mainboard, the warranty still goes on for a little time left. But I don't have any replacement parts for "replace one thing" method. I'll go to repair center for problem detection, if I can't do anything else to do.

Thanks for your answers!

BR

---

### Post by dino99 on 2015-05-22
you are missing a swap partition that can explain that random freezing.

general info:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Steps to create a swap partition, after installation:
[http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation](http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation)

---

### Post by rockwinder on 2015-05-22
I used to use swap file but it still freezed. And what about windows? Now I just created a swap file.

```
UID=3a6e30b4-96c3-439b-99e4-d29d30c50656 /               ext4    errors=remount-ro 0       1
# /winC was on /dev/sda2 during installation
# UUID=3EF64D40F64CF9A3 /winC           ntfs    defaults,umask=007,gid=46 0       0
# /winE was on /dev/sda4 during installation
UUID=7A8A66228A65DB61 /winE           ntfs    defaults,umask=007,gid=46 0       0
# swap
/swapfile/4096mb.swap    none    swap    sw    0    0
```

BR

---

### Post by rockwinder on 2015-05-22
Hello,

I ran Memtest today. Results ([http://imgur.com/rwYAOFG](http://imgur.com/rwYAOFG)): ```
WallTime: 09:47:03, Pass: 9, Error: 0
```

But it shows RAM as 320 MHz (DDR640) / CAS: 1-3-3-3 / DDR2 (64 bits). CPU is shown correct.

Why is that? My RAM is 1600 MHz DDR3 and CAS is 9-9-9-24 ([http://www.corsair.com/en-us/vengeance-low-profile-4gb-ddr3-memory-kit-cml4gx3m1a1600c9](http://www.corsair.com/en-us/vengeance-low-profile-4gb-ddr3-memory-kit-cml4gx3m1a1600c9))

There is a setting about memory in Memtest. The default is getting info from BIOS that shows wrong value as I explained. And there is a 2nd option is "probe" and it freezes the pc.

BR

---

### Post by tgalati4 on 2015-05-22
You can try updating the BIOS on the motherboard if there is a patch for better memory detection.  You can also change the CAS timing manually and set it to some conservative values and see if stability improves.  Unfortunately, when you build your own system, you have to wring out these types of issues.  Try some different RAM, or reduce RAM to a minimum set and see if the behavior changes.

---

### Post by rockwinder on 2015-05-22
I'll try manual CAS timing when I get home. But Asus said my RAM is compatible with the mainboard: [http://dlcdnet.asus.com/pub/ASUS/mb/SocketAM3+/M5A99FX_PRO_R20/M5A_Series_DRAM_QVL_201406.pdf](http://dlcdnet.asus.com/pub/ASUS/mb/SocketAM3+/M5A99FX_PRO_R20/M5A_Series_DRAM_QVL_201406.pdf)

BR

---

### Post by Easy Limits on 2015-05-23
Is the RAM speed setting in the BIOS set correctly to match your actual RAM speed (1333Mhz)?

---

### Post by dino99 on 2015-05-23
Myself have learnt the hard way about what crappy 'auto' ram bios settings can do: random booting errors, kernel panic, boot at lower speed
Since i have set the voltage and cas manually, then all the previous errors are gone

---

### Post by rockwinder on 2015-05-24
Thanks for your answers. I updated BIOS (version: 2603) yesterday and it didn't freeze for 1 day yet. I'll test for a few days more. Hope it solved my problem.

BR

---

### Post by tgalati4 on 2015-05-24
Install *uptimed* and use *uprecords* to keep track of your uptime progress:

```
sudo apt-get install uptimed
uprecords
```

It should look something like:

> tgalati4@Mint17 ~ $ uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
->   1    32 days, 06:30:01 | Linux 3.13.0-24-generic   Wed Apr 22 11:58:01 2015
     2    32 days, 06:28:31 | Linux 3.13.0-24-generic   Wed Apr 22 11:57:46 2015
     3    22 days, 03:49:07 | Linux 3.13.0-24-generic   Fri Jan 16 08:56:25 2015
     4    16 days, 02:37:28 | Linux 3.13.0-24-generic   Tue Mar 24 13:08:32 2015
     5    12 days, 12:44:16 | Linux 3.13.0-24-generic   Sun Feb 15 07:06:15 2015
     6    12 days, 01:15:47 | Linux 3.13.0-24-generic   Fri Feb 27 19:52:00 2015
     7    11 days, 15:37:26 | Linux 3.13.0-24-generic   Fri Apr 10 16:52:10 2015
     8     7 days, 19:02:52 | Linux 3.13.0-24-generic   Thu Mar 12 19:19:13 2015
     9     7 days, 15:47:18 | Linux 3.13.0-24-generic   Sat Feb  7 14:34:35 2015
    10     0 days, 23:58:55 | Linux 3.13.0-24-generic   Thu Apr  9 16:19:52 2015
----------------------------+---------------------------------------------------
NewRec     0 days, 00:01:29 | since                     Sun May 24 18:26:31 2015
    up   157 days, 03:05:47 | since                     Fri Jan 16 08:56:25 2015
  down   -28 days, -18:-34: | since                     Fri Jan 16 08:56:25 2015
   %up              122.417 | since                     Fri Jan 16 08:56:25 2015


---

