---
title: "not really a support thread - backlight dimmed, what to do"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2006-10-28
my girlfriend has a hp pavilion dv1000 laptop (running windows xp sp2, 1.5 years old) and a week ago, its backlight just stopped working. the desktop visible only if you use a flashlight or similar. then the next day, it worked again. the day after, it was gone for good. 

so I'm documenting here what I have done, and what I should have done :) in case someone gets in trouble as well... 

here is what I did: 
google the problem, order an inverter, replace the inverter, pray that it works. it kinda worked, except that when I first started the laptop plugged in, the backlight was still dim (damn!). but when I unplugged it, the backlight came back (damn! damn!). I tried fn+f4, didn't work. tried fn+f8 (increase brightness), didn't work (DAMN! my moneeeey). then I tried, for some reason, fn+f7 and the backlight came back (yuppee!). For some weird reason, the f8 and f7 changed places. I don't care, it's working.

here is what I should have done:
1. try these: fn+f4 (use external monitor); fn+f7 (decrease brightness); fn+f8 (increase brightness) -I did try only f4 and f8 $0
2. boot with Ubuntu LiveCD to check if it's a bad Windows -I did that $0
3. reset cmos by taking out its battery -see the laptop's documentation, I didn't do that $0
4. change inverter[*] -I did that, I'm hoping it will survive $50
4,5. change the lcd maybe $150
5. take it to a laptop guy $400 -aie
6. buy new laptop $600+ -oyyy

[*]
[LIST]
[*]*Make sure you've got no static on you, or you'll ruin stuff and go to step 5
*Take out the battery first!!!!!
[/LIST]
there are 6 black round plastic things on the lcd. take them out. then unscrew the screws under those black plastic things. then take out the bezzer (or whatever its name is, the black cover around the lcd). the inverter is the long-ish electronic-looking thing on the bottom of the lcd, right where the "HP" logo is if you put the black cover back
[LIST]
[*]*Make sure you don't have static on you
*Take out the battery first!! 
[/LIST]
Take out the cables. its very hard to take them out, be careful not to hurt the little cables (or you'll probably go to step 5 above). I used a pair of tweezers. 

Before engaging in all this, please browse the web and do extensive research. read how others managed to change the inverter, and whether there were oher solutions to the problem.


As an end note, I would appreciate anyone who has another idea on the issue. 

this stuff is for documentation purpose only and I am not responsible if something bad happens. 
good luck.

---

### Post by draeath on 2006-10-28
I've seen someone replace the backlight before. Basically there are three ways:

1. The inverter went, not the actual light. I think this is more common, not sure. It may be easy enough to salvage one from an otherwise toasted laptop of similar characteristics.

2. The laptop uses an ultra-bright white LED (or series of LEDS) that went out for some reason. Maybe one burnt out and the series circuit broke - possibly simply bypassing said LED may help, or replacing.

3. The laptop uses a cold-cathode tube. This is the dangerous/hard one. There (saw it on hackaday.com once upon a time) is a way of taking a cold cathode tube from somewhere else and refitting it to fit into the laptop.
**Do not do this yourself, unless you know what you are doing.** Cold cathode tubes have mercury vapor - much more harmfull than normal mercury.

---

### Post by towsonu2003 on 2006-10-28
> **draeath said:**
> 
2. The laptop uses an ultra-bright white LED (or series of LEDS) that went out for some reason. Maybe one burnt out and the series circuit broke - possibly simply bypassing said LED may help, or replacing.

3. The laptop uses a cold-cathode tube. This is the dangerous/hard one. There (saw it on hackaday.com once upon a time) is a way of taking a cold cathode tube from somewhere else and refitting it to fit into the laptop.
**Do not do this yourself, unless you know what you are doing.** Cold cathode tubes have mercury vapor - much more harmfull than normal mercury.

that's why I added the step 4,5 heheh but of course, I wasn't sure if the lcd comes with the bulbs... does it?

thanks for adding this great info :)

---

### Post by draeath on 2006-10-28
Usually the back of the LCD includes a plastic lens-like thing (covers the whole back side of the LCD panel) with the light source built in, but it may not. It depends :)

The thing to look for is the larger guage wires going to the screen. The smaller (or ribbon-style) ones are for data to the LCD (for the actual display) and the larger ones go to/from the inverter to the light source.

---

