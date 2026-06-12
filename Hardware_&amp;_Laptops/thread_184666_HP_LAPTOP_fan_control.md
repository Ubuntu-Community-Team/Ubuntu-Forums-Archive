---
title: "HP LAPTOP fan control"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by binarychen on 2006-05-30
Hi,

I am a software engineer and buy a HP dv1000 laptop, I am boried by the fan noise and can anyone tell me how to program it so that I can control it to run always with low speed instead run constantly when the temp is high?

binch@BIN:/proc/acpi/thermal_zone/THRM$ cat *
<setting not supported>
cooling mode:   passive
<polling disabled>
state:                   ok
temperature:             54 C
critical (S5):           83 C
passive:                 78 C: tc1=2 tc2=3 tsp=50 devices=0xc16dbee0

Thanks a lot.

Binary Chen

---

### Post by Kabal on 2006-05-30
I use i8k(mon) for my laptop.
It's just perfect for me :)

(sorry I8kmon is for Dell laptops)
[http://manpage.willempen.org/1/i8kmon](http://manpage.willempen.org/1/i8kmon)

---

### Post by binarychen on 2006-05-30
Anyone knows there is one for HP laptops?

Thanks!

---

### Post by Vorian on 2006-06-02
Upgrade to 5.10 or 6.06!  Much better laptop support.

---

### Post by johnsawyer on 2007-12-16
I’ve been searching the web for hours how to change the settings that **under Vista the laptop fan would not be always running while on AC power.** I've tried multitudes of power configurations. When I run on AC the fan is constantly on, although it’s not excessively loud.  If running on batteries, the notebook is silent. Under Windows XP the fan turned on only when the temperature rose above a certain level, regardless whether it was running on battery or plugged in. I thought it had to do something with the absence of nVidia PowerMizer settings under Vista. I tried SpeedFan, Notebook Hardware Control (NHC), RivaTuner – some of them don’t work on x64, some don’t have signed drivers etc. I read that one guy even soldered a resistor to reduce the fan speed.

[B]Well, the solution to silence my HP nw9440 mobile workstation notebook was really simple:
In BIOS under System Configuration | Device Configurations there is a setting called “Fan Always on while on AC Power” and it was “Enabled”.[/B] Vista’s ACPI was actually conforming to this BIOS setting and XP’s ACPI was ignoring this setting. I just disabled it and the laptop is much more pleasant to use – even without earplugs ;) I nevertheless put a CD box under the touchpad to improve cooling – so that the fan doesn’t need to turn on that often.

I hope this helps someone. :)  The same should work on other more recent HP laptops running Vista (nx9420, nx8420, 8510p, 8510w, 8710p, 8710w), and presumably also on Dell, Gateway, Asus... If you don’t see the setting, try upgrading to the latest BIOS firmware.

---

### Post by aoeuid on 2008-01-05
I have an hp dv9000, and my final recourse was to just buy a damned cooling pad and tape a bent paperclip into the fan :D

I looked far and wide, and even tried going to hp, but they gave me a fat finger (as is to be expected) and none of the fan control or whatever programs worked...

So ya. Paperclip and cooling pad is the best I could get. If anyone still has any better solutions, please reply (or at least skype :)

---

### Post by gfowler on 2008-01-05
> **aoeuid said:**
> I have an hp dv9000, and my final recourse was to just buy a damned cooling pad and tape a bent paperclip into the fan :D

I looked far and wide, and even tried going to hp, but they gave me a fat finger (as is to be expected) and none of the fan control or whatever programs worked...

So ya. Paperclip and cooling pad is the best I could get. If anyone still has any better solutions, please reply (or at least skype :)

Sorry no solution for you but just an aside, your battery life should really suck now, since stalled motor current is much higher than that of one running.  Not to mention heat generation in the stalled fan motor, can one say 'fire hazarrd"?

Jerry

---

### Post by neilslade on 2008-01-13
I have an h zv5000---  powerful machine

P4 3 GHZ  100GB HHD

fan noise?

Horrific.

cannot find a solution yet except to hard wire a resistor/fan control than will deal with the 5 V fans--

a royal pain in the ***.

It would be SO SIMPLE for HP to make a quiet computer--- but no, they have to be cheap ***.

---

### Post by neilslade on 2008-01-13
Okay, so I built a fan control

[IMG]http://www.neilslade.com/gifs/teeny.jpg[/IMG]

