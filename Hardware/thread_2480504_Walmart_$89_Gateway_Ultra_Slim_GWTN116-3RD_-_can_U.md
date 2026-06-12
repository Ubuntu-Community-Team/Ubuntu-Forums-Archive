---
title: "Walmart $89 Gateway Ultra Slim GWTN116-3RD - can Ubuntu be loaded easily?"
date: 2022-11-01
forum: Hardware
---

### Post by John Nagle on 2022-11-01
Walmart is currently offering a very low cost x86 PC: a ["Gateway Ultra Slim"]("https://www.walmart.com/ip/Gateway-11-6-Ultra-Slim-Notebook-HD-Intel-Celeron-Dual-Core-64GB-Storage-4GB-RAM-Mini-HDMI-1-0MP-Webcam-Windows-10-S-Microsoft-365-Personal-1-Year-In/589018777"), for US$89. Model GWTN116-3RD. If Ubuntu can be loaded on that, it would be a nice option for when you need a really small machine. Not finding any references to it on this forum.

Someone tried and [commented on Reddit]("https://www.reddit.com/r/GatewayUSA/comments/txokch/gwtc1162_installing_linux_mint_and_ubuntu_almost/"):

[I]I  bought GWTN116-3 which is the 3rd generation at Walmart online for $80.  The problem is similar which is no wifi or sound. I couldn't get the  sound to work as the driver is missing. The tricky part is that `lspci`  does not show any Ethernet controller. `lsusb` returns Realtek  Semiconductor Corp. 802.11n WLAN Adapter without model number. You can  get the model number from Windows 10. I followed the discussions at [https://www.reddit.com/r/linuxmasterrace/comments/r51hh7/comment/hmxm4np/](https://www.reddit.com/r/linuxmasterrace/comments/r51hh7/comment/hmxm4np/) to figure out the steps to install the realtek rtl8723du driver from github at [https://github.com/lwfinger/rtl8723du/tree/v5.13.4](https://github.com/lwfinger/rtl8723du/tree/v5.13.4)  which has the README instructions; long story short. The commands to  get wifi on Ubuntu 22.04 are: 1. hil@hil-gateway:~$ sudo apt-get update  && sudo apt-get install make gcc linux-headers-$(uname -r)  build-essential git # install build tools for compiling the driver  kernel module. 2. wget [https://github.com/lwfinger/rtl8723du/archive/refs/heads/v5.13.4.zip](https://github.com/lwfinger/rtl8723du/archive/refs/heads/v5.13.4.zip)  # the git clone command timed out. Downloading the zip as the  alternative. 3. unzip v5.13.4.zip && rtl8723du-5.13.4/  && make # start building the kernel driver module. 4. sudo make  install && sudo modprobe -v 8723du # install and load the kernel  driver module. You should have wifi available on the Ubuntu 22.04.1  LTS. Rebooting still has Wifi. Command output is at [URL="https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb"]https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb

[/URL][/I][URL="https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb"]
[/URL]So apparently it can be made to work. Full support for something that cheap would be useful.

---

### Post by TheFu on 2022-11-01
> **John Nagle said:**
>  So apparently it can be made to work. Full support for something that cheap would be useful.

Driver support is something that the vendor is responsible.  With every OS, it has always been the responsibility of the purchaser to ensure the hardware and software meets their needs.  In short, contact the company behind Gateway laptops (this year) and let them know what you want.

