---
title: "Nec 20wgx2"
date: 2008-05-24
forum: Hardware
---

### Post by bonega on 2008-05-24
Hi.

Previously I had this monitor set up on a dvi-connection, this worked fine with automatic detection.
Now I try to use vga and my max resolution is 640x480.

Can anyone post their modeline either from xorg.conf or that commandline tool( forgot the name).

Thanks

---

### Post by speculatrix on 2009-04-16
I have an nvidia fx5200 and NEC 20WGX2pro, and I had a lot of problems making it work on the DVI port - the NEC told xorg that its max res was 1440x900 or something. Oddly, it worked fine on the VGA interface but of course the quality wasn't so good. When I overrode it, I got visible snow on the screen, flickering horizontal lines of primary colours and sometimes the screen would blank out. Lots of googling showed other people had problems driving this monitor.

It worked fine on windows BUT I had to override the resolution; although I took note of the frequencies the monitor reported it didn't help. Then I discovered a program called powerstrip which analysed the timing on windows and generated a modeline. Success! A perfect stable picture with DVI on linux. It took me a long time to get this working so I found reported problems and signed up to post my results, I hope they help people!
:popcorn:


```

PowerStrip timing parameters:
1680x1050=1680,48,32,80,1050,3,6,21,119250,772

Generic timing details for 1680x1050:
HFP=48 HSW=32 HBP=80 kHz=65 VFP=3 VSW=6 VBP=21 Hz=60

VESA detailed timing:
PClk=119.25 H.Active=1680 H.Blank=160 H.Offset=32 HSW=32 V.Active=1050 V.Blank=30 V.Offset=3 VSW=6

Linux modeline parameters:
"1680x1050" 119.250 1680 1728 1760 1840 1050 1053 1059 1080 +hsync -vsync

```

p.s. I think this works because the clock frequency limit on the monitor is quite low, and the only way to achieve it is to have fairly short sync pulses, they'd be too short for a CRT but are fine for a DFP. I can port my /etc/X11/xorg.conf if that helps.

---

