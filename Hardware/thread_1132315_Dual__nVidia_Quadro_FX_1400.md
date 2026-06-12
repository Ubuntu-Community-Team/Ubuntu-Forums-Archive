---
title: "Dual  nVidia Quadro FX 1400"
date: 2009-04-21
forum: Hardware
---

### Post by NepentheDream on 2009-04-21
I have a Desktop that runs two of these. Each card and run two monitors. I can get ubuntu to see on of them and run two monitors, but I can't get it to see the other.
If I unplugged then main one then it will see the second one and use it. These cards are in slot 1 and 3 of a AMD K8 board. I don't know what it is right off the top of my head. The bios has a PCI express configuration which allows you to switch the boot of the PCI slots. If I switch in the bios the boot priority for the cards the second card will start the boot. The Ubunbtu boot screen comes up then the screen goes black, but the monitor light stays enabled, and the other card takes over and comes up.

If I lspci then I get this

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0a:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2)
.

AS you can see it still only sees 1 VGA controller.

Any thought on how to get the the other card to work?
Thanks Alan

---

### Post by NepentheDream on 2009-04-22
I have tried a few steps now that talks about manually programming the xorg file. The problem is that it doesn't even see the second video card or it does assign it a BusID so I can program it.

---

### Post by NepentheDream on 2009-04-22
anyone?

---

### Post by NepentheDream on 2009-04-23
Really know one has a thought on this?

---

### Post by NepentheDream on 2009-04-27
Any thoughts would be great on this.

---

### Post by NepentheDream on 2009-04-28
Come on no one wants to help on this?

---

### Post by NepentheDream on 2009-04-28
This is getting bad, Is it that no one wants to help or is this a really a odd thing?

---

### Post by NepentheDream on 2009-05-01
Does anyone know if in version 9 if it works better at detecting hardware?

---

### Post by NepentheDream on 2009-05-05
come on, no one? I guess Ubuntu isn't ready then.

---

### Post by tacoboye on 2009-05-14
> **NepentheDream said:**
> come on, no one? I guess Ubuntu isn't ready then.

lol, "I guess Ubuntu isn't read then." 

I wouldn't be so quick to make such a verdict based on people's willingness to offer free advice.  I hope you figure out your problem.  

Good luck

-james

---

### Post by NepentheDream on 2009-05-29
> **tacoboye said:**
> lol, "I guess Ubuntu isn't read then." 

I wouldn't be so quick to make such a verdict based on people's willingness to offer free advice.  I hope you figure out your problem.  

Good luck

-james

I wasn't quick to make a verdict. I was posting this problem for a Month before I get a response. I did do a lot of reading and before I posted. I researched for at least a month before I posted, but no answers any where. I did read where people had like problems, but they were using two different video cards, where I am using two of the same video cards. They also had had the hardware show up so it was a matter of hard coding what the system already saw. I ran this exact system in windows for to years without any problems with the video cards. I just hate windows.
I do appreciate your post, but I find it amazing that no one has any thought on this. I did talk to co-workers and they say they get teh same response from the forums, so maybe that is where the problem is.

Anyway, still don't have it working.

---

### Post by NepentheDream on 2009-06-23
I still have no luck with this. Since the two video cards are the same, I think it just doesn't realize that, but it doesn't see it at all.

---

### Post by NepentheDream on 2009-07-29
Can anyone help on this. This is driving me nuts. I need to be able to use more than one Monitor. I hate windows, but it is what is used at work, and I will have to go back to windows if I can't figure out why it won't use dual cards.

---

