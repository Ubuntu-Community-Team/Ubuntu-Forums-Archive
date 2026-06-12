---
title: "Sound issue ATI SB450"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by equium on 2007-07-07
I'm running Ubuntu 7.04 on a Toshiba Equium/Satellite L30-149 and I have a ATI SB450. This card is known for having problems. After I manually installed the latest ALSA driver, util and lib and added "options snd-hda-intel model=3stack probe_mask=1" to alsa-base. This gave me sound in speakers but not in headphones. Then I tried "options snd-hda-intel model=toshiba probe_mask=1" which gave me sound in headphones only! 

I've tried model=auto too, but never get sound in speakers, only headphones. Help?!

---

### Post by stedevil on 2008-03-06
I also have a Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip

For those that don't have exactly this laptop you can verify if you have the same sound hardware via
System menu > Preferences > Hardware Information > SB450 HDA Audio [advanced]-tab
pci.subsys_product_id int 65329 (0xff31)
pci.subsys_vendor_id int 4473 (0x1179)

Even if you don't have the same it might be worth a shot to try out the below.

I've managed to get the following working with ALSA 1.0.16 (maybe works on earlier versions too, haven't checked)
* Speakers 
* Headphones
* PC-speaker Beeps (Line-in) 
* Front Mic 

all you need to do is put the following in your /etc/modprobe.d/alsa-base
options snd-hda-intel model=dallas

Then 
sudo rmmod snd_hda_intel
sudo modprobe -v snd_hda_intel
(or just reboot)

Ill report this to the ALSA devs, hopefully it will make it into ALSA 1.0.17 to work automagically.

PS Anybody that dont know how to manually compile and install the latest ALSA drivers, check the "Update to the Latest Version of ALSA" section in this howto
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

PPS

Another good way to REALLY find out what exact hardware you have is to do 
lspci -vvnn

...
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device [1179:ff31]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 19
	Region 0: Memory at d0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
...

---

### Post by stedevil on 2008-03-10
Ok, here is some important info straight from a HDA-INTEL developer that might be very helpful when trying to make your sound hardware work

> Toshiba tends to use teh same subsystem ID even though they are using different codecs.  It's not unheard of.  The driver is supposed to first look at the codec ID, then look at the pci subsystem ID and match the system to one in the table.

> 
[The ALC861] codec is very different from the 861VD. ALC861 is for versions A, B, and C for this codec.  The ALC861VD is the "Version D", and has added capabilities and is probably a newer manufacturing process. ...it's the codec ID/Subsystem ID combo that uniquely defines the audio system.  Some manufactures don't even make it that easy.

---

### Post by papparainen on 2008-07-06
> **stedevil said:**
> I also have a Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip

all you need to do is put the following in your /etc/modprobe.d/alsa-base
options snd-hda-intel model=dallas

Then 
sudo rmmod snd_hda_intel
sudo modprobe -v snd_hda_intel
(or just reboot)

Ill report this to the ALSA devs, hopefully it will make it into ALSA 1.0.17 to work automagically.

I can confirm that this fix works in Ubuntu 8.04 for the Toshiba Equium L30-149.

I did it like this:
sudo nano /etc/modprobe.d/alsa-base
and added this to the very end: options snd-hda-intel model=dallas
then just ctrl+x and save. 

Hope that this helps beginners.

After reboot I finally had sound yet again!. Strange enough, sounds worked OK in Ubuntu 7.04. All this time earphones worked, though.

---

