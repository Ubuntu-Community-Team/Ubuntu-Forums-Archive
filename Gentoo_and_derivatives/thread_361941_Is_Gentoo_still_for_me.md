---
title: "Is Gentoo still for me?"
date: 2007-02-15
forum: Gentoo and derivatives
---

### Post by Resurrection on 2007-02-15
Deep in my heart, I love my stable and fast Ubuntu system.

However, as an experiment to learn and see something different I tried Gentoo.  On a separate hard drive of course!  

Well, my experience has not be positive.  It took me a week just to get X to install correctly using portage, and that was the first thing I installed after putting in a bare functional system.  Then, I was able to get GDM installed (after some effort) with the goal of using fluxbox.  I never got that far.  I have been distracted by the fact that system is unable to GLX with my nvidia GeForce 5500 card.  Keep in mind that the same hardware runs Ubuntu 6.10 with Beryl flawlessly.  And it ran Badger and Drake flawlessly as well.  Gentoo forums and even nvnews forums have been unable to solve my mysterious "glx" failures.  

But I really want to stick with trying Gentoo, because:
1)  I don't like being beaten by a machine
2)  I actually love the idea of portage.  Being able to easily (somewhat true) and quickly compile software natively is the biggest draw to me.

I am only going to "play" with this setup, it won't be for any kind of daily use or production.  Thats what Ubuntu is for!

So my question is, should I just try a reinstall (maybe something is so deeply borked that I won't find it)?  Or give up?  Or is there an alternative out there that gives me a Portage-like software management system that maybe won't break things the way that Portage and Gentoo sometimes can?  

Seems like with linux distros you have three choices:  Download source and compile on your own (ala LFS, which can be painful), use a Portage system to download and compile (removing some pain, but adding breakage), or use packaged software and managers (and possibly add bloat to your system).  Is there some other choice I'm missing?

Of you other Gentoo users out there, have you ever been completely conquered by problems on the distro?

As a side note, this forum is more friendly than Gentoo forums.  Did not have a personal bad experience there, but saw some people take a few beatings if you know what I mean.  Thanks for that!

---

### Post by pay on 2007-02-15
You could try Sabayon. It's based on Gentoo but has everything setup for most users with kde and fluxbox installed.

---

### Post by Rodneyck on 2007-02-15
You might want to look over this post I started and look at the link in my initial post, it covers some of what you speak of in this thread. 

[http://www.ubuntuforums.org/showthread.php?t=361550](http://www.ubuntuforums.org/showthread.php?t=361550)

To answer you question, you might want to start over again. I have read on forums where things do not configure properly or break, a complete re-install/re-compile can do the trick. Not sure why, but it does.  I think this is mentioned in the article in that link, if I am not mistaken.

---

### Post by maxamillion on 2007-02-15
Gentoo is a brilliant distro and I must give credit where credit is due ... but I am truly too impatient to run it on anything I own.

---

### Post by Rodneyck on 2007-02-15
> **maxamillion said:**
> Gentoo is a brilliant distro and I must give credit where credit is due ... but I am truly too impatient to run it on anything I own.

LOL... I admire your honesty.  \\:D/

---

### Post by Resurrection on 2007-02-15
Thanks Rodneyck.  I think I will give it one more try (just because I am already 70% through a reinstall right now:) ) but I don't have my hopes up.  After reading the article you linked to, it would seem that gentoo reminds me of something else:  I know some military guys who are tankers for a living (they operate abrams tanks).  Tanks seem uber cool until after talking with these guys you realize that for every hour they spend "having fun" driving their tanks and shooting, they spend about 5 or 6 hours just doing maintenance.  It would seem that Gentoo is that way.  For every week you spend tweaking and experimenting, you seem to spend more weeks trying to figure out how to un-break the things that broke from an emerge.  

I just wish once and for all, someone could settle definitively the myth about whether natively compiled software is faster or not.  That is Gentoo's big drawing card, minimal size and max speed, but is it really true?  I wonder............Then maybe we would all know if we are wasting are time compiling or not.

---

### Post by rai4shu2 on 2007-02-15
In my experience, it depends on the hardware. Some CPUs are better with natively compiled kernels, and others see no real difference.

For example, if you're using a stripped down version of a P4 with a small level 1 cache, you would be better off optimizing for space than speed. It flushes the cache less often, and therefore gives you a huge speed improvement.

---

### Post by runningwithscissors on 2007-02-15
> **Resurrection said:**
> I have been distracted by the fact that system is unable to GLX with my nvidia GeForce 5500 card.  Keep in mind that the same hardware runs Ubuntu 6.10 with Beryl flawlessly.  And it ran Badger and Drake flawlessly as well.  Gentoo forums and even nvnews forums have been unable to solve my mysterious "glx" failures.
Well, I saw your thread there. Getting GLX working is usully as simple as emerging nvidia-drivers and using eselect to set the nvidia driver to handle GLX. (eselect opengl set nvidia) and enabling the Load glx line in xorg.conf.

> **Resurrection said:**
> I am only going to "play" with this setup, it won't be for any kind of daily use or production.  Thats what Ubuntu is for!
Well, I use Gentoo for daily production use _and_ for play ;) 

