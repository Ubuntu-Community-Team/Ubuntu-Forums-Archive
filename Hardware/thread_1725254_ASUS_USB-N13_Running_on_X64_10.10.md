---
title: "ASUS USB-N13 Running on X64 10.10"
date: 2011-04-09
forum: Hardware
---

### Post by goldeneyegazza07 on 2011-04-09
Hi guys

I have just dual booted my main computer and have just realised that my current wireless card (Netgear WN111) will not work with X64 bit Ubuntu 10.10 but will with Windows 7 X64.  I have been looking around and I think getting a ASUS USB-N13 will be the way to go to replace my current one to make it work on both.  My question is has anyone else got this card and does it work out of the box on 64Bit without me having to connect up to the net to get it to work because I have no way to connect to net while im inside ubuntu at this stage until I can get a wireless card that works with it.

Any help would be appriacited

---

### Post by skalig on 2011-04-11
I would also be very interested in that, as I'm looking for a USB Wlan adapter. Has anybody experience with that device?
Or could anybody recommend a good and compatible USB Wlan N adapter for Ubuntu 10.10 x64?

Thank in advance

---

### Post by vcrpex on 2011-04-12
i am using asus usb-n10 running on 64bit maverick, but i do have to follow the instructions by chilli555 to get it up and running. once it is up and running, it never drop by itself unless my router got problems. one thing you can do is to copy and paste the solutions and download the appropriate files before trying to install 10.10.

---

### Post by skalig on 2011-04-13
You mean that post: [http://ubuntuforums.org/showpost.php?p=8916939&postcount=17](http://ubuntuforums.org/showpost.php?p=8916939&postcount=17) ?

---

### Post by goldeneyegazza07 on 2011-04-18
Hi guys

I have gone ahead and bought the device.  At first it did not work but I then shared the wireless connection from my one of my laptops which was also was running ubuntu 10.10 via ethernet and did the updates rebooted the computer and WLAN USB started working without any extra effort.  I hope this post helps people in the future in choosing the WLAN USB in the future is was a little frusating at first but once I did a little mucking around with it the device started and still is working fantasically on ubuntu and win 7.

Thanks for your help :)

---

### Post by fjgaude on 2011-04-27
> **skalig said:**
> I would also be very interested in that, as I'm looking for a USB Wlan adapter. Has anybody experience with that device?
Or could anybody recommend a good and compatible USB Wlan N adapter for Ubuntu 10.10 x64?

Thank in advance

Well, the ASUS USB-N13 wireless adapter is robust but the software that is designed to work with it covers so many pieces of other hardware, making it tough for a good out-of-box experience

I used the latest 2011_0107_RT3070_Linux_STA_v2.5.01_DPO_Modified driver and it worked just as thought it would. Did have to blacklist the rt2800usb driver, in /etc/modprobe.d/blacklist.conf, that tries to load at boot-up. 

I'm running Ubuntu 11.04 Released as of today.

Good luck!

---

