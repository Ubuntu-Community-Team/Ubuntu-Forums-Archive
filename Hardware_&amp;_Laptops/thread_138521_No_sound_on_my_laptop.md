---
title: "No sound on my laptop"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by Bou on 2006-03-02
I just bought a laptop, ad it works mostly fine. However, there's no sound and I don't know where to begin to solve this situation. Can you help me guys?
anks a lot.
Th

---

### Post by swamytk on 2006-03-02
if your provide some info on your laptop model, which OS and version and what is the error message you are getting.... i can help you!

---

### Post by Bou on 2006-03-02
[QUOTE=swamytk]if your provide some info on your laptop model, which OS and version and what is the error message you are getting.... i can help you![/QUOTE]

I'll copy the info I gave on other thread: It's a Packard Bell R9750. [here]("http://www.tecnologia.carrefour.es/electronic_productdetails.asp?Query=&ProdTypeId=13&CatId=1004040&PrevCatId=0&ProdId=2516159&ST=BF1004040") is some more info about it, unfortunately there was no proper information about it inside the package and there doesn't seem to be on PB's homepage either.

I'm using the last version of Dapper, and there's no error message at all... I just get no sound.

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

### Post by Sandlst on 2006-03-02
On my computer, the default volume controls do not work right...under volume control I have to click on the preference, and put a check mark on "front" to get the front volume control, which is muted by default.  Sound comes after I un-mute it and turn it up, hope this helps.

---

### Post by Bou on 2006-03-02
[QUOTE=Sandlst]On my computer, the default volume controls do not work right...under volume control I have to click on the preference, and put a check mark on "front" to get the front volume control, which is muted by default.  Sound comes after I un-mute it and turn it up, hope this helps.[/QUOTE]

Yeah it did, in fact thanks to you I could fix it ^^ cheers man, I owe you!

---

