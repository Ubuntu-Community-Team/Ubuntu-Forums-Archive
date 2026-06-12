---
title: "Using a modern mouse should not be hard"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by jsma on 2006-06-27
Like a lot of people on the ubuntu forums, I've recently switched from proprietary software to OSS. Ubuntu is great in so many ways (I tried FC5, CentOS and OpenSUSE as well). 

One thing these OS'es all have in common, is that getting multi-button mice to work as advertised is a royal pain, involving endless hours of forum searching, xorg.conf hacking and Ctrl-Alt-Backspace (repeat ad infinitum). Obviously, this is not distro dependent but has to do with something 'under the hood'. I don't know if this is something that should be fixed at the kernel level, or the x server level (I'll set aside the ridiculously restricted config options available in GNOME's gui Mouse Preferences). 

So what is the bottleneck here? Why are so many of us (hundreds if not thousands, just check any distro forum) wasting hours of our lives just trying to get our mice working? What will it take for a group of talented developers to get this fixed so we can all collectively get on with our lives and be productive computer users? If it's money, let's start a fundraiser. If it's a lack of programmers, I'm sure there is enough talent in these forums alone that could assist in this. 

Bottom line: There are hundreds of posts on the ubuntu forums alone of people wrestling with their mouse configurations. Perhaps rather than posting idiosyncratic hacks of our configuration files (which only seem to work for the individual posting them but require additional tweaks for everyone else), we should instead find out how to help wherever help is needed to get this streamlined and integrated so that this process doesn't have to be repeated for each individual install out of many thousands. 

I'm fully aware that I'm a bit ignorant of how the various pieces of software that make a distro fit together. But it seems insane that this many 'people-hours' are being spent getting 'forward/back' buttons working. It seems like this could be supported and integrated at a much lower level (and GNOME could make a better graphical interface to configure these buttons in accordance with modern expectations). If OSS is to really going to take off, the user probably should not be immediately faced with the task of hacking text files to get a mouse working appropriately. 

SO, anyone know what needs to be done and how we can all help get this over with?

"You may say I'm a dreamer, but I'm not the only one."

j-s

p.s. I really love Ubuntu so far, and really appreciate all the hard work that has gone into making this distro a reality. So far, it has been the easiest distro I've worked with (the live cd -> installer approach is beautiful and the most people friendly of all). The community here seems like a real 'community'. I hope that we can pool our resources in a more effective way to eliminate some of the most common frustrations.

---

### Post by simonn on 2006-06-27
[QUOTE=jsma]So what is the bottleneck here?[/QUOTE]

At a guess, I would say that it is a combination of most/all programmers use standard 3 button/scroll wheel mouse and the fact that multi-button mouse all use different undocumented proprietry methods and hacks to enable the multiple buttons.

Don't blame the OS, blame the hardware manufacturers and lack of standards/documentation and the people who support them by buying their products.

It is partly chicken and egg, partly economic and partly moral. I am capable of programming this kind of stuff, but I have far more interesting things to do with my time so I buy hardware I know works with linux and strongly agree with my statement above - do not support manufacturers that do not support you. This means that I have neither the hardware to hack or the incentive to do it. 

The only hardware we (my GF and I) own that did not have linux support, Uwatec Smart Pro dive computer, (any only has crappy support now) I have hacked the protocol for (still need to document it properly though, but it will be included in the next release of [http://gdivelog.sf.net)](http://gdivelog.sf.net)). That was because dive computers are expensive to replace - it cost more than my Linux PC (and after taking into tax into account, my iBook too!) - and we owned it before I stopped using windows.

---

### Post by jsma on 2006-06-27
Points taken. 
As far as how most/all programmers use mice...that's nice, but I thought programmers are programming for non-programmers :) Example: GNOME exists so that people don't have to use CLI to use a computer, etc. Ubuntu et al are targetting non-tech users...the software should be designed around the user and not vice versa. I'm not blaming anyone for the current state of affairs. As I said before, I'm amazed and very grateful to all who have worked so hard to make this stuff available for free. I just am trying to figure out what it will take to improve one not so small problem area for common users.
As I said, I really don't know what it takes to get this going under the hood. If I did, I would solve it for everyone. But from toying with 'xev' I can see that the button clicks register at some level in the OS (to the X server? don't really know what that means). So what can we do to bridge the gap and make it easier to use a gui to say 'use button y for action x'? The clicks are 'heard' by the machine...so why can't this be integrated in a more transparent way? Doesn't seem like we'd have to create config hacks for every mouse ever made. And if we do, I guess we could add these to some sort of collection and have the user pick their mouse from a dropdown...configured and ready to go. I can't even find decent documentation on the options in xorg.conf to even know what's available...for instance "ButtonMapping". I 'get' that this maps physical buttons to logical buttons but what are the logical buttons and what order are they in? 
If someone can point me to any documentation (even poorly written technical documentation) on the 'hackable' option fields in xorg.conf, I'd put effort into writing a more user friendly guide to editing xorg.conf...and if/when I manage to learn programming I'd gladly contribute code.

---

### Post by simonn on 2006-06-27
google on xmodmap.

[http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)

---

