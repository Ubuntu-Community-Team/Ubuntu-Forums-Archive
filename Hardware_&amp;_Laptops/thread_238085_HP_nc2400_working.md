---
title: "HP nc2400 working"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by sweRascal on 2006-08-17
Just wanted to let you all know that I have just installed an HP nc2400 succecfully with Ububtu Dapper 6.06.1.
Only thing I had to do is install the 1280x800 resolution patch.
I have even installed aiglx and Compiz according to the tutorials found here and it works beautifully.
So far I have not found any problems but will report back here if I do.

Just gotta say I love Ubuntu....:D

---

### Post by joefke on 2006-10-17
what about suspend? does it wake up after s2ram/s2disk?

i read some reviews about the notebook... they were reporting runtimes between 5:30h to 6h. did you measure it? any differences between linux and windows?:-k 

there are no buttons to scroll -- does that bother you?

i'm so close to buying it... :rolleyes: 

greetings

joefke

---

### Post by tyr14 on 2007-10-05
> **sweRascal said:**
> Just wanted to let you all know that I have just installed an HP nc2400 succecfully with Ububtu Dapper 6.06.1.
Only thing I had to do is install the 1280x800 resolution patch.
I have even installed aiglx and Compiz according to the tutorials found here and it works beautifully.
So far I have not found any problems but will report back here if I do.

Just gotta say I love Ubuntu....:D

I have installed ubuntu feisty fawn 7 in my notebook hp nc2400...

I was a windows user, and i don't know hot to install the 915resolution patch for 1280x800 resolution, i was reading that with reboot, that resolution is lost :(, and wireless does not work, i can't connect at school :(.

Ubuntu is very friendly and prettier than windows vista, but if can't connect to wireless, and resolution is poor, i can't keep it.:confused:

---

### Post by sweRascal on 2007-10-05
Ive installed Feisty on several 2400 with great succes. What is your problems more exactely?

---

### Post by tyr14 on 2007-10-07
> **sweRascal said:**
> Ive installed Feisty on several 2400 with great succes. What is your problems more exactely?

Actually I'm not a linux master, I'm new about linux, and don't know hot to get 1280x800 with ubuntu.

And Wireless don't appear, i don't know how to install devices in linux :(, Linux is a pretty SO.

Ubuntu in hp compaq nc2400, works fine, usb devices too, cd dvd too, the only one problem is the resolution and the wireless that is not working here.

---

### Post by sweRascal on 2007-10-08
Can you please post some more information about your specifit 2400 please. There are delivered with differend network adapters.
You can do a lspci and just post the return data.
For the 1280-800 just install the i810 graphics fix that is in the repository. (i think thats what its called without checking.) Just start synaptics and its usually right there.

---

### Post by tyr14 on 2007-10-08
> **sweRascal said:**
> Can you please post some more information about your specifit 2400 please. There are delivered with differend network adapters.
You can do a lspci and just post the return data.
For the 1280-800 just install the i810 graphics fix that is in the repository. (i think thats what its called without checking.) Just start synaptics and its usually right there.

Hi, i'm using sabayon with live cd, my network adapter for ethernet and wireless is broadcom, bluetooth is working, and is more stable than ubuntu, my ubuntu is "cdr" i will burn ubuntu 7.04 dvd for check if it changes.

Ubuntu iso (cdr 700mb) isn't complete, i'm sure that dvd is so much better :) I love sabayon and Ubuntu!!!!!!!!!!!!!!!!!!!!

---

### Post by sweRascal on 2007-10-09
Hey there, I installed my nc2400 that has the Broadcom network adapter and Intel WLAN adapter and an Intel graphics adapter. All work out of the box, all I have to do to get a clean image is to install the i810 patch. To get even better results I also tweak xorg.conf to get the correct dpi settings for fonts.
All done, works like a charm.
You shouldnt get any different results using the CD or the DVD to install. What CD are you using? The Alternate, client or server?

---

### Post by tyr14 on 2007-10-09
> **sweRascal said:**
> Hey there, I installed my nc2400 that has the Broadcom network adapter and Intel WLAN adapter and an Intel graphics adapter. All work out of the box, all I have to do to get a clean image is to install the i810 patch. To get even better results I also tweak xorg.conf to get the correct dpi settings for fonts.
All done, works like a charm.
You shouldnt get any different results using the CD or the DVD to install. What CD are you using? The Alternate, client or server?

I'm using WLAN Broadcom 802.11 b/g, this wireless adapter works fine with knetwork manager in sabayon, but i don't have wireless network with ubuntu network manager.

May I change knetwork for network manager? I have Ubuntu 7.04 in DVD

Here is my LSPCI

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:09.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
ubuntu@ubuntu:~$

---

### Post by meiserer on 2007-12-14
> **sweRascal said:**
> Just wanted to let you all know that I have just installed an HP nc2400 succecfully with Ububtu Dapper 6.06.1.
Only thing I had to do is install the 1280x800 resolution patch.
I have even installed aiglx and Compiz according to the tutorials found here and it works beautifully.
So far I have not found any problems but will report back here if I do.

Just gotta say I love Ubuntu....:D


I would be so happy to follow you with a working ubuntu (7.10) installation on my nc2400. Installation itself runs smoothly, also components like wlan, display with correct resolution and so on work fine. But there is one thing that drive me really mad:

1) Hibernate: even if the machine goes down at the very end the hibernation itsself tooks to much time and give me error messages like this:

[I]  usb_device usbdev4.1: pm: resume from 0, parent usb4 still 2 
[121.992000] usb_endpoint usbdev5.1_ep00: PM : resume from 0 parent usb5 still 2 [/I]

Do you have any ideas to help me with? I would be so glad, but please keep in mind that I am absolutely new to linux, if you give me any advices ;-)

Cheers

---

