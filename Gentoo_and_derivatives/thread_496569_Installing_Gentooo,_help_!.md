---
title: "Installing Gentooo, help !"
date: 2007-07-09
forum: Gentoo and derivatives
---

### Post by mips on 2007-07-09
I'm considering installing Gentoo on my laptop via a minimal install cd + net.

Anyone here care to act as a mentor when I get stuck ?

---

### Post by coffeecat on 2007-07-09
> **mips said:**
> when I get stuck ?

When??!! Have faith in yourself. :lol:

I'm not offering to act as a mentor but, believe me, it's not as difficult as it might appear, particularly as you already have considerable Linux experience. Make sure you have the [Gentoo handbook]("http://www.gentoo.org/doc/en/handbook/index.xml") handy - preferably displaying on another machine or printed out - and you should be fine.

Don't forget [Gentoo forums]("http://forums.gentoo.org/").

You'll almost certainly need to compile your own kernel to get it to run properly on a laptop, but genkernel should keep you going until then.

A few random tips: Once you have a working system - even one without a GUI - emerge gentoolkit and read up about revdep-rebuild. You'll be needing it before long. :wink:

You'll need to be updating config files in /etc on a fairly regular basis after most updates. I prefer dispatch-conf to the standard etc-update, but you might wish to research this.

You might want to bookmark the [Gentoo Wiki]("http://forums.gentoo.org/"). It's unofficial which is why it's not linked on the main Gentoo site. Also, be warned that it's somewhat curate's egg-ish. Much of it is good, but some is outdated or even misleading.

Best of luck. :)

---

### Post by zaratustra on 2007-07-09
Don't ask for help before you even need it:)  No problem, we will help ya. Maybe not in few minutes, but in few hours we will.

---

### Post by mips on 2007-07-09
Busy getting the stage3 tarball, so far so good.

I know what ssh is & does but have never used it until now and I must say its the dogs ********. I simply just copy and paste from my desktop to a terminal which I have a sshd session running in, great stuff.

---

### Post by termite on 2007-08-07
I went over to Gentoo a few months ago, intending to dual-boot with Ubuntu.  Since day 3 (when I finally got KDE to not look stupid), I haven't booted  back into Ubuntu at all.

Nothing against Ubuntu, it's awesome, but Gentoo really is more fun, and I've learned loads.  To think that a few months ago I didn't know what chroot'ing even was!

Have fun!  You will get stuck, and then you'll recompile some stuff, and they you'll edit some config files, and then you'll have a fast as hell system with exactly what you want.

One tip: don't use the Desktop profile.  It has way way too many USE flags set and will install too much.  Figure out what USE flags you need and install that way.  You'll save yourself a lot of recompilation.

I don't hang out on here much, but feel free to PM me on the Gentoo forums.  I'm termite there as well.

---

### Post by Bachstelze on 2007-08-07
> **termite said:**
> 
One tip: don't use the Desktop profile.  It has way way too many USE flags set and will install too much.  Figure out what USE flags you need and install that way.  You'll save yourself a lot of recompilation.

Why ? Just disable the USE flags you don't need in your make.conf...

---

### Post by Lord Illidan on 2007-08-07
> **mips said:**
> Busy getting the stage3 tarball, so far so good.

I know what ssh is & does but have never used it until now and I must say its the dogs ********. I simply just copy and paste from my desktop to a terminal which I have a sshd session running in, great stuff.

Same here, used it at work, was installing Gentoo from Windows :P

Also, what I did on my home pc, was compile many of the needed things under a chroot on Ubuntu...

---

### Post by termite on 2007-08-07
Because the desktop profile is bloated.  I spent hours the other day disabling USE flags and ended up slimming down by around 100 useless packages (mostly gnome).

I think adding flags is better than disabling them.  There's less breakage that way and you learn more.

---

### Post by Bachstelze on 2007-08-07
Well, why did you install the Gnome packages at all, if you didn't want them ?

---

### Post by termite on 2007-08-07
Because I was a silly n00b who came from Ubuntu and didn't know what was going on!  So I just picked the Desktop profile, not realizing how insanely huge it was.

Now I'm am wiser to the ways of the Pygoscelis papua :)

---

### Post by HardcoreLinux on 2007-10-16
Just get another computer and read the manual you should be fine.

---

### Post by handy on 2007-10-17
> **termite said:**
> Because I was a silly n00b who came from Ubuntu and didn't know what was going on!  So I just picked the Desktop profile, not realizing how insanely huge it was.

Now I'm am wiser to the ways of the Pygoscelis papua :)

Sheesh, & my wife calls *me* obtuse!

Thank you for educating me about the Gentoo penguins.

