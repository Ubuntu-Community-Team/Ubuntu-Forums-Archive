---
title: "Can't adjust display backilght on Acer Aspire One 725-0884"
date: 2013-01-03
forum: Hardware
---

### Post by jweber53 on 2013-01-03
There are similar threads but I think this model has significantly different cpu and graphics processor from earlier models. It has c-70 cpu (not c-60) and the graphics processor is "nee ATI Device 980a". I've tried other solutions posted, but none work.

I can use the Fn arrow keys and see the the brightness slider operating. Furthermore the values in the files in /sys/class/backlight/acpi_video0/ change in the the range 1-10 to reflect the changes, but the screen stays max bright.

```
root@nardis:/sys/class/backlight/acpi_video0# cat actual_brightness brightness max_brightness 
6
6
10

```

I've tried installing the AMD fglrx and fglrx-udate drivers downloaded from AMD and manual install. They go through the install routine but fail just before completion with an error pop-up saying the hardware is not supported.

When I try to use the additional drivers tab from software sources to use the fglrx drivers, it never completes and when I reboot the system it has no graphics and only a text prompt. I did not try to uninstall and just reinstalled the OS (12.10).

Ubuntu 12.04 will boot the USB media and give me the first text screen, but after that the screen is blank with a minute or two of USB activity. I suspect the video is not supported.

I tried Fedora 18 Beta live to see if the 3.6 kernel might be different, but same results as Ubuntu 12.10.

I suspect maybe I have to wait until AMD comes out with a driver(?). This is not a production system and I have time to test and report as necessary.

Here are some informational outputs:
```

root@nardis:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 980a
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
root@nardis:~#  lspci -v -s 00:01.0
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 980a (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0740
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=256]
	Memory at 90200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: radeon
	Kernel modules: radeon

root@nardis:~#  cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 20
model		: 2
model name	: AMD C-70 APU with Radeon(tm) HD Graphics
stepping	: 0
microcode	: 0x500010d
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips	: 1996.49
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

<snip>

```

---

### Post by Kanakiri on 2013-01-20
Hi, I've been having the same problem with this model. I have found several possible solutions for other Acer laptops/netbooks but none of them worked. Has there been any other solutions? Thanks.

---

### Post by angeline2 on 2013-01-20
As "temporaly solution" you can type:
xrandr --output LVDS --brightness 0.n      (n= 3 to 9)

---

### Post by jweber53 on 2013-01-20
> **angeline2 said:**
> As "temporaly solution" you can type:
xrandr --output LVDS --brightness 0.n      (n= 3 to 9)

This solution saves the eyes, but doesn't help prolong the battery life. Another similar solution that I've been using is xcalib. I use 

```
xcalib -gc 1.2 -co 80 -a
```

as a keyboard shortcut to dim in increments with each application and then

```
xcalib -c
```

as another keyboard shortcut to clear the setting and restore full brightness. Again this only looks like dimming. The backlight is still sucking up the juice. On a full battery, I get a projected battery life of about 3.5 hours and the time estimate drops much more quickly than real time. When I had Windows8 running on this and the display somewhat dimmed, it reported 4.5-5 hrs life.

At least these solutions allow you to use the laptop in dim light public places and not blind everyone around you :)

Thankyou angeline2, I've been meaning to post this workaround, but have been hoping for the real fix.

---

### Post by Kanakiri on 2013-01-22
Thanks for the solutions but I'm really looking for something that lets me adjust the backlight itself. The brightness itself doesn't really bother me, but I'm only getting maybe 1.5 hours of battery life with it at 100% at all times. A bit annoying considering I bought it because my three-year old Dell laptop's battery was shot and buying a new one wasn't worth it.

Guess I'll pay attention for some kind of driver update or something similar.

---

### Post by jweber53 on 2013-01-23
I filed a Linux tech driver request at the AMD website for this, referring to this post. I'll post any further results.

---