> **Resurrection said:**
> So my question is, should I just try a reinstall (maybe something is so deeply borked that I won't find it)?
No! Nothing is ever so broken with a Linux system so as to require a reinstall. Usually the problem can be tracked and solved without a reinstall.

> **Resurrection said:**
> Or give up?  Or is there an alternative out there that gives me a Portage-like software management system that maybe won't break things the way that Portage and Gentoo sometimes can?
To be honest, maybe you just had some tough luck. I've known lots of Linux CDs refuse to work correctly for many people. Maybe you just hit bad luck with Gentoo.

> **Resurrection said:**
> Of you other Gentoo users out there, have you ever been completely conquered by problems on the distro?
Nope. ;)
Currently I am battling my broken SELinux policy, but that is not something that is easy to set up to begin with. I am just not finding the time to read the reams of documentation to better understand it.

> **Resurrection said:**
> As a side note, this forum is more friendly than Gentoo forums.  Did not have a personal bad experience there, but saw some people take a few beatings if you know what I mean.  Thanks for that!
The Gentoo forums are known to be rather friendly. They were founded with an express desire to _not_ be like typical Debian IRC and mailing-list users (who were notorious back then for yelling at people asking the most innocuous of questions).
Yes there are a few people who have the #debian mentality (you shouldn't touch Gentoo without a copy of TFM) and they can be a bit abrasive to people who say stuff like, "but this works so easily in Windows", but overall they're as friendly as online forums can get.

---

### Post by yabbadabbadont on 2007-02-15
> **runningwithscissors said:**
> The Gentoo forums are known to be rather friendly. They were founded with an express desire to _not_ be like typical Debian IRC and mailing-list users (who were notorious back then for yelling at people asking the most innocuous of questions).
Yes there are a few people who have the #debian mentality (you shouldn't touch Gentoo without a copy of TFM) and they can be a bit abrasive to people who say stuff like, "but this works so easily in Windows", but overall they're as friendly as online forums can get.

Just stay out of the "Off The Wall" forum and you should be fine.  OTW is not nearly as heavily moderated as are the Cafe and Backyard here.  Just FYI.  :)

---

### Post by runningwithscissors on 2007-02-15
> **yabbadabbadont said:**
> Just stay out of the "Off The Wall" forum and you should be fine.  OTW is not nearly as heavily moderated as are the Cafe and Backyard here.  Just FYI.  :)
Thanks. I'll try to cut down on my OTW trolling. ;)

---

### Post by Resurrection on 2007-02-16
Your right, runningwithscissors about my thread.  But still after posting about glx in there and in nvnews forums, still no luck getting it too work.  So, I don't think the first install was as much broken, as maybe I just gooned it up with bad kernel options (I used genkernel instead of doing config myself, despite my better gut instinct) or use flags.  I am trying it again, although I have to be out of town for the next week or so, so won't be able to try again till next week.  Seems that maybe the automatic configuration scripts like genkernel and xorg-config seem to cause me more grief than gain, I think I will avoid them in the future.  

