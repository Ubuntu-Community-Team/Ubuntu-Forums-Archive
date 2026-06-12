---
title: "So I bought the laptop and installed Ubuntu. What now...?"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by Bou on 2006-03-01
Hi, I just bought a Packard Bell laptop for using with Dapper. I would like you to answer -if possible- to a few questions:

-How can I set the screen resolution to be wide screen?

-Is there a way to emulate the wheel scroll? I could do that by dragging my finger through the side of the touchpad on the copy of Windows that cae preinstalled, but now it doesn't seem to be working.

Thanks a lot.

---

### Post by Winux123 on 2006-03-01
Try "sudo dpkg-reconfigure xserver-xorg" minus the quotations.

I think that is the correct , you should be able to setup your screen resolution this way, not sure about your emulated scroll wheel. Hope it helps.

---

### Post by ubuntu-mike022465 on 2006-03-01
If it's an ALPS or Synaptic touchpad try here for instructions...

[http://ubuntuforums.org/showthread.php?t=78904&page=1](http://ubuntuforums.org/showthread.php?t=78904&page=1)

Hope it helps

M. \\:D/

---

### Post by Bou on 2006-03-01
Just tried the reconfigure-thingy. It didn't work.

---

### Post by towsonu2003 on 2006-03-01
[QUOTE=Bou]
-How can I set the screen resolution to be wide screen?
[/QUOTE]
Email the manufacturer and ask for the detailed specifications of your monitor. Than run sudo dpkg-reconfigure xserver-xorg and when it comes to that, choose (sounds like) "detailed configuration of monitor. 

The most important values are horizontal and vertical sync values (I think), so be sure the detailed specs document that the manufacturer sends you includes that. Once you set your sync values, it should give you the correct resolution... at least that's what happened in my installation.

---

### Post by Bou on 2006-03-02
[QUOTE=towsonu2003]Email the manufacturer and ask for the detailed specifications of your monitor.[/QUOTE]

I'm not sure the anufacturer will give me any information; I phoned them yesterday for some info and they told me they sell the computer complete with the software and they can'ttake responsibility for any changes made to it. I will, try, anyway.

However, I just noticed one thing: If I use the "nv" driver I get the right resolution for a widescreen, but I don't if I use the "nvidia" driver -which is necessary for Xgl and hardware acceleration, I think-. Could this information be useful at all?

---

### Post by hw-tph on 2006-03-02
First off, we need more information. What kind of laptop is this? Brand and exact model name, please. Also, post the output of the **sudo lspci** command to see what kind of hardware it has.

In most cases it is possible to get most things working but it may require some work.


Håkan

---

### Post by Bou on 2006-03-02
[QUOTE=hw-tph]First off, we need more information. What kind of laptop is this? Brand and exact model name, please.[/QUOTE]

Sure, it's a Packard Bell R9750. [here]("http://www.tecnologia.carrefour.es/electronic_productdetails.asp?Query=&ProdTypeId=13&CatId=1004040&PrevCatId=0&ProdId=2516159&ST=BF1004040") is some more info about it, unfortunately there was no proper information about it inside the package and there doesn't seem to be on PB's homepage either.

Here's my lspci

> 0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 6200 TurboCache (rev a1)
0000:02:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:02:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:02:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:02:02.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
david@portatil:~$

---

### Post by towsonu2003 on 2006-03-02
[QUOTE=Bou]they told me they sell the computer complete with the software and they can'ttake responsibility for any changes made to it.[/QUOTE]
Don't tell them that you are installing a new operating system. "you just need some information about this laptop, because a friend of you is interested in buying a new one but s/he wants to see detailed specifications" or something like this.
Also, please attach /var/log/Xorg.0.log (as a file, not as text) after you boot using nvidia. And you will want to check whether proprietary drivers (nvidia) support your "nVidia Corporation GeForce Go 6200 TurboCache (rev a1)"...

---

