---
title: "Sound sometimes doesn't work"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by domstyledesign on 2006-10-31
Sometimes when i boot my laptop the sound doesn't work.  Sometimes it does.  I have a toshiba s3503.

lspci shows my sound card as:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

alsamixergui gives me the following sliders:
"Head.., Front, Front Mic, Mic, Capture, Capture 1, Capture 2, Caller ID, Input Source, Input Source 1, Input Source 2, Off-h.."

The first slider (which i assume is meant to be the master control) is all the way down and will not move up

here's some other (hopefully) useful info:
```
cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0x52080000 irq 58
```
```
cat /proc/asound/devices
 22: [0- 6]: digital audio playback
 30: [0- 6]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
```
```
cat /proc/asound/timers
G0: system timer : 1000.000us (10000000 ticks)
G1: RTC timer : 976.562us (100000000 ticks)
  Client sequencer queue 0 : stopped
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-3: PCM capture 0-0-3 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-1-3: PCM capture 0-1-3 : SLAVE
P0-6-0: PCM playback 0-6-0 : SLAVE
P0-6-1: PCM capture 0-6-1 : SLAVE
```
```
cat /proc/asound/pcm
00-00: ALC262 Analog : ALC262 Analog : playback 1 : capture 2
00-01: ALC262 Analog : ALC262 Analog : capture 2
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
```

any ideas?

---

### Post by KLineD on 2006-10-31
I have exactly the same problem (and the same soundcard, but different laptop) with my laptop. Both with Dapper and Edgy. I posted the problem some time ago but found no solution. So here I am...

---

