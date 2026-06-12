---
title: "Twinhead E10 notebook, no wifi with xubuntu"
date: 2008-05-21
forum: Hardware
---

### Post by sleep.sleep on 2008-05-21
Hi,
i just bought a twinhead E10 notebook,
below is the dmesg i got

[http://www.whitecoder.com/e10.txt](http://www.whitecoder.com/e10.txt)

it came preloaded with neoshine linux, but too heavy imo, so it is really slow.

i format the drive and put xubuntu on it. (work much better now)
but, the wifi doesn't get function.

could anyone of you know how to tackle this?
i am quite sure the support for that device should be available since neoshine is linux too so as xubuntu.

---

### Post by sleep.sleep on 2008-05-21
here the output of lspci command.
> 
00:01.0 Host bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] Host Bridge (rev 33)
00:01.1 VGA compatible controller: Advanced Micro Devices [AMD] Geode LX Video
00:01.2 Entertainment encryption device: Advanced Micro Devices [AMD] Geode LX AES Security Block
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0f.0 ISA bridge: Advanced Micro Devices [AMD] CS5536 [Geode companion] ISA (rev 03)
00:0f.2 IDE interface: Advanced Micro Devices [AMD] CS5536 [Geode companion] IDE (rev 01)
00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio (rev 01)
00:0f.4 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] OHC (rev 02)
00:0f.5 USB Controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] EHC (rev 02)

where is the wifi?? but the wifi led is on.... :(

---

### Post by nicedude on 2008-05-21
A casual glance through your dmesg file and I see nothing that jumped out at me. Due to this device not showing up in lspci that is odd as mine even before working still showed up incorrectly. I would suggest you do some research and see if you can find out what wifi chipset it has ( I tried but couldn't find it, you might though ) also below I will give you a couple commands to try that might help.

Update your PCI known device list of known devices

run this update command -> sudo update-pciids

Then try running lspci again and if no wifi info try running the lspci like below

lspci -vv

still no good info then try

lspci -vvv

Hope these help you find some info on your device and if you do find anything related to the wifi in questions then I would post that here.

---