### Post by RagingAvatar on 2013-02-03
I too am having this issue, I'm running x64 12.10 Ubuntu.
Let me know if they get back to you please!

---

### Post by jheise0967 on 2013-02-19
Hi all,

i have the same problem with my netbook.

Using an ACER Aspire ONE 725 with C-70 and HD7290 with 12.04LTS 32Bit.

The Ubuntu12.04 driver working ok on 3D mode but only with external powersupply.
Also the  display brightness can be set with Fn-keys or in the software settings panel.

In battery mode the screensaver or powerdown works not ok...
(working only if the brightness set below 20%.)

The UBUNTU proprietary driver has the "unsupported hardware" watermark which can not be removed.  I tried to remove the watermark but the X-server never starts correctly.

I tried also to install the new Beta Driver from AMD (18Feb2013) also not working with HD7290. 

Maybe there is any way to implement the correct functionality for the HD7290.

Tested before the ACER722 with HD6290 and all is working perfectly.

Best regards

---

### Post by jheise0967 on 2013-02-20
Hi all, 

installed Ubuntu 12.04.02 64Bit yesterday....

Same problem 

Regards

---

### Post by nicbaird on 2013-03-02
Hi everyone!

I also have not been able to find a working video card driver solution for this latest line of Acer Aspire One models.

Mine is the AspireOne725-0826 with the C70 processor, and the 'nee ATI Device 980a' graphics card. I'm running the latest 64 bit Ubuntu and think it's a good fit, besides the lack of driver support for the video card.

I've tried solutions for similar models that suggested drivers that would most likely cover mine, but they have not worked/finished installing before detecting  the incompatibility.

I've not very good at Ubuntu, but I've always been able to find solutions for any of my problems on these forums, but it's been a couple days and I'm stumped.

I imagine someone in this most excellent community will point to a solution in not too long, but I'm just adding my voice to yours.

--Nic

---

### Post by raring on 2013-03-09
Hi, 

I'm using a brand new Acer Aspire One 725 (C7xkk) and the brightness controls via FN keys work like a dream in Raring Ringtail (13.04) due out in about four weeks.
Just thought you'd like to know !

---

### Post by raring on 2013-03-09
> **nicbaird said:**
> Hi everyone!

I also have not been able to find a working video card driver solution for this latest line of Acer Aspire One models.

Mine is the AspireOne725-0826 with the C70 processor, and the 'nee ATI Device 980a' graphics card. I'm running the latest 64 bit Ubuntu and think it's a good fit, besides the lack of driver support for the video card.

I've tried solutions for similar models that suggested drivers that would most likely cover mine, but they have not worked/finished installing before detecting  the incompatibility.

I've not very good at Ubuntu, but I've always been able to find solutions for any of my problems on these forums, but it's been a couple days and I'm stumped.

I imagine someone in this most excellent community will point to a solution in not too long, but I'm just adding my voice to yours.

--Nic

Yes I have same specs, I tried Steam on this laptop (via windows) and Team Fortress 2 was quite playable though when I tried it via Ubuntu it was un-playable thus AMD's driver support for their graphics cards is attrocious. Hopefully it'll improve, I miss TF2 via steam on my linux system.

---

### Post by angeline2 on 2013-03-09
Hi thank!
But what ablout secure boot with 13.04 ?

---

### Post by raring on 2013-03-10
> **angeline2 said:**
> Hi thank!
But what ablout secure boot with 13.04 ?

I just installed via usb key like normal.

p.s. Windows 8 is a complete mess, how did it past M$ quality control I'll never know.

---

### Post by black veils on 2013-03-10
it may seem silly but did you lot restart the computer after using the Fn keys to adjust it ?  my acer computer only changes brightness if i restart, so maybe thats all you need to do.

---

### Post by jweber53 on 2013-03-10
> **raring said:**
> Hi, 

I'm using a brand new Acer Aspire One 725 (C7xkk) and the brightness controls via FN keys work like a dream in Raring Ringtail (13.04) due out in about four weeks.
Just thought you'd like to know !

