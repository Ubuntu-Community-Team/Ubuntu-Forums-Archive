---
title: "GDM Reset When Resolution Changed"
date: 2008-11-03
forum: General Help
---

### Post by mlissner on 2008-11-03
I just "upgraded" to Ibex, and since then, when I change from using my external monitor as a display to using my laptop screen, GDM is reset, and I am logged out of the computer.

My usual process is this: 
1 - open the screen resolution tool
2 - turn on my monitor screen at the correct resolution
3 - turn off my laptop screen
4 - press apply

At this point, display is generally switched from the laptop to the external monitor, no problem. The problem occurs later when I want to disconnect the monitor and go mobile again. In that case, the process is the same, except when I press apply (step 4), GDM is reset, and I have to log into the computer again. 

This is really frustrating because I switch from workstation to mobile regularly, and I didn't have this problem with hardy. Now I am constantly reopening documents & applications, which takes considerable time.

Any suggestions?

---

### Post by mlissner on 2008-11-05
Bump?

---

### Post by mlissner on 2008-11-24
No forum love. Double bump?

---

### Post by mlissner on 2008-12-08
Well, I've reinstalled the system in hopes that this was a problem caused by upgrading rather than one caused by bad drivers. That hasn't helped either. Does anybody have any ideas on how to track this down, or how to pin point what's causing the problem? In case it helps, my graphics card is: 

```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Lenovo Device 20b5
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+

```Thanks, and may the triple bump do the trick.

---

### Post by mlissner on 2008-12-09
yay, I finally figured this out. Turns out that since the hardy version, a change has been made that forces you to open your laptop screen before you make the setting change. 

So when you want to switch from external monitor back to laptop screen, first open the laptop, then do the switch on the external monitor, then disconnect the external.

Jeez. These kinds of changes can be a real pain to figure out by trial and error.

EDIT - Thanks for the help Forum!

---

