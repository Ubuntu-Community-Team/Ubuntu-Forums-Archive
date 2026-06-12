---
title: "problem in &#65288;gnome control center----display&#65289;"
date: 2014-03-26
forum: Hardware
---

### Post by liu3 on 2014-03-26
[COLOR=#000000]I have a laptop with I7&#65292;Ivybridge &#65292;the card is INTEL HD 4000.[/COLOR]
[COLOR=#000000]when I connect extra VGA monitor ,the laptop LVDS display turn off.[/COLOR]
[COLOR=#000000]I try to set mirror mode by (gnome control center----display ),but it seems no useful.[/COLOR]
[COLOR=#000000]but,I can set mirror mode by xrandr --output LVDS1 --same-as VGA1.[/COLOR]
[COLOR=#000000]I wonder why the gnome control don't work? [/COLOR]
[COLOR=#000000]what should I do to if I want set mirror mode by gnome control center&#65311;[/COLOR]
[COLOR=#000000]Thanks&#65281;[/COLOR]

---

### Post by liu3 on 2014-04-01
It seems that the monitor VGA1 is primary monitor.
I change (home/.conf/monitor.xml),set the LVDS1 as primary monitor,but when I plug in VGA monitor ,the laptop monitor still turn off .
I need your help.....Thanks!

---

