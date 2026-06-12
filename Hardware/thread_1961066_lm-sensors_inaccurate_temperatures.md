---
title: "lm-sensors inaccurate temperatures?"
date: 2012-04-18
forum: Hardware
---

### Post by for.i.am.root on 2012-04-18
Hi:

So I am running an overclocked rig and Ubuntu 10.04 x64 and am having issues with my temperature read outs. This computers main duties: FTP server, SSH server, TorrentServer (Remote / Web management), Media Server for Android Tablet(s)/Phone(s), Xbox 360, and PS3. Once this issue is figured out it will be back to a "headless" machine.

The motherboard has a "built-in" alarm for the CPU that is set to go off when the CPU reaches 70 C. I have yet to hear that alarm, however, lm-sensors is reading my CPU temp at ~80 C under extreme load for ~30 minutes.

Extreme load defined as (in this instance):
(6) running instances of: ```
 while [ $? -eq 0 ]; do stress --cpu 8 --io 4 --vm 2 --vm-bytes 128M --timeout 30s; done 
``` all in a seperate window.
Transcoding video (PS3 Media Server transcoding a 2.5 hour 720p video serving to PS3 and a 45 minute 720p video being served to Xbox 360) and handling light web browsing (3-4 tabs).

Given that Smart CPU fan control *should* increase fan speed to dissipate heat, if my rig is running almost 10 C OVER the tCase of this CPU, why is it not spinning at max? It is running at about 80 - 82% of max. I also do not get the (audible) CPU alarm from the board.

My rig has as of yet to shutdown from the strain / heat. Had some problems with random freezes / failed boots before upping the Vcore a little. Also had random freezes at 9x333@1.4500 settings, however, no problems at the current 12x266@1.4500

The BIOS reports a temperature of 30C with a fan speed of 2163RPM. Ubuntu @ idle reports 42 @ 1654. Why would the fan speed be higher at a lower temp?

lm-sensors found 8 different (relevant) sensors (after detect) on this board, listed below along with their reported temps:
temp1 0 C
temp2 ERROR
temp3 ERROR
Core0 79 C
Core1 77 C
temp1 -55 C
temp2 -2 C
temp3 21 C

Rig specs:

Gigabyte G41MT-S2PT Rev. 1.1 MoBo
[http://www.gigabyte.com/products/product-page.aspx?pid=3972#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3972#ov)

Intel Pentium Dual Core e2220 (1M Cache, 2.40 GHz, 800 MHz FSB)
[http://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-%281M-Cache-2_40-GHz-800-MHz-FSB%29](http://ark.intel.com/products/32430/Intel-Pentium-Processor-E2220-%281M-Cache-2_40-GHz-800-MHz-FSB%29)

(2) Generic Kingston 2GB DDR3-1333 CL9 RAM (9-9-9-24)

CPU Fan Max Speed:		4066
CPU Actual speed:		3325
CPU Clock Ratio:		12
CPU Host Frequency:		266
System Memory Multiplier:	4.00A
Memory Frequency:		1066
CPU Vcore:			1.4500
Stock CPU:			12*200=2400
OC'd CPU:			12*266=3192

Any ideas?

Other than replace the rig. I know it's outdated, however, it is not for "daily" use. Mainly just streaming *ahem* "stuff" to other hardware and downloading *ahem* "stuff" for said streaming (like pictures of family and what not.....).
Eventually I will convince the wife to let me build a new one and the 2500k will become the "monster in the closet".

---

### Post by Yellow Pasque on 2012-04-18
Some mobo fan control algorithms are less than great. I prefer to turn off the mobo fan control and use pwmconfig to do it myself.

Since you're mainly file-serving, do you really need to overclock/volt?

> I also do not get the (audible) CPU alarm from the board.
Do you have the PC speaker on your case (assuming it has one) properly connected to the mobo?

---

### Post by for.i.am.root on 2012-04-18
Hi Temüjin:

It's also transcoding HD content and streaming it over the LAN to multiple devices at the same time. I had some stuttering when transcoding 720p to both the Xbox and PS3 at the same time.

The system speaker is connected and functioning properly. At least I think it is. beep makes it go beep at least. :-D

Thanks!

---

