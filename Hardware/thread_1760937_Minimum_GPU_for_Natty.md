---
title: "Minimum GPU for Natty?"
date: 2011-05-17
forum: Hardware
---

### Post by rg4w on 2011-05-17
I see some laptops on the Ubuntu certification list which have only Intel integrated GPUs, but I had heard somewhere that one needs either AIT or NVidia to run Unity 3D.

What is the minimum GPU I can use for the full Unity experience?

I don't need strong gaming, but I do need full Unity.

Thanks in advance -

---

### Post by LinXNut on 2011-05-17
I have never really used Unity, but perhaps you can look here?

[http://unity3d.com/unity/system-requirements.html](http://unity3d.com/unity/system-requirements.html)

---

### Post by coffeecat on 2011-05-17
> **LinXNut said:**
> [http://unity3d.com/unity/system-requirements.html](http://unity3d.com/unity/system-requirements.html)

I think that's the wrong Unity.

@rg4w, I have a three-year old laptop with integrated Intel graphics and it runs Unity just fine. That's the Unity that comes with Ubuntu Natty. :wink:

---

### Post by kev77 on 2011-05-17
i'm using lubuntu 11.04 on a compaq f500, lovely and fast

---

### Post by rg4w on 2011-05-17
Thanks, but I was referring to the Unity in Natty (not the first time this ambiguity has caused confusion). :)

After more searching I managed to dig this up:
[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

> The following hardware have the required capabilities for Unity: 
[LIST]
[*]All GPUs released today by either NVidia, AMD or Intel.
[*]GPUs released by NVidia and AMD over the last 5 years.
[*]GPUs released by Intel after the GMA 950 (*).
[/LIST]
(*) Except for GPUs with no appropriate driver support or missing features.It's a good start, but still leaves open the question of whether a given system has all the features needed to run Unity.

I've been shopping for a new laptop, and have found finding all the compatibility requirements a bit overwhelming.

But even more so, what strikes me most is the number of machines that don't appear to be able to run Natty except in fallback mode, including the majority of systems sold at Costco, Target, and most other mainstream stores.

Makes me sad to consider the possibility of Ubuntu niching itself in the pursuit of cool graphics. :(

Given the info I found I'll mark this solved, though it would be nice to see Unity runnable on more, if not most, systems.

---

### Post by rg4w on 2011-05-17
Thanks for the additional info, guys.

@Coffeecat:  Which Intel GPU?

---

### Post by coffeecat on 2011-05-17
> **rg4w said:**
> @Coffeecat:  Which Intel GPU?

Fwiw, this is the relevant part of the output from lspci -vvv:

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device 9045
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 46
    Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at e140 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Sony Corporation Device 9045
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at d0400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
```I don't know whether "Mobile 4" equates to any of the GMA series, and wikipedia is unforthcoming on this. All I can say is that Natty Unity works well with it. Posting from my Sony laptop in Unity with the Intel graphics now.

---

### Post by rg4w on 2011-05-17
Thanks, Coffeecat.  Opens up my options...

---