I'm not sure what the number "C7xkk" represents (?). I'm curious to know the graphics and other hardware on your Acer. Please post the output of these commands:

```
lspci -nn
cat /proc/cpuinfo
```

Thanks

---

### Post by raring on 2013-03-11
```
tux@akira:~$ lspci -nn ; cat /proc/cpuinfo
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 14h Processor Root Complex [1022:1510]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:980a]
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] [1002:1314]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1512]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 14h Processor Root Port [1022:1513]
00:10.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB XHCI Controller [1022:7812] (rev 03)
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7801]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 14)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 2
model name    : AMD C-70 APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x500010d
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 1996.22
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 2
model name    : AMD C-70 APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x500010d
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat cpb hw_pstate npt lbrv svm_lock nrip_save pausefilter
bogomips    : 1996.22
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate cpb


```

Please note that the original nplify wifi card 'Broadcom' and bluetooth module created awful problems and started fighting with other Atheros cards on my network.. so I switched it out for an Atheros chipset.

---

### Post by angeline2 on 2013-03-11
it's not the same computer !

---

### Post by raring on 2013-03-11
> **angeline2 said:**
> it's not the same computer !

My brightness controls don't work in 12.10 either, try 13.04 off a live usb key to test it.

I'm sure it'll work for you as well.

---

### Post by angeline2 on 2013-03-11
Due to a very slow network, I can't download right now 13.04, will see later sorry. Thanks

---

### Post by jweber53 on 2013-03-11
Thanks for posting your specs. It appears to be the same as mine except for the wireless which I also changed out from a broadcom 4313 to a broadcom 4312 (very poor performance). I will test 13.04 and post the results.

---

### Post by jweber53 on 2013-03-11
I verify that 13.04 (build from 20130311) running from a live USB does fix the backlight dimming problem on my system. Now we'll have to see if it still works when doing an upgrade from 12.10, once 13.04 is released.

---

### Post by jweber53 on 2013-03-22
I just upgraded to the latest kernel and other updates to my 12.10 system using software updater and the problem appears to be fixed!


```

jweber@nardis:~$ uname -a
Linux nardis 3.5.0-27-generic #45-Ubuntu SMP Tue Mar 19 23:38:37 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
jweber@nardis:~$
```

---

### Post by angeline2 on 2013-03-22
I have to be patient...
The last linux-signed-kernel-generic is 3.5.0.25.39
Whait & see...
RGDS

---

### Post by jweber53 on 2013-03-22
I think you might get 3.5.0-27-generic #45 if you enable quantal-proposed (as I have) in the software updater. Look at the info on  

 [https://launchpad.net/ubuntu/+source/linux-signed](https://launchpad.net/ubuntu/+source/linux-signed)

---

### Post by angeline2 on 2013-04-04
Bingo, the kernel 3.5.0.27 solved this problem.  To day !

---

### Post by Smallwheels on 2013-04-19
Thank you for this thread. I wanted to learn if this computer was compatible with Ubuntu. A review on Amazon said the graphics didn't work well. Though this thread didn't actually say it had poor graphics or good graphics, the absence of comments about it gave me confidence to buy one. Knowing that one problem with the brightness has been sorted out with 13.04 is good news. 

I hope the other features like Bluetooth and WiFi work well. Though Acer says it works only with a maximum of 4 GB RAM. I've seen an expert tech say on a video that this model will accept 8 GB and work even better. 

Seeking an Aspire One A0725-0600 soon. 


Smallwheels

---

### Post by jweber53 on 2013-04-19
I just ordered an 8GB upgrade based on what I read in various reports. We'll see!
Is there a better, more preferred thread for the ram and WiFi and other topics...like a general forum or thread for this particular laptop?

---

### Post by Smallwheels on 2013-04-19
Search for Acer 725 and you'll get tons of threads about this computer.

---