Yeah, I thought getting glx working would be simple as well, but not true so far.  And if you notice from my thread there, no one had any more suggestions besides the most obvious ones.  Its either something in my kernel or something in the way that gentoo emerges nvidia-drivers.

When I say that I have seen some unfriendliness (not towards me) I am referring to people who try to suggest how to make Gentoo better i.e. maybe providing more versions in Portage than just the most current ones.  Seems people like that get beat up pretty good.  Also folks who try to even provide constructive criticism as they switch away from Gentoo seem to get beat up as well, as if they committed a sin by going back to an easier distro.

Don't get me wrong, I am not bashing Gentoo or their forums.  I like Ubuntu better and these forums better, but I don't fault Gentoo (yet).  I think that I may though if I redo everything and Gentoo still doesn't do glx.  It should not be that complicated.

That brings to mind a question:  On Ubuntu still if I am not mistaken (I am not in front of my machine), aren't the proprietary nvidia drivers installed with two packages:  one for the driver and one for glx?  On Gentoo, to get them you just "emerge nvidia-drivers".  I know I know, comparing .deb packages to Gentoo portage is not a like comparison, but maybe you can see what I am getting at?

---

### Post by runningwithscissors on 2007-02-16
> **Resurrection said:**
> Your right, runningwithscissors about my thread.  But still after posting about glx in there and in nvnews forums, still no luck getting it too work.  So, I don't think the first install was as much broken, as maybe I just gooned it up with bad kernel options (I used genkernel instead of doing config myself, despite my better gut instinct) or use flags.  I am trying it again, although I have to be out of town for the next week or so, so won't be able to try again till next week.  Seems that maybe the automatic configuration scripts like genkernel and xorg-config seem to cause me more grief than gain, I think I will avoid them in the future.  
Maybe a reinstall would be the best option (even though I believe that it isn't necessary). You could pay a bit more attention to the "Configuring NVIDIA drivers part" during the installation and it may work. ;) Because there is no reason for it to not work. If it works with Ubuntu, it _must_ work with Gentoo also.

> **Resurrection said:**
> Yeah, I thought getting glx working would be simple as well, but not true so far.  And if you notice from my thread there, no one had any more suggestions besides the most obvious ones.  Its either something in my kernel or something in the way that gentoo emerges nvidia-drivers.
It has more to do with whether X is finding your driver properly. Lots of things can cause it not to. A conflicting driver in the kernel. The module not being loaded at all, etc.

> **Resurrection said:**
> When I say that I have seen some unfriendliness (not towards me) I am referring to people who try to suggest how to make Gentoo better i.e. maybe providing more versions in Portage than just the most current ones.  Seems people like that get beat up pretty good.
Oh, those people. Yeah, few people like them. If you look at most of their suggestions from the point of view of someone who has used Gentoo, they are really not implementable, nor do they contain any methods or ideas as to how something might be implemented. Hence the dismissal of their ideas.
They're a bit like, you know "I'd love a flying car" kind of suggestions. Sure, we'd all love one, but how are we going to make one?

> **Resurrection said:**
> Also folks who try to even provide constructive criticism as they switch away from Gentoo seem to get beat up as well, as if they committed a sin by going back to an easier distro.
Mostly they provide criticism from their high horse rather than constructive criticism. Like, my productivity is hurt by using Gentoo. Or stuff like, I don't have time for all this compilation stuff. And then go on to se ports and FreeBSD. It's hard to take people like those seriously.

Having said that, yes the Gentoo devsphere is rather political and abrasive. ;) But the users are friendly.

> **Resurrection said:**
> Don't get me wrong, I am not bashing Gentoo or their forums.  I like Ubuntu better and these forums better, but I don't fault Gentoo (yet).  I think that I may though if I redo everything and Gentoo still doesn't do glx.  It should not be that complicated.
It shouldn't. And it isn't. Like I said, it could just be a bit of bad luck for you. I do not expect people to stick to Gentoo despite that. If it doesn't work for you, it's best that you try something else.

