---
title: "ICH7 Audio / Toshiba Laptop / 15.04"
date: 2015-07-24
forum: Hardware
---

### Post by phil-lchost on 2015-07-24
Fix from later in the thread: Booting with pci=use_crs fixed this issue.

Hi,


I've had 15.04 on a Toshiba Portege for a little while now that I basically use as an SSH terminal most of the time, and only recently realised that I have no sound hardware available - only the dummy driver is present in my mixer.


It's ICH7 based, so I had rather expected it would work out of the box, and it certainly *seems* like it's being claimed in lspci:

```

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Device 0001
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 29
        Region 0: Memory at 100000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0300c  Data: 41a2
        Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0
                        ExtTag- RBE-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=01
                        Status: NegoPending- InProgress-
                VC1:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=1 ArbSelect=Fixed TC/VC=80
                        Status: NegoPending- InProgress-
        Capabilities: [130 v1] Root Complex Link
                Desc:   PortNumber=0f ComponentID=02 EltType=Config
                Link0:  Desc:   TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
                        Addr:   00000000fed1c000
        Kernel driver in use: snd_hda_intel

```

I've also tried
```

options snd-hda-intel model=toshiba

```


in /etc/modprobe.d/alsa-base.conf


I've tried adding my user to the audio group:
```

audio:x:29:pulse,phil

```

and still, no luck (this as root, even) with getting a usable device:
```

# sudo aplay -l
aplay: device_list:268: no soundcards found...

```



Any suggestions for what I can try next, please?

Phil

---

### Post by dino99 on 2015-07-24
i have the same ich7 chipset on an old mobo; sound was working as expected, and suddenly, a couple months back, the sound failed; After asking pulseaudio devs, they told me to check: bios setting, be sure to set 'hda' setting (mine was working previously with 'ac97'), then check the jack(s) they needs to be plugged stricty by color.

Now sound works again; of course paref & pavucontrol can be used to adjust the settings (but usually the system identify the hardware and set the paramaters as expected after a cold boot)

---

### Post by phil-lchost on 2015-07-27
Hi Dino

Thanks for your input!

Unfortunately, as this is a laptop (or certainly, on this particular laptop) no options in the BIOS for the audio chipset whatsoever :(

Phil

---

### Post by Yellow Pasque on 2015-07-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by phil-lchost on 2015-08-01
Hi!

> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a](http://www.alsa-project.org/db/?f=765ebb6d1347e57bab7bace7b49a92e6e5d0391a)

Thanks in advance for any advice you can offer!

---

### Post by Yellow Pasque on 2015-08-01
[https://bugzilla.kernel.org/show_bug.cgi?id=99221](https://bugzilla.kernel.org/show_bug.cgi?id=99221)

Try booting with 'pci=use_crs' as the bug reporter did.

---

### Post by phil-lchost on 2015-08-03
> **Temüjin said:**
> 
Try booting with 'pci=use_crs' as the bug reporter did.

This works. Great catch, thanks! (although, it's broken my volume wheel, it seems!?)

Now the only thing I have to be sad about is my 3G modem/rfkill not working (doesn't look like that's going to be a goer, since the toshiba_acpi patch required was removed a long time ago).

---

