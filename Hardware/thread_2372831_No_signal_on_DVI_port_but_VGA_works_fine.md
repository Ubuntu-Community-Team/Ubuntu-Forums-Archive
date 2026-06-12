---
title: "No signal on DVI port but VGA works fine"
date: 2017-09-29
forum: Hardware
---

### Post by linuxyogi on 2017-09-29
Hi,

When I connect my monitor using the DVI cable there is no signal displayed on the monitor. It just  stays on standby but when I connect using VGA cable it works fine.

Any ideas ?

GeForce GTX 650
Samsung SMB 2230

---

### Post by Autodave on 2017-09-29
Since no one else has jumped in, the first thing I would try is another DVI cable. If that doesn't fix it, try your monitor on a different computer.

I am assuming that you have the current Nvida driver installed from the repositories?

---

### Post by linuxyogi on 2017-09-29
> **Autodave said:**
> Since no one else has jumped in, the first thing I would try is another DVI cable. If that doesn't fix it, try your monitor on a different computer.

I am assuming that you have the current Nvida driver installed from the repositories?

I have a HDMI to DVI cable which I use to connect my Raspberry Pi to the monitor (this monitor has no HDMI port). I used this cable to try as an alternative and still no signal on the monitor.


I have tried connecting  my Raspberry Pi to this monitor using the above mentioned  HDMI to DVI cable and it works just fine.

Yes I have the latest NVIDIA driver installed.

---

### Post by Autodave on 2017-09-29
When you hook it up, go into Nvidia settings and see what it is seeing there. You should be on X Screen 0 and it hopefully has your monitor recognized. (I am assuming that you are disconnecting the VGA cable completely: from both the card and the monitor. Leaving the VGA cable connected to the card can cause the card to view the DVI cable as a secondary screen.)

---

### Post by Autodave on 2017-09-29
Just thought of something to try if what I posted above doesn't work.  Hook up only the DVI cord to the monitor and PC. Do this w/o either the monitor or PC being turned on. Put monitor on first for about 10-15 seconds and then turn PC on and see what happens.

---

### Post by linuxyogi on 2017-09-29
> **Autodave said:**
> When you hook it up, go into Nvidia settings and see what it is seeing there. You should be on X Screen 0 and it hopefully has your monitor recognized. (I am assuming that you are disconnecting the VGA cable completely: from both the card and the monitor. Leaving the VGA cable connected to the card can cause the card to view the DVI cable as a secondary screen.)

The VGA cable is connected  to an external TV Tuner box. I just tried booting without the vga cable connected to the TV Tuner box but same result.


> **Autodave said:**
> Just thought of something to try if what I posted above doesn't work. Hook up only the DVI cord to the monitor and PC. Do this w/o either the monitor or PC being turned on. Put monitor on first for about 10-15 seconds and then turn PC on and see what happens.

Just did this but no signal.

---

### Post by Yellow Pasque on 2017-09-29
Can you see the BIOS/POST screen? In other words, is this just an issue with Ubuntu or is it a general hardware issue?

---

### Post by efflandt on 2017-09-29
What monitor or other display were you using for this computer before? HDMI to DVI should not be a problem if it works for your Raspberry Pi. I use DVI to HDMI because I was using my HDMI cables for other things and I think my current GTX 1060 might have mini-HDMI. Are you sure that the HDMI end is plugged into the GTX 650 and not integrated (motherboard) graphics?

Have you tried booting with the monitor already on and its DVI input selected if it has more than one input? X looks for displays when it starts and does not necessarily automatically notice displays that are hotplugged or turned on after it starts, although, it notices my HDTV when it is in standby and should notice them if you go to Settings > Displays > Detect Displays (button).

Graphics cards can fail, depending upon who made the card. The most recent one I had fail was a cheap GT 430 made by Galaxy, which began failing shortly after its 1 year warranty expired. Although, the initial symptom in Linux was that keyboard and mouse button input would appear to stop, although, mouse cursor usually still moved. Eventually graphics would glitch and/or in syslog the nvidia driver showed hardware not responding. The only other one I had fail was a TNT card at work many years ago. I never had any trouble with the GT 220 included with my PC, EVGA GTX 550 Ti (which replaced GT 430), MSI GTX 750 Ti, or Asus GTX 1060 each in same PC, other than nouveau driver not initially supporting GTX 750 Ti or GTX 1060 (nvidia drivers worked).

---

### Post by linuxyogi on 2017-09-30
> **Temüjin said:**
> Can you see the BIOS/POST screen? In other words, is this just an issue with Ubuntu or is it a general hardware issue?

No I don't see bios/post. This I guess is a general hardware issue.





> **efflandt said:**
> What monitor or other display were you using for this computer before? HDMI to DVI should not be a problem if it works for your Raspberry Pi. I use DVI to HDMI because I was using my HDMI cables for other things and I think my current GTX 1060 might have mini-HDMI. Are you sure that the HDMI end is plugged into the GTX 650 and not integrated (motherboard) graphics?

Have you tried booting with the monitor already on and its DVI input selected if it has more than one input? X looks for displays when it starts and does not necessarily automatically notice displays that are hotplugged or turned on after it starts, although, it notices my HDTV when it is in standby and should notice them if you go to Settings > Displays > Detect Displays (button).

Graphics cards can fail, depending upon who made the card. The most recent one I had fail was a cheap GT 430 made by Galaxy, which began failing shortly after its 1 year warranty expired. Although, the initial symptom in Linux was that keyboard and mouse button input would appear to stop, although, mouse cursor usually still moved. Eventually graphics would glitch and/or in syslog the nvidia driver showed hardware not responding. The only other one I had fail was a TNT card at work many years ago. I never had any trouble with the GT 220 included with my PC, EVGA GTX 550 Ti (which replaced GT 430), MSI GTX 750 Ti, or Asus GTX 1060 each in same PC, other than nouveau driver not initially supporting GTX 750 Ti or GTX 1060 (nvidia drivers worked).

I was using DVI to DVI cable with this monitor but it just suddenly stopped displaying  any signal. There is no integrated HDMI port in this motherboard. I guess my graphics card too is failing  but I am not sure.

---

### Post by Autodave on 2017-09-30
That kinda sounds like a bad card. One last thing you can try: hook up only DVI cable. Boot machine using boot disc and see if you get a picture. If none that way, I would be  looking at least for another video card to try.

---

### Post by linuxyogi on 2017-10-01
What a waste of money specially because the card is not fully dead. I will invest on a new card soon. Thanks for your replies.

---

### Post by ice-wolf on 2018-01-04
> **Autodave said:**
> When you hook it up, go into Nvidia settings and see what it is seeing there. You should be on X Screen 0 and it hopefully has your monitor recognized. (I am assuming that you are disconnecting the VGA cable completely: from both the card and the monitor. Leaving the VGA cable connected to the card can cause the card to view the DVI cable as a secondary screen.)

I have only one monitor; I can get DVI to work by choosing "secondary" monitor and disabling VGA one in Ubuntu 
 (otherwise if I try to use just the DVI cable, monitor says no signal).
 Is there any way to make DVI work with just the DVI cable instead of having both DVA and VGA plugged in?

---