from [http://www.overclockers.com/tips910](http://www.overclockers.com/tips910)



small enough to put inside the memory card bay--  but will require wiring inline with the main fan.

I am starting to think the fan is defective, as it would just always run at full bore, different from fan #2.

I bought a good replacement fan pulled from a like-new HP ZV5000  so next week I'll know if the fan noise is due to bad design, or broken fan...

stay tuned---  

still would like software to adjust fan speed--

my GUESS is that you could reduce fan speed 30-70% and not increase heat that much-- especially if the fan runs all the time.

It seems much smarter to run a fan at a constant slower speed, than stupid programming that runs a fan on and off and on and off and on and off

---

### Post by entropico on 2008-01-15
> **neilslade said:**
> I have an h zv5000---  powerful machine

P4 3 GHZ  100GB HHD

fan noise?

Horrific.

cannot find a solution yet except to hard wire a resistor/fan control than will deal with the 5 V fans--

a royal pain in the ***.

It would be SO SIMPLE for HP to make a quiet computer--- but no, they have to be cheap ***.

I have the same machine ( I think, zv5000 is a family name, not a specific model), and the same problem with the constant fan.

I also have problems recording the fan speeds, temps, voltages with every windows temp monitoring program that claims to have VIA VT1211 (Super IO / Southbridge with Hardware monitor) support. Speedfan, Hmonitor, SensorsView etc., they all report bogus values. Only voltages seems to work for me, thoug the values seem slightly out of range.

Hmonitor has actually listed zv5000 vt1211 support as verified, as of a rather early version (forget exactly which). Perhaps you will have better luck? Mayb e newer version of the VT1211 chip?

My exact model is zv5000t (DL228AV). The motherboard is labeled HR60 something.. I forget exactly I wish I would have written down the names/numbers on the chips.
I should run lspci to get the device IDs.

In any case, the VT1211 datasheet is publicly available! It does include software fan controll (on,off, speed) and speed monitoring. It includes programming information, though there may be a more detailed guide available elsewhere. (There is a kernel module supporting it, it's developers or code may be usefull)

So a little bit of screwing around with the VT1211 hardware monitoring procedures should indicate what is up. I'll be messing with this shortly and will get back to this thread
In the meantime, try the mentioned kernel module and windows programs, maybe they will work for you? Maybe there are variations of the chip, and via could help? 

Goodluck and thanks,as I said before I should be back here within a few days with whatever I find.

---

### Post by entropico on 2008-01-16
I should also mention, that the fan comes on about a second after a cold (sitting for a day) boot, around when the OS is loading, ad then it stays. Even  after shuting the thing off and turning it on again. So... I'd think it is temp related... I'll try to verify that behavior tomarow.

I installed a mobile pentium 4 M cpu (originally it was a plain pentium 4), that scales the CPU freq from 3.0 to 1.6 GHz when not in use to conserve batteries. The drop in heat output from the fan vent due to scaling is very noticeable with my bare hand. It can withstand higher temps but has the same max heat disipation rate. The fan doesnt seem to care though... only time it is off is in standy mode, and as mentioned, after being off for a day (ok, maybe so many housr depending on room tmep),  just untill the OS starts loading.

I know from experimentation that the fan regulation is not pure sftware controlled. With a broken CPU (missing vital pins), as the dumby CPU heated up, the fans would turn on and off as usual. Somethig hardware based must have been doung that ( Not entirely sure , but I'm pretty sure ther was no way for the CPU to have been working with shorted pins)

As I mentioned in the last post, if you can find out the CPU temp somehow ( I'm trying to do that myself) please tell what it is and how you got it :) (Ofcourse it has to do with the VT1211 but I meant 'how' in terms of programs that support it)

---

### Post by entropico on 2008-01-16
So, it seems various third-party windows hardware monitoring utilities say I have a VT211, however.... they don't say how they come to this conclusion.

I ran LSPCI from a live CD, I don't see a VT1211 or anything via realted:

HP ZV5000 Series ZV5000t DL228AV:

-[0000:00]-+-00.0  ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833]
           +-01.0-[0000:01]----05.0  ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
           +-13.0  ATI Technologies Inc OHCI USB Controller #1 [1002:4347]
           +-13.1  ATI Technologies Inc OHCI USB Controller #2 [1002:4348]
           +-14.0  ATI Technologies Inc SMBus [1002:4353]
           +-14.1  ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
           +-14.3  ATI Technologies Inc Unknown device [1002:434c]
           +-14.4-[0000:02-07]--+-00.0  Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
           |                    +-02.0  Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320]
           |                    +-03.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
           |                    +-04.0  Texas Instruments PCI1620 PC Card Controller [104c:ac54]
           |                    +-04.1  Texas Instruments PCI1620 PC Card Controller [104c:ac54]
           |                    +-04.2  Texas Instruments PCI1620 Firmware Loading Function [104c:8201]
           |                    +-07.0  NEC Corporation USB [1033:0035]
           |                    +-07.1  NEC Corporation USB [1033:0035]
           |                    \-07.2  NEC Corporation USB 2.0 [1033:00e0]
           +-14.5  ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
           \-14.6  ATI Technologies Inc IXP AC'97 Modem [1002:434d]

0000:00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
	Subsystem: ATI Technologies Inc Unknown device [1002:1234]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 64
	Region 0: Memory at f6000000 (32-bit, prefetchable)
	Region 1: Memory at f4000000 (32-bit, non-prefetchable)
	Capabilities: [a0] AGP version 3.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>

0000:00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f4100000-f41fffff
	Prefetchable memory behind bridge: f8000000-fbffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

0000:00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01) (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc Unknown device [1002:434c]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f4001000 (32-bit, non-prefetchable)

0000:00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01) (prog-if 10 [OHCI])
	Subsystem: ATI Technologies Inc Unknown device [1002:434c]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f4002000 (32-bit, non-prefetchable)

0000:00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 16)
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: I/O ports at 8040
	Region 1: Memory at 38000000 (32-bit, non-prefetchable)

