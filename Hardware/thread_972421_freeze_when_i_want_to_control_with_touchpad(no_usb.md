---
title: "freeze when i want to control with touchpad(no usb mouse plugged in)"
date: 2008-11-05
forum: Hardware
---

### Post by ibomb on 2008-11-05
Hi there, i have this very annoying problem, when i want to use only my touchpad in my laptop the whole system freezes nothing ever responses.It doesnt matter if:
1)start the system with usb mouse plugged ---everything is fine but after the startup, plug the mouse out then it freezes...
2) start the system without mouse after the startup screen it freezes again 

i searched the forum and people mentioned that it was an issue about kernel.
and after they entered the startup option i8042.nomux=1 and/or i8042.reset=1  their problems were solved but it didnt change anything for me. my laptop is a little old one Acer Travelmate 4002 with synaptics touchpad. And i dont know what to do.Anyone have ideas you're welcome...thanks

---

### Post by jek_king on 2008-12-05
> **ibomb said:**
> Hi there, i have this very annoying problem, when i want to use only my touchpad in my laptop the whole system freezes nothing ever responses.It doesnt matter if:
1)start the system with usb mouse plugged ---everything is fine but after the startup, plug the mouse out then it freezes...
2) start the system without mouse after the startup screen it freezes again 

i searched the forum and people mentioned that it was an issue about kernel.
and after they entered the startup option i8042.nomux=1 and/or i8042.reset=1  their problems were solved but it didnt change anything for me. my laptop is a little old one Acer Travelmate 4002 with synaptics touchpad. And i dont know what to do.Anyone have ideas you're welcome...thanks

I have the same problem with the same laptop, i have tryed everything: adding to the xorg.conf a new section for the mouse, the startup options which you says... but nothing works.

Please help us xD

And i got other problem. When i power off the computer it hangs when this message is displayed

acpi exitings

Thanksand sorry for my poor english

---

### Post by shantanubhadoria on 2009-01-09
Sorry to bump this topic. But I have this same issue on my compaq 770TU (c700 series) running itrepid ibex.
if while booting up or after the xserver has loaded, As soon as I use the touchpad the thing hangs up and the caps lock key starts blinking for some reason.
Has anybody found a solution to this issue yet???
guys wht was the thread where the above solution was stated? can you paste the link.

Please note I never faced this issue with Hardy Heron. Any leads??

---

### Post by Hulky42 on 2009-01-23
I've the same hang / freeze issue with my Dell Latitude C610 laptop. Not only when using the touchpad (probably a Synaptics touchpad) but also when using the laptop in a docking station with separate keyboard and mouse (via a Belking KVM switch). So it looks like that the 'Hanging Daemon' is not critical about the hardware. The good news is that after a hard switch-off (pressing the On/OFF button ca 8 seconds, the laptop boots flawless next time. Unfortunately I've no clue how to solve this...

---

### Post by Dex73 on 2009-02-02
My Gateway freezes sometimes. I can still move the pointer around and the only thing I can see is the background. (this usually happens after a long period of inactivity) Also I have the show pointer when ctrl is pressed feature turned on and it doesn't function either.

---

### Post by khodi_k on 2009-04-09
Same here. I use 8.9 netbook. I tried both Intrepid and Jackalope with it.  Whenever I use touchpad keyboard freezes as well as the touchpad itself. But the USB mouse still works, so I tried to restart. OS shuts down but the screen remains blank, and there's no way to start the computer, so I just remove the battery. I dunno what could be the reason. Any thoughts?

---

### Post by byshn on 2009-04-11
i have the same problem.
My laptop is Acer TravelMate 2300NLCi with 512 DDR SDRAM running Ubuntu 8.04.

Symptoms: 
After running for some times, the underside of my laptop is going hot, and suddenly the keyboard and touchpad is very hard to respond; the keyboard will responded after i pressed A SINGLE KEY FOR VERY LONG TIME. And I mean it is a single key. And the result such as: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa. The touchpad didn't respond at all.
I have mouse plugged in and its still functioning.

I dont have any idea,so if it is happened, i just unplugged the power cord so my laptop is going off... and restart the computer again.

Is this ACPI problem? :(

Thanks for any ideas and suggestions

---