***_[http://animaldiversity.ummz.umich.edu/site/accounts/information/Pygoscelis_papua.html](http://animaldiversity.ummz.umich.edu/site/accounts/information/Pygoscelis_papua.html)_***

---

### Post by happysmileman on 2007-10-17
> **termite said:**
> I went over to Gentoo a few months ago, intending to dual-boot with Ubuntu.  Since day 3 (when I finally got KDE to not look stupid), I haven't booted  back into Ubuntu at all.

Agreed, now Ubuntu is completely wiped and Compiz-fusion has never run faster. Though it can take a while to set up at first

---

### Post by handy on 2007-10-23
After spending 2 very enjoyable days installing 64bit Gentoo from the minimal CD, I reached an impasse, the entire 2nd day was spent attempting to get modular or monolithic X to function?  No help on the Gentoo forum solved the problem...

So I thought I would use the 32bit Live CD, & start again.  Bad move, the Live CD is full of bugs & works for very few people, according to posts I read on the Gentoo forum.

Having had some days away from the Gentoo install, during which I spent a day to install & setup Kubuntu 7.10 on my 2nd machine, I went back to the Gentoo install, did some reading on the Gentoo forums & have decided that I will cancel my current plans of installing Gentoo for the time being.

It is unfortunate that the Gentoo dev's have been stretched to the point of releasing poorly tested software, I now understand what people were referring to in the Sabayon forums, with regard to Gentoo's problems.

Hopefully it won't take too long before most users will be able to follow the Gentoo Handbook's instructions to a successful installation.

For those interested the following link is very informative regarding these problems:

***_[http://forums.gentoo.org/viewtopic-t-558042-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-558042-postdays-0-postorder-asc-start-0.html)_***

---

### Post by coffeecat on 2007-10-23
> **handy said:**
> So I thought I would use the 32bit Live CD, & start again.  Bad move, the Live CD is full of bugs & works for very few people, according to posts I read on the Gentoo forum.

I think you'll find that it's a case of a very few people making a disproportionate noise about the trouble they've caused themselves when they used the live installer.

Over a year ago I used the 2006.1 live CD to make an install of Gentoo. It wasn't as straightforward to use as the Ubuntu CD, but it's not meant to be. I got myself a working system and I'm still using the same install, fully and incrementally updated and tweaked over the months, and it's going fine. Perhaps it was just as well that I only found the posts on Gentoo forums about how it was impossible to use the 2006.1 CD to install, **after** I had done a successful install from it. :wink:

Then the 2007.0 CD was released and there was the inevitable moaning and groaning from all the pebkacs. I remember the thread you link to. Intrigued by accusations that the CD was wiping partitions without notice, I tried it out for myself. I can tell you that those accusations are **complete, utter and unremitting bilge and poppycock**. No way could I get the live CD to wipe partitions without warning me first and popping up a yes/no window. Frustrated that I couldn't bork my hard drive this way ( :wink: ) I continued on and did a completely successful fresh install with it. :roll:

If I remember correctly, there are quite a few other inaccurate complaints on that thread. I couldn't reproduce the sudo -s problem of the OP and there's a particularly inspired piece of drivel about grub somewhere.

Don't mistake the whingeing of those with finger and brain trouble with the comments of the experienced Gentoo crowd, who much prefer a console install and  who make reasonable points about some of the bugs in the GUI installer. Yes, the GUI installer has a lot of rough edges, but don't believe a lot of what is in that thread.

Good luck if you try again. Read the handbook carefully and you should be fine.

> **handy said:**
> Hopefully it won't take too long before most users will be able to follow the Gentoo Handbook's instructions to a successful installation.

Err... Actually, many people have been following the handbook's instructions to a successful installation for some years now. The Gentoo handbook is generally regarded as a very fine piece of documentation. Why not try the stage 3 installation from a tarball?

---

### Post by coffeecat on 2007-10-23
**handy**, another thought. One problem with Gentoo is that you have a chicken and egg situation. It's difficult making a successful install if you don't have some experience of running and maintaining Gentoo. In the year prior to making my 2006.1 install I had installed Gentoo twice, but with only partial success. But I had learnt something and perhaps this is why I was able to find my way around the admitted bugs of the GUI installer. For example, the file make.conf doesn't make (no pun intended) much sense unless you've been running Gentoo before or have some experience developing and compiling software. It's all explained in the handbook but nothing beats hands-on experience.


And even then it's a steep learning curve..... :?

Have fun! :)

---

### Post by handy on 2007-10-23
***coffeecat:***  Thanks for your posts.

Sorry, I didn't mention that I had tried the LiveCD install, which failed crashed on me.

I agree that some are prone to whine, still I have watched in the Ubuntu forums that people will have all kinds of trouble, when I have had a smooth upgrade or fresh install.  I have also had very difficult problems to track down, which turn out to be motherboard chipset related.  There are so many variables involved, it is amazing that computers work at all! :lolflag:

I just followed a very well written wiki howto for the installation of Arch Linux, which went very well until it was time for the initial upgrade of the system, then it fell in a heap, with unsynchronized dependencies!

I think I'll just enjoy the simplicity of Kubuntu 7.10 for a while on both machines until I get bored or inspired to try something else.  Hopefully 3.5 Sabayon will not waste cpu cycles, which is what started my adventures into Gentoo & Arch! :)  Which has been fun & educational, but I do have other things that I would like to use the computer for.

---

### Post by rsambuca on 2007-10-23
handy, I can't help but think you are making the gentoo installation much more difficult than it should be.  If you do a stage 3 tarball installation, you can do it from your kubuntu installation, and it doesn't take more than an hour of initial fiddling to get the base install.  Then let it run overnight compiling your desktop environment of choice.

---

### Post by handy on 2007-10-24
> **rsambuca said:**
> handy, I can't help but think you are making the gentoo installation much more difficult than it should be.  If you do a stage 3 tarball installation, you can do it from your kubuntu installation, and it doesn't take more than an hour of initial fiddling to get the base install.  Then let it run overnight compiling your desktop environment of choice.

I didn't have any trouble until it was time to install X.  As previously stated I tried for many hours, different ways, different X's?  That was via the stage 3 tarball.  Due to that I tried the liveCD which I found to be poorly named! :-)

