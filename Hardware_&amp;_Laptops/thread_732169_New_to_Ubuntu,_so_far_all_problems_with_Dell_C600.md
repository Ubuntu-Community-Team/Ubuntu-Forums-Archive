---
title: "New to Ubuntu, so far all problems with Dell C600"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by Hansolo1 on 2008-03-22
Read the other posts about this and so far no help because the solutions are not clear or just plane dumb luck.

Tried installing 7.1 about 10 times.  Had to use safe graphics mode to get a screen.  Half the time that did not even work but I always heard the boot up music.  The other half of the time it was so painfully slow I quit several times.  Last night I ran it starting at 6pm, finialy pooped out at 12am.  got as far as the partition loader.  Wow 6 hours to get to that point.  Started agan and fell asleep wok to an I/O error.

Trying alternate text installer now and it has reached installing the base system so it seems to be going well so far.

If you have a C600 dell, don't bother trying Unbunu 7.1 Live CD. Use Xbuntu or try the alternate installer.

I'll post when the alternate installation is finished.

---

### Post by Hansolo1 on 2008-03-22
Ok... I am writting this from ubunto on my Dell C600.

The Alternate installation ISO worked so much better.  Only about an hour to get it done. Recognized my PCMCIA network card automatically and is working well. Maybe have some of the mouse pointer freezes but is not too bad.  Have to check the other posts I saw about that.

Se 166 updates avaliable as soon as I got to the desk top.  Think I'll hold off for a while least something breaks. :-)

More later as I play.

Best,

---

### Post by firecrow8 on 2008-03-22
I had a simlar issue on my Compaq F500 as well.

the deal is this

ubuntu may not be able to detect your monitor/video card settings right away but once you get the system installed and successfully boot into it you should be fine. either becuase you've found the manual settings while in it or it has been able to figure it out.

so:
to get ubuntu to stop detecting things you have to enter extra info into your boot settings

pres f6 at the boot menu (if not installed, pres e if installed)

when you see that long list of things. add some comands at the end

here are hte comands that worked for me:
```
noapic nalapic vga=792
```

once you find the right group of commands to add to your boot string you'll be fine. 

there are a number of posts that helped me under the terms **blank screen** or **monitor issue** and a few others relating to monitor/graphics cards.

you'll get it working...

---

### Post by Hansolo1 on 2008-03-22
Thanks for the tip.

I was able to install without any issues using the alternate (text based) installation.  Once installed it has done a great job detecting everything.  Even found propritary driver to support my Microsoft MN-720 Wireless PC card adapter.

---

