---
title: "Toshiba Satellite P875"
date: 2012-08-25
forum: Hardware
---

### Post by JaySeeJC on 2012-08-25
I want to say I am in no way a linux beginner. I am not afraid of the command line and in fact prefer it.
I recently got a new Toshiba Satellite P875. I would like to describe the issues/annoyances i have come accross in my kubuntu install.

1. FIXED It has a multi-touch trackpad and seems to be treating it like a mac trackpad, with all the multitouch gestures. I would like to disable most of these gestures, mainly only keeping the two-finger touch to scroll. I would like to also be able to turn on/off with a hotkey, as I often bump it while typing.

2. It also has both intel and nvidia gpus, but X seems to only be using intel. If possible, I would like a script to be able to switch between the two, otherwise i would like to figure out how to configure it to use the nvidia gpu instead of the intel.

3. I picked up a small wireless mouse as well. It's no-name (Vibe) Model No. M-902. It seems the wireless receiver that came with the mouse isn't being detected by the kernel. "lsusb"s output doesn't change when the receiver is plugged in. 

4. The laptop also comes with a hdmi port. I don't have a hdtv to use with it but I was wondering if any special config would be required to get it to work should i come across something to output it to. 

5. FIXED The speakers don't work but the  headphone jack does. alsamixer only shows the "Master" and "PCM" output  channels, and no other audio cards.  pavucontrol also only shows one  output, analog output.

6. Though I say I'm not new to linux, I'm ew to having a laptop and so any other general laptop advise would be much appreciated.7

Thanks in advance for the help, I'm sure you guys can help me out.

---

### Post by SeijiSensei on 2012-08-25
> **JaySeeJC said:**
> 1. It has a multi-touch trackpad and seems to be treating it like a mac trackpad, with all the multitouch gestures. I would like to disable most of these gestures, mainly only keeping the two-finger touch to scroll. I would like to also be able to turn on/off with a hotkey, as I often bump it while typing.

Did you look at the settings in System Settings > Input Devices?  I have no idea whether you can turn any of this off and on, but that's the place to look.

> 2. It also has both intel and nvidia gpus, but X seems to only be using intel. If possible, I would like a script to be able to switch between the two, otherwise i would like to figure out how to configure it to use the nvidia gpu instead of the intel.

Look into the [Bumblebee Project]("http://bumblebee-project.org/").

> 3. I picked up a small wireless mouse as well. It's no-name (Vibe) Model No. M-902. It seems the wireless receiver that came with the mouse isn't being detected by the kernel. "lsusb"s output doesn't change when the receiver is plugged in. 

I use Logitech products exclusively because they routinely work on Linux without any fuss.

> 4. The laptop also comes with a hdmi port. I don't have a hdtv to use with it but I was wondering if any special config would be required to get it to work should i come across something to output it to.

Once you have support for the NVIDIA card configured, you can use its associated utility to select the output device.

---

### Post by JaySeeJC on 2012-08-25
> Look into the [Bumblebee Project]("http://bumblebee-project.org/").The bumblebee project looks quite interesting, but doesn't seem to be working for my setup. Running "optirun glxspheres" returns the following error, running as root or not:
```
[ 1953.142930] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 1953.142989] [ERROR]Aborting because fallback start is disabled.
```The lspci -vv output of the nvidia and intel cards is as follows:
```
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fb12
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 7
    Region 0: Memory at d8000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at c0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 3000 [disabled] [size=128]
    Expansion ROM at c2000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis+
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -3.5dB
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Capabilities: [128 v1] Power Budgeting <?>
    Capabilities: [600 v1] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel modules: nouveau, nvidiafb

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fb12
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at da000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at d0000000 (64-bit, prefetchable) [size=128M]
    Region 4: I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee3000c  Data: 4179
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [a4] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: i915
    Kernel modules: i915


```> I use Logitech products exclusively because they routinely work on Linux without any fuss.I agree, but I was pressed for time and it was the only mouse i could afford at the time, as I only had cash on me. I'm currently using a wired logitech desktop mouse.

Another quirk that I noticed is that the speakers don't work but the headphone jack does. alsamixer only shows the "Master" and "PCM" output channels, and no other audio cards.  pavucontrol also only shows one output, analog output.

My above post will be updated to reflect this new issue.

---

### Post by SeijiSensei on 2012-08-26
> **JaySeeJC said:**
> Another quirk that I noticed is that the speakers don't work but the headphone jack does. alsamixer only shows the "Master" and "PCM" output channels, and no other audio cards.  pavucontrol also only shows one output, analog output.

Again you should be using the applications in System Settings if you're using KDE.  Check SS > Multimedia > Phonon and see how your devices are configured.

---

### Post by JaySeeJC on 2012-08-26
> **SeijiSensei said:**
> Again you should be using the applications in System Settings if you're using KDE.  Check SS > Multimedia > Phonon and see how your devices are configured.
That wasn't the problem. Compiling an updated kernel fixed the audio problem. Currently running 3.2.5. Bumblebee is still giving me the same error. I'll do a bug report to them. I've realized that this laptop is a satellite P870 as well. 
```
baseboard-manufacturer: TOSHIBA
baseboard-product-name: Portable PC
baseboard-version     : MP
system-manufacturer   : TOSHIBA
system-product-name   : Satellite P870
system-version        : PSPLBC-02L00R
bios-vendor           : Insyde Corp.
bios-version          : 1.50
bios-release-date     : 07/02/2012

```

Please note I am very grateful for all your help so far [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"). I really don't mean to sound stuck up or anything, I just really want to get the most out of this machine and that's simply not possible running window$.

---

### Post by JaySeeJC on 2012-08-26
Found a fix partially for the touch pad here:
[http://nialldonegan.me/2007/05/21/disabling-synaptic-touchpad-while-typing-in-linux/](http://nialldonegan.me/2007/05/21/disabling-synaptic-touchpad-while-typing-in-linux/)

Currently looking into the multitouch customization.

---

