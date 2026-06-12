---
title: "Looking for a Wireless chip that has Linux drivers"
date: 2022-07-04
forum: Hardware
---

### Post by xinelo on 2022-07-04
Dear all,

**# Background **

I have a semi-old desktop machine that I inherited from my company, where I would like to install Ubuntu. However, in the office it used to connect to the internet through an Ethernet cable and does not have a Wireless chip inside that sees WIFI networks. 

I have tried with a TP-Link Mini Wireless N USB Adapter (TL-WN823N) but I wasn't able to compile the drivers that TP-Link provides, their technical support replied that their drivers only support an older kernel than the one I am trying to use. 

If I'm not mistaken Ubuntu 22.04 uses Kernel 5.15, but the available driver for TL-WN823N v3 supports up to kernel 4.9.60.

I have failed to find other chip models that could have better support. The two IT re-sellers in my local area that I have contacted couldn't help either, they only get TP-Link products and one other brand that is not better.

**# Question**

That's what I've tried out. So my question in this forum now I suppose must be:

Could you recommend a chip model that has drivers for kernel 5.15 (that Ubuntu 22.04 uses)?

If not, do you have any other suggestion? 

**# Hardward info**

Here's some information about the machine:

> Machine manufacturer: LENOVO
Product name: 30C70009MB
Product version: ThinkStation P330
Processor manufacturer: Intel(R) Corporation
Processor version: Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
UDI: Intel(R) Core(TM) i7-8700 CPU @      3.20GHz - INTEL
Display Name: Intel(R) Core(TM) i7-8700 CPU @               3.20GHz - INTEL
Model: Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz
Vendor: INTEL
Number of cores: 6
Number of enabled cores: 6
Number of threads: 12
Signature: 906ea
Max speed: 4.600 GHz
Current speed: 3.192 GHz
Features: MMX, EM64T, SSE, SSE2, SSE3, SSSE3, 
          SSE4.1, SSE4.2, AES, AVX, AVX2, CLMUL, 
          FMA, PSE, PSE-36, IDA/Turbo boost, 
          HTT, XD, VMX
Cache L1: 6 x 32 KB Data, 6 x 32 KB Instruction
Cache L2: 6 x 256 KB Unified
Cache L3: 1 x 12 MB Unified

Please let me know whether there's any other piece of information that might be relevant. I have access to the machine on Windows 10 and the BIOS.

Thanks.
Manuel

---

