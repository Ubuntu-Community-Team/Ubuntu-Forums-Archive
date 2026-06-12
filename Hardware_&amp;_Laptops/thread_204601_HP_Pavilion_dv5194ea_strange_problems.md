---
title: "HP Pavilion dv5194ea: strange problems"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by david_e on 2006-06-27
I am installing Ubuntu 6.06 on an [hp pavilion dv5194ea]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00651238&lc=en&jumpid=reg_R1002_USEN") and I am experiencing a lot of strange problems. 

At first everithing was loking fine, but I had this error at boot time:

```
[17179570.656000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.656000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.656000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.656000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.656000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.656000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.656000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[17179570.692000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0

```

An lspci check show:

```
mradice@hp-ubuntu:~$ lspci | grep 0000:00:1c
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
```

and:

```
mradice@hp-ubuntu:~$ lspci | grep 0000:06
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
```

but everything was working fine so I installed the Nvidia drivers. Worked on the computer on the whole day without a problem (even wireless worked very good out of the box) looking for infos for the errors above but suddenly the computer lockuped: the imagine on the screen stays fixed and the computer don't respond to any command. I had to restart it with the power botton. After sometime (30min) it crashed again. And again after 15 minutes.

Today I was able to work for six hours before it crashed again. 

It looks like an overheating problem. Reading the kernel messages I always found this message when the computer crashes:

```
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [__report_bad_irq+42/160] __report_bad_irq+0x2a/0xa0
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [handle_IRQ_event+61/112] handle_IRQ_event+0x3d/0x70
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [note_interrupt+135/240] note_interrupt+0x87/0xf0
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [__do_IRQ+253/272] __do_IRQ+0xfd/0x110
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
Jun 26 22:57:33 localhost kernel: [17181504.188000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Jun 26 22:57:58 localhost kernel: [17181528.804000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Jun 26 22:58:22 localhost kernel: [17181552.960000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
```

I am using the proprietary nvidia drivers and kernel-686 (smp) and I don't understand this problem as the computer wasn't really very hot....

Don't know if it matters, but every crash happened when i was using firefox, but actually I am always using firefox so...

PS: sorry for my English

*** EDIT ***
I had also other minor problems with the video card: with nvidia drivers when I hit Ctrl+Alt+F1 I have only a black screen and when the computer shouts down I don't see the usplash, but a black screen.
Nvidia-Settings tools says my video card has 512Mb of video ram, but I know it's just 256 moreover even under winxp it says I have 512Mb of video ram... could this be an hardware video card problem?

---

### Post by mpalla on 2006-06-27
Could you post the full dmesg output?
Have you tried to use a livecd (Knoppix for example)? It'd be useful to do a comparison...

---

### Post by david_e on 2006-06-27
Thanks for the reply.

I have attached the full dmesg output. I have already tried booting with slax-live: it crashed on pcmcia drivers load, but I was able to succesfully boot with slax no-pcmicia cheatcode. I was also able to boot with kubuntu 6.06 RC live cd, with this I had the same boot error that with ubuntu 6.06 now, but everything was working with that as long as I tried it (didn't use it for much time).

With GParted Live CD I had no problem at all.

*** EDIT ***
I have attached the 386 kernel dmesg as I have now experienched a crash even with this kernel

---

### Post by david_e on 2006-06-27
I have tried knoppix live as suggested. Both knoppix 4 (kernel 2.6.12) and knoppix 5 (kernel 2.6.17) halted during boot: they displayed a message about an error in /etc/init.d/rc and the init was switched to run level 0 (halt) just after the identification of the CPU....

Knoppix 5 says rc was out the expected memory flow...

---

### Post by david_e on 2006-06-27
I have installed lm-sensors and I have noticed that one CPU temperature is always 0C, so I have read again my dmesg and found this:

```
[17179580.584000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179580.584000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179580.588000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[17179580.588000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179580.596000] ACPI: Thermal Zone [TZ01] (46 C)
[17179580.608000] Critical temperature reached (0 C), shutting down.
[17179580.608000] ACPI: Thermal Zone [TZ02] (0 C)
```

This is from the 686 kernel, but I have found it even in the 386 one...

---

### Post by evil_elman on 2006-06-29
```

Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
Jun 21 00:01:06 localhost kernel: [17179572.644000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

```

Same problem. Lockups as well. Lockups only occur when abusing network connections of any sort (especially during BT downloads or during multi-tap browsing). It doesn't happen for me in 'general use'.

Everything else is working fine.

---

### Post by Andrew-buntu on 2006-06-30
I have a Pavilion dv5000t and I get those same "Cannot allocate resource" messages when I boot up.  And, until I updated to the latest BIOS, I also received a warning at every boot about "Temperature reached critical point 0C Shutting down".  I was using the 686 kernel until the other day.
But I've never had problems with my computer shutting down randomly.  And AFAIK all of my hardware works (never tried to use a HyperCard or PCMCIA card though).  So I don't think those particular messages will help you solve your hardware issues.  I always assumed that the second Thermal Zone was unused because both CPU cores were actually on the same die, experiencing the same ambient Temp (just a theory).
To get rid of the blank terminal problem, you need to remove "splash" from your /boot/grub/menu.lst on the kernel you're using.  nvidia proprietary driver can do splash or terminals but not both.  Don't know why but that's what I've discovered from experience.  And when my laptop comes out of suspend, my terminals disappear anyway.  Finally re:nvidia, just because you can't see the terminals, doesn't mean they're gone.  I've typed into them to reboot my computer and restart X after attaching a TV to my S-video output and they always work.
Sorry I can't tell you what your problem is... but if you want me to post any output from my working laptop for comparison, I'd be happy to do so when I'm home.

---

### Post by david_e on 2006-07-03
Thank you for your replies. Sorry I forgot to subscribe this topic and I didn't see them until now.

For the terminals with the nvidia drivers: it is possible to have both splash and terminals by adding the option:

```
vga=791
```

after "splash" in the menu.lst file.

I also have experienced lockups when "abusing" my network connection, but [COLOR="Red"]only[/COLOR] when using proprietary nvidia drivers. 

If you have windows or ubuntu with nvidia drivers could you please post the amount of video RAM shown?

I think that the card has 256Mb video RAM plus 256 shared RAM and for some reason nvidia drivers under ubuntu conflicts with kernel when they both are using the same shared RAM: when using the nv drivers an lspci -v show that the video card has only 256 Mb RAM... maybe we could try the nvidia drivers and issue an:

```
dpkg-reconfigure xserver-xorg
```

forcing the video RAM to be set at 256Mb and see if there are any more lockups.

---

### Post by Andrew-buntu on 2006-07-03
[QUOTE=david_e]
If you have windows or ubuntu with nvidia drivers could you please post the amount of video RAM shown?
[/QUOTE]

Looks as if I have 256M, too.  Here's my lspci -vv for the video card:
```

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 30a5
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
**        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]**
        Region 3: Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] #10 [0001]

```
I'm using the nvidia proprietary drivers with a custom 2.17.3 kernel.

---

### Post by david_e on 2006-07-03
Thanks: maybe I could try with a custom kernel and see if everything works also with nvidia proprietary drivers... but the computer is not mine and I don't know what the owner will think about recompiling the kernel... :D 

Eventually I will continue using the nv drivers as the seems to work very well...

---

