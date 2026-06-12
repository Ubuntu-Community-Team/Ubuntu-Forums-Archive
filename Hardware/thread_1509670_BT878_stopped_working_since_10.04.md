---
title: "BT878 stopped working since 10.04"
date: 2010-06-14
forum: Hardware
---

### Post by Sunday87 on 2010-06-14
Hi!

My BT878 tuner card does not work since the update to 10.04. tvtime crashes without saying anything useful:
```
<21:02:05> alex@firefly:~$ tvtime -d /dev/videobt
Starte tvtime 1.0.2.
Lese Konfiguration aus /etc/tvtime/tvtime.xml
Lese Konfiguration aus /home/alex/.tvtime/tvtime.xml
Channels count non available
```
but it does indeed set a valid channel (of my old config file). After the crash kdetv is able to show teletext (but no video), but i didn't use kdetv before.

```
<21:00:52> alex@firefly:~$ dmesg | grep bt8
[   10.105950] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   10.172959] msp3400 0-0040: MSP3415D-B3 found @ 0x80 (bt878 #0 [sw])
[   10.259350] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   10.444855] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
<21:06:36> alex@firefly:~$ dmesg | grep bttv
[   10.105039] bttv: driver version 0.9.18 loaded
[   10.105042] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   10.105848] bttv: Bt8xx card found (0).
[   10.105869] bttv 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.105880] bttv0: Bt878 (rev 2) at 0000:03:06.0, irq: 21, latency: 64, mmio: 0xfbfff000
[   10.105948] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   10.105950] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   10.105953] IRQ 21/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.105995] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   10.108497] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   10.146532] bttv0: Hauppauge eeprom indicates model#61344
[   10.146534] bttv0: tuner type=5
[   10.390838] bttv0: registered device video1
[   10.390857] bttv0: registered device vbi0
[   10.390874] bttv0: registered device radio0
[   10.401941] bttv0: PLL: 28636363 => 35468950 .. ok
alex@firefly:~$ lspci
[...]
03:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
03:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

```

I am using 64bit Kubuntu 10.04 and have been using 64bit 9.10 before with which the card had worked perfectly (including lirc), then I did a regular upgrade through update-manager and the card stopped working (lirc doesnt work either). It has been working since 5.04 on 32bit in my old machine.
Is there hope? I do not really want to go back to 9.10 and stay there forever...
tia

---

### Post by Azyx on 2010-07-07
My KDETV with BT878 also stop working. Still have 8.04

---

### Post by zorrito_1978 on 2010-08-21
hello all!
I got problems since ubuntu9.04, kdetv stops working, dunno why, but doesn't recognize the card, so I've switched to tvtime.
Now I've recovered a bt878 card, and in 10.04 kdetv still don't work and tvtime plays no audio, even with the trj cable connected between tvcard exit and line in of the audio card

keine ahnung!!! (speechless!!!)

take a look at this:
[http://ubuntuforums.org/showthread.php?t=60441](http://ubuntuforums.org/showthread.php?t=60441)

when i grep that log no hex code is given
I use nvidia proprietary driver

---

### Post by anewbie on 2011-03-18
damn i made the mistake of doing a kernel upgrade (apt-get update/apt-get upgrade) with 10.04 and now my tv card (bt878) stopped working :(

Anyone find a fix for this issue ?

---

### Post by sodapop_ on 2011-09-04
i use archlinux but i have similar problems after kernel update  radio stopped working (you can hear static but can't change stations) tv works fine.

---

### Post by anewbie on 2011-09-04
I found that after a reboot it worked. The only changed I made between reboots was to switch the cable on my nvidia card from dvi to vga. I know I've had this problem before so I'm not sure the cable switch made a difference; rather I think it might has somethign to do with some sort of device conflict.
-
I've since upgraded to 11.04 and a new sb system (using the 2500k  built in graphics on a z68 mb). I've had some instability unrelated to the bt878 card but so far it has worked like a charm in this system. Its actually a 11 year old card with regular (daily) use since 2004. 
-

---