### Post by Yellow Pasque on 2022-07-04
This may help:
[https://askubuntu.com/questions/1211157/how-do-i-get-a-tp-link-tl-wn823n-v3-wireless-adapter-working](https://askubuntu.com/questions/1211157/how-do-i-get-a-tp-link-tl-wn823n-v3-wireless-adapter-working)
[https://github.com/clnhub/rtl8192eu-linux](https://github.com/clnhub/rtl8192eu-linux)

---

### Post by kurt18947 on 2022-07-04
I'm not up to speed on newer USB wifi adapters. If you look thru the wireless and networking forum you should get a feel for what devices are plug & play and what is a challenge to get working. You could always look at thinkpenguin.com for networking devices known to work with minimal or no fussing. Something to be aware of with devices that plug into a laptop's internal M2 connectors - some companies whitelist network adapters. This means approved devices are burned into the laptop's BIOS. If a device is not listed in the BIOS it may plug in but it won't work. Lenovo Thinkpads are notorious for this. USB devices are not an issue AFAIK.

---

### Post by xinelo on 2022-07-05
Thank you, both. 

I hadn't seen there was a Networking and Wireless section in the forum, my question was perhaps more appropriate there.

Thanks for the various references, I'll see what I can find. 

Please notice that my machine is not a laptop, it's a desktop computer (Lenovo ThinkStation). 

I'm not necessarily looking for a USB device, I think I would prefer a network adapter that can be installed inside the box.

Cheers, Manuel

---

### Post by #&amp;thj^% on 2022-07-05
> **xinelo said:**
> I'm not necessarily looking for a USB device, I think I would prefer a network adapter that can be installed inside the box.

Cheers, Manuel

This one may be Overkill but it's a dandy. [https://www.lenovo.com/us/en/p/accessories-and-software/thinkcentre-and-thinkstation/thinkcentre-and-thinkstation-cables-and-adapters/4xc0t22654?orgRef=https%253A%252F%252Fwww.google.com%252F](https://www.lenovo.com/us/en/p/accessories-and-software/thinkcentre-and-thinkstation/thinkcentre-and-thinkstation-cables-and-adapters/4xc0t22654?orgRef=https%253A%252F%252Fwww.google.com%252F)
Another one I have worked with is this: [https://www.bhphotovideo.com/c/product/1465165-REG/asus_pce_ac58bt_wireless_ac1200_dual_band_pcie_wi_fi.html](https://www.bhphotovideo.com/c/product/1465165-REG/asus_pce_ac58bt_wireless_ac1200_dual_band_pcie_wi_fi.html)

---

### Post by SeijiSensei on 2022-07-05
> **xinelo said:**
> Please notice that my machine is not a laptop, it's a desktop computer (Lenovo ThinkStation). 

I'm not necessarily looking for a USB device, I think I would prefer a network adapter that can be installed inside the box.

Are you looking for a wired or wireless adapter? For a wired adapter, I'd use this:  [https://www.newegg.com/intel-expi9301ctblk/p/N82E16833106033](https://www.newegg.com/intel-expi9301ctblk/p/N82E16833106033)

Apparently this TP-Link AC1200 PCI adapter [https://www.newegg.com/tp-link-archer-t5e-usb-2-0/p/0E6-002W-005N2](https://www.newegg.com/tp-link-archer-t5e-usb-2-0/p/0E6-002W-005N2) uses the Intel 7265 chip ([https://superuser.com/questions/1701382/installing-tp-link-ac1200-t5e-pcie-adapter-on-debian-11](https://superuser.com/questions/1701382/installing-tp-link-ac1200-t5e-pcie-adapter-on-debian-11)). According to [https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/wireless.html), that chip is supported by the standard iwlwifi drivers that come with the Ubuntu kernel. I don't think you would need to follow that elaborate installation mechanism described in the Debian article. My guess is you'd install the device, and Linux would recognize it at a reboot.

If you're choosing wireless, how fast is your router? Are N speeds sufficient? If you have a USB port to spare, and you're within reasonable range of your router, I'd go with one of these: [https://www.amazon.com/wifi-adapter-usb-pc-network/dp/B008IFXQFU/](https://www.amazon.com/wifi-adapter-usb-pc-network/dp/B008IFXQFU/). You'll never notice it.

---

### Post by Yellow Pasque on 2022-07-05
> **xinelo said:**
> I hadn't seen there was a Networking and Wireless section in the forum, my question was perhaps more appropriate there.

No worries. It could fit in either forum.

Did you try to get the adapter you already have working with the links I gave you? What was the outcome?

---

### Post by mIk3_08 on 2022-07-06
> **xinelo said:**
> Dear all,

**# Background **

I have a semi-old desktop machine that I inherited from my company, where I would like to install Ubuntu. However, in the office it used to connect to the internet through an Ethernet cable and does not have a Wireless chip inside that sees WIFI networks. 

I have tried with a TP-Link Mini Wireless N USB Adapter (TL-WN823N) but I wasn't able to compile the drivers that TP-Link provides, their technical support replied that their drivers only support an older kernel than the one I am trying to use. 

If I'm not mistaken Ubuntu 22.04 uses Kernel 5.15, but the available driver for TL-WN823N v3 supports up to kernel 4.9.60.

I have failed to find other chip models that could have better support. The two IT re-sellers in my local area that I have contacted couldn't help either, they only get TP-Link products and one other brand that is not better.

**# Question**

That's what I've tried out. So my question in this forum now I suppose must be:

Could you recommend a chip model that has drivers for kernel 5.15 (that Ubuntu 22.04 uses)?

If not, do you have any other suggestion? 

**# Hardward info**

Here's some information about the machine:

Please let me know whether there's any other piece of information that might be relevant. I have access to the machine on Windows 10 and the BIOS.

Thanks.
Manuel

Try BrosTrend USB WiFi adapter 1200Mbps of speed, they says that it is supported with Linux kernel up to 5.18 with running Operating System  Ubuntu, Debian Linux Mint, Kali, Pop!_OS and etc.  Regards and cheers

---

### Post by kurt18947 on 2022-07-06
I think SeijiSensei's choice should work. I don't have wifi on my desktop machines, ethernet via MoCA has been foolproof. Notebooks have had Intel wifi and no muss no fuss, wifi was recognized by the live USB and continued to work once installed.

---

### Post by xinelo on 2022-07-18
This seemed to work. Thanks!

---

