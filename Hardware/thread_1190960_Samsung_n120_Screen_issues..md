---
title: "Samsung n120 Screen issues."
date: 2009-06-18
forum: Hardware
---

### Post by Rbrewer19 on 2009-06-18
I just bought the Samsung N120 Netbook. Everything works fine out the box with the exception of the FN keys, and screen brightness which randomly brightens and dims. I have found little documentation about these issues. Does anybody know how to make the FN keys work? Or how to at least make the screen brightness work properly?

---

### Post by elleP on 2009-07-04
I have the same laptop and problems, it is stuck at a low brightness at the moment and I can't seem to get it brighter. If I find something I'll post it here.

---

### Post by Kronprinsen on 2009-08-02
you can set the powersave mode not to adjust screen brightness when running on batteries. You can also add the lcd screen applet to the panel by rightclicking and adding it.

---

### Post by amiteffect on 2009-09-02
i hav samsung n120 ... can any body tell me how to adjust screen brightness in ubuntu .
how to add applet in conrtrol pannel
plz help me guys

---

### Post by srvu on 2009-09-03
I found this at SammyNetbook and it works.  My only problem after doing it was that I couldn't get the keys to stop (like I was holding the key down and it was repeating).  I could get it to stop by hitting a side arrow key, but what made me undo it for now is that I lose keyboard function after adjusting the brightness.  So I'd like to see what others say with their system.

[http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?29576](http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?29576)

Hope this helps.

---

### Post by magicfab on 2009-09-14
I've filed a bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/429351](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/429351)

Also check the Samsung N120 team on Launchpad:
[https://launchpad.net/~samsungn120](https://launchpad.net/~samsungn120)

---

### Post by MrPerfect72 on 2009-10-08
1. Download xbacklight from the synaptic package manager

2. Adjust through the terminal with
xbacklight -set 50 (or any number between 0-100)

---

### Post by Thibaud74 on 2009-11-07
With the n140, xbacklight says "No outputs have backlight property"... I thank that the difference between the n120, n130 and n140 was only about time battery...
For the n120, have a look here :
[http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?29576](http://www.sammynetbook.com/plugins/forum/forum_viewtopic.php?29576)

---

### Post by cowdogmoocat on 2010-07-18
my n120 is also having backlight problems:cry:. lucky the BIOS can adjust the backlight, so all you have to do is use fn+up or fn+down before selecting ubuntu. to change screen brightness, reboot. :-|

---

