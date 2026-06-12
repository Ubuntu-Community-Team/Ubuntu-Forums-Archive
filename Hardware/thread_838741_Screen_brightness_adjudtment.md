---
title: "Screen brightness adjudtment"
date: 2008-06-23
forum: Hardware
---

### Post by dan93z28 on 2008-06-23
Hello,

I hope this is the appropriate section.  I have had Hardy ubuntu installed for about 3 months now, and i just recently installed kde 4 to try it out. I installed it using synaptic.  I was wondering if there is a program that allows you to adjust the screen brightness.  I am using an HP dv6000, and kde does not recognize the fn keys for brightness adjustment. I looked through all the programs that came with kde and could not find one with a screen brightness option. As it sits now the screen brightness is a little too dim for my personal taste.  I tried going into the power management settings, but i didnt find any option for screen brightness.

Thanks for any help.

---

### Post by sdennie on 2008-06-23
If you can't find any gui applications to do it, you could try xbacklight.  For example, to set it to 50% brightness, try:

```

xbacklight -set 50

```

---

### Post by dan93z28 on 2008-06-23
my eyes thank you greatly.  is there a way to add this to the startup in kde so that it will automatically set my screen brightness when i log in?

---

### Post by sdennie on 2008-06-23
I've never used KDE but, it sounds like you can go to Control Center->KDE Components->Session Manager.  If that makes sense.  I just googled for "ubuntu kde startup programs" so, maybe you can find something better.

---

### Post by apche93 on 2008-08-18
um, hi.

im using ubuntu 8.04 and i just installed the xbacklight prgm.  

when i entered "xbacklight" into terminal, it gave out 100.000000.

that is as usual b/c my eyes are and do burn at the brightness of my sony vaio laptop.

now i tried "xbacklight -set 50"  and nothing happened!  i entered in "xbacklight" into terminal again and it said "50.000000" but still no change to the screen!

anyone have solution?

---

### Post by nuras on 2008-11-04
I tried changing it through the power manager. I had the same prob. All i did was to right click on the Battery button on the task bar and then change the brightness. Hope this helps.

---

### Post by wavis on 2009-11-25
```
$ xbacklight
No outputs have backlight property
$
```

---

### Post by smoosh on 2009-12-06
I get the same message as wavis. ugg.

---

