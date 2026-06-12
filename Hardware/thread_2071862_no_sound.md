---
title: "no sound"
date: 2012-10-16
forum: Hardware
---

### Post by unibroker on 2012-10-16
I have 2 outboard speakers and usually there is a choice under sound settings for analog output, which always works.  This morning I had no sound but when I went to Sound under System Settings and under the Output tab there is only one choice, HDMI/DisplayPort2 High Definition Audio Controller.  My monitor has no speakers.

This setup worked as recently as yesterday.  I have since booted a live cd of the same Ubuntu only 64 bit during which I never changed the settings (it is my understanding they aren't retained anyway).  

Thanks in advance for any assistance.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
rm -rf ~/.pulse
logout 
login
check the setting there again
if still no sound
run this
```
aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'
```
it will generate some terminal commands, run each till you find the one that makes sound and post the command that made noise

---

### Post by unibroker on 2012-10-16
> **pqwoerituytrueiwoq said:**
> rm -rf ~/.pulse
logout 
login
check the setting there again
if still no sound
run this
```
aplay -l | grep card | sed 's/://g' | awk '{print "speaker-test -Dplughw:"$2","$7" -c2"}'
```
it will generate some terminal commands, run each till you find the one that makes sound and post the command that made noise

After ```
rm -rf ~/.pulse
``` Output in Sound settings is now empty and therefore could not Test Sound.  I then performed the commands posted and no sound from any of them.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
did you logout and in again? (reboot if you prefer)
the rm -rf ~/.pulse would reset your accounts sound config
what does this give
```
lspci | grep Audio
```

---

### Post by unibroker on 2012-10-16
> **pqwoerituytrueiwoq said:**
> did you logout and in again? (reboot if you prefer)
the rm -rf ~/.pulse would reset your accounts sound config
what does this give
```
lspci | grep Audio
```

I did logout and in again.

Output from the command gives:  

```
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
```

I'll try your first instruction and reboot this time.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
Never seen that before, no chipset on the sound card
maybe this will give us something useful
```
lspci -vv -s 01:00.1
```

---

### Post by unibroker on 2012-10-16
> **pqwoerituytrueiwoq said:**
> Never seen that before, no chipset on the sound card
maybe this will give us something useful
```
lspci -vv -s 01:00.1
```

Returned:
```
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8354
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
```

BTW, rebooted and now have under Sound what was in the original post.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
Assuming this is a desktop, with a dedicated sound card make sure it is seated properly in the system

try the commands that long command generated again
if still nothing what does [FONT=Courier New]aplay -l[/FONT] give you

---

### Post by unibroker on 2012-10-16
> **pqwoerituytrueiwoq said:**
> Assuming this is a desktop, with a dedicated sound card make sure it is seated properly in the system

try the commands that long command generated again
if still nothing what does [FONT=Courier New]aplay -l[/FONT] give you

It is a desktop.  Still the same results with the long command.  Just to mention, before today when I used to go into Sound, Output there were multiple options one of which started with "Analog...".  That is the option that worked because my outboard speaker have a single pole plug (don't know the correct term but they are old style).  Since I've had the problem the Analog option is missing as well as ANY option beside what was in OP.

Output from your last intruction.  Thanks for the assistance!

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by pqwoerituytrueiwoq on 2012-10-16
make sure the onboard audio is enabled in your bios
assuming it already is shutdown the system (this fixes my onboard etherent)
switch the PSU off (or unplug)
wait 30 seconds
switch the PSU on (or plugin)
boot the system and hope it works
if [FONT=Courier New]aplay -l[/FONT] does not have more output, it is safe to assume the onboard audio has played it's last tune (hardware failure)

---

### Post by unibroker on 2012-10-16
> **pqwoerituytrueiwoq said:**
> make sure the onboard audio is enabled in your bios
assuming it already is shutdown the system (this fixes my onboard etherent)
switch the PSU off (or unplug)
wait 30 seconds
switch the PSU on (or plugin)
boot the system and hope it works
if [FONT=Courier New]aplay -l[/FONT] does not have more output, it is safe to assume the onboard audio has played it's last tune (hardware failure)

Eureka!  Success.  The problem was that somehow the bios, onboard audio was not enabled.  I'll investigate the why but in the meantime thank you very much.

---

