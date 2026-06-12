---
title: "[SOLVED] LCD Brightness on Boot - emachines M6809"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by crjackson on 2007-09-30
Okay, so I've read a few REALLY OLD threads and found no help.

Here's the problem:

I can set the brightness using the function buttons and it starts to boot using max brightness.  Then as soon as the OS starts to load, it turns down very dim.  I can and do use the function keys to turn it up again, but banking on the function key for brightness about 20 times a day can't be good.

Is there a setting or something I can configure to prevent ubuntu from dimming the output?  I just want it to hold the bright setting unless manually turned down.

---

### Post by crjackson on 2007-10-01
bump for help...

---

### Post by crjackson on 2007-10-01
...

---

### Post by crjackson on 2007-10-12
So there is no solution to this then?

ANYBODY....

---

### Post by Pipboy2000k on 2007-10-12
Wow, thats really awkward...have you tried switching the monitor to a different computer to see if its just going bad?

i wouldnt expect what i just said to actually happen, but with electronics you never know...


sorry none of these guys responded to your thread...but they all probably have half baked ideas like mine...


try testing it with a CRT monitor as well...

---

### Post by crjackson on 2007-10-13
> **Pipboy2000k said:**
> Wow, thats really awkward...have you tried switching the monitor to a different computer to see if its just going bad?

i wouldnt expect what i just said to actually happen, but with electronics you never know...


sorry none of these guys responded to your thread...but they all probably have half baked ideas like mine...


try testing it with a CRT monitor as well...

Thanks for the reply.  It's an m6809 emachines which is a laptop.  No it's not going bad, I'm just tired of having to turn up the brightness on every reboot.  When using XP it holds whatever my last setting was upon reboot.  There is a setting somewhere in an unknown boot file that will fix this, but I have no idea where it is.

---

### Post by nick_h on 2007-10-13
Have a look at vbetool.  Perhaps the command:
```
sudo vbetool vbefp setbrightness <int>
```
might do something.

Read the man page for vbetool before using it.

---

### Post by crjackson on 2007-10-13
> **nick_h said:**
> Have a look at vbetool.  Perhaps the command:
```
sudo vbetool vbefp setbrightness <int>
```
might do something.

Read the man page for vbetool before using it.

Thanks, I will...

---

### Post by crjackson on 2008-07-02
Issue resolved by installing 8.04 Hardy

---

