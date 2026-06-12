---
title: "Problem with max resolution on external monitor and Intel gfx"
date: 2009-04-29
forum: Hardware
---

### Post by bogoliubov on 2009-04-29
Hello. I run 9.04 (lpia) on my Acer Aspire One, which has intel graphics (945GME). After adding a "virtual" line in xorg.conf I can have a max resolution of 2048x2048.

But when I connect the laptop to an external monitor the max resolution reported by xrandr is 1368x1024, when it should be 1920x1080. 
So how can I solve this? I want to have a high resolution on the external screen (and I turn the built-in screen off)

---

### Post by bogoliubov on 2009-04-29
bump...

---

### Post by vaughany on 2009-05-08
Bump.  I am having a similar issue, though I had attributed it to 1) crap quality monitor and 2) low-spec Intel gfx chips. Any help in this area is appreciated, expecially by a n00b. :)

---

### Post by ecormier on 2009-06-08
I have an Acer Aspire with a GME945 as well and after adding the virtual line to my xorg.conf I can get a resolution of 1680x1050 on my 22" dell monitor...so it looks like the card/driver can support higher resolutions ....are you still having this problem? try updating (I notice some new intel xorg upgrades recently) and try it again and let me know if it's still the same

here's the screen section from my xorg:
Section "Screen"
[INDENT]Identifier	"Default Screen"[/INDENT]
[INDENT]Monitor		"Configured Monitor"[/INDENT]
[INDENT]Device		"Configured Video Device"[/INDENT]
[INDENT]SubSection "Display"[/INDENT]
[INDENT][INDENT]Virtual	2048 2048[/INDENT][/INDENT]
[INDENT]EndSubSection[/INDENT]
EndSection

and the output from "xrandr -q":
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 2048 x 2048
VGA connected (normal left inverted right x axis y axis)
   1680x1050      60.0 +
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
LVDS connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1

---

### Post by bogoliubov on 2009-08-25
I just tried and I can't get above 1360x768, even though the monitor should handle 1920x1200. No idea why...

---

### Post by bogoliubov on 2009-09-08
...but when I booted 9.10 LiveCD (well USB actually) I can get the higher resolutions. So it seems there is some kind of bug in 9.04...

---

