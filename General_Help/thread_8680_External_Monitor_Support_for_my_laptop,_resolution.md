---
title: "External Monitor Support for my laptop, resolution and refresh rate"
date: 2004-12-20
forum: General Help
---

### Post by nehalem on 2004-12-20
Ok, so I got my laptop and I'm getting along ok so far.  I can get a signal to an external monitor but need help in making this a solution that will work.

My laptop is 1680x1050.  My monitors are 1024x768 and 1600x1200.

There are two different issues here.  

First of all is there a way to get XRandR working with the fglrx drivers?  I've noticed that everytime I enable them they XRandR dies.

Now, I want to be able to use my laptop at work and home.  Instead of just using the laptop I want to use external monitors (along with a keyboard and mouse), I find I'm more productive this way.

So I figured I would just switch Resolutions when needed to the external monitors res.  For example, when I connect to the 1600x1200 monitor I simply change to that res and close the lid to my laptop (which turns off my laptop screen).  The problem that comes up here is that I can't seem to get X11 to offer the 1600x1200 opton.  I explicity define the option "1600x1200" and it will offer me more options (like 1680x1200) but not that option!  How can I get the option I need?  

Next is I would like to change the refresh rate for when I use CRTs (in my case when I use my 1024x768 monitor).  But with X being configured for LCD monitor it only offers the 60hz option.  How can I get more options here??

In the end the ideal solution would be to have it so I could click something to go back and forth between the monitors (laptop and LCD).  I know ATI has a laptop mode option but I couldn't seem to get it working....  I guess the last option is to use several configuration files and have to restart my computer (or X but I don't know how) everything time I want to use a different display (not a great solution).

Thanks in advance.

---

