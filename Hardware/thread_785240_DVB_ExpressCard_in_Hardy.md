---
title: "DVB ExpressCard in Hardy"
date: 2008-05-07
forum: Hardware
---

### Post by jdpipe on 2008-05-07
Hi all

I have a Dell XPS M1530 and all seems to be working well so far, except webcam (haven't tried yet) and the TV card (don't know what to try). This TV card is a AverMedia HC82 NanoExpress ExpressCard DVB-T tuner that was sold with the computer by Dell.

What can I do to test to see if this card works or not? I tried 'lspci' and 'lsusb' and 'lspcmcia' but none of them appeared to show my TV card.

What packages would I need to install in order to *attempt* to use this card? Or do I need to do some kernel module bizzo?

Cheers
JP

---

### Post by jdpipe on 2008-05-30
The AverMedia people told me that the AverTV HC82 ExpressCard TV tuner is not and will never be supported on Linux.

I have not been able to work out any way of even detecting the presence of this hardware.

---

### Post by prismatic7 on 2008-06-02
try:

```
sudo modprobe pciehp pciehp_force=1
```

which will load drivers for the pcie hotplug interface. after that, you MAY be able to see your card using lspci.

---

### Post by 5m0k3 on 2008-06-15
lspci now reveals ```
0c:00.0 Multimedia controller: Philips Semiconductors Unknown device 7160 (rev 03)
```

Upon further investigation, sudo lspci -vvnn displays the following: ```
0c:00.0 Multimedia controller [0480]: Philips Semiconductors Unknown device [1131:7160] (rev 03)
	Subsystem: Avermedia Technologies Inc Unknown device [1461:0455]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at fe600000 (64-bit, non-prefetchable) [disabled] [size=1M]
	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [50] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <256ns, L1 <1us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
	Capabilities: [74] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [80] Vendor Specific Information
```
I've had no luck v4l-dvb.  I still have no /dev/dvb/ directory.

---

### Post by aaamos on 2008-10-04
Hmm, I have the same card, an AverMedia HC82 NanoExpress TV card, in a Dell Studio 17 - I can get to the same stage, i.e. getting it to recognise "Philips Semiconductors Unknown device 7160 (rev 03)". If anyone knows what to do beyond that I'd appreciate any hints... :)

---

### Post by denhamcoote on 2009-01-07
*raises hand*

Yeah, I'd also love any further info - Sitting with a Studio 17.  No fingerprint reader, no TV, no remote, and as of 8.10 no video in apps like cheese.  :(

---

### Post by jdpipe on 2009-01-07
> **denhamcoote said:**
> No fingerprint reader, no TV, no remote, and as of 8.10 no video in apps like cheese.  :(

For me, the fingerprint reader works (using thinkfinger, not fprint), the remote works (the one that fits into the expresscard slot, not the big fat one), and the webcam works too (with Skype, Cheese, but not with Empathy/Gabble).

It is only the TV card that's not working for me, but I've had confirmation from the manufacturer that they will not be providing drivers.

---

### Post by madmufflon on 2009-01-16
hey, 
i got the same probleme
i'm looking for a solution, if any of you got one please post it.
what i found:
[http://jusst.de/hg/saa716x/summary](http://jusst.de/hg/saa716x/summary)
this seems to be the driver required, especially because in the changelog there apears a HC82 ([http://jusst.de/hg/saa716x/rev/4a74d800ee61](http://jusst.de/hg/saa716x/rev/4a74d800ee61)), which is our dvb card. But even after installing it did not work for me
if i got a solution i will tell you guys

---

### Post by jdpipe on 2009-01-19
> **madmufflon said:**
> hey, 
what i found:
[http://jusst.de/hg/saa716x/summary](http://jusst.de/hg/saa716x/summary)
this seems to be the driver required, especially because in the changelog there apears a HC82

That's right. Well spotted! In the file

/saa716x-e1225092bc77/linux/drivers/media/dvb/saa716x/Kconfig

it claims explicitly that the HC-82 card is supported. I managed to compile but haven't yet tested it, because I put the card in a box somewhere!

---

### Post by madmufflon on 2009-01-20
i managed to include saa716x_core and _hybrid via modprobe, but unfortunately it did not change anything. There are no displayed errors(even in dmesg), but  /dev/dvb does not exist. if you have succes i would appreciate any hints you could give on how you made it work.

---

### Post by 5m0k3 on 2009-02-02
I'm in the same boat as you all.  I did notice, however, that prior to a reboot, dmesg | grep saa revealed ```
[ 1730.134988] saa716x_core: Unknown parameter `saa716x_hybrid'
```

---

### Post by egawrangler on 2009-04-06
Anyone have an update on this...?

sooooooo close....yet so far away!

-EGA

---

### Post by jdpipe on 2009-04-06
The HC82 driver package from Avermedia includes a bunch of files -- is there any way of using those drivers in a similar way to that which ndiswrapper uses, perhaps?

---

### Post by Digital_Warrior on 2009-05-14
has any one got this to work. I have tried everything I can with out any luck. 
If you look at [http://jusst.de/hg/saa716x/rev/a5dc0309adc7](http://jusst.de/hg/saa716x/rev/a5dc0309adc7) you can see some one was working on it but I do not know what is going on with that project.

---

### Post by madmufflon on 2009-06-11
hey,

seems like there has been some progress:
[http://jusst.de/hg/saa716x/summary]("http://jusst.de/hg/saa716x/summary")
The developer claims the driver is working now.
but unfortunately even after installing the driver the card does not work (at least on my dell studio 15).
Has somebody of you succeeded in making it work?

p.s.: to compile the drivers i had to copy a file out of the v4l-dvb sources into the v4l folder in the drivers folder.

---

### Post by max38 on 2009-07-14
I also managed to compile the saa716x driver by adding one file as indicated previously. But for me too it does not work and Dmesg and /var/log/messages are empty.
My tv card is avermedia AVerTV duo hybrid on pciE. The chipset is saa7162.
I tried to contact the developer of the driver Manu Abraham without success.
Did somebody managed to contact him to have more information?
It is all in Manu's hand.

---

### Post by nDrewPJ on 2009-11-22
Please merge topics! All about AverMedia NanoExpress!!

[http://ubuntuforums.org/showthread.php?t=847610&highlight=nano+express](http://ubuntuforums.org/showthread.php?t=847610&highlight=nano+express)
[http://ubuntuforums.org/showthread.php?t=1263901&highlight=nano+express](http://ubuntuforums.org/showthread.php?t=1263901&highlight=nano+express)
[http://ubuntuforums.org/showthread.php?p=8367220#post8367220](http://ubuntuforums.org/showthread.php?p=8367220#post8367220)

PS. Let's vote for this bug at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215624)

---

### Post by harlock59 on 2010-03-14
there used to be a driver available i think, but i'm not sure

it was something like saa187

it's possible to check at linuxtv's wiki

---

### Post by denhamcoote on 2010-08-19
> **jdpipe said:**
> For me, the fingerprint reader works (using thinkfinger, not fprint), the remote works (the one that fits into the expresscard slot, not the big fat one), and the webcam works too (with Skype, Cheese, but not with Empathy/Gabble).

It is only the TV card that's not working for me, but I've had confirmation from the manufacturer that they will not be providing drivers.

I know this comes as an awfully delayed reply, but... How'd you manage to get your remote working?  Using the patched lirc drivers?  I've gotten it working to a point, but nothing that I'm 100% happy with.

Sorry to stray from the original topic.

---

