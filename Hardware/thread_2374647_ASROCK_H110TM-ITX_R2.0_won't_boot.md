---
title: "ASROCK H110TM-ITX R2.0 won't boot"
date: 2017-10-17
forum: Hardware
---

### Post by michaelvv on 2017-10-17
I Have this Motherboard with an Intel Kaby Lake i5-7600T CPU.

When I try to boot Linux from (ubuntu 17.10 , ubuntu 17.04 , Arch Linux) it just
Shows the bootloader, and starts to boot and after 2-3 secs it just reboot.

I have a sufficient PSU and Memory (Mem tested for 3 hours), so I suspect there are some compatible problems.

I can't get a newer BIOS ( have the newest one ) is it 1 year old, and I have wrote the same on the ASROCK forum.

I have added noacpi , intel_idle.max_cstate=2 nothing works.

Secure Boot - Off
CMS enabled
CSM sub-option Launch Storage OpROM Policy to UEFI Only

Even a fresh linux 4.13.x installed on SSD doesn't boot.

Thanks Michael.

---

### Post by oldfred on 2017-10-17
Have not seen posts on newer Asrock.
But UEFI is often very similar as just an update for Intel chips.

 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode) 

Even newer Asrock. Need i915.alpha_support=1, not sure if yours does or not?
[https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1](https://www.phoronix.com/scan.php?page=article&item=asrock-z370m-itx&num=1)

---

### Post by michaelvv on 2017-10-18
Okay a little progress.

What I did.

Clear the BIOS CMOS, to get to a state off here we are.

<b>BIOS</b>
Secure Boot - Off
CMS enabled
CSM sub-option Launch Storage OpROM Policy to UEFI Only
disabled speedstep , and turbo

<b>Kernel boot</b>
i915.alpha_support=1

I can Install the kubuntu 17.10 BETA on my SSD, works fine.

But when I try to login, still using <b>i915.alpha_support=1</b> The system crashes.

Will try to install the Ubuntu Server right now.

Thanks Oldfred for your tips.

Little update. My Ubuntu 17.04 server "kickstart" image runs fine.

I have a complicated "DAC" so I can comfirm USB 2.0/3.0 is as on my newer laptop.
When I play music it uses quite a lot of IRQs.

Power consumption is very very nice. Playing music throught USB and running LMS server (SMB) uses 17 watt.

The most during the installation and compiling is 30 Watt so far.

System is Intel i5-7600T , 8 Gb RAM , and older Samsumg 128 GB SSD disk.

Running a home build Linux Realtime Kernel 4.11.12-rt9 (the Newest) works fine. 

Did not run any insane Compiling yet, so what max it, I really don't know.

---

