---
title: "Compaq Presario 2100 Project"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by Bladerunner71 on 2007-06-02
Hi everybody,

I have a new-2-me old laptop that I have been working on the last couple of days.  The laptop itself is about 4 years old (judging by the 2003 mfg stickers all over the place). The problems that I have are listed below in the notes that I'm taking.  I'm trying to be as accurate as possible, but If you have installed Feisty Fawn on a Presario 2170US laptop, please let me know what you did to get it to work.  Here are my notes (any Ideas will help):

Compaq Presario 2100 (2170US)
Product #: DK587A-A101

INITIAL SPECIFICATIONS:	Mobile Intel Celeron 2.0 Ghz
					15&#8221; XGA TFT Active Matrix Display (1024 X 768 Resolution)
					40 GB Hardrive 
					256 MB RAM (64 MB Shared Video Memory)
					DVD/CD-RW
					Microsoft XP Home Edition
					

Cost of Laptop: FREE
Problems So Far: Bad HDD (TOSHIBA 40 GB)

Game Plan:
OS:	Ubuntu Studio 7.04 Feisty Fawn 
HDD:	Seagate Momentus 80 GB
RAM:	Kingston 512MB DDR266 PC-2100 (HP/COMPAQ Specific)(x2) 

Purchases/Cost/Ordered From & Item #:
Seagate Momentus 5400.3  ST980815A 80 GB 5400 RPM ATA-6 HDD/$59.99/NEWEGG Item #: N82E16822148128
Kingston 512MB 200-Pin DDR SO-DIMM DDR266 (PC-2100)/$56.99 (x2)/NEWEGG Item #: N82E168201141323
TOTAL (Incl. Tax/Ship/Rush Order Fee): $193.06

5/27/07

Received Broken Laptop from friend. Purchased New HDD and RAM From NEWEGG.  Compaq is not my first choice for a laptop, but what the hell, it was free.  What a perfect project for a Linux laptop.  I am running Ubuntu Studio on my desktop, so I'll match it up with that.  I decided to max out the RAM because its available and reasonably cheap.  So with 64 MB Shared Video, that leaves about 960 MB for other stuff.

6/1/07
Received RAM and HDD from New Egg.  Installed without a hitch and booted up faster than the 256 MB setup.  Showing 959 MB of RAM after install.  HDD is nice and quiet compared to the Toshiba (before it broke).   Attempted install of Ubuntu Studio which failed due to &#8220;Critical Temperature&#8221; 128dg Celsius. Hmm, after I got that went to the forums. Followed one bit of advice to try the Ubuntu Live CD. Tried that a couple of times, but same thing, except now I actually get to the desktop.  Cool, so moving right along, everything seems to be working alright, I'm going to install...NOT!!! As soon as I click the install icon, termination alert &#8220;Critical temperature 128dg C&#8221; AGAIN, except when it goes for final shutdown it shows a critical temp. of 47-58dg C before it closes.  I had already downloaded Fedora 7 KDE Live, tried that out and voila , live CD came up without any error.  But heres my take on Fedora 7:  If I wanted a stock KDE I would've built my own KDE (it does not give you any software options to install, it installs the WHOLE KDE operating system.)  It is definitely not near as good as FC-6.  So, I shut it down for the night.  Try it again in the morning.

6/2/07
Well, tried it again.  Laptop cool as a cucumber.  Popped in the the Ubuntu Live CD again, as it was booting grabbed a cup of coffee, came back to watch the desktop come up.  I got to the splash screen and received the termination signal, Critical Temperature alert (128dg C, I'm seeing a trend here).   The temperature never goes above 128 as some of the posts I've read on the Forum do.  Posting this on the forums to see if anybody can help.  I am a newb, so I hope they give me a break and possibly some fresh ideas.  The goal here is to have Ubuntu or Ubuntu Studio running on the thing solo, like my desktop.  How does one OS work, but the other not?  And I know for a fact that its not even close to 128dg C. I would say the 47-50 range is more accurate.  But, I'll see what the GURU's have to say.

*My wife just finished playing Mahjonng from the Fedora 7 Live CD.  She played it for about 1.5 hours without  receiving any temperature alerts.  Fan was on, felt like a normal laptop after use.  Also, I thouroughly cleaned  it inside and out awaiting the parts.

10:59 am Well it seems I have just installed Ubuntu.  Don't know how or why it all the sudden let me accomplish this milestone, but I'm installing the updates as I type this.  So it can be done.  This ROCKS.

---

### Post by Bladerunner71 on 2007-06-03
Well, it is installed and works fine and dandy:p So far no major issues whatsoever(that I can see), but it can be done.  I was actually getting nervous about doing this project reading about issues people have w/ COMPAQ, but here is what I did prior to and after installing

On the BIOS, disabled Legacy USB- I did this because everything I read about linux on COMPAQ said that this needs to be done.  

Everything worked out of the box. Video, Audio, yada yada yada.  I did not have to update any drivers for this.  If it works, don't change a thing.  Why risk it?

Wanted Ubuntu Studio, but as my notes indicate, issues installing.  So I just downloaded the theme;)

