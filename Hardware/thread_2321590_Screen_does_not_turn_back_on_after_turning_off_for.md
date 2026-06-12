---
title: "Screen does not turn back on after turning off for inactivity, but suspend works fine"
date: 2016-04-23
forum: Hardware
---

### Post by unflavored on 2016-04-23
I have just installed 16.04 on a HP Compaq nc6000.  In System Settings -> Details, the graphics line says "Gallium 0.4 on ATI RV350".  The relevant line in lspci: "01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 / RV366660/M11 [Mobility Radeon 9600 (Pro) / 9700]"  

[SIZE=2] **The problem:** [/SIZE]
If the screen turns off due to inactivity, it will not come back on.    

I can only force it back on by closing the lid and going into suspend, then waking from suspend, because suspend works fine.    

Right now my workaround is to set "Turn screen off when inactive for: Never" but I'd like a better workaround or fix.  Please help me troubleshoot this.

---

### Post by unflavored on 2016-04-23
Correction: suspend does **not** work fine. Sometimes I can't click on anything after coming back from suspend.

I suspect the problem of the screen not turning on is related to Compiz. I have the problem in Unity, and in Gnome Session (Compiz), but so far it has not happened in Gnome Session (Metacity).  Suspend is still buggy in Metacity.

---