> **Resurrection said:**
> That brings to mind a question:  On Ubuntu still if I am not mistaken (I am not in front of my machine), aren't the proprietary nvidia drivers installed with two packages:  one for the driver and one for glx?  On Gentoo, to get them you just "emerge nvidia-drivers".  I know I know, comparing .deb packages to Gentoo portage is not a like comparison, but maybe you can see what I am getting at?
The legacy drivers have that 2 package structure.
Maybe your card uses those. You may need to do some research on that.
The nvidia-drivers package is the newer driver package.

---

### Post by Resurrection on 2007-02-16
No, I have an Nvidia GeForce 5500 PCI 256MB card.  Not a legacy card.

---

### Post by Rodneyck on 2007-02-16
> **Resurrection said:**
> 
I just wish once and for all, someone could settle definitively the myth about whether natively compiled software is faster or not.  That is Gentoo's big drawing card, minimal size and max speed, but is it really true?  I wonder............Then maybe we would all know if we are wasting are time compiling or not.

I would like the answer to this as well. It is actually what has attracted me to Gentoo or Gentoo-based distros, such as Sabayon. Sabayon seemed much faster (with beryl running and AIGLX configured) than on (K)Ubuntu.  Kororaa also seemed to have a speed boost.

---

### Post by Resurrection on 2007-02-16
Yes, I have heard good things about Sabayon, maybe I will try that next.  I just don't like KDE (personal preference) so it would bother me to have all that K-stuff installed that I don't need / don't use.  Is there a version of sabayon or a distro like it that doesn't have KDE?  Kororaa I believe is not being maintained very well, correct?

---

### Post by igknighted on 2007-02-16
> **Resurrection said:**
> Yes, I have heard good things about Sabayon, maybe I will try that next.  I just don't like KDE (personal preference) so it would bother me to have all that K-stuff installed that I don't need / don't use.  Is there a version of sabayon or a distro like it that doesn't have KDE?  Kororaa I believe is not being maintained very well, correct?

Sabayon comes with KDE and fluxbox on the mini edition.  If you install the DVD version you get KDE, Gnome, Fluxbox and a few others I think.  I might recommend just installing the mini and emerging gnome (or whatever DE you want), the DVD has a LOT of extra stuff.  If you like that go for it, but some of the menu's go from the top to the bottom of my screen, so be aware.

---

### Post by Resurrection on 2007-02-16
Thanks for the tip then.  I probably will try Sabayon if I am conquered by Gentoo.  Currently I just down, but not out.  I'm not ready to throw in the towel yet.

---

### Post by RAV TUX on 2007-02-18
> **igknighted said:**
>  the DVD version you get KDE, Gnome, Fluxbox and a few others I think. 

also XFCE and E16.

---

### Post by Resurrection on 2007-02-24
*SIGH*

Well, I tried Gentoo again, only to not even be able to get it to boot.  This after doing nothing different on the previous installs, where at least I had a boot able system.  So I tried Sabayon DVD release:

What a bunch of crap.  There was an option to install the window manager or DE of my choice as promised.  Little did I realize that it would install all the other window managers / environments as well, plus a ton of stuff that I don't want.  I am very disappointed.  Fortunately, the problem is fixed easily, since it didn't affect my Ubuntu install at all.

Is there a way to force Sabayon to just install one environment and the programs that go with it, i.e. If I choose KDE, just KDE apps and not all the Gnome stuff?  I am not pleased with all the extra stuff that is installed.

---

### Post by RAV TUX on 2007-02-25
> **Resurrection said:**
> *SIGH*

Well, I tried Gentoo again, only to not even be able to get it to boot.  This after doing nothing different on the previous installs, where at least I had a boot able system.  So I tried Sabayon DVD release:

What a bunch of crap.  There was an option to install the window manager or DE of my choice as promised.  Little did I realize that it would install all the other window managers / environments as well, plus a ton of stuff that I don't want.  I am very disappointed.  Fortunately, the problem is fixed easily, since it didn't affect my Ubuntu install at all.

Is there a way to force Sabayon to just install one environment and the programs that go with it, i.e. If I choose KDE, just KDE apps and not all the Gnome stuff?  I am not pleased with all the extra stuff that is installed.use the mini edition CD, it only installs KDE and fluxbox.