0000:00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349] (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 255
	Region 0: I/O ports at 01f0
	Region 1: I/O ports at 03f4
	Region 2: I/O ports at 0170
	Region 3: I/O ports at 0374
	Region 4: I/O ports at 8060

0000:00:14.3 ISA bridge [0601]: ATI Technologies Inc Unknown device [1002:434c]
	Subsystem: ATI Technologies Inc Unknown device [1002:434c]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

0000:00:14.4 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:4342] (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=69
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: f4200000-f42fffff
	Prefetchable memory behind bridge: 30000000-37ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

0000:00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at f4003000 (32-bit, non-prefetchable)

0000:00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01) (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at f4003400 (32-bit, non-prefetchable)

0000:01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+ DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f8000000 (32-bit, prefetchable)
	Region 1: I/O ports at 9000
	Region 2: Memory at f4100000 (32-bit, non-prefetchable)
	Capabilities: [58] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=7 SBA+ ITACoh- GART64- HTrans- 64bit+ FW+ AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026] (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4208000 (32-bit, non-prefetchable)
	Region 1: Memory at f4200000 (32-bit, non-prefetchable)
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

0000:02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Hewlett-Packard Company NX9500 Built-in Wireless [103c:12f4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at f4204000 (32-bit, non-prefetchable)

0000:02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at a000
	Region 1: Memory at f4208800 (32-bit, non-prefetchable)
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4209000 (32-bit, non-prefetchable)
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 3c000000-3ffff000
	I/O window 0: 0000a800-0000a8ff
	I/O window 1: 0000ac00-0000acff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin B routed to IRQ 10
	Region 0: Memory at f420a000 (32-bit, non-prefetchable)
	Bus: primary=02, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

0000:02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device [103c:006b]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 255
	Region 0: I/O ports at a400
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:07.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation Hama USB 2.0 CardBus [1033:0035]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (250ns min, 10500ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f4206000 (32-bit, non-prefetchable)
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:07.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43) (prog-if 10 [OHCI])
	Subsystem: NEC Corporation Hama USB 2.0 CardBus [1033:0035]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (250ns min, 10500ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at f4207000 (32-bit, non-prefetchable)
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:02:07.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04) (prog-if 20 [EHCI])
	Subsystem: NEC Corporation USB 2.0 [1033:00e0]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (4000ns min, 8500ns max), Cache Line Size: 128 bytes
	Interrupt: pin C routed to IRQ 11
	Region 0: Memory at f4208c00 (32-bit, non-prefetchable)
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-





So um, I'm starting to thik now there isn't a VT1211 after all. No idea why some programs think I have it.

That SMbus looks interesting, I'll keep playing around.

---

### Post by entropico on 2008-01-17
Ok Scratch all that...

I thin the reason the Fan speed can be controlled even when the CPU is not functioning, is because it is controlled by an ACPI Embedded Controller.

Looking at the Windows Device Manager I can see there is such a controller on the ISA bus listening on IO ports 66 and 66.

It follows a standard layed out in the ACPI spec.... fan controll should be possible with linux ACPI suuport??

I found a temp monitor program for windows that uses the standard ACPI termal zone stuff, it works! Only such program I found that works. All the others detect a chip I dont think I have and , in any case, don't work.

So, this embeded controller is possibly the KBC firmware mentioned in the bios. (maybe)
In any case, ACPI and it's compliant controllers seem to hold the secrets, even if they are a part of a larger SouthBridge or other IC which may not have an available datasheet.

I'll keep this thread updated with whatever I may find next.

---

### Post by entropico on 2008-01-17
I've looked further into why many tmep monitor programs failed to get readings.

From SpeedFan 4.33
Win9x:NO  64Bit:NO  GiveIO:YES  SpeedFan:YES
I/O properly initialized
Linked ISA BUS at $0290
Linked ATI IGP SMBUS at $8040
Scanning ISA BUS at $0290...
SuperIO Chip=VIA VT1211
Linked ISA (flat) BUS at $EC00
Scanning AtiIgp SMBus at $8040...
SMART Enabled for drive 0
Found HITACHI_DK23FA-60 (60.0GB)
End of detection

Scanning SMBus at $8040...
Decoding DIMM #0
 Memory type is DDR
 Module Rows : 2
 Levels : 2.5V
 Parity : NO PARITY
 Refresh Rate : 7.8us
 Total Size : 256MB
Decoding DIMM #1
 Memory type is DDR
 Module Rows : 2
 Levels : 2.5V
 Parity : NO PARITY
 Refresh Rate : 7.8us
 Total Size : 256MB

Scannig SMBus at $8040
 device found at $50 $51 $69

From Hmonitor:

SMbus at $8040
ISA Port $290
Main Chip VT1211

From Sensors View Pro 3.1
Vt1211 (not much explaination or detail)

From Notebook Hardware Controll 2.0r06:
No chip Level info, However thi is the only program that correctly read the CPU temp.
I think all the other programs try to read the chip directly, while NHC has some windows API do the work.
NHC does not read the correct CPU clock frequency (or atleast it is contadicted by 3 other programs, and sbserved heat output)

Windows device manager (and this is the HP OEM version factory installed on the laptop) does not list anything on port $290 despite sensor programs 'detecting' something there.
$8040 is listed as ATI SMBus
$62 and $66 are the ACPI compliant controller's ports

So... now... time to see what the KBC firmware does and to read more of the ACPI spec.

---

### Post by Whiffle on 2008-01-17
Have you tried lm-sensors and sensors-detect?

---

### Post by neilslade on 2008-01-19
First, I appreciate Entropico's efforts--  however, for years I've simply manually controlled my desktop noise by installing decent fans and using speed controllers. And my desktop nosie is ZILCH, despite 3 hard drives, a P4 3.2GHz,and  a big *** video card. 

So-- I solved my problem by simply switching my
Automatic fan transmision" to a Manual Transmission setup simply using a physical fan speed controller torn out of a Zalman laptop Cooling pad, and rewired both my fans to run off 5V from a USB plug. All fan speed is manually controlled now through a simply dial mounted on the side (internally) of the case in a spare drive bay area.  

ALL photos below text.



THIS MODIFICATION IS FOR PEOPLE WITH EXPERIENCE or GUTS. It will take a couple of hours of work-- now that I've figured all this stuff out for anyone willing to give it a shot.


FIRST- DOWNLOAD THE SERVICE MANUAL FROM HP or your Manufacturer to dis-assemble your computer. You will NEVER be able to figure out how to take your laptop apart without it, no way, no how. These things are like Chinese puzzles-- here's the download for HP ZV5000 service manual\:
[http://h10032.www1.hp.com/ctg/Manual/c00212209.pdf](http://h10032.www1.hp.com/ctg/Manual/c00212209.pdf)

 It should be reproducible if necessary with other models or brands, if you do your homework as to fan layout, etc. Obviously software fan speed control is going to be way easier-- providing you can figure it out or find one that works-- alas, there appears to be no such thing for the HP ZV5000, a particularly noisy machine stock configuration with a P4.

Here are my results with my HP ZV5000-a Pentium 4 3 GHZ ,2GB RAM,  100GB HHD laptop.  now, silent as the ocean waves, 30 miles away.

I tried in vein to use software to control the fan speed, and there were no applications that did this. Speedfan could not, and I couldn't find anything else to work. Modifying the ACPI is WAY above my head- so was out.


1) I did try the Zalman Laptop Cooling Pad. [http://www.zalman.co.kr/usa/product/view.asp?idx=224&code=030]("http://www.zalman.co.kr/usa/product/view.asp?idx=224&code=030")

{Although it looks nice, is extremely quiet and virtually inaudible, it does ABSOLUTELY NOTHING to cool down the temperature of either the HHD or the CPU.  It does indeed blow some air across the bottom of my laptop- but alas, my ZV5000 bottom does not get hot like some other laptops I've had and noticed.

Users of such machines may see a good result with the Zalman. However, the design of this HP, and probably many others, uses significant heat sinks and fins, and the air is blown out the side of the laptop case, not out the bottom-- so blowing air across the bottom, or into the bottom fan inlets of such a designed laptop, as I've now noted, won't do any good at all.

For a moment I thought increasing the airflow into the two fan port holes on the bottom would help, but alas, even when I stuck a fan blowing additional air right into these openings, nothing cooled down further.

I measured the temperature with and without the cooling pad. Even at high speed, it has zero effect. Some people have reported good results. I had absolutely none, without question. It does allow the laptop to remain at a nicer angle for typing however. It also would allow better ventillation if you have the laptop in bed or on an uneven surface.

BUT, my money was not wasted ($50 from newegg)- since the controller from the Zalman was superior to my micro controller - 1) had a power LED 2) added a USB port 3) had much smoother speed control variance and more precise control over RPM over a longer sweep rotation- very important.


2) I did appreciate the nearly inaudible fan noise from the Zalman-- only in a completely silent environment can you hear anything at all- like all my other Zalman fans, which I LOVE. So I got to thinking that I could take the fans from the Zalman, and swap with the noisy fans in my laptop- being that they  are the right size, 5VDC, as well as LATERALLY blowing fans (not like a typical case fan which blows air away  perpendicularly from the fan- lateral fans blow the air sideways.


I removed the fans from the Zalman, but before I finished trying to modify them for my laptop, it occurred to me that perhaps they were making less noise just because they had reduced RPM.

So, I tested the stock fan replacement (Sunon fans, MAGLEV bearings- which are extremely quiet, as are the ADDA hypro bearing fans found in the Zalman pad) through the Zalman pad speed controller...

EUREKA!! Sure enough, the Sunon stock fan was even quieter than the ADDA run at the same speed.

Why?  It has a smaller fan blade area displacement.

Getting the ADDA/Zalman fans to fit was proving to be a lot of hassle since they were marginally taller tthan the stock fans-- so given that the stock fans were actually quieter run through the Zalman controller-- it then made perfect sense to simple control the fans through the Zalman laptop cooler speed control and leave the stock fans where they were.

The only question remained was whether or not reducing the RPM with the speed controller would hamper the cooling, and make things dangerously hot-- either long or short term, and under load or not.

The one thing to keep in mind, is that in order to run the fans through the Zalman controller, you have to power the fans through another 5V source other than the regular motherboard fan pin connectors.

This is because both fans are temperature controlled, and the board varies the fan speed according to the temperature of the CPU and other.

This also means cutting and clipping the fan wires from the plugs-- so you have to be committed to this method, otherwise, you will have some micro soldering to do to reconnect the plug if you change your mind later-- but I don't think you will...

Fortunately, the ZV5000 has 3 USB connectors, any of which can be tapped to power the fans, and the Zalman runs BOTH fans on one 5V supply.

For testing, I just used a short USB cord, clipped the end opposite the flat plug, and connected the black (ground) and red (+5V) leads first to one fan, then both.

VOILA!! It worked like a charm.

The first thing I noticed was that the highest fan speed is in fact reduced a bit, and then you can adjust and reduce even further finally down to fan off.

I then connected BOTH FANS.  They must be connected IN PARALLEL rather than series, otherwise, you will not have enough voltage to run both fans. I..e this means connect the black wires from both fans together, and then this connects to the black wire from the Zalman controller. You then connect the red wires of both fans, and this connects to the red wire of the controller.

You can connect only one, the main center fan, but then, the CPU side fan will come off and on, and it makes far more noise than both fans running slowly and quietly all the time.  I suggest connecting the center fan first and testing, then connecting both fans. If you only have one fan in your computer, obviously, just connect this one.

The motherboard uses a yellow wire to monitor fan speed, and this will be clipped, and taped off, and it will not be used any longer on both fan plugs. In fact, you should remove the cut white plugs entirely from the board, they are not needed for this mod.

You will need to remove to heat sinks and CPU to access the lead wires for the side CPU fan. Be VERY careful removing the headsink assembly-- because very likely the thermal compound will be sticky and the CPU will lift off with the heat sink.

**[COLOR="Red"]GET SOME ARTIC SILVER 5 to replace the stock thermal compound.[/COLOR]** This is the best stuff made, I've read every single review of thermal compounds. It is $10 at any Radio Shack. Use a very thin layer, spread with a warm finger evenly. MORE IS NOT BETTER. THINK THIN!! Clean the CPU and bottom of the heat sink with denatured alcohol and a lint free cloth, then apply. Artic Silver will possibly reduce the temp of the CPU of up to 8 - 10 degrees. It takes a few hours before this stuff reaches its best thermal conductivity as the particles find optimum position-- after a few hours of use, just watch your temp drop.

WARNING!!!!!!!!!!: When you replace the CPU be EXTREMELY EXTREMELY CAREFUL not to bend any of the pins. If you break a pin, you are screwed and will have to replace the CPU. If the CPU does not come off with the heat sink, make sure and UNLOCK THE CPU with the turn screw on the plastic mounting (counter clockwise) before trying to lift off. When you replace, it should take just a tiny amount of pressure to get it to seat-- then relock the mounting (clockwise).

When you retighten the heat sink screws, alternated every other screw, tightening a little bit at a time to keep even pressure, like on the nuts on a car wheel. Work your way around  #1, 3, 2, 4, 1, 3, 2,4  until everything is as tight as it will go. Don't strip the screw heads, use the right size screwdriver.

BLOW OUT THE HEATSINK FINS with air. Make sure there are no dust bunnys hibernating in your laptop heatsink fins, including the extra aluminum port that sits in between the fins. (Easy to miss that one).

Run the wires from each fan under the fan assembly frame above the mother board. Be careful and don't knock anything. Stay away from screw holes, because when you put the case back together, you don't want to screw through a wire.

You will have to find a place to house the fan speed control-- hopefully, you will have an un-used aread in your case where it will fit.

I put mine in the spare drive bay area above my DVD drive-- it was the PERFECT size.

Make sure ALL SOLDER JOINTS and anything conducting power is insulated from contact with any metal-- say, the top of the DVD drive. What, you want to fry your computer or what?!?!

I actually modified the side of the spare bay and cut and reglued the control slots from the Zalman cooler, and when I was done-- it looked like factory. See the photos. This required very careful cutting of plastic, gluing, and application of epoxy to really glue it permanently, and then spraying with black paint. Don't rush, or it will look like crap.

If you can not find any place to put the Zalman controller, you may want to use the smaller micro controller as shown above, which will fit in a much tighter spot like inside a memory card bay. Bear in mind, it may be a bitch and way too much work to adjust the speed with that kind of set up.

With the Zalman controller mounted with the controls accessable on the outside of my laptop case-- its perfect-- I can adjust the speed any time instantly. The LED indicates power, and to boot-- I've gained an extra USB port!

Right now, to use the controller, I must plug in a USB cable when the computer is on as shown-- otherwise, there is no power to the fans. In the future, I will simply hardwire this power connection internally so it will always be connected, and then I will actually have 5 external USB ports on my laptop.  Overkill, but what the heck.

The fan control will indeed slow the fans down to STOP, so use a bit of white paint or liquid paper, and place a mark on the rotary speed control showing you the slowest speed you can run, otherwise you'll have to turn your computer over to visually verify if the fans are actually running or not-- this is so quiet.


Be VERY carefully putting the case back together-- it will be very easy to cut or smash your new non-stock wires. Go slow, don't force anything and you'll be fine. Test immediately and visually to make sure both fans are running.  first time I re assembled my case, I smashed a wire, and one fan didn't work-- i.e. temperature immediately hit 70C within minutes--- not good. With both fans quietly running-- 50C no sweat.

With this setup, both fans will run continuously all the time-- but slower than stock, and ultimately will cool more efficiently and considerably  quieter.

THE RESULTS:

My laptop runs COOLER THAN EVER!!!

At idle, the machine runs at 48-52C, even doing email or simple word processing.

[B]When the fans are both going full blast, it is  quieter than stock. But I can reduce the fan speed to virtually silent operation, and the computer even under load will operate under completely acceptable temperatures from 54- 62C.  Under very heavy load, I can crank the fans full blast, and I've never seen it hit 69C.  
[/B] 

In the coffee shop today, the fans going full speed could not be heard AT ALL. What a huge change from the stock fan speed configuration. Ow. Once you have a silent computer, you can never go back and be happy.

Think of a manual speed control like you would a stick shift on your car. YOU are under control at all times.

Doing so, you can actually operate your computer cooler, MUCH more quiet, and increase the life of your machine.

ALWAYS monitor the temperature with a continuous visible readout in your system tray.

My favorite monitoring free program is Notebook Harward Control at [http://www.pbus-167.com/]("http://www.pbus-167.com/")
this is a FANTASIC free program that lets you adjust all kinds of things, including CPU clock, readouts, and other things that will ultimately have an impact on your fan speed, noise, and battery life. Highly recommended-- in fact, don't even DREAM of messing with your fan speed without this program, and turn it on EVERY time you turn on your computer if you are manually controlling fan speed.

Every 6-8 months take the case off and blow out your heat sink and cooling fins, as accumulated dust will render all of your work and your fan mods non-operational.

[IMG]http://www.neilslade.com/gifs/fan1.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan2.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan3.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan4.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan5.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan6.jpg[/IMG]<P>
[IMG]http://www.neilslade.com/gifs/fan7.jpg[/IMG]<P>


Cheers-- good luck-- be careful, go slow and delicate-- and have fun...
Neil
[http://www.BrainRadar.com](http://www.BrainRadar.com)

[http://www.EasyPaintYourCar.com](http://www.EasyPaintYourCar.com)
[http://www.InkJetHelper.com](http://www.InkJetHelper.com)
[http://www.MyOwnPublishing.com](http://www.MyOwnPublishing.com)
[http://www.neilslade.com/Papers/Painting.html](http://www.neilslade.com/Papers/Painting.html)
[IMG]http://www.neilslade.com/gifs/neil.jpg[/IMG]

---

### Post by neilslade on 2008-01-20
A little follow up here--  

LAPTOP COMARISON:

I just bought a little used Dell D600 Latitude for a friend today, and have it next to my ZV5000.  It is a Celeron M 1.6 Ghz with 750MB ram--  well, it certainly runs virtually silent and relatively cool CPU (under 48C) all of the time, and 1.6 GHZ is nothing to sneeze at.

But, the 14" screen is not particularly bright, and with onlya max resolution of 1024X768.

The top and bottom of the case gets quite warm to the touch, and on one's lap would indeed become uncomfortable before long.

It is nice and small, so a rather convenient size, utilitarian, good for travel, but nothing terribly exciting.
$400 refurbished.  But is good to show how quiet a mobile processor can be in a modest set up.

By comparison

My ZV5000 is a true desktop replacement, P4, 3 GHZ, extremely bright and large widescreen with noticably sharper 1280 X 800 resolution. 

Today, the second day after fan installation- and with two days on the Artic Silver 5 (takes five days to set in, so I'm told)- under 100% CPU load, the hottest reading I got with my fans on full (which is actually far below full stock RPM) was 67C)-- which is quite respectable considering the load and RPM.

Under typical load running a defrag program, I'm seeing 54C which is just fine.  
If I run a video under You tube, it will jump to 57-58C  When listening to music on the Youtube video, no fan sound can be heard, even at full speed.

Reducing fan speed significantly reduces the fan whir but results in various  temperature increases (but all between 2-8 degrees increase) depending on the amount of attnuation.  It will be interesting to see temperatures after a week of seating in of the artic silver.

---

### Post by neilslade on 2008-01-22
THAR SHE BLOWS!!!!

[IMG]http://www.neilslade.com/gifs/newlap.jpg[/IMG]

Well, I was faced with what looked like more AC jack problems-- so once again I disassembled in order to finally soldier that sucker in properly-- well it LOOKED okay--

and while I was at it, decided to internalize all the power leads to the fan control so I wouldn't have to connect any USB cables outside the machine. Did that, but it took a while to figure out that I needed THREE connections-- looking down from a typical USB plug, you need the left edge, the second from the left, for the 5V-- but the control from the zalman also needs to have the metal sheld around the USB plug case grounded from a source, so I just ran a case ground wire and soldered it to the top of the USB plug inside the control box. Without that, nothing turns on. That's why pluging in a cable works-- the cable sheld naturally provides the ground, with the power on two of the inside leads. Without the ground- zip. I didn't realize until after I connected the power and nothing happened.

I cannot stress how much care must be taken soldering inside a laptop-- one small drop of solder in the wrong place, on a board connection-- you've ruined your computer, and you may not be able to find it.
Same thing for small little bits of wire, or dropped bolts.

This is really hazardous work, and frankly, IT IS INSANE unless you are extremely diligent, clean and careful.

I have total respect for laptop repair people now, and laptop construction. These are absolutely astonishing machines. And amazing how tough they are the way people just toss these things around. 

I tell you, I sure will handle mine with more care and respect from this point.

Anyway-- after I got the internal fan power sorted out, and got the case all back together-- the LCD screen wouldn't turn on.

OH CRAP!*!&@&!&@


It was just that I forgot to put in my RAM memory. Oops.

Did that, Screen back on.

Everything looked okay till I discovered the AC power was not better than before. Even worse.

So what was it?

I finally took my test meter to the plug itself on the CORD.  The cord was shorted out right at the plug end, it was never the jack on the board and laptop at all!!

I resoldered the plug on the cord, and it works better, but I really need a new plug--- off to radio shack.

Well at least I have a new heavy duty jack on the computer and that should last considerably longer than the notorious poor HP jacks.

So anyway, that's my adventure..

I had to take off the heatsink again this dis-assemble, and replace the artic sivler 5 again, but its running a nice cool 52C typing here.

One note-- when I removed the heatsink, the surface was remarkably rough, not at all like the quality surfaces I've seen on aftermarket heat sinks on Zalman and other cooler arrangements. 

So I took some 1500 and 2500 grit waterproof sandpaper and a small hard block and gently wet sanded the surface of the area that contacted the CPU a bit smoother, got out some of the obvious scratches and imperfections they were tool lazy to remove at the factory. This should help in heat transfer, and I was rather shocked to see this on a retail $2000 machine. Be careful doing this, only try to take off a mini-microscopic amount at most-- just smooth it out barely-- it would be very easy to make things worse. It has to be totally level.

Then smooth on a very thin layer of Artic Silver 5, and again, tighten the screws diagonally slowly, a few turns at a time, alternately in an X pattern, not clockwise, to keep pressure more even.

Good luck if you are crazy enough to try this mod.

But if you are-- you'll love the reduction in noise, and the ability to run the fans exactly as you like and get better cooling and extend the life of this monster zv5000.

Neil
Neil
[http://www.BrainRadar.com](http://www.BrainRadar.com)

[http://www.EasyPaintYourCar.com](http://www.EasyPaintYourCar.com)
[http://www.InkJetHelper.com](http://www.InkJetHelper.com)
[http://www.MyOwnPublishing.com](http://www.MyOwnPublishing.com)
[http://www.neilslade.com/Papers/Painting.html:guitar:](http://www.neilslade.com/Papers/Painting.html:guitar:)

---

### Post by neilslade on 2008-01-22
The Laptopjack Song

I'm a Laptopjack, and I'm okay.
I sleep all night. I work all day.

I cut down trees. I eat my lunch.
I go to the lavatory.
On Wednesdays I go shoppin'
And have buttered scones for tea.

Chorus:He's a Laptopjack, and he's okay.
he sleeps all night and he works all day...

I cut down trees. I skip and jump.
I like to press control, alt, and delete.
I put on women's clothing
And hang around in bars.

Chorus:He's a Laptopjack, and he's okay.
he sleeps all night and he works all day...

I cut down trees. I wear high heels,
Suspenders, and a bra.
I wish I'd been a girlie,
Just like my dear Mama.

Chorus:He's a Laptopjack, and he's okay.
he sleeps all night and he works all day...


[IMG]http://www.neilslade.com/gifs/mounties.jpg[/IMG]

AND NOW THE MOVIE VERSION!!!
[URL="http://www.youtube.com/watch?v=HooUO-PkG0Q"][COLOR="Red"]
http://www.youtube.com/watch?v=HooUO-PkG0Q[/COLOR][/URL]

*************

Neil
[http://www.BrainRadar.com](http://www.BrainRadar.com)

[http://www.EasyPaintYourCar.com](http://www.EasyPaintYourCar.com)
[http://www.InkJetHelper.com](http://www.InkJetHelper.com)
[http://www.MyOwnPublishing.com](http://www.MyOwnPublishing.com)
[http://www.neilslade.com/Papers/Painting.html](http://www.neilslade.com/Papers/Painting.html)

---

