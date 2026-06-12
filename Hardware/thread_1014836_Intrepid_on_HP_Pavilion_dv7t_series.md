---
title: "Intrepid on HP Pavilion dv7t series"
date: 2008-12-18
forum: Hardware
---

### Post by 10101011 on 2008-12-18
I just installed Intrepid on a new HP Pavilion dv7t laptop:

> 
Intel(R) Core(TM)2 Duo Processor T9400 (2.53 GHz)
4GB DDR2 System Memory (2 Dimm)
512MB NVIDIA GeForce 9600M GT 
500GB 7200RPM SATA Dual Hard Drive (250GB x 2)
Webcam. Intel Next-Gen Wireless-N Mini-card with Bluetooth


I've had some trouble getting sound working until I followed the advise on [this page]("http://www.linlap.com/wiki/HP+Pavilion+dv7t") - add '/etc/modprobe.d/sound' containing:
> 
options snd-hda-intel model=hp-m4 enable_msi=1
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel


The webcam seems to work, but is stuck at low resolution (tested using cheese).

The graphics card needed extra boot options (pci=nommconf) otherwise it would freeze the desktop periodically (this is supposed to be fixed in the latest beta driver).

Suspend doesn't seem to work yet - I haven't had time to fiddle with it.

Does anyone else have any experience with the dv7t?

---

### Post by pointym5 on 2009-02-01
I've just finished an Intrepid (32-bit) install on a new dv7t.

My webcam works, and is not stuck in low-res mode (tried cheese and luvcview). To get sound working, I added that modprobe.d file and also (via the Gnome sound preferences UI) set all the inputs and outputs explicitly to use pulseaudio. Without that, mostly audio didn't work at all - certainly not the microphone.

I've tried a Skype video call, and though a couple of acquaintances running Intrepid on new dv5t notebooks have been able to do Skype video, for me it'll only run one way video. In other words, either I can see who I'm talking to, or they can see me, but not both. It's not a bandwidth issue because from inside the same network on another machine (not a dv7t) Skype works fine.

---

