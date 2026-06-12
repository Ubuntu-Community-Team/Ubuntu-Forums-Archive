---
title: "Build/buy a Linux dedicated machine?"
date: 2014-01-23
forum: Hardware
---

### Post by shearer4 on 2014-01-23
Any suggestions on either building a desktop box?  My local MicroCenter offers a couple cases and motherboards. How much ram? How big a drive? Is it worth doing OR, should I look at System 76?  I have monitors and keyboards so for $600-$700, I could buy a box from them.  Just want it to play around with. Hey, people spend more than that on cameras as a "hobby".  

Thanks.

---

### Post by adam33 on 2014-01-23
I've always built my desktop boxes.  I like that I can put exactly what I want in there, nothing more and nothing less.

For running Linux, that may be a good idea, as you can pick components you know are compatible (your wifi adapter, video card, etc).
You can build a pretty powerful computer for that kind of money these days.

---

### Post by shearer4 on 2014-01-23
Thanks Adam33 .  That's what I seem to be seeing.  I run all Mac stuff here, so have not really been on the build your own thing for a long time. 
Any ideas about optimal ram, disk drives?

---

### Post by adam33 on 2014-01-23
What do you plan on using the computer for?

---

### Post by shearer4 on 2014-01-23
I know it sounds...wrong, but just playing? Like I said, some people have hobbies. One of mine has always been messing with PC's.  I'm looking pretty old here, but I'm recently : early retired, and just looking for something to occupy my time. 

That's a long way of saying; just learning Linux and maybe write some routines of my own?  

Nothing heavy.

---

### Post by adam33 on 2014-01-23
Alright, well in that case, you have a lot of choices.  You could even go with something like a [Raspberry Pi]("http://www.element14.com/community/community/raspberry-pi"), or something a little more powerful like a [Mars Board]("http://www.marsboard.com/"). The Raspberry Pi isn't the most fun to use if you want to be in a desktop environment, but it's great if you're just using ssh.  The Mars Board has quite a bit more power for running a desktop environment.

If you want a full power PC, i'd go with an i5, 8-16 gigs of ram, an SSD (128GB-256GB),  and depending on if you plan on playing any games, or anything graphically intensive, you would want an AMD or Nvidia video card, I am not well versed in which models have the best Linux support at the moment though, so that'd take some research.

---

### Post by 1clue on 2014-01-23
We definitely need more information.

If your idea of playing is 3d games then that's one thing, if you just want to learn shell commands and scripting that's another.  Or if you want to use it as a normal computer for facebook, youtube, etc.  Or a set top box?

If you want to make small devices that interact with the world, the Raspberry Pi or an Arduino is where you want to start looking.

Building your own system is definitely in the cards.  I do it with all my desktops, but unfortunately laptops don't work that way.

So tell us more:  What sort of things do you envision doing with it?  Do you want it to have a keyboard and monitor?  A mouse? Do you want it to be your primary workstation?  A server?

---

### Post by shearer4 on 2014-01-24
Thanks for the tips. I'm not a big gamer, but just thought I would probably be using Linux and many of the free apps, to email, surf the web, and learn to use terminal commands. etc..  

Like I said, a hobby, so can only build so many birdhouses, right?  

Thanks.

---

### Post by shearer4 on 2014-01-24
You probably already got it. I just want to learn shell commands, scripting and use it to interact over the internet. Never been a big gamer.  I only use Facebook to look at pictures of my grandkids.
 
I don't see this becoming my primary computer for; say banking, investments, writing, photography, just because I am so comfortable with the Mac in those areas. 

So; just by looking at adam's  links, I can see that there is a world of very small console type devices.  Probably not for me. Another learning curve. Keyboards and mice yes.  In particular a full keyboard. Wifi or ethernet, depending on the size of the unit and where I have to put it. 

 I've seen people reference cheap laptops that either come with , or can be formatted to Linux.  Also seen some very bad experiences related about those in the ultra cheap range.  So, just something to keep poking and come to a logical conclusion.

---

### Post by 1clue on 2014-01-24
OK so you want a general purpose desktop.  You need something about the size you would choose to do those things if you were using Windows.  My own preferences tend to be a bit ... roomier? than what most people pick.

I've had some really bad experiences with ultra-cheap junk too.  I build my own equipment from new parts, and the only OS it ever sees is Linux.  I generally spend some 4-digit number of US dollars which does not start with a 1.

The old saw about Linux being the fastest operating system you can put on your computer came from the days before XFree86 came out.  Which was a LONG time ago.  It was a real operating system, and you didn't have to install a GUI.  You can still install non-GUI (Ubuntu Server for example) but you don't seem to want that.  People make claims about full-featured GUI Linux installs with KDE or Gnome being faster, I don't see that.

If you want to surf the web, then you need a GUI.  There are lighter weight ones (Xfce or Lxde for example) but generally speaking, when you install Ubuntu or Kubuntu you'll get about the same performance you would if it was Windows.  The more you load it up with special effects and apps running all the time, the slower it will run.  Most people seem to gravitate toward the heavier stuff.

If you're going to experiment and try different things, you might consider something that can run virtual machines.  8g or more, that sort of thing.  Then you can have a stable and consistent desktop that always works, and then have one or more VMs to experiment with.

If you have experience buying Windows hardware, shoot for the same sort of thing.  If you're willing and able to build your own, then hit the same places you normally go (newegg, amazon, etc) and you can make sure all the components work with Linux before you buy.

