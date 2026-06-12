---
title: "Ubuntu support for HP250G5 not listed - could I use HP240G4?"
date: 2017-05-29
forum: Hardware
---

### Post by 2dogs2 on 2017-05-29
I have recently purchased a Windows10 HP250G5 notebook laptop and want to install ubuntu. Firstly I checked the official ubuntu support site ([https://certification.ubuntu.com/certification/make/HP/](https://certification.ubuntu.com/certification/make/HP/)) and noticed that if I restricted the support level to 16.04LTS there was no HP support. A search for 14.04LTS came up with the list below which didn't include the HP250 series. Anything between 240 and 340 was for the AMD chipset and not Intel.

So I chose the closest with Intel processor ie 240G4.

Looking up the HP specs for both the 240G4 and 250G5 at the HP sites showed (listed below) similarities between the two. (also listed below)

Has anybody else has travelled this path and come to the same conclusions or have I made errors of judgement? And could it be that the ubuntu list of certified support for HP is out of date?

(first post on this site - please excuse any protocol errors)


--------------------- Reference -------------------------

PC Details:
===========
System Model. . . . . . . . .         HP 250 G5 Notebook PC 
System Type . . . . . . . . . x64-based PC 
Processor . . . . . . . . . . .               Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz, 1601 Mhz, 2 Core(s), 2 Logical Processor(s) 
BIOS Version/Date . . . . .   Insyde F.24, 20/01/2017 
SMBIOS Version . . . . . . .      2.8 
BIOS Mode . . . . . . . . . .            UEFI 


Ubuntu list of certified HP support:
====================================
HP 240 G4 Notebook PC Laptop . . . . . . . . . Pre-installed by manufacturer Intel Realtek Semiconductor Co., Ltd. Intel
HP 241 G1 Laptop . . . . . . . . . . . . . . . . . . Pre-installed by manufacturer AMD processor Realtek Semiconductor Co., Ltd
HP 245 G2 Laptop . . . . . . . . . . . . . . . . . .                        Available from ubuntu.com AMD processor Realtek Semiconductor Co., Ltd.
HP 245 G4 Notebook PC Laptop . . . . . . . . .      Pre-installed by manufacturer AMD processor Realtek Semiconductor Co., Ltd.
HP 255 G2 Laptop . . . . . . . . . . . . . . . . . .                        Available from ubuntu.com AMD processor Realtek Semiconductor Co., Ltd.
HP 340 G2 Notebook PC Laptop . . . . . . . . .      Pre-installed by manufacturer Intel Realtek Semiconductor Co., Ltd. Intel 


Sites
=====
[https://support.hp.com/us-en/product/hp-240-g4-notebook-pc/7609932/document/c04616132](https://support.hp.com/us-en/product/hp-240-g4-notebook-pc/7609932/document/c04616132)
[https://support.hp.com/us-en/product/hp-250-g5-notebook-pc/10180321/document/c05078579](https://support.hp.com/us-en/product/hp-250-g5-notebook-pc/10180321/document/c05078579)


Specs
=====

HP240G4:
.                    . . . . .Processors . . . . . . . . . . . . . . . . . . . . . . . . . . . .                                                         Graphics
Intel Core i5-5200U with Intel HD . . . . . . Graphics 5500        Intel HD Graphics 5500 (Integrated) 
Intel Core i3-5010U with Intel HD . . . . . . Graphics 5500        Intel HD Graphics 4400 (Integrated) 
Intel Core i3-4005U with Intel HD . . . . . . Graphics 4400        Intel HD Graphics (Integrated) 
Intel Pentium N3700 . . . . . . . . . . . . . . . AMD Radeon R5 M330 (2 GB DDR3 dedicated, switchable)* (discrete) 
Intel Celeron N3050 
   

HP250G5:
                   .                    . . . . .Processors . . . . . . . . . . . . . . . . .  . . . . . . . . . . .                                                          Graphics
Intel Core i7-6500U with Intel HD Graphics . . . . . 520          Intel HD 520 (Integrated) 
Intel Core i5-6200U with Intel HD Graphics 520 . . Intel HD Graphics 5500 (Integrated) 
Intel Core i3-5005U with Intel HD Graphics 5500 . Intel HD Graphics 405 (Integrated) 
Intel Pentium N3710 with Intel HD Graphics 405 . .Intel HD Graphics 400 (Integrated) 
Intel Celeron N3060 with Intel HD Graphics 400 . .         AMD Radeon R5 (up to 2 GB of dedicated video memory) (discrete) 
                                                                         . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .Support HD Decode, DX12, and HDMI

---

### Post by efflandt on 2017-06-01
Not quite sure what support you would be looking for. I added 64-bit 16.04 on a low end HP Win10 laptop with slow Pentium CPU that as near as I can tell is model 15-ac147ds. Basically it would be best to use Win10's own "Disk Management" to shrink its OS partition and install Ubuntu to the unallocated space. But I never know exactly what Ubuntu is going to do automatically, so I use "Other" for partitioning instead of something automatic. But I imagine a 2-core Celeron will be even slower than a 4-core Pentium, so I would not expect it to play games. Even with RAM bumped up from 4 GB to 8 GB, minecraft is unplayable in Linux (1-5 fps). Although it works fine for on-line things including streaming video. I bought the laptop to set up for someone who decided they did not have the money to pay me for it right now, so I primarily use it for WebEx in Win10 (which I can HDMI output to my 32" HDTV if not doing something else on my desktop PC).

Grub boot loader may not come up automatically after installation, so you may need to press the UEFI hotkey during boot to select "ubuntu".

---

### Post by Bucky Ball on 2017-06-01
> **efflandt said:**
> Basically it would be best to use Win10's own "Disk Management" to shrink its OS partition and install Ubuntu to the unallocated space.

Welcome. Not only would it be best, it is essential you use Windows software to shrink the Win OS partition and NOT Linux software (Gparted for instance). This is not an either/or. Use Win software to resize Win OS partitions, Linux software for resizing Linux partitions (EXT). Resizing a Win OS partition with Linux software has a good chance of totally screwing your Windows boot. 

For a dinky little thing like that machine I wouldn't be bothering with Ubuntu at all, but would be going for one of the lighter flavours. Xubuntu would fly on that (and Lubuntu with even greater speed and altitude!). Ubuntu is going to be a little sluggish and you're using a lot of resources before you even start opening apps. 

Depending on your level of expertise, a -core or minimal install would work best as you would only install what you want/need. Very light. If you want any further info on that, just ask.

---

### Post by johndough2 on 2017-06-01
Hi

GParted will not normally touch my W10 partitions because the option for "Fast Startup" in Power options; System settings.

The 'disk' is put into a suspend mode, despite the words shut down being used when you exit windows.  There is no clean shutdown and not everything seems to get written to disk.

Once the fast startup option is unchecked a clean shutdown is achieved.  Now I would resize.

---

### Post by Bucky Ball on 2017-06-01
As above. You also need to boot into Win and switch off hibernation, depending on the Win version, as otherwise Win 'claims' the disk and nothing else can access it when Windows is 'off' (it's actually just 'sleeping'). Neat, huh? Not. :|

Same with Faststart, as stated by johndough2 above. I think the probs with Ubuntu and secure boot have also been rectified, but you'll need to check that or switch off.

---

### Post by Vic_Paine on 2017-06-03
The only reliable way to shut windows down (turning off fast boot didn't work for me) is in a command prompt with ```
Shutdown /s /t 0
``` coutesy of kagashe here ```
[https://ubuntuforums.org/showthread.php?t=2362087](https://ubuntuforums.org/showthread.php?t=2362087)
```  
This has the advantage that shutdown is almost instant.  Although booting is slower the overall shutdown/start time pretty much the same as the win default.

---

### Post by gordintoronto on 2017-06-03
Don't sweat the certification site, which is always out of date. Because your laptop was introduced several months after the latest LTS version was released, I would download Ubuntu Mate 17.04 and use Pendrive Linux to create a bootable flash drive. Then try it!

Note: if you use 17.04, you will need to upgrade to 17.10 within a couple of months of its release, then to 18.04 (another Long-Term Support release) within a couple of months of its release. Then you can get off the treadmill.

Generally, HP laptops are very Linux-friendly, with Wi-Fi support being the only question mark.

There's a lot of good advice about making space for Linux in the above messages.

New hardware, old OS, bad combo.

---