Between my daughter and myself, we put it to good use yesterday.  She mainly worked on her myspace and I spent time downloading stuff and setting it up.  We had it on for approximately 12 hours without any errors.

So all and all, Be PERSISTANT. Don't give up. It will eventually work out ok.  I wasn't about ready to install Windows on it again.  I read pretty much all the horror stories on this forum about  the critical temperature errors and how to correct them.  I didn't want to post anything about it, but I was starting to get discouraged and not 30 minutes after my first post, I was installing UBUNTU.  Amazing what happens when you ask for help, things just come together as if it were a miracle. 

 I have made a chart on what works and what doesn't on the laptop.  If it is blank, I haven't tested it yet. So feel free to use it if you want.  It is pretty much based on the Ubuntu Laptop Team's Templates.

Thanks

---

### Post by Gauss1777 on 2007-07-15
I have a Compaq Presario 2100 with AMD processor. I read about your temperature problem, although maybe is not a problem and u have a diferent processor I would tell u anyway.

My computer sometimes happend to turn off suddenly, I think because of the CPU protection it has. This use to happen when the CPU fan was at its full and when windows was insisting in making the CPU to work (I'm trying to migrate to linux). So I opened the computer and decided to see if the heatsink had proper contact with the CPU. **I found that between the CPU and the heatsink was a horrible thin piece of aluminium**. I don't know if this was supposed to help trasfering heat, sure it doesn't help at all. I removed it and clean all the mess it had to "transfer heat" with isopropyl alcohol and applied some arctic silver 5 to the core and put the heatsink back. You can use any other compound to transfer heat, not specifically arctic silver, I just happen to had from those days I use to have "xtreme computers"... days gone.

Now I hope my computer is cooler than before, but I'm still trying to make some things to work with ubuntu so that I can migrate completely.

---

### Post by Gauss1777 on 2007-07-15
BTW, I was about to open a new topic. But since it's a similar laptop the one I have I'll post here.

Mine has an Athlon XP processor. I tried the last Ubuntu and it was almost everything right out except some things:
- The button that allows to swtich display type doesn't work (Fn + F5). It allows to switch between LCD's laptop and an external display. However all other options like changing volume level or brightness work.
- Ubuntu doesn't recognize my external display, I can use it because both displays works at the same time, but I want to deactivate the LCD's laptop and set a diferent resolution for my external monitor.
- The point is: How do I change the resolution for my external monitor? I hate to use it with 60 Hz and I can't change that too.
- My laptop uses Ati 320M. How can I tell if I have 3D support or how can I activate it? I want to play Diablo II with 3D support, I don't know if that's possible, it uses Direct3D. I know it is possible to make it run with Wine, but I want it to make it run with 3D support. I also want 3D support to make run Beryl or something like that.
- How to get USB2 support? It would be great because the transfer rate with my external HD is slow. However it's great Ubuntu already recognize these external devices right out.

---

### Post by haxorsyhp0r on 2007-10-03
I have a Compaq Presario 2140us that i also received from a friend.  Anyways on with my point, i put Ubuntu 6.06.1 and the video is not working right. as it loads i can use the LCD built in screen but near the end it goes completely black and i can only use an external screen. i have the ATI radeon 320m video. Nothing i do seems to work... but i am also a noob at this so any help will be much appreciated.

---