If you buy something prebuilt, you stand a significant risk of the hardware inside not matching the specs on the web site.  They love cutting corners and putting in junk somewhere, usually the thing you were counting on to be good.  They also love putting in junk you don't care about, which you don't have to buy when you build your own.

I think the typical Ubuntu user uses around 4g RAM or so for a desktop.  If all you do is browse then it's hard to use more than that.  If you use a couple VMs you'll want more, which is why I said 8.  Personally for my next system I'm hoping for 32 to start and 64 as a max because it's going to be mostly a virtual machine host.

Also keep in mind that a whole lot of people pick Linux because they don't have to pay for it, and they put it on old junk hardware that's either too slow to run Windows, or that they picked up for a bargain somewhere.  There's nothing wrong with that, I've done it myself, but your last post suggests to me that you're not that way.  Be careful when people give advice that you see where they're coming from.

As for scalability of Linux:  You can get it on embedded stuff like Raspberry Pi as was pointed out earlier, and you can go to the other extreme too.  According to the most recent top500.org statistics, 96.4 of the fastest supercomputers in the world run some form of Linux, and you have to go down a LONG ways to get to something that doesn't.

Things that don't tend to work well are bleeding edge sound cards, video cards, TV cards, that sort of thing.  The stuff that tends to work really well would be server hardware and network cards.  Mainstream just-about-anything works.  Network printers, better be careful and figure out your exact model.  I bought a Canon MF8050Cn multifunction laser, and tried over a year before I could get it to work on Linux.  Works fine now, by the way.

---

### Post by mörgæs on 2014-01-24
> **1clue said:**
> 
Also keep in mind that a whole lot of people pick Linux because they don't have to pay for it, and they put it on old junk hardware that's either too slow to run Windows, or that they picked up for a bargain somewhere.


That's what I wound suggest. Begin with whatever old stuff you can get for free (or almost free). 'Junk' is often used relative to Windows' insane hardware demands, not indicating that the hardware is failing. Only if you have identified a bottleneck in practical use it's worth considering to buy something better.

Say, an Intel Pentium D or one of the oldest Core with 2 GB of memory. Should not cost you much.

---

### Post by shearer4 on 2014-01-26
Good point re; old hardware. My old office (work) is loaded with it.

---

### Post by shearer4 on 2014-01-26
All my questions answered!  Thanks. I'm realizing that my current, older MacPro is probably perfect for running Linux for my purposes. Maybe as good a way to just do another "lesser" Mac for my usual needs.  The older MacPro with 1.5T or drive space and 16G of ram is perfectly fine and runs Ubuntu and Mint really well now that I have things tweaked properly. Thanks in large part to you and others for the help.  I hate that the Pro architecture from 2006 has been superseded, and  can't run more current versions of OSX or get things fully synced up with my MBP or my wife's MBP, but I guess that's progress.Thanks for taking so much time with  this answer.

---

### Post by bc.haynes on 2014-01-26
1clue, thank you for your breakdown of possibilities. I, too, am retired and would have built my own machine (if my eye was better). I applaud shearer4's move to a better OS than Windows. I am convinced that I want to permanently ditch Win. Too many problems. Thank you, too, shearer4 for the post.

---

### Post by 1clue on 2014-01-26
Frankly I have my eyes on that new Mac Pro.  12 cores, up to 64g RAM, 1T SSD with super-fast interface, and 6 20gbps external ports.  Gotta love it.

I'm exploring built systems with 10gbE right now, they will certainly be cheaper but not nearly as sexy as the Mac.

---

### Post by mörgæs on 2014-01-27
> **shearer4 said:**
> All my questions answered!  Thanks.

Good, please mark the thread 'solved'.

---

### Post by unibroker on 2014-01-27
> **shearer4 said:**
> All my questions answered!  Thanks. I'm realizing that my current, older MacPro is probably perfect for running Linux for my purposes. Maybe as good a way to just do another "lesser" Mac for my usual needs.  The older MacPro with 1.5T or drive space and 16G of ram is perfectly fine and runs Ubuntu and Mint really well now that I have things tweaked properly. Thanks in large part to you and others for the help.  I hate that the Pro architecture from 2006 has been superseded, and  can't run more current versions of OSX or get things fully synced up with my MBP or my wife's MBP, but I guess that's progress.Thanks for taking so much time with  this answer.

I've had your request for a couple of years and every time I get the urge to build a machine I can't justify it other than time filler (semi-retired).  My 2006 HP desktop is sufficient for building custom ROMs for my Nook Color ereader.  These two "gadgets" have taught me a lot regarding the linux world  AND I've got a lot more to learn.  I haven't exhausted either one's capabilities and that keeps me from building a desktop.  Good luck in your journey.

---

### Post by Bucky Ball on 2014-01-27
For surfing and emailing you won't need much. I've just set up a little Dell netbook for a friend with an Atom 1.6Ghz processor and 1Gb RAM and it does what you're talking about just fine.

I'd probably go for an i3 or equivalent and a couple of gb of RAM. More than adequate for doodling. I have an i3 with 4Gb and it would eat up what you want to do. My desktop doodles aimlessly for hours with an old P4 3Ghz CPU and a gb of RAM.

(I must add that all the installs I speak of are minimal installs; the Dell install is about 2.6Gb and the desktop just over three).

---

