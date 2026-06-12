---
title: "DV6 laptop issue"
date: 2011-09-18
forum: Hardware
---

### Post by walding on 2011-09-18
Hi,

I installed ubuntu 11.04 on my DV6 laptop and every thing went fine, BUT

when I shutdown it or restart it, it crashes.
So I have to hold the power button until the laptop powers off
specs:
HP pavilion Dv6
core i7
4gb ram
ati graphics card

This problem seems to be common to all those with DV6 laptops.  Mine is the 3180EA, but others have reported exactly the same problem, with no solution.


This is the second installation of Ubuntu I've done on it.  The 1st time, I also activated the restricted driver for the ATI graphics card.  However, this resulted in Ubuntu not booting up at all!

SO, I suspect that it's the combination of integrated Intel and dedicated ATI graphics cards that is the problem?
I have no idea how to confirm this, how to find what is freezing the shutdown process, or how to fix it!

Any ideas?  There are some other threads that cover this, but I have been advised not to add this to those, but to start a new thread instead.  If you'd like me to add links to the other threads I've found, I'll do so...the etiquette for what to do here isn't clear to me, sorry.

Thanks.

---

### Post by mörgæs on 2011-09-18
You are more than welcome to link to relevant threads and web pages. It will only help people from suggesting the same solutions once more. 

How does the computer behave if you use only open source drivers?

---

### Post by walding on 2011-09-19
This one is the most helpful, as there is a reply with more info....
[http://ubuntuforums.org/showthread.php?t=1786836](http://ubuntuforums.org/showthread.php?t=1786836)

No, it doesn't behave with just open source drivers.  It won't shut down at all (freezes during shut-down).  The only solution is to hold the power button until it turns off, which clearly is not ideal!

Is there a way to find out what it is that's causing the freeze?
And, my second question is - if it turns out to be the graphics cards with inadequate drivers, is there a way round that?

---

### Post by owiknowi on 2011-09-19
power off 'the hard way' as a last resort, when really nothing works anymore, can damage your computer.
with some distro's you can find out whether they work at all, is by using a live version; some distro's won't even boot, but ctrl-alt-del then still works.

---

### Post by walding on 2011-09-19
Indeed!  Hence the reason I'm using Windows at the moment...
...which is damaging my sanity.

---

### Post by owiknowi on 2011-09-19
just to keep you from going insane: you could try pardus 2011.1 for the time being (multi boot).

it runs remarkably well on this particular hp dv6 series (uses the intel chipset and disregards the ati card, still works like a charm, though).
even the wireless card works out of the box...

tried to fire up my ubuntu 11.04 installation in order to test something, but alas, as usual the computer went straight to zero kelvin.

---

### Post by walding on 2011-09-19
Thx.  Perhaps it's about time I tried another Distro.  I tried so many pre-2006, but settled on Ubuntu.
I was hoping to do video editing on this, so would still prefer it to use both cards!
A

---

### Post by mörgæs on 2011-09-19
Trying various distros is always a good idea.

If you want more help on the graphics drivers for Ubuntu, this thread is worth reading:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by SeijiSensei on 2011-09-19
What if you shutdown from the menus rather than using the power button?

What if you type "sudo shutdown now" at a terminal prompt?

---

### Post by monarch12 on 2011-09-19
Hi,
I bought a HP DV6 3043TX an year ago. I very recently installed ubuntu  10.10 32 bit on it. So I'm a newbie at this stuff. In windows, there is a  functionality called the Switchable graphics using which I could switch  between HD 5650 and Intel HD. After I installed ubuntu, additional  drivers for ATI were asked for, which I clicked activate in the  additional drivers menu. The computer wouldnt boot at all into the  gnome-desktop at all after that. So I removed the X11 configuration  files and restarted it and it worked well. 

Now when I try to the Visual effects in the appearance menu to Normal or  high, it is reverting to none. I've installed Compiz hoping that it  would help, but it didnt.  What should I do to get these right and  fixed?Can you please help me out in these two regards?

Thanks

---

### Post by walding on 2011-09-20
I've tried shutting down every way I know,  including the terminal.  It freezes at the aubergine screen.

---

### Post by walding on 2011-09-20
I have now successfully downloaded and installed the ATI driver.  Still same shutdown problem, though!

---

### Post by mörgæs on 2011-09-20
[http://ubuntuforums.org/showthread.php?t=1846962](http://ubuntuforums.org/showthread.php?t=1846962)

---

### Post by mörgæs on 2011-09-21
> **monarch12 said:**
> Hi,
I bought a HP DV6 3043TX an year ago. I very recently installed ubuntu  10.10 32 bit on it. So I'm a newbie at this stuff. In windows, there is a  functionality called the Switchable graphics using which I could switch  between HD 5650 and Intel HD. After I installed ubuntu, additional  drivers for ATI were asked for, which I clicked activate in the  additional drivers menu. The computer wouldnt boot at all into the  gnome-desktop at all after that. So I removed the X11 configuration  files and restarted it and it worked well. 

Now when I try to the Visual effects in the appearance menu to Normal or  high, it is reverting to none. I've installed Compiz hoping that it  would help, but it didnt.  What should I do to get these right and  fixed?Can you please help me out in these two regards?

Thanks

There is a number of DV 6 threads in Hardware and Laptops, so I took the liberty of moving your post.

---

### Post by walding on 2011-09-21
I'm now away from home for a week, but think the best next step would be to do a verbose shutdown so I can see where it gets stuck (I'll post back here).  
Have totally forgotten how to do a verbose shutdown without the graphics etc. - can anyone tell me please?

Thanks,

A

---

### Post by walding on 2011-09-29
Hello,
Just wondering if anyone has any ideas on how I might start to diagnose and fix this problem, please?
Thanks!

---

