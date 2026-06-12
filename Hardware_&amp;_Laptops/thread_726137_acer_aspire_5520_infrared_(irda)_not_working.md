---
title: "acer aspire 5520 infrared (irda) not working"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by natirips on 2008-03-16
How do I install infrared drivers / tools / utils / anything-that-makes-it-work for Acer Aspire 5520G laptop, Ubuntu Gusty Gibbon 7.10.
Edit: Now I'm on Ubuntu 8.04 Hardy Heron.

Here's output of lspci:```
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```(if it's of any use).

I've already tried irxfer but it ain't working at all, it's like my mobile phose doesn't exist. I know that the same phone could connect to another laptop and another mobile phone, so I'm sure I'm not doing anything wrong with the mobile phone.

I've also tried ircp:```
natirips@natirips-laptop:~/temp$ ircp -r
Waiting for incoming connection

natirips@natirips-laptop:~/temp$ touch a
natirips@natirips-laptop:~/temp$ echo abcqwetuiokhgdffghn > a
natirips@natirips-laptop:~/temp$ mv a a.txt
natirips@natirips-laptop:~/temp$ ircp a.txt 
Connecting...failed
natirips@natirips-laptop:~/temp$ ircp a.txt 
Connecting...failed
natirips@natirips-laptop:~/temp$ 

```While I was trying to send the file from my phone to computer, my mobile said that it couldn't find any devices, and while I was trying to send the file from laptop to mobile, that "Connecting...failed" part appeared immediately.

Any help appriciated.

---

### Post by natirips on 2008-03-30
bump

---

### Post by Tigin on 2008-05-09
i need that solution too , if any one can help :)

---

### Post by Ashrael on 2008-07-05
Me too! I want to get irda working on my acer aspire 5920G, so any ideas are welcome.

Also, i think bluetooth hardware is installed but not working. I saw when vista installed that it offered me to connect bluetooth devices, but then....acer software started installing and now no bluetooth anymore!!!!! 

I suspect that the acer software disabled the hardware somehow? anybody have a clue... would be nice if we got bluetooth for free :) 

attached hwinfo.tar.gz......is a txt file...


So you see it seems to exist.....

any ideas welcome... TIA

---

### Post by natirips on 2008-07-06
@Ashrael: Isn't there a button somewhere on your laptop to switch on/off the bluetooth? For me it works out-of-the-box. I have line of buttons between my power button (near display) and speakers, one of the has a bluetooth symbol on it. My bluetooth activates when I press it.

@others: As for 5520G, I later noticed it doesn't really have IRDA, it has CIR receiver (for remote controlers), which looks alot like IRDA. Although it also works on the same principle as IRDA (using infrared e-m waves), I'm not sure if the computer understands them the same way.

---

### Post by Ashrael on 2008-07-24
@natirips: thanx, sorry i did not react sooner, vacation etc..
There is a button for bluetooth on the laptop, but it supposedly has no bluetooth, BUT: when you open it up for the first time, and Vista installed (oooh) It started up the first time with the blue light on saying that i could now connect bluetooth devices, THEN: the acer software kicks in, it installs for about half an hour, and after that i never could enable the bluetooth again! I did this on two identical laptops (if i'd only known)...
So i started digging and found a device that has an invalid VID and PID...

Illegal Vendor ID
/0/100/1e/9.4


product: Illegal Vendor ID
vendor: Illegal Vendor ID
bus info: pci@0000:0a:09.4
version: ff
width: 32 bits
clock: 66MHz
capabilities:
	bus mastering,
	VGA palette,
	PCI capabilities listing
configuration:
	latency: 255
	maxlatency: 255
	mingnt: 255
this device hasn't been claimed

Hope anyone can help here...

About the CIR, ive got the same laptop here with winXP on it, i'll post what i can find...

---

### Post by natirips on 2008-07-24
> **Ashrael said:**
> @natirips: thanx, sorry i did not react sooner, vacation etc..
There is a button for bluetooth on the laptop, but it supposedly has no bluetooth, BUT: when you open it up for the first time, and Vista installed (oooh) It started up the first time with the blue light on saying that i could now connect bluetooth devices, THEN: the acer software kicks in, it installs for about half an hour, and after that i never could enable the bluetooth again! I did this on two identical laptops (if i'd only known)...
So i started digging and found a device that has an invalid VID and PID...

Illegal Vendor ID
/0/100/1e/9.4


product: Illegal Vendor ID
vendor: Illegal Vendor ID
bus info: pci@0000:0a:09.4
version: ff
width: 32 bits
clock: 66MHz
capabilities:
	bus mastering,
	VGA palette,
	PCI capabilities listing
configuration:
	latency: 255
	maxlatency: 255
	mingnt: 255
this device hasn't been claimed

Hope anyone can help here...

About the CIR, ive got the same laptop here with winXP on it, i'll post what i can find...
Vista, XP, Acer software (are you even using Ubuntu? ^^).... I've never seen something like that on my laptop, yet Bluetooth worked out-of-the-box, while irda doesn't even exist to begin with... There's just CIR. This is just a wild guess but I imagine the diffrence between cir and irda is like the diffrence between CD and DVD (or ROM and RAM) - they don't do the exact same function, they just work on the same principle. I imagine CIR can only recieve data and cannot send it. Although, I might be all wrong. I initially thought it had IRDA because they look the same on the outside (a small black semi-transparent plastic rectangle). I noticed it was CIR while reading the manual that came with the computer.

---

