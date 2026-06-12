---
title: "Ubuntu installation on USB disk"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Brian88 on 2009-10-09
I want to install Ubuntu (9.04) on an 8GB Kingston USB flash disk (because my computer at the moment don't have any harddrives because it's defective and I am waiting for the RMA process 'till next week - but I need my computer to work.) 

I know, I could get it to work because newer Ubuntu system has an option to "create USB startup disk", but the problem is that my computer doesn't natively support USB booting.

On another portable distros, there are some middle-man booting tools like "livecd fromusb" cheatcode on MCNLive and WakePup for Puppy Linux. Is there any similar tools for Ubuntu?

Thanks for your help.

---

### Post by SteveDee on 2009-10-09
Just in case you haven't already fully investigate your BIOS, on a couple of my many computers, USB memory stick booting is not supported by any of the USB-xxx options.

But it does appear in the hard disk list (e.g. on Phoenix AwardBIOS select "Advanced BIOS Feature" > "Boot Sequence" > "Hard Disk Boot Priority") and can be selected from here.

---

### Post by Brian88 on 2009-10-09
> **SteveDee said:**
> Just in case you haven't already fully investigate your BIOS, on a couple of my many computers, USB memory stick booting is not supported by any of the USB-xxx options.

But it does appear in the hard disk list (e.g. on Phoenix AwardBIOS select "Advanced BIOS Feature" > "Boot Sequence" > "Hard Disk Boot Priority") and can be selected from here.

It doesn't show up.
My motherboard is ASUS P4S333.
The boot configuration looks like this: [http://www.fixya.com/brands/manuals/A/ASUS/p4s333_p4s33_f9ca78514f1b509bc8a1d69f63100dfe/images/4559EC18B356593909841D9D636C2362.jpeg](http://www.fixya.com/brands/manuals/A/ASUS/p4s333_p4s33_f9ca78514f1b509bc8a1d69f63100dfe/images/4559EC18B356593909841D9D636C2362.jpeg)

The USB disk doesn't show up on the IDE hard drive or Removable Device options. On the removable device options there are USB-ZIP, but it does not work.

---

### Post by Mighty_Joe on 2009-10-09
[How To Make A USB Boot CD for Ubuntu]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")

---

### Post by kurocan on 2009-10-09
> **Mighty_Joe said:**
> [How To Make A USB Boot CD for Ubuntu]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")
cek TKp dulu :P

---

### Post by Brian88 on 2009-11-16
Thanks for all your help. It's now solved.
But regarding to the Ubuntu-on-disk I have an issue :

[http://ubuntuforums.org/showthread.php?t=1328189](http://ubuntuforums.org/showthread.php?t=1328189)

Thanks for all your help.

---

### Post by abrazafi on 2009-12-23
Hi All,

I tried to install kubuntu 9.10 on 16 Mb USB stick. After installation, the system is very slow, I guess doing a lot of swap's... 
Would the USB, stick version 2.0, prevent this slow response? 
Meants, will be faster, etc.

Thanks,
Abdon.

---

### Post by Brian88 on 2009-12-23
> **abrazafi said:**
> Hi All,

I tried to install kubuntu 9.10 on 16 Mb USB stick. After installation, the system is very slow, I guess doing a lot of swap's... 
Would the USB, stick version 2.0, prevent this slow response? 
Meants, will be faster, etc.

Thanks,
Abdon.

Do you mean an 16GB flashdisk?
Is it regular install or an USB boot disk?

Yes, USB 2.0 will drastically improve the performance, as the speed is much different (12 Mbit/sec vs 480 Mbit/sec).

But, if you're using USB 2.0 disk on a computer with only USB 1.1, the speed will not increase as the speed used is the 12Mbit/sec one.

---

### Post by SteveDee on 2009-12-24
USB 1.1 and USB 2.0 are interface standards, but the max transfer rates quoted for these standards are NOT the transfer speeds for your USB memory stick. There are other limitations which make these devices slower than expected and a USB stick will always be much slower writing data than reading it.

This means that you will not achieve the 480Mbit/s (60MByte/s) transfer speed of USB 2.0.

Its best to consult the manufacturers data sheet, although while these are readily available from companies like SanDisk, you won't find transfer speeds for a lot of the cheaper brands.

---

### Post by abrazafi on 2009-12-29
Thanks Steve and Brian ...
Yes, this is a normal install and it is flash memory.

I switched to the USB 2.0 and not too much difference.
Still a lot of waiting at the begening.

I run the TOP:

top - 21:13:54 up 18 min,  2 users,  load average: 0.05, 0.32, 0.33
Tasks: 148 total,   1 running, 147 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.2%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2061168k total,   704928k used,  1356240k free,    34660k buffers
Swap:   706820k total,        0k used,   706820k free,   334228k cached

disk usage is:
>df -k .
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             14848280   4337516   9756516  31% /

>uname -a
Linux antec 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

---

