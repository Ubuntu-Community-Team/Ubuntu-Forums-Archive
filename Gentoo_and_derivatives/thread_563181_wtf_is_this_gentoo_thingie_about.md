---
title: "wtf is this gentoo thingie about?"
date: 2007-09-29
forum: Gentoo and derivatives
---

### Post by Chymera on 2007-09-29
so, i've been using sabayon for quie a while now, and wanted to see what the distro on which it is based is like... 
SO why is it that you have to compile everything? and how do you even go about installing it? i cant even figure out how to get my pppoe connection running.... do i need it for the installation? and what on earth is a tarball?

---

### Post by elvis on 2007-09-29
Gentoo is a highly customisable source-based Linux distribution.

Gentoo is certainly not targeted at an audience who is not savvy to the basics of compiling code and doing some fairly heavy manual customisations.  

To answer a few of your questions:
> **Chymera said:**
> SO why is it that you have to compile everything?

The beauty of free software is that you get the source code.  With distros like Ubuntu, Sabayon and others you are largely at the mercy of the developers who build the packages for you.  You get whatever features they deem appropriate when you install said packages.

Gentoo gives users a slightly deeper control method over package installation via "USE flags".  These are flags that can turn on or off certain features of software at compile time.

Why bother?   For a lot of reasons.  For example: About 2 years ago I was given the task of upgrading an LTSP thin client system for one of my clients.  The previous systems administrator had used Slackware and KDE, which was extremely memory hungry when all 25 users logged in at the same time to the server with 2GB of RAM (requiring upwards of 90MB per person, forcing the machine quickly into swap disk-thrashing hell).

First off, I chose a more sensible window manager (XFCE) with a smaller memory footprint.  Initially I built the system using Debian (where Ubuntu gets its roots).  Now the problem here was that any time I installed something trivial that had a KDE or Qt dependancy, Debian insisted I install half the KDE system.  Additionally, per-user memory use was down on the initial Slackware/KDE system, but still not reasonable - around 50MB per person.

I tried a second time with Gentoo.  Using Gentoo's USE flags, I could tell the system that when building the binaries, I didn't want KDE or Qt support for any GUI applications (obviously some applications require a basic amount if they are built on Qt, but for others where there was GTK and Qt support, the Qt support could be left off).

Additionally, I could set compile-time flags to optimise binary building to use less memory (using the -Os flag, compared to the default -O2 or very memory expensive -O3 flags that some people use).  Coupled with the fact that most binaries had half the unnecessary features chopped out courtesy of the USE flags, per-program memory use dropped dramatically.

This time I had better success.  Memory use per person was down to a very reasonable 30MB per person (1/3 of what it was under Slackware/KDE), meaning the machine wasn't forced into swap merely logging users in.  The business owner was happy, as it meant the system performed better without the need to purchase and test new hardware.

Additionally, I could disable a great deal of unnecessary things.  Being a point-of-sale frontend, the business owner wanted me to disable multimedia playback, music playback, etc.  This was all accomplished easily with USE flags (Debian on the other hand forced me to install a host of music and audio players when installing an XFCE desktop).

That's just one example of Gentoo's customisable portage system, and I could give plenty of others, but I think you get the picture.

Gentoo is not for everyone.  In fact, many of the people who use it really don't need most of it's features.  If all you are after is a simple desktop system that handles a lot of low-level defaults for you, Ubuntu is a far superior choice.  There's way more to customising a Linux system than just slapping Beryl/Compiz on it and tweaking themes.  Any software where the source is provided means near unlimited configurability, and Gentoo is designed with that in mind.

> **Chymera said:**
> and how do you even go about installing it? i cant even figure out how to get my pppoe connection running.... do i need it for the installation? and what on earth is a tarball?

Attempting to install Gentoo without first RTFM (Reading The Fine Manual) will not get you very far.  Even as a user with 10+ years full-time Linux use under my belt, I still have to refer to the Gentoo Handbook when installing this distro:
[http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)

Again, this distro was NOT designed for mindless click-and-install.  It has a very different purpose to other general-use distros.  By all means try it if you like, but if compiling code and configuring PPPoE connections by hand is not your cup of tea, give it a miss, as it's probably not for you.

---

### Post by bernied on 2007-09-29
The only question elvis didn't answer...

A tarball is a zipped, tar archive. You are probably talking about the stage 3 tarball, which is a packed-up almost-complete system, which includes the portage package management system, the compiler and other software needed to get started. The stage 3 tarball does not include a kernel. It also doesn't include any kind of desktop. This stuff has to be compiled.

---

### Post by Caffeine_Junky on 2007-09-29
Thanks for the info Elvis & Bernied!  ...nice posts,  ..very informative

---

### Post by Chymera on 2007-09-29
well i havent anything against configuring my internet connection manually... besides, do you really believe there is any other way of configuring pppoe than manually? And it actually isnt that much of a big deal, really; just that gentoo wont swallow up any command, pppoeconf pppoeconfigure pppoe-start pppoe-setup, and many other variations....

as for the installation manual, i really dont understand why it is impossible for you to install a gentoo linux without checking it, especially if you sai you have over 10 years of experience with linux systems,  since it basically tells you to follow the guidelines of the installer, which eventually jams because it cant configure the internet connection :confused:

