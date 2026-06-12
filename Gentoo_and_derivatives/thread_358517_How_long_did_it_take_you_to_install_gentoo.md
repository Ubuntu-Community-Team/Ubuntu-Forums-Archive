---
title: "How long did it take you to install gentoo?"
date: 2007-02-10
forum: Gentoo and derivatives
---

### Post by slimdog360 on 2007-02-10
Ive been going since 9:30pm last night, its now 3:32pm the next day and its up to emerging package 253 of 532. So a bit under half way. Im hoping it will be done by tomorrow morning.

I chose to install kde, fluxbox and blackbox on top of the base install.

If this install stuffs up Im throwing my computer out of the window.

---

### Post by rogerdugans on 2007-02-10
First time I installed Gentoo-
Spent a week or so and screwed it up. lol

First time I **successfully** installed it- about a day and a half for the base, same for xfree86 and kde, so about 3 days for a full, bloatware gui Gentoo install.
And that was my third or fourth try.....

Since then, installing Gentoo has gotten a lot easier but it is still pretty easy to screw it up, and compiling stuff can take a long time, depending on hardware.

Last time I installed Gentoo it was fairly quick- started in the evening, done in the morning.

But I have had LOTS of practice.

Gentoo is a great distro in a lot of ways, amigo, and well worth the effort if you really want an optimized system.
But it still ain't easy.

---

### Post by mark_alec on 2007-02-11
First time it took me a whole weekend.  Now I am pretty sure I can churn out an install on a newish box in a few hours (let it compile stuff while doing more interesting real life activities.)

---

### Post by pichalsi on 2007-02-11
First time last week it took me 2 days but then I found out I want to repartition the disc so I installed again yesterday in around 12 hours (mostly compiling). But its still far from being custiomized and I only have a few basic programs. What I found most time-consuming was reading the manual to set the use flags, make parameters and configuring the kernel, xorg and antialiasing. But i had the configuration files saved from last week so it was easier last time. 

However it was nice to learn some stuff again, thats why I wanted to do it (I had a lot of free time after exams :)).

---

### Post by zaratustra on 2007-02-11
It really depends what you want to install. First, stage1 or 2 are now unsupported, so you are doing it on your own. I think you should not use stage1 or 2, not because they are unsupported but because gentoo installer ins't best thing that could happen to you, and you can always install stage3, and then do a emerge -e system if you want everything to me compiled. I have been messing around with stage1 including bloody bootstrap and stuff failed on opendlap package, maybe 100/110 package, after a 10 hours of doing stuff. I have done no additional packages install, and install them after my hand. I have some gentoo expirience, so i have done this (stage3 install, downloaded stagea and portage snapshaot before, packages were compiled, not from CD) cca one hour, then, when I have runnnig system, making custom kernel conf and installing it (half an hour), and additional packages (X, firefox, amarok, xfce, openoffice) -> may vary a lot..half an hour - INF:P.... also you need some extra configuring if you want that everything works (few hours)

---

### Post by slimdog360 on 2007-02-11
just checked it this morning about 5:30am before I went to work (Im there now) and it was up to package 447 of 532. Next time Im not choosing kde straight away.

---

### Post by RAV TUX on 2007-02-11
> **slimdog360 said:**
> just checked it this morning about 5:30am before I went to work (Im there now) and it was up too package 447 of 532. Next time Im not choosing kde straight away.I would suggest you start with Fluxbox or E16

---

### Post by slimdog360 on 2007-02-12
> **RAV TUX said:**
> I would suggest you start with Fluxbox or E16

hindsight is always 20/20

---

### Post by mips on 2007-02-12
> **slimdog360 said:**
> hindsight is always 20/20

I learned that a while ago. When I installed BSD the first things I installed were X, Fluxbox, Firefox, Xchat2. Reasoning was that these are basic things to get me into a GUI and give me the tools to access support and keep me busy while things are happening in the background.

---

### Post by pay on 2007-02-12
I either copy the gnome files from the liveCD or install fluxbox and then emerge kdebase-startkde

---

### Post by slimdog360 on 2007-02-12
Well its done, I must say its not all that fantastic just yet. When I installed my username didnt take and so when I rebooted I was left without a way to login, because gentoo seems to disables the root user login through kdm or whatever. Luckily I managed to create a new user by going back into a console login.

All in all it took a bit over two and a half days, but I think that if I hadnt emerged kde it would have taken a sigificantly shorter period.

---

### Post by pay on 2007-02-12
Theres Sabayon, which is based on Gentoo but it has KDE on the liveCD so you don't have to compile it.

---

### Post by v8YKxgHe on 2007-02-12
I've yet to manage a successful install of Gentoo! I've tried around 4 times ... every time I get Installation Failed!

---

### Post by highneko on 2007-02-12
When I was new to linux less than a year ago I did a good job probably but when it was compiling I thought it went into an endless loop and something was wrong so I shutdown manually. All the compiling text scrolling across the screen, I thought something was wrong.
:lolflag:

---

### Post by pay on 2007-02-12
> **AlexC_ said:**
> I've yet to manage a successful install of Gentoo! I've tried around 4 times ... every time I get Installation Failed!What errors are you getting?

---

### Post by v8YKxgHe on 2007-02-12
> **pay said:**
> What errors are you getting?

Honestly can't remember, twas a while ago now. I gave up in the end :)

---

### Post by zaratustra on 2007-02-12
> **pay said:**
> What errors are you getting?for me, it failed on openldap package

---

### Post by pay on 2007-02-12
> **zaratustra said:**
> for me, it failed on openldap packageSaying it failed doesn't help, but posting the first error message can help in finding out what went wrong.

---

