---
title: "TV card bt878 - black&amp;white output"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by art2003 on 2006-03-31
SEE LAST POST FOR THE SOLUTION THAT WORKED FOR ME AND BROUGHT COLORS TO LIFE

Hello have purchased a second hand TVcard. It sort of works but the colours are very very dull, almost black and white, actually black and white with a bit of blue. The card has a sticker "MM201PCTV" and Samsung. Ubuntu sees the card and loads the modules out of the box but just basically no colour but a bit of blue.

lspci:
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

dmesg:
[4297651.908000] bttv0: detected by eeprom: Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [card=23]
[4297652.002000] bttv0: Modtec: Tuner autodetected by eeprom: Temic 4066 FY5
[4297652.002000] bttv0: using tuner=18
[4297652.002000] tuner 0-0061: type set to 18 (Temic PAL_I (4066 FY5))
[4297652.002000] bttv0: i2c: checking for Bt832 @ 0x88... found
[4297652.003000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4297652.005000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4297652.008000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4297652.026000] bttv0: registered device video0
[4297652.028000] bttv0: registered device vbi0
[4297652.028000] bttv0: PLL: 28636363 => 35468950 . ok
[4297652.042000] bt878: AUDIO driver version 0.0.0 loaded
[4297652.046000] bt878: Bt878 AUDIO function found (0).
[4297652.046000] ACPI: PCI Interrupt 0000:00:0a.1[A] -> GSI 18 (level, low) -> IRQ 18
[4297652.046000] bt878(0): Bt878 (rev 2) at 00:0a.1, irq: 18, latency: 32, memory: 0xcdcff000

lspci -v
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cdcfe000 (32-bit, prefetchable) [size=4K]

0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cdcff000 (32-bit, prefetchable) [size=4K]

---

### Post by Joeb on 2006-04-01
[QUOTE=art2003]Hello have purchased a second hand TVcard. It sort of works but the colours are very very dull, almost black and white, actually black and white with a bit of blue. The card has a sticker "MM201PCTV" and Samsung. Ubuntu sees the card and loads the modules out of the box but just basically no colour but a bit of blue.
[/QUOTE]

What TV program are you using?  If you are using TvTime, are you sure the hue and saturation settings aren't just set too low?

---

### Post by art2003 on 2006-04-01
hello and thanks for your post.
I set Hue to 100 and saturation to 98 and now can see blue ok, so it is all still in black and white but anything in blue shows ok. Anything else I can do?

---

### Post by Michael Matthews on 2006-04-01
It can be caused by incorrect channel tuning. I used to have to do that with xawtv. If color channel is not tuned correctly colors will be dull or none at all.
Not sure how to do this with tvtime which I have to assume you are using.

---

### Post by art2003 on 2006-04-01
I have xawtv and same dull black and white image as well so by all means if you can tell me how you sorted your problem in xawtv I will try that.

tvtime looks a bit nicer but if xawtv is the one to work in colour thats the winner!

---

### Post by art2003 on 2006-04-01
Problem fixed with tvtime. Thanks to Joeb and Matthew for their suggestions.

I've set hue in ~/.tvtime/tvtime.xml to 50
the default value 0 was no good
and the 100 suggested was the same, but 50 brings lovely colours!

I would like to mention that this tvcard under windows XP has an awful picture with unofficial drivers as the manufacturer didn't release even windows 2000 drivers, never mind XP.

Whereas in Ubuntu it works perfectly (black and white out of the box and in colour once config file is edited and hue set to 50)

---