I wouldn't hold my breath.  If you like, you could create a custom distro, based on Ubuntu, just for this hardware.  Then you could include the exact drivers needed in the ISO yourself.  For a guide on how to accomplish this:  [https://www.linuxfromscratch.org/lfs/](https://www.linuxfromscratch.org/lfs/)
[https://wiki.ubuntu.com/DerivativeDistroHowto](https://wiki.ubuntu.com/DerivativeDistroHowto) is another guide.  A level 2 distro shouldn't be THAT hard, though I've never done it. Of course, this would imply that there are drivers for all the hardware.  This could become a nice little business.  Sorta like what Mr. Chromebox does for ChromeOS-based hardware.

If the wifi driver is available already, that's most of the issue, assuming all the other hardware is working.  Eventually, the driver will get included in a Linux Kernel update and that driver will automatically get installed.  That's the nature of new hardware and why we recommend avoiding bleeding edge hardware, waiting 12-18 months for the hardware to become supported by Linux.

---

### Post by VMC on 2022-11-01
Thank You for bringing this item to my attention!
 I just now bought the i3 version for $149. It has full HDMI port instead of mini HDMI:
[https://www.walmart.com/ip/Gateway-15-6-Ultra-Slim-Notebook-with-Carrying-Case-Wireless-Mouse-FHD-Intel-Core-i3-1115G4-Dual-Core-4GB-Memory-128GB-SSD-Windows-11-S/580892989](https://www.walmart.com/ip/Gateway-15-6-Ultra-Slim-Notebook-with-Carrying-Case-Wireless-Mouse-FHD-Intel-Core-i3-1115G4-Dual-Core-4GB-Memory-128GB-SSD-Windows-11-S/580892989)

---

### Post by mIk3_08 on 2022-11-02
> **John Nagle said:**
> 
*I  bought GWTN116-3 which is the 3rd generation at Walmart online for $80.  The problem is similar which is no wifi or sound. I couldn't get the  sound to work as the driver is missing. The tricky part is that `lspci`  does not show any Ethernet controller. `lsusb` returns Realtek  Semiconductor Corp. 802.11n WLAN Adapter without model number. You can  get the model number from Windows 10. * Have you tried to run the "Try Ubuntu" before installing the full Linux Ubuntu Operating System for the purpose of testing the hardware. This is cool laptop though. Regards and cheers.

---

### Post by VMC on 2022-11-02
Yes, 'Try Ubuntu', if that works, then from terminal ID hardware. Maybe look into BIOS. <F2> when booting. I'll know more when I get mine on Friday.

---

### Post by VMC on 2022-11-02
> **John Nagle said:**
> ...

[I]I  bought GWTN116-3 which is the 3rd generation at Walmart online for $80.  The problem is similar which is no wifi or sound. I couldn't get the  sound to work as the driver is missing. The tricky part is that `lspci`  does not show any Ethernet controller. `lsusb` returns Realtek  Semiconductor Corp. 802.11n WLAN Adapter without model number. You can  get the model number from Windows 10. I followed the discussions at [https://www.reddit.com/r/linuxmasterrace/comments/r51hh7/comment/hmxm4np/](https://www.reddit.com/r/linuxmasterrace/comments/r51hh7/comment/hmxm4np/) to figure out the steps to install the realtek rtl8723du driver from github at [https://github.com/lwfinger/rtl8723du/tree/v5.13.4](https://github.com/lwfinger/rtl8723du/tree/v5.13.4)  which has the README instructions; long story short. The commands to  get wifi on Ubuntu 22.04 are: 1. hil@hil-gateway:~$ sudo apt-get update  && sudo apt-get install make gcc linux-headers-$(uname -r)  build-essential git # install build tools for compiling the driver  kernel module. 2. wget [https://github.com/lwfinger/rtl8723du/archive/refs/heads/v5.13.4.zip](https://github.com/lwfinger/rtl8723du/archive/refs/heads/v5.13.4.zip)  # the git clone command timed out. Downloading the zip as the  alternative. 3. unzip v5.13.4.zip && rtl8723du-5.13.4/  && make # start building the kernel driver module. 4. sudo make  install && sudo modprobe -v 8723du # install and load the kernel  driver module. You should have wifi available on the Ubuntu 22.04.1  LTS. Rebooting still has Wifi. Command output is at [URL="https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb"]https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb
[/URL][/I][URL="https://gist.github.com/hilliao/ce62ae6870d0f8511fa73803a4d841eb"]
[/URL]So apparently it can be made to work. Full support for something that cheap would be useful.

Yes those gethub instructions are needed for each new kernel. This is not the only new laptop with that Realtek wifi/wlan issue. I had a Lenova with the same Realtek, but didn't won't to bother with the github info at the time. This Gateway is so cheap its worth the effort.

---

### Post by mIk3_08 on 2022-11-02
> **VMC said:**
> I'll know more when I get mine on Friday. Wow! cool. Good Luck. Actually, you can do it. Its just that, their are hardware/software system configurations that are not so friendly here in Linux. I mean its not that kind of easy job to the newbie but for elite like you it will be not that kind a complicated situation. You can handle it easily. Regards and cheers.

---

### Post by TheFu on 2022-11-02
> **mIk3_08 said:**
> Wow! cool. Good Luck. Actually, you can do it. Its just that, their are hardware/software system configurations that are not so friendly here in Linux. I mean its not that kind of easy job to the newbie but for elite like you it will be not that kind a complicated situation. You can handle it easily. Regards and cheers.

Flexibility has a price. Complexity.  OTOH, if 80% of the world used Linux, we'd have Linux preinstalled with all the drivers fully tested by the vendors and life would be different.

I think Gateway laptops are owned by Acer these days, so I'd expect the lowest end quality of an Acer laptop and perhaps some BIOS settings that are commonly not available, like AMD-v/VT-x to be completely inaccessible, so even if the CPU can support some great things, the BIOS may prevent it.
[https://arstechnica.com/gadgets/2020/09/we-found-out-who-makes-walmarts-new-gateway-laptops-and-its-bad-news/](https://arstechnica.com/gadgets/2020/09/we-found-out-who-makes-walmarts-new-gateway-laptops-and-its-bad-news/) says that EVOO are the sub-sub manufactures.
> More accurately, EVOO imports devices made by Shenzhen Bmorn Technology, a Chinese national brand.
Be careful out there.

---

### Post by mIk3_08 on 2022-11-03
> **TheFu said:**
> 
[https://arstechnica.com/gadgets/2020/09/we-found-out-who-makes-walmarts-new-gateway-laptops-and-its-bad-news/](https://arstechnica.com/gadgets/2020/09/we-found-out-who-makes-walmarts-new-gateway-laptops-and-its-bad-news/) says that EVOO are the sub-sub manufactures.

Thanks a lot TheFu for the info. Its not quite a good news but sad to say its a bad one. :-( Again Thanks a lot. Regards and cheers

---

### Post by TheFu on 2022-11-03
> **mIk3_08 said:**
> Thanks a lot TheFu for the info. Its not quite a good news but sad to say its a bad one. :-( Again Thanks a lot. Regards and cheers

The comments in that link are telling.  The fact that the company send a Pentium when a Ryzen 5 module had been ordered says much about the poor logistics of the time.  The return policies are next to impossible to meet as well. I'd be certain to buy this INSIDE a Walmart, not via mail, to ensure Walmart returns would work as expected.  OTOH, it's just under $100, so what do we expect?

2 guys in my LUG bought a Gateway laptop deal over the summer through Walmart.  Both just because it was really cheap - sorta like how we all bought our first raspberry Pi computers years ago ---- because they were cheap.  1 of those orders wouldn't boot Linux at all. He returned it.  The other had wifi issues and he missed the return window trying to get it working.  It is a boat anchor now, until a Linux kernel with the driver support happens.

I like really cheap computers, provided some usefulness can happen.  I think I'll be buying refurbished Dell laptops in the $200-250 price range going forward every 3-7 yrs.  New, those are normally $850+ laptops, but after 3 yrs, the price drops drastically, especially for corporate leased equipment.  Plus, it will be the Latitude, not the consumer Inspiron line. Latitude is made just a little better and holds up well, IME.  Dell keyboards have been the only ones that can take my typing more than 2 yrs.  Acer, Asus, Toshiba keyboards have all had 10+ failed keys in that time.  I'm used to mechanical keyboards with that special "feel".  I'm not beating on the keys, but they need to have feedback so I know they are hit.  Lacking feedback, hitting the bottom will happen every time.

---

### Post by VMC on 2022-11-03
Just received my gateway i3-1115G4. I was just going to return it from what I knew about the wifi that was mentioned on the first post.

To my amazement, everything worked. Wifi detected and worked on Windows, and Ubuntu.
On the installed Windows I knew it would work, but trying and update to Windows 11, it to worked.

From the first post, I was remembering Lenova laptop that nothing worked except the installed Windows.

Here's what I get on my gateway:```
$ lspci -nnk | grep 0280 -A2
00:14.3 Network controller [0280]: Intel Corporation Wi-Fi 6 AX201 [8086:a0f0] (rev 20)
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Wi-Fi 6 AX201 [8086:0264]
```

---

### Post by TheFu on 2022-11-03
> **VMC said:**
> Just received my gateway i3-1115G4. I was just going to return it from what I knew about the wifi that was mentioned on the first post.

To my amazement, everything worked. Wifi detected and worked on Windows, and Ubuntu. 

Which release and kernel?

---

### Post by VMC on 2022-11-03
Current release Ubuntu 22.10, 5.19.0-23-generic

---

