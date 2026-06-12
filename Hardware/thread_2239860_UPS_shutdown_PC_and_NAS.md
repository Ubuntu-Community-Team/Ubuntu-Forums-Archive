---
title: "UPS shutdown PC and NAS"
date: 2014-08-16
forum: Hardware
---

### Post by yngve2 on 2014-08-16
Hello.

Im kind of a newbie on Linux, but i love Ubuntu and open source mentality.

I like to know if i can get this to work:
My UPS has only one lan-to-usb-cable port, and i want to have my pc and my nas conected to the software in the UPS.

Can i fake the UPS control cable signal over lan? Can i use a usb-hub?
or is it some other setup that will work?

From Nas ups setup:
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Minimum UPS Capacity
                           [TABLE]
[TR]
[TD][/TD]
[TD]Minimum UPS Capacity[/TD]
[TD]                              50                                      %                 [/TD]
[/TR]
[TR]
[TD="colspan: 3"][/TD]
[/TR]
[TR]
[TD="class: note, colspan: 3"]                     [IMG]http://192.168.1.184/r40851,/adv,/res/image/i_note.gif[/IMG]Note:[/TD]
[/TR]
[TR]
[TD="class: note, colspan: 3"]                     º                      This feature will not work now because there is no UPS control cable connected.[/TD]
[/TR]
[TR]
[TD="class: note, colspan: 3"]                     º                      The NSA automatically shuts down if the UPS's remaining charge gets down to this level.

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX[/TD]
[/TR]
[/TABLE]

My ups: APC Back-UPS ES Power-Saving 700va
My nas: Zyxel NSA325v2 
My pc: latest Ubuntu with apc software.

Thank You!

---

### Post by tgalati4 on 2014-08-16
*apcupsd* has a master-slave configuration, but it requires the daemon (*apcupsd*) running on both systems (the PC and NAS in this case).

Looking at the manual for your UPS, I don't see a serial or USB connection, so I don't know how you would connect to it.  The RJ11 and RJ45 connections are for pass-through protection, not communication.  Regardless, you can write a script that sends a command to your NAS to shutdown every time your PC shuts down--you would have to research ways to do this.

You could also connect the UPS to the NAS and write a script to ping a network share once every 2 minutes.  If the network share is missing (because the NAS shut down), then shut down the PC.  

You can't really use a hub for splitting the signal, but if you know the signaling protocol, you can make a custom Y-cable for simple/dumb serial signaling that detects when a pin goes to ground.  You would have to get into the details of UPS signaling to make this work reliability and not burn anything out.

Oh, and welcome to the forums.

---

