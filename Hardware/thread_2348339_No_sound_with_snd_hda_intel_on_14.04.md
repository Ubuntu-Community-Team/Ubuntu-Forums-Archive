---
title: "No sound with snd_hda_intel on 14.04"
date: 2017-01-02
forum: Hardware
---

### Post by jlumpe on 2017-01-02
Just a few days ago I stopped getting sound on my Asus F555LA laptop. It had been working fine previously and I hand't made any changes to system configuration or installed any updates or software that I know of before it stopped.

I'm seeing the following error messages:

```

[    2.820152] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.839888] snd_hda_intel 0000:00:1b.0: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[    6.843896] snd_hda_intel 0000:00:1b.0: No response from codec, disabling MSI: last cmd=0x000f0000
[    7.847941] snd_hda_intel 0000:00:1b.0: Codec #0 probe error; disabling it...
[    8.859983] snd_hda_intel 0000:00:1b.0: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0000
[    8.860297] hdaudio hdaudioC1D0: no AFG or MFG node found
[    8.860300] snd_hda_intel 0000:00:1b.0: no codecs initialized

```

I was also getting a lot of these:

```

[   15.803752] snd_hda_intel 0000:00:03.0: spurious response 0x0:0x0, last cmd=0x770503

```

which for some reason I haven't seen the last few times I've booted (after removing the changes below).

After reading the advice of some people with similar issues I've tried adding:

```

options snd-hda-intel single_cmd=1
options snd-hda-intel probe_mask=1

```

to a file in /etc/modprobe.d but it didn't seem to have any effect. I've also tried ```
options snd-hda-intel model=basic
``` in addition to those two, as well as just ```
options snd-hda-intel probe_only=0,1
``` on its own.

Some more system info:


```

$ uname -r
4.4.0-57-generic

```

```

$ lspci -vv

00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:19ad]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 51
    Region 0: Memory at b221c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee003d8  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag- RBE-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
    Kernel driver in use: snd_hda_intel


00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device [1043:19ad]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at b2218000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Kernel driver in use: snd_hda_intel

```

The module parameters also look sorta weird:

```

$ grep '' /sys/module/snd_hda_intel/parameters/*


/sys/module/snd_hda_intel/parameters/align_buffer_size:-1
/sys/module/snd_hda_intel/parameters/bdl_pos_adj:32,1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
/sys/module/snd_hda_intel/parameters/beep_mode:N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
/sys/module/snd_hda_intel/parameters/enable:Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
/sys/module/snd_hda_intel/parameters/enable_msi:-1
/sys/module/snd_hda_intel/parameters/id:(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
/sys/module/snd_hda_intel/parameters/index:-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
/sys/module/snd_hda_intel/parameters/jackpoll_ms:0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
/sys/module/snd_hda_intel/parameters/model:(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
/sys/module/snd_hda_intel/parameters/patch:(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
/sys/module/snd_hda_intel/parameters/position_fix:-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
/sys/module/snd_hda_intel/parameters/power_save:0
/sys/module/snd_hda_intel/parameters/power_save_controller:Y
/sys/module/snd_hda_intel/parameters/probe_mask:-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
/sys/module/snd_hda_intel/parameters/probe_only:0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
/sys/module/snd_hda_intel/parameters/single_cmd:N
/sys/module/snd_hda_intel/parameters/snoop:-1

```

---