---

### Post by Dylnuge on 2007-02-25
I like Ubuntu fine. There are a few things I miss from my semi-working Gentoo installation-the three weeks it took, the four more weeks of wireless strugles, and failure to get ALSA to work-ever-were not among them.

However, if anyone is interested in learning a **ton** about Linux, Gentoo trumps. The three weeks of installation were the most informative of my life, and having seen about every common problem you can have thrown at you, I am now much better at helping people on the forums.

I only gave up Gentoo because I finally decided that I had passed the break-even point on time-gained vs time-lost. Actually, I probably passed it a while ago. Trust me, there was no wat Gentoo was going to speed up my process enough to save me three weeks over Ubuntu. Maybe an hour. And thats not counting the endless suffering of upgrades, USE flags, lack of binaries, and the lack of a graphical package manager or at least something that said "bla is not a package, but there are 2 packages with bla in them."

---

### Post by Resurrection on 2007-02-25
> **RAV TUX said:**
> use the mini edition CD, it only installs KDE and fluxbox.

I'm working on figuring out Virtualization (want to try out 64 bit versions on a different machine, but not willing to dual boot or trash the Windows install on there quite yet), so I think I will just try it out on VMware after I get it figured out a little better.

One day, I hope to see my dream come true of a DVD release of a distro that as part of the install process gives you only the most basic system with a DE or window manager, and then before installation completes, gives you a long list of software that can be installed and you just tick all the boxes of what you want installed.  Sort of like Automatix built into the install process.   I actually saw a customized Windows installation that worked well this way.  After you installed windows, you got a menu that allowed you to choose software, registry tweaks, and other hacks and they would all be installed after you were done choosing.  Saved a lot of time when reformating/reinstalling.

---

### Post by coplan on 2007-04-23
Sounds wierd to be posting on the Ubuntu forums...but I love Gentoo.  So why am I using Ubuntu right now?  Simply put, it's better for my laptop.  There's a lot of hardware that I can't figure out how to configure in Gentoo that Ubuntu seems to do flawlessly.  So this is a bit of a research mission for me.  I intend to go back to Gentoo as soon as I learn enough about my laptop to properly configure things in Gentoo.  It sounds twisted, but that's what I'm doing.  

The stumbling blocks for me were to specific pieces of hardware:  My SD card reader (a Texas Instrument reader that uses the tifm modules) and my media buttons on the keyboard.  Struggled with them for several weeks and loaded a Kubuntu disk on a whim.  So far, I love Ubuntu, and I may continue to use it on my laptop.  But I miss the USE flags terribly and the easy-upgrade system.  Apt is great, but its nothing compared to portage when you want to update every single package on your system.

If you're serious about Gentoo...take lots of notes on your working Ubuntu system.  But be prepared, Gentoo is definately a love/hate relationship.  As an OCD tweaker with 12 years Linux experience, I have some strong biased views that I can only achieve with distros like Slackware -- or Gentoo.  But for general production use, Ubuntu seems to be better and more stable.

---

### Post by monoment on 2007-04-24
I have played with Gentoo over the years and I decided that it is not for me. I expect stability and ease of use from my operating system and Gentoo cannot guarantee me any of that. If you feel happy to re-compile a new glib for a few hours with every patch and like to watch stuff getting "emerged" then this might be a perfect distribution for you. The big advantage is that you can compile the packages the way _you_ want them to be compiled, but you can do that with any other distribution as well.

To me, it is a slightly improved LFS. Good to learn and teach Linux and get to know your system. But that's where it ends as well.

If you like the learning curve of LFS, customized builds of Gentoo and ease of use of Ubuntu, then look at "Arch" ([www.archlinux.org](www.archlinux.org))

---

### Post by cotcot on 2007-05-09
Gentoo is a challenge. I got all my troubles solved with the help of the forums except 1 (the driver for my epson printer). 
If you consider a reinstall then read carefully the idea behind the use flags. If I would reinstall I would put them more in package.use than in make.conf.

---

