---
title: "AMD 5350 ASRock AM1H"
date: 2015-11-11
forum: Hardware
---

### Post by huw3 on 2015-11-11
Hi folks,

I'm struggling to get any audio out of my new HTPC. AMD 5350, ASRock AM1H-ITX. OS is Ubuntu server 14.04.03 running Openbox and Kodi. Graphics drivers are AMD Catalyst. Strangely Ubuntu doesn't seem to have detected audio hardware at all.

$ aplay -l
aplay: device_list:268: no soundcards found...

BUT lshw gives me

*-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 02
             width: 64 bits
             clock: 33MHz

Can anyone tell me how to get Ubuntu to recognise the audio device permanently and get the drivers into the system?

TIA

---

### Post by innocuous_name on 2015-12-28
Did you resolve this issue?  I'm starting a build with this setup, so curious.

---

### Post by SR_ELPIRATA on 2016-01-16
Hey, I think server versions by default dont use audio :) (I may be wrong on that one, but Id personally never tried a server version for HTPC) I'd stick with a desktop version instead. You also can try first with a live cd/usb.

PS: I also have the Azalia controller... and up to this day I only get 2 channels via analog and hdmi (but I currently dont have an HDMI Receiver to check 5.1 setups).  If possible, I would like to know if you guys are setting it thru HDMI or analog, thanks!

---

