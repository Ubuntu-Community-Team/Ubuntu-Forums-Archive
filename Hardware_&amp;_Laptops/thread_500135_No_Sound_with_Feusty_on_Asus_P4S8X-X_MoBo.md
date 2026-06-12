---
title: "No Sound with Feusty on Asus P4S8X-X MoBo"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by Jallu59 on 2007-07-13
Hi

For a while ago I installed Feisty with my new motherboard ASUS P4S8X-X.
I have managed to solve every other problem, but one thing still remains. There's no sound at all. 

I have studied the SoundTroubleshooting - Community Ubuntu Documentation. 
Below are the results of some commands.

The thing I wonder most is: Why is the <access denied> on that lspci-listing below ? What does it mean ? And how to solve the problem ?

Somehow the ingrated audio system is confusing. On the other hand there is the Sis SI7012 (an AC'97 interface ?) and then there is the ADI AD1980 6-channel audio CODEC.

Yours
Jallu59

Hardware: Asus P4S8X-X, P4(2,8GHz), 1024MB RAM, ATI 8564, Samsung 80GB HD

jallu@ARMAS:~$ aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: SI7012 [SiS SI7012], laite 0: Intel ICH [SiS SI7012]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

jallu@ARMAS:~$ lspci -v
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80b0
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 9400 [size=256]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>

---

