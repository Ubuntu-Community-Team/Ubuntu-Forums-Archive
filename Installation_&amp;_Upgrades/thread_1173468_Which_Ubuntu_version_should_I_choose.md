---
title: "Which Ubuntu version should I choose?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by CynicalPsycho on 2009-05-29
I'm trying to decide which version of Ubuntu I want to run.

I'm stuck between 2 things really: 
The version 8.04, 8.10, or 9.04 
and 64 vs 32 bit.

My machine specs
I'm running a 64 bit dual core processor with 4 gigs-o-ram.
and I'm currently running 64 bit ubuntu 8.10

And so far I've had no trouble running this machine, But I have a new HDD that I want to install ubuntu on, and I'm trying to determine the best route to take.

Now from my understanding of it [SIZE="5"](please feel free to correct any false assumption I have.)[/SIZE] there are pros and cons to both the 64bit and 32bit builds.

The pros of the 64bit being the ability to run the select few 64bit programs that perform better than 32bit but have the con of being relatively less compatable with other programs and machines that aren't 32 bit...

While the pros of 32 bit are they're more compatible with more programs and machines than 64 while their con is their inability to run programs at the 64bit level.

With these assumptions it makes me want to lean more toward a 32 bit version, partly because the HDD i plan on installing this OS to is in an enclosure that enables it to be more mobile and work on various computers. That and I haven't seen much of a marked improvement in 64 bit programs.

So unless anyone has any further evidence to present to the court in favor of 64 bit I'm thinkin ill go 32...

as for the version I'm also kind of torn.
i know the 8.04 is under long term support
and I know that I liked how 8.10 ran on my system
but i'm also curious about 9.04 but i'm also worried about compatibility issues in it...

does anyone have any input on the subject? all replies are appreciated :)

---

### Post by ParanoidMetroid on 2009-05-29
Nvidia display drivers are a little problematic in 9.04 (but still easy to correct, assuming it's even an issue for you).  Other than that I'm not really noticing any significant difference between 9.04 and 8.10, and the few changes that I have noticed are unquestionable improvements.

As for the 64 vs 32 bit debate, it depends.  If you're only installing from trusted ubuntu repositories, I suggest 64 bit.  I haven't run into any compatibility problems there.  But if you need to install and run programs that can't be made available in the synaptic package manager and want to make life easier, I suggest using 32 bit.

Edit: I just now noticed you plan on making your new HDD mobile.  In that case I definitely suggest 32 bit.

---

### Post by CynicalPsycho on 2009-05-29
> **ParanoidMetroid said:**
> Other than that I'm not really noticing any significant difference between 9.04 and 8.10, and the few changes that I have noticed are unquestionable improvements.
What sort of improvements you speak of?

---

### Post by ParanoidMetroid on 2009-05-29
Nothing major.  It loads up faster, and the menus are better organized.  I'm also noticing better video streaming, however that could be because I installed my video codecs using ubuntu-restricted-extras instead of letting totem or firefox attempt it like I did in intrepid.  Another thing I like is the way jaunty handles notifications by using a quick two second pop-up in the upper-right corner (it makes programs like liferea and pidgin much nicer IMHO).  The big one though is the speed: it's not a lot, but it is noticeable.

One small thing I forgot to mention is that some of the configuration files got renamed.  For example if you need to edit your alsa configuration file it's been renamed to alsa-base.conf instead of simply alsa-base.  Just something you might want to be aware of.

---

### Post by Mark Phelps on 2009-05-30
I'm going to make a suggestion here -- do what works best for you ...

The different versions of Ubuntu DO behave differently due to decisions made by the developers regarding what defaults to set at install time.

The best way (IMHO) to determine "what works best for you" is to download and burn LiveCDs of the different versions, boot from each one (in LiveCD mode) and see which one works best -- from the standpoint of detecting the hardware automatically.

As has been said, 9.04 has been plagued by display problems due primarily to the dropping of restricted driver support by ATI/AMD and some known problems with intel video chipsets.

Also, there are other Linux versions you might want to consider.  The latest Mint (v7) is getting rave reviews as is OpenSuse.  Check out distrowatch.com for the complete set, including download locations and reviews.

---

### Post by ExWindowsDude on 2009-05-30
> **Mark Phelps said:**
> I'm going to make a suggestion here -- do what works best for you ...

As has been said, 9.04 has been plagued by display problems due primarily to the dropping of restricted driver support by ATI/AMD and some known problems with intel video chipsets.

Also, there are other Linux versions you might want to consider.  The latest Mint (v7) is getting rave reviews as is OpenSuse.  Check out distrowatch.com for the complete set, including download locations and reviews.


Mark, I stumbled on this thread by accident. I'm on a Dell Vostro 200 (hey, got it free)---*Grin*

Anyway--when I used Xubuntu 7.04---everything installed PERFECT(video drivers and Sound, etc.).

I did a brand new install of Xubuntu 9.04 and have no sound (and display looks like a "vanilla" driver).

Is this part of the "known" issues you speak of?
Did not mean to go  off topic---but since it's part of your answer....did not want to create a new thread....

BTW---even with the troubles---I recommend Xubuntu---CynicalPsycho

Simply because it's "easy"---and their is LOTS of support in the "universe" of packages...

---

### Post by badaveil on 2009-05-30
You may find 9.0.4 compatible with your pc but the real question is have the manufacturers of your current and future peripheral components come up with 9.0.4 drivers. Last June, when I installed 8.0.4, I found that not many manufacturers of printers have 8.0.4 drivers but HP and Brothers so I ended up with a Brothers Printer. You will find compatibility of drivers is the main issue.

---

### Post by Mark Phelps on 2009-05-30
The reference to "known issues" is simply that, newer is not necessarily better.  I have a laptop that works great with 8.04 but newer versions present unfixable problems.

Also, not all variations of Linux install or work equally well on the same machine.  The different versions use different versions of the kernel, different versions of Xorg, and different versions of apps.  Some combinations work better than others.

I have one laptop that won't install ANY version of Ubuntu newer than 7.04, works great with PC Linux OS 2007 but can't handle 2008 or newer, works great with OpenSUSE but not other recent Linux distros.

So, just because Ubuntu 9.04 is out doesn't mean that it's necessarily the best choice for a particular machine.

---

### Post by badaveil on 2009-05-30
Mark

Very interesting what you wrote here.

Q: If I just wanted to stick to Ubuntu and 8.0.4 didn't work on a pc/notebook would be it wiser to choose the latest version or older versions?

---

### Post by ExWindowsDude on 2009-05-30
> **badaveil said:**
> You may find 9.0.4 compatible with your pc but the real question is have the manufacturers of your current and future peripheral components come up with 9.0.4 drivers. Last June, when I installed 8.0.4, I found that not many manufacturers of printers have 8.0.4 drivers but HP and Brothers so I ended up with a Brothers Printer. You will find compatibility of drivers is the main issue.

badaveil you are correct, I should have been more clear. 

CynicalPsycho--(before all else, make sure the distro is supported by your computer manufacturer). 

For example, I installed 7.04 everything worked great on my Dell, when I installed 9.04....my sound and Video is not "perfect"---I just thought I might have to download other drivers...Actually, it's a known Dell Issue...and the fix is installing the Dell ISO. (found this on another forum thread). 

[http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)


So, I guess I should ask you what Model/Manuf. CPU you are using?

---