---

### Post by handy on 2007-10-24
I'm currently installing Sabayon 3.4f; the liveCD identifies my graphics card & installs the latest nVidia binary drivers for it, which is something that all my efforts tried in four different ways, each at least twice, could not accomplish in my Kubuntu 7.10 install on the same machine.

This box must have a nasty combination of hardware as far as Kubuntu 7.10 is concerned.  Perhaps Gentoo as well?

At least Sabayon likes it!

I'll put up with beagled.helper stealing my cpu cycles, at least I'll be able to join my guild in Guild Wars again... & blast some Xivilai to vent my latent frustration in Oblivion! :lolflag:

***[Edit:]** The quick Sabayon install is done, not only graphic card with latest binary drivers, also my monitor is correctly identified & setup.  It can be done, & I know full well that Ubuntu will do it right too in a future release.  Those of us who need improvements to make it easy for us too, naturally look forward to [I]that* release.[/I]

---

### Post by cotcot on 2007-10-28
> **handy said:**
> 
It is unfortunate that the Gentoo dev's have been stretched to the point of releasing poorly tested software, I now understand what people were referring to in the Sabayon forums, with regard to Gentoo's problems.

Hopefully it won't take too long before most users will be able to follow the Gentoo Handbook's instructions to a successful installation.

For those interested the following link is very informative regarding these problems:

***_[http://forums.gentoo.org/viewtopic-t-558042-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-558042-postdays-0-postorder-asc-start-0.html)_***

It is not the LiveCD that is buggy. I have used it a lot without any problem. It is only the graphical installer on the liveCD that is not performing well. This is well known in the gentoo community and it is not recommended at all to use this installer. Gentoo is to be installed manually following the very good handbook. If you want gentoo getting installed with a graphical installer try sabayon; but do not expect a higher speed than ubuntu. (I have tried it myself)

---

### Post by Skarjoko on 2007-12-29
> **cotcot said:**
> It is not the LiveCD that is buggy. I have used it a lot without any problem. It is only the graphical installer on the liveCD that is not performing well. This is well known in the gentoo community and it is not recommended at all to use this installer. Gentoo is to be installed manually following the very good handbook. If you want gentoo getting installed with a graphical installer try sabayon; but do not expect a higher speed than ubuntu. (I have tried it myself)

Man, I've been trying to install gentoo from the LiveCD for a week now, with it failing every single time. Both the GTK and dialog-based installers don't work for me. *sigh*, all that time wasted...

I'm gonna give the install cd a go later on today. Does the install cd allow you to pick and choose the CFLAGs you want, or do you have to manually recompile the kernel after the install?

---

### Post by rsambuca on 2007-12-29
> **Skarjoko said:**
> Man, I've been trying to install gentoo from the LiveCD for a week now, with it failing every single time. Both the GTK and dialog-based installers don't work for me. *sigh*, all that time wasted...

I'm gonna give the install cd a go later on today. Does the install cd allow you to pick and choose the CFLAGs you want, or do you have to manually recompile the kernel after the install?

Why don't you just do the stage3 tarball installation?

---

### Post by cubekid on 2008-01-07
Why would you do anything but the stage3 install? ;)

No, but seriously, the stage3 install is the best way to install gentoo. you just can't be 1337 without it :lolflag:

---

### Post by Bachstelze on 2008-01-07
> **cubekid said:**
> 
No, but seriously, the stage3 install is the best way to install gentoo. you just can't be 1337 without it :lolflag:

Yes, you can. If you do a stage1 ;)

---

### Post by mips on 2008-01-07
> **HymnToLife said:**
> Yes, you can. If you do a stage1 ;)

That depends whether you are into S&M or not.

---