### Post by justin whitaker on 2007-02-12
> **AlexC_ said:**
> I've yet to manage a successful install of Gentoo! I've tried around 4 times ... every time I get Installation Failed!

Right there with you. Something always seems to go wrong...ah well, Sabayon is sweet.

---

### Post by manmower on 2007-02-12
Three years ago on a Pentium 3 800 MHz with 192MB of RAM, about three days to a full KDE system on first try. The documentation was so good you could hardly mess up, but maybe that has changed over the years. Either way I learned little from it and basically was back to using Windows within weeks...

---

### Post by neowolf on 2007-02-12
In the past, I've  have installed Gentoo w/GNOME Desktop in 3h50m, with a slight bit of cheating with the Packages CD :D
In the present, I can't be bothered with Gentoo, Debian or Ubuntu suit me much better.

---

### Post by runningwithscissors on 2007-02-14
It doesn't take more than about an hour and a half or so.
Once it is done, I emerge some lightweight utils for use, and compile KDE overnight.

Mind you, you don't really need to install it often. Just run an update every other week and you'll always be up-to-date.

---

### Post by jdhore on 2007-04-16
i was successfully in a CLI only Gentoo environment within less than 3-4 hours...then it took me another 2-3 days to get Gnome working/installed because of me getting pissed about compiling 200 packages and going back to Ubuntu for the night or because i was having problems. The Install i did was a straight Stage 3 install, then i installed xorg, then i installed Gnome and all the HUGE dependencies (Mainly the help files, Evolution and Firefox).

---

### Post by ghowells on 2007-04-16
Back in 2003 (using 2003.1 I think) it took me 3 1/2 days on an old P3 500 with 128MB of RAM to get from zero to bare XFree86!  This was pre-graphical installer days and I had to follow the Gentoo Handbook to get it done but man did I learn a lot!  I still think that installing Gentoo in text-mode is the most informative tool when starting-out in the Linux world :)

---

### Post by jdhore on 2007-04-16
> **ghowells said:**
> Back in 2003 (using 2003.1 I think) it took me 3 1/2 days on an old P3 500 with 128MB of RAM to get from zero to bare XFree86!  This was pre-graphical installer days and I had to follow the Gentoo Handbook to get it done but man did I learn a lot!  I still think that installing Gentoo in text-mode is the most informative tool when starting-out in the Linux world :)

i agree! i learned a hell of a lot when i did my gentoo install...i was amazed i even felt comfortable in CLI for like 7 hours straight with IRC goin and listening to music on the ipod...it was good...but i am having 1 or 2 minor issues and when i fix them, i think it's off to Gentoo fulltime

---

### Post by Ateo on 2007-05-14
I perfected my install time over the years.

Today, I can get a fully working Gentoo server installed in 18 hours. This includes LAPP, DNS and other stuff.

LAPP = Linux, Apache, PostgreSQL and PHP.

---

### Post by ghevan on 2007-05-25
Im a new user to gentoo, been using it for 5 months after a year of breezy.

Installing the base system was a pain, mainly because I started installing at midnight (LOL) took me 6 hours following the handbook. Next day I spent 4 hours to get X working. (I forgot to add wacom, mouse and keyboard on the input devices in the make.conf). And on the third day and after hours of compiling GNOME with some stops (complaining about packages, asking me to fix things =/)  I 've got a working desktop system. Probably It took me 8 hours that last day, but im not sure.

After hours of compiling GNOME I decided XFCE was best LOL.

---

### Post by ns80 on 2007-07-25
With the handbook around, it would around 6-7 hours to get the barebones system ready with a stage 3 install from command line. I once did a [Stage 1/3 install]("http://forums.gentoo.org/viewtopic-t-319349.html") which took almost 3 days to get the base system. X configuration took a couple of hours including the package installation. Fluxbox was done in 3-4 hours and Gnome took almost a day to complete.

---

### Post by distroman on 2007-08-07
The first time I installed Gentoo was om a pentium 667 MHz it was very exciting and a nightmare at the same time. It was not to be. I moved on to try SimplyMEPIS and later SuSE acttully stock with SuSE for quit some time I am sure that's why I hate KDE today.

Second time was on a AMD 1.5 GHz still a struggle but this time I made it, but I could not settle for gnome-light, nope, I had to get the full package, that made for a good +24 hours learning lesson. Then I found Debian and finally Ubuntu Breezy Badger. 

The third time was actually in VMware I enjoyed that install and things was starting to make more sense.

The fourth and current install are on a AMD 5200 X2 and was done in less then a day with gnome-light and what not that 5200 can really do some crushing. 

I am not a Gentoo user (I enjoy the ease, I as I see it, of Ubuntu to much) still I do enjoy exploring/playing with Gentoo and learning as I do other with distributions.  All in all the installation took a couple of years. :eek:

---

### Post by Lord Illidan on 2007-08-07
Took me a couple of days, kept getting some settings wrong!

---

### Post by distroman on 2007-08-07
^ Yes it easy to make that kind of mistake with gentoo, it's a learning process :lol:

---

### Post by raijinsetsu on 2007-08-07
I can do a normal stage3 install in about an hour.
BTW - there's no reason to compile the larger packages(Gnome, Xwindows, Firefox/Bon Echo, etc.), so get the binaries for these whenever you can.

Compiling with specialized options can really only speed up basic system services, and these compile within a minute...

---

### Post by insane_alien on 2007-09-22
i used binaries for the initial install since i couldn't be bothered dragging my pc to the router(why won't gentoo detect my wireless card? EVERYTHING else does.) so i was stuck with a networkless install.

i'm looking for what packages i need for wireless and i'll hook it up to get them. then rebuild the system properly. still using gnome 2.16. gah.

---

