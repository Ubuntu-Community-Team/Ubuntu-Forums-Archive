---
title: "compiz vs xrandr - bug or expected problem"
date: 2011-05-14
forum: Hardware
---

### Post by MaxWiz on 2011-05-14
Samsung N210, Ubuntu 11.04

I'm not sure if the problem I am having is a bug or just the expected behaviour given the bodge I am using. I have a netbook with a native 1024x600 resolution. Sometimes I need to switch to a higher non-native resolution 1280x750 or 1365x800.

I use a little script that issues the command with all the variables calculated.

```
xrandr --fb $H"x"$V --output $device --scale $scale"x"$scale --panning $H"x"$V
```

This works perfectly in Gnome but fails to work properly in Unity.

In unity issuing the command leaves a black strip across the top and down the right side of the screen that does not get drawn correctly. Only the top panel and the unity launcher are draw in these black areas. A rectangle in the bottom left that would be 1024x600 worth of the 1280x750 does get drawn correctly.

Is it possible that compiz is getting the values for screen geometry from two different sources?

Is this a bug or am I just doing something that shouldn't work? Has anyone had success using zrandr to get higher than native resolution in unity.

---

### Post by MaxWiz on 2011-05-14
I thought the attached screen shots might aid my poor explanation.

---

### Post by dknight212 on 2011-05-18
Exactly the same problem and, oddly, same laptop running 11.04 (fresh install).

In 10.10 (running Unity as well) I was able to run:

xrandr --output LVDS1 --mode 1024x600 --scale 1.25x1.25

to get 1280x750.

Now I get the same black sections as you.

I've looked on the Voria forums to see if anyone else has the same problem.

---

### Post by dknight212 on 2011-05-18
Aha, potential solution: run unity --replace (via ALT-F2) after running xrandr.

---

### Post by MaxWiz on 2011-05-19
That does seem to work. This would suggest that we need to launch unity after xrandr. I will investigate running xrandr early in the start up.

Ideally I would like the setup I had in 10.10. I would work with native resolution and run my script by hitting a function key to switch to 1280x750 when needed. Not an option if xrandr needs to be in place before unity :confused:

---

### Post by dknight212 on 2011-05-20
Yep, unity --replace is not the best or fastest solution but it's workable. Not sure why I could do without --replace when running xrandr on unity on 10.10, can't remember if I was running 2d or the full thing as I played around a lot.

---

### Post by markemberson on 2011-05-20
Ive got this to (acer aspire one), but this was working fine when i first installed 11.04, seems an update has broken it.

Its not too much of a hardship to run the above when needed, i tend to use this all the time and i had it set to run on startup before, hopefully it will be fixed again soon :P

---

### Post by gpunktet on 2011-05-26
Hey there,

I have the same problem too, but with two monitors (LVDS and VGA) Actually I think, the desktop size is still as big, as the "old" resoluation was and is not adjusted. 

By the way:

compiz --replace

works as good as 

unity --replace

for me ...

---

### Post by craigtyson on 2011-05-27
So I'm getting the same issues with a 1005HA eeepc

If I scale my 1024x600 lcd display to 1024x768 I get a blank band at the top or sometimes the bottom of the screen + other random strangeness with the status bar.

unity --replace fixes it but if I run 
unity --replace& (ie just spawn it off on its own process)

from a terminal in the desktop ie under my account, I only have to do it once and can go back and forth between resolution without issue.

Would this be some sort of permissions issue then???  Ie unity running under the wrong account or with the wrong permissions

C

---

### Post by dknight212 on 2011-05-30
Craig

That's interesting, I can repeat the same result, ie running unity --replace& in terminal, once the screen resolution has been set to the largest size, then I can freely switch resolution without executing unity --replace again and no black bands.

For the record, Unity picks up the resolution change and reports:

  Monitor 0(primary)
   0x0x1280x750

** (<unknown>:7545): DEBUG: PanelController:: Updated Panel for Monitor 0
** (<unknown>:7545): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=750

(Stating the obvious) So presumably this is not happening properly when the screen resolution change is run before unity --replace&

---