---

### Post by bernied on 2007-09-29
You've just pointed out the main problem of the graphical installer for gentoo. It was never meant to be the same as the installers for other distros (ie. easy), and I remember it particularly telling me so, something like 'even though this installer looks pretty, you still need to RTFM'.

Try installing from your existing OS (I'm assuming you have a linux system running that has got your pppoe sorted out??). Some info here:
[http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5](http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5)

---

### Post by elvis on 2007-09-29
> **Chymera said:**
> well i havent anything against configuring my internet connection manually... besides, do you really believe there is any other way of configuring pppoe than manually? And it actually isnt that much of a big deal, really; just that gentoo wont swallow up any command, pppoeconf pppoeconfigure pppoe-start pppoe-setup, and many other variations....
By "manually" I mean hand-writing your own providers file.  I would consider "pppoeconf" and other tools to be automated tools.

Bringing PPPoE up for install is documented in the Gentoo Handbook.

> **Chymera said:**
> as for the installation manual, i really dont understand why it is impossible for you to install a gentoo linux without checking it, especially if you sai you have over 10 years of experience with linux systems,  since it basically tells you to follow the guidelines of the installer, which eventually jams because it cant configure the internet connection :confused:
I've been away from Gentoo for about 18 months now.  I can tell you straight up that 2 years ago installing Gentoo was completely different to the install methods today.  These days most of the fiddly work is done for you.  Once upon a time there were far more tasks required and config files that needed to be hand coded or else things would break.

Not necessarily a difficult task.  But one where if you didn't have a checklist beside you to remind you of all the little things needed, it meant doing things over until you remember it all.

---

### Post by Chymera on 2007-09-30
well yes the manual does say smth about it, it sais pppoe-setup should work :(

---

### Post by elvis on 2007-09-30
> **Chymera said:**
> well yes the manual does say smth about it, it sais pppoe-setup should work :(

Perhaps posting on the Gentoo forums about Gentoo installer issues would be more appropriate, and gleam you the responses you desire?

---

### Post by cotcot on 2007-11-21
Do not use the gentoo graphical installer. It is well known that it can cause problems. Moreover you are missing some of the benefits of the distro (use flags per package) unless you recompile what you just installed.

---

### Post by jdong on 2007-11-21
One thing to add, before Ubuntu I was primarily a Gentoo user:

Please don't let "compiling everything" sound more frightening than Gentoo makes it. Gentoo's Portage handles all of the grunt work for you, all you have to do is tell it what to compile. For example, "emerge gtkpod" is the same thing as "apt-get install gtkpod", only in Ubuntu the command fetches a prebuilt gtkpod binary while in Gentoo gtkpod will be built on your system automatically from sources.

---

### Post by Chymera on 2007-11-24
that's a relief.... why did you change to ubuntu then?

---

### Post by jdong on 2007-11-25
> **Chymera said:**
> that's a relief.... why did you change to ubuntu then?

Hmm, well first off, I'd like to preface my reason with that I deeply respect the Gentoo team, and even wanted to be a Gentoo developer before Ubuntu came along, and I still respect the Gentoo folks and their great work and upstream cooperation to this day.


My growing reason was just too much maintenance work. Ubuntu's stable releases allow me to blindly apply security updates with extremely minimal chances of breakage, while in gentoo applying every update blindly at the end of a week is asking for an unbootable system. Also, a fresh install takes forever to set up and configure to defaults that suit me, while Ubuntu's settings more suit me out of the box.

The final straw was at the time I left, Gentoo had two nearly consecutive serious breakages that knocked out an important LAMP server that I maintained (it was pushed out as a security upgrade so I applied it with more urgency than caution) and another kernel update left my system totally unbootable, both of which upon inspection seemed like simple bugs that represent careless pushing into repositories. I realized that I needed to find a more dependable OS.

Now of course I have no idea how much of my experiences from 3 years back apply to modern day Gentoo. Please don't take what I just said as a flame against Gentoo -- I certainly don't mean it that way. They are my experiences. Some people walk away from Ubuntu with similar "ugh nothing worked right" stories, and I'd sure not want them to generalize that Ubuntu's like that for everyone!


At any rate, this is FOSS. Try everything because you are free to do so, rather than solely relying on our words.

---

### Post by Chymera on 2008-01-05
jdong 10x very much for the info you gave me, it helped me decide to try out what may not be the most user-friendly but definitely the most interesting and handy distro I used till now, if things don't take a sudden turn this will most likely be my last post on this forum :)

---

### Post by Bachstelze on 2008-01-06
> **Chymera said:**
> jdong 10x very much for the info you gave me, it helped me decide to try out what may not be the most user-friendly but definitely the most interesting and handy distro I used till now, if things don't take a sudden turn this will most likely be my last post on this forum :)

Being a Gentoo user doesn't mean you can't post here anymore ;)

(But the Gentoo forums are indeed very nice, too)

---

### Post by jdong on 2008-01-06
> **Chymera said:**
> jdong 10x very much for the info you gave me, it helped me decide to try out what may not be the most user-friendly but definitely the most interesting and handy distro I used till now, if things don't take a sudden turn this will most likely be my last post on this forum :)

Awesome, glad you like Gentoo :). Have fun with whichever distro suits you :)

---

