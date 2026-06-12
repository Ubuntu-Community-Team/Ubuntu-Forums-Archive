---
title: "Video Card Help"
date: 2010-11-21
forum: Hardware
---

### Post by Xynche on 2010-11-21
Hello, I'm new to Ubuntu/Linux

I'm currently running Ubuntu 10.04, and I'm having trouble with media players and games.

When I try to run certain games I get a black screen with the white blinking "_" and then my machine reboots.

When I try to watch movies or videos the program just closes.

I believe it has something to do with my video card. I don't know how to get my system info to post it. 

Any help on the subject would be great.

---

### Post by Hippytaff on 2010-11-21
if you do
```

lspci

```
in a terminal (open a terminal with CTRL+ALT+T) it will output info on pci devices :-)

---

### Post by Xynche on 2010-11-21
Thanks, is this the info needed?

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04)
01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Hippytaff on 2010-11-21
> 
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

this is the integrated graphics device. Do you have any other graphics cards or are you using this one?

Also it might not a a graphics card issues. when this happens take a look at the log files to see if you can glean any info from them.

system -> Administration -> log file viewer

and 

```

dmesg | grep vid

```
or if that returns nothing
```

dmesg | tail

```

---

### Post by Xynche on 2010-11-21
Well I just tried the video player and it runs now, but games still crash.

I'm not sure what to do with the codes you posted after I have "System Log Viewer" opened.

---

### Post by Hippytaff on 2010-11-21
Sorry, my advice was confusing, I meant you can use the log viewer to view the logs to see if there is anything that would point to the problem. The commands I posted are for you to use in the terminal to view the dmesg information, which kind of logs stuff as it happens....so just after something did not work
```

dmesg | tail

```
will show you the last few entries of the dmesg log.

---

### Post by Xynche on 2010-11-21
```
dmesg | grep vid
[    0.000000] BIOS-provided physical RAM map:
[    0.290601] pci 0000:00:02.0: Boot video device
[   14.424418] Linux video capture interface: v2.00

```and 

```
dmesg | tail
[132650.937902] stereo mode not supported
[132777.775644] stereo mode not supported
[132777.882934] stereo mode not supported
[132780.545055] stereo mode not supported
[132780.657943] stereo mode not supported
[132780.822984] stereo mode not supported
[132796.610843] stereo mode not supported
[132796.724274] stereo mode not supported
[132796.837303] stereo mode not supported
[132803.308119] stereo mode not supported

```

I'm not sure what these mean though.

---

### Post by Hippytaff on 2010-11-21
what games are you trying to play? are they playable in linux? if not try using Wine
[http://www.winehq.org/](http://www.winehq.org/)

that log looks like a soundcard thing rather than video!? :-s

---

### Post by Xynche on 2010-11-21
Mupen64plus and Tremulous, they where both from Ubuntu download center so they should work. I think it's only the 3D games because 2D stuff works fine.

I'll try using wine for windows alternatives though if they cant work.

EDIT: Thank you so much for your help. I searched for stuff to make my Internet faster (was having problems). I just installed some packages and just about everything seems to function perfectly.

I guess this is solved now?

---

### Post by Xynche on 2010-11-26
I apologize for bringing this back up, but it seems that I still have an issue.

I have Mupen64 working fine, but other games such as Warsow, OpenArena, and Tremulous all give me a black screen.

When I start them I get sound but I cannot see anything. I can press escape and can tell that it does something.

I'm almost certain it's because my graphics card is incompatible with Ubuntu. I was just wondering if there was any way to run the graphics through software instead of hardware?

On my old computer I would play CounterStrike 1.6 and the graphics card was horrible so I set the graphics to software and everything ran fine. Is there anyway to do that with games/apps in Ubuntu?

---

### Post by Hippytaff on 2010-11-26
Don't know...maybe start a new thread, and maybe post it the games sub-forum to get it answered quickerer (is quickerer a word?)

---

### Post by Xynche on 2010-11-26
Alright, well thanks for trying. :D

---

### Post by Hippytaff on 2010-11-26
I'm right in thinking that we sorted your initial problem out though? :-)

just to be sure :-)

---

### Post by Xynche on 2010-11-26
Ya, My initial and biggest problem was no video playback.

That meant no movies and stuff :(. 

Now I just need some gaming help, but I could live without computer gaming if necessary.

---

