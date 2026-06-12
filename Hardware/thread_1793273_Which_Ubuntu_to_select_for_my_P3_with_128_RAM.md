---
title: "Which Ubuntu to select for my P3 with 128 RAM"
date: 2011-06-29
forum: Hardware
---

### Post by anix86 on 2011-06-29
Hi Guys,
 
I have this old P3 with 128 MB RAM and it idle for quite sometime.
I am planning to install ubuntu version on it, i know latest flavours of ubuntu do not support this weak h/w conf.
 
but still i want to give it a try, so let me know which version or flavour of ubuntu should i go for.
 
Thanks in Advance..
 
Regards
Anix

---

### Post by ajgreeny on 2011-06-29
Probably all the ubuntu family are too big for that machine, though you might just about get away with Lubuntu.  On my old laptop it uses about 90MB ram at rest,but as soon as I use firefox it goes up a lot, to perhaps as much as 170MB, so your 128 will struggle.

I sugest you have a look at other lower requirement distros, eg puppy, slitaz, DSL (if it's still being developed).

You could also install the ubuntu minimal install CD, [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and then add openbox window manager, xorg and whatever applications you feel you must have.

---

### Post by snowpine on 2011-06-29
128mb RAM is borderline for any modern Linux distribution. I would max out the RAM (or frankly, upgrade to a newer system via Craigslist/Freecycle/Goodwill/family/friends/work if at all possible). 

If you're stuck with 128mb then I recommend learning about the many wonderful command-line (CLI) applications available for Linux. An old computer can be used as a music jukebox, torrent slave, digital photo frame, router, etc. You'll find some good suggestions on this site:

[http://kmandla.wordpress.com](http://kmandla.wordpress.com)

To answer your **specific** question, the only Ubuntu recommended for your system according to the [Ubuntu System Requirments]("https://help.ubuntu.com/community/Installation/SystemRequirements") is the Server edition, which is command-line/terminal only (no GUI). Even then you are at the absolute bare minimum requirements.

---

### Post by psusi on 2011-06-29
You want to run Ubuntu on an ancient PC that is less powerful than your average modern cell phone?  Seriously, just go recycle that junk.

---

### Post by JC Cheloven on 2011-06-29
I disagree with the "throw it away" policy of the wasteful consumer society. I encourage you in your intent. With a pc like that I worked marvels not so long ago. 

Today it could still be used as a desktop pc using Lubuntu or Puppy linux as suggested (make sure to setup some swap space though), or for a CLI home file server.

Best

JC

---

### Post by psusi on 2011-06-29
Recycling a broken down rusted out old clunker is not waste.  It had many years of service; now it is just a waste of electricity to plug it in.

You might be able to fine tune a custom built kernel and get a command line setup going in 128 mb of ram, but not any kind of gui.

---

### Post by snowpine on 2011-06-29
> **psusi said:**
> Recycling a broken down rusted out old clunker is not waste.  It had many years of service; now it is just a waste of electricity to plug it in.

+1. Also there is the intangible cost of **human** resources... Does your time have value? What is the advantage of doing something slowly on outdated hardware when the same task can be performed quickly on modern hardware?

> **psusi said:**
> You might be able to fine tune a custom built kernel and get a command line setup going in 128 mb of ram, but not any kind of gui.

-1. I personally have done 128mb GUI installs of several distros including SliTaz, AntiX, and CentOS. Not that I *recommend* this, but it is possible! :)

---

### Post by psusi on 2011-06-29
> **snowpine said:**
> 
-1. I personally have done 128mb GUI installs of several distros including SliTaz, AntiX, and CentOS. Not that I *recommend* this, but it is possible! :)

Is that a bare X11 server with the most stripped down, basic wm and shell imaginable?  I can't see a gnome session running with that little ram.

---

### Post by snowpine on 2011-06-29
> **psusi said:**
> Is that a bare X11 server with the most stripped down, basic wm and shell imaginable?  I can't see a gnome session running with that little ram.

LXDE, Fluxbox, and Xfce, respectively.

There was a distro called Debris that claimed to run Gnome in a very small footprint, but I never tried it. I do not recommend Gnome (especially the current version) for very old hardware.

---

### Post by BigD77 on 2011-06-29
I have a Pentium 3 HP with 512 MB of RAM.  I loaded it with Lubuntu 11.04 and it runs great.  There are some limits though.  When I tried to stream a radio station and record it with Audacity, that was too much for the processor.  Maxed it out at 100% but the RAM was running at 192 MB of 512.  I may have to create a swap partition if there isn't one already.  For me, it was just a challange to try and see if I could do it.  But it runs quicker than the original OS that was on it when brand new....Windows Mistaken Edition (WinME).

:popcorn:

---

### Post by ajgreeny on 2011-06-29
> **BigD77 said:**
> I have a Pentium 3 HP with 512 MB of RAM.  I loaded it with Lubuntu 11.04 and it runs great.  There are some limits though.  When I tried to stream a radio station and record it with Audacity, that was too much for the processor.  Maxed it out at 100% but the RAM was running at 192 MB of 512.  I may have to create a swap partition if there isn't one already.  For me, it was just a challange to try and see if I could do it.  But it runs quicker than the original OS that was on it when brand new....Windows Mistaken Edition (WinME).

:popcorn:
Nothing specifically to do with the original question, but there are far better ways to stream radio than using audacity to record it.  Try streamtuner and streamripper or just plain old mplayer in terminal for a much less resource hungry way.

However rather than take over this thread, start another, and ask how else it can be done, then link to the new one from here and I'll keep a look out, and try and help you.

---

