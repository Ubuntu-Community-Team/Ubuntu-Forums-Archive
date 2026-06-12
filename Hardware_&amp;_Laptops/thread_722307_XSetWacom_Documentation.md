---
title: "XSetWacom Documentation?"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by Akoi Meexx on 2008-03-12
Well, after following the tutorial found [here]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133"), I got my Bamboo up and running with the latest linuxwacom development driver. No biggie, I've done this before, just had issues and needed a reformat.

However, when I run wacomcpl, I can only adjust the actions for one of the buttons on the pad itself.  After some more searching, I ran across an earlier post [here]("http://ubuntuforums.org/showthread.php?t=631881&highlight=Wacom+Bamboo") that gives the xsetwacom commands for configuring all four bamboo tablet buttons(I did note that the < and > buttons were in fact transposed. Easily tested and fixed) to some basic functions. < is scroll up, > is scroll down, FN1 is left click, FN2 is right click.

My question is, is there any documentation, aside from using xsetwacom list mod in the terminal, is there any additional documentation on xsetwacom? I've searched here on the forums, I've checked on the LinuxWacom driver site, I've googled. Can't find a thing anywhere. I'd like to reconfigure my < and > buttons on the pad to Undo and Redo, respectively, but have no idea what the key entries would be. I know the modifier gets put in as CTRL, but after that what? :confused:

Not sure if this was more a hardware question or a software question, but any help would be appreciated.

---

### Post by oldsoundguy on 2008-03-12
What you are seeing here and at the Wacom site is a "work in progress" and it is amazing the progress that has been made.  Mostly because Wacom has not only set aside site space (the "lip service" that some manufacturers such as HP do), but actually have real live bodies working on the various issues.  One of the first manufacturers to pull their head out of the sand and realize that the days of Windows are numbered. You can only patch a leaky tire so many times before it has to be thrown away. 
But, thus far there has been no documentation project initiated from what I can tell.  There soon MAY be.

Another hardware area that looks to be coming on board is the makers of display calibration/color management  hardware.  Two software programs competing out there but only one actually is attempting to make theirs automatic and trying to tie it in with existing hardware such as the Eye 1.

It all boils down to demand.

Photographers and graphic artists have long since gravitated to the Mac, but their sell out to Windows via the Intel route, and their really exorbitant price structure is driving  that market to look elsewhere for hardware solutions and they do NOT want Windows because of the inherent vulnerability and instability of the system.

Add to that the fact that whole countries such as China and India will be mostly Linux in the next few years .. and you have some incentive to start moving now .. just that some are either dragging their feet or still feel intimidated by the decertification threats from MS. (Big deal, just as long as their software works .. who cares?)

Just hang in there .. the advances in Linux in the past 3 -5 years from a "basically geek" system to a USER based system is astounding!  I have had a Linux system on at least one computer since Mandrake 4, and really feel that the system is ready for any user willing to work a bit on set up, but still not ready for granny with her eMachine.

Now if the stupid laptop makers would just quit making strictly proprietary garbage, a lot of THOSE issues would go away!

---

### Post by Akoi Meexx on 2008-03-12
Haha, tell me about it. I'm at work right now, and I insist on running Linux on my Dell Laptop. Unfortunately, it's the D830 with Intel HDA audio. **That** was fun getting set up.

I've been using Linux steadily since a RC version of Ubuntu 7.04, but it's been my mistress for a few years.

Thanks for the words of encouragement though, I'll keep an eye on the linuxwacom site then. Didn't realize the site was being maintained by Wacom themselves, pretty swift! :D

---

### Post by Akoi Meexx on 2008-03-12
Rather than edit, I wanted to bring attention to this:
[http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

Google Search site:linuxwacom.sourceforge.net xsetwacom. This might help a lot of people.

**Edit:** While I was able to get the "<" key to work as just CTRL, I couldn't get it to use CTRL+Z. Any pointers?

**Edit 2:** Haha! Lentus Vici, indeed. xsetwacom pad button1 "CORE KEY CTRL \z" = Edit>Undo. Hope this helps anyone else, I'm going to go map redo now and enjoy my graphics work. :D

---

### Post by oldsoundguy on 2008-03-12
Good Find!!

---

