---
title: "Should I try LinuxFromScratch or Gentoo??"
date: 2007-03-11
forum: Gentoo and derivatives
---

### Post by billdotson on 2007-03-11
I have both the ISOs burned onto CDs and I want to know which one to try out first.  I hear Gentoo and LinuxFromScratch are those masochistic OSes that take a long time to get working but in the end they are incredibly fast and tailored to what you need the OS for so there is no extra baggage.  Although I am not sure if i know enough about compiling and BASH to get either of them working.  I am using Ubuntu currently and it seems to be really slow on my Core 2 Duo system.  It often takes 3-5 seconds to open the drop-down applications menu, mono crashes all the time and gnomebaker hates my PC.

---

### Post by igknighted on 2007-03-11
Both are good choices.  Personally I love gentoo, but I haven't tried LFS.  I might say go with LFS first, however, as Gentoo 2007 is coming out soon so try LFS now and Gentoo when 2007 comes out.

---

### Post by po0f on 2007-03-11
billdotson,

I'd personally suggest using Gentoo because it has a package manager.  I don't know if LFS has one or not though.  Both are source based distros, which I'm sure you already know.  I sure hope you're prepared for this ordeal.  ;)

---

### Post by billdotson on 2007-03-11
maybe I should do LFS first to learn how to do it all (as it has a walkthrough) and then when Gentoo 2007 comes out I should know enough about Linux from LFS to have fun setting up Gentoo instead of ripping my hair out in frustration.

---

### Post by igknighted on 2007-03-11
> **billdotson said:**
> maybe I should do LFS first to learn how to do it all (as it has a walkthrough) and then when Gentoo 2007 comes out I should know enough about Linux from LFS to have fun setting up Gentoo instead of ripping my hair out in frustration.

I would say the opposite is true.  I know I suggested LFS first due to Gentoo 2007 coming out soon, but if you want to learn as you go Gentoo is the way to go.  Gentoo is the best documented distro in linux.  The manual can walk you through every step of the install explaining what is going on.  I don't know what the LFS documentation is like, but I doubt it can compare to Gentoo.

---

### Post by Kateikyoushi on 2007-03-11
I tried LFS after years of using freeBSD and maybe 3-4 years of gentoo, was fun way to kill a weekend but I hardly benefit from it all, probably because of previous gentoo installs, I would choose gentoo anytime.

---

### Post by billdotson on 2007-03-12
I guess I will go with Gentoo 2007 when it is released.. sounds like I will learn a large amount of stuff about Linux and will end up with a blazing fast and fully customized Linux OS when I am done.

---

### Post by igknighted on 2007-03-12
> **billdotson said:**
> I guess I will go with Gentoo 2007 when it is released.. sounds like I will learn a large amount of stuff about Linux and will end up with a blazing fast and fully customized Linux OS when I am done.

Or almost as likely end up with a HD partition full of files that won't boot for crap ;-).  I jest, although my first Gentoo install turned out like that sadly.  If I were you (and you could spare it) I would try this on your fastest computer, as it will noticeably cut down compile times.  My old P4 chip (a 3ghz one) took almost 4 hrs to complete a kernel compile, but my 1.9ghz dual core AMD chip did it in between 1/2hr and 1 hr (I dunno exactly, I expected it to be longer so I walked away).

---

### Post by billdotson on 2007-03-12
I only have one machine but I think it could handle a compile pretty quickly.

I'll be putting the Gentoo on my USB 2.0 external HDD along w/ Ubuntu.  I have got roughly 240GB of unused space as of now.

---

### Post by daschl on 2007-03-18
i'm sorry, but i cannot agree with some of you guys..


Linux From Scratch is good when you want to learn how to build your own distro and so on, but i would not recommend it for anything that we call a "productive environment" .. 

gentoo is a great distribution and i use it a lot in server environments. i also used it for my desktop os but i prefer ubuntu here. why? because i dont want to spend so much time compiling stuff.. and my athlon 64 is so powerful that i cannot find any speed differences when modifying use flags (and - of course - waiting for compilation erros ;))

---

### Post by scoon on 2007-03-18
Hey there, 

After years of running gentoo, I am now running ubuntu.   The main reason, is that it takes a lot of time to compile and I never really noticed much speed difference.  I definately used aggressive use flags and what nots.  If you have some time to burn, I'd definately suggest gentoo.  It is a great distro to use if you have a ton of time.  If you are nervous about the commitment, the best way to gain some edu-tainment and possible speed increases would be to compile your own kernels and learn from there.  Definately check out CK kernels. 

 We all need to walk before running, and I have found that kernel compiling is a very good way to start.

-scoon

---

### Post by kambei on 2007-03-18
If you try Linux From Scratch... you will discover a whole new appreciation for the capabilities of Debian package management tools... :-)

LFS (the book) is an excellent learning resource for Linux... By default, the system it teaches you to setup does not come with a native package management system... But there are several detailed HOWTOs in the 'Hints' section of the website that propose alternative packaging methods and many informative threads in the mailing list archives debating the pros and cons of each.

Great for experimenting on a free partition/box... but quite a bit of work for daily use...

---

### Post by mysticrider92 on 2007-03-30
Either one of those will be a bit tricky to learn and use, but I would recommend Gentoo for the package management and documentation, especially if you want to learn about the inside of your Linux system. If you want more of a LFS-like system, you could try following the Quick Install Guide on the Gentoo docs and do a Stage1 install, where you have to do everything from bootstrapping to kernel config and compiling. If you are successful with that, LFS would be no problem at all.

---

### Post by Burning Bronx on 2007-03-30
From my experience with both I would say LFS is a bit more educational (yet a lot more time consuming and frustrating for the newcomer), however Gentoo is a lot more practical - great documentation, great packaging (thought they do too make mistakes - don´t let anyone fool you) and still educational enough. 
Still if you want a scoop on the insides you could start with Ubuntu too. Like the guys before me said you could learn a lot from a simple kernel compilation. Like basic tools for gaining info on your system (it´s weird how most users don´t even know some of the most basic stuff about their system), learning about the toolchain and what it consists of, etc. 
Start with what you have, make a smooth cut down kernel for your current distro and then go on and see how an LFS or a Gentoo works out.
Peace to you friend.
Burn.

---

### Post by coplan on 2007-04-23
LFS -- tried it once last summer and spent three months racking my brain.  I learned a lot, but I would never subject myself to that *ever* again.  And I've been using linux for 12 years.

Gentoo, on the other hand, handles a lot of the tedious stuff for you.  You can get a pretty damn efficient machine out of Gentoo without too much effort.  You just can't match the USE flags (default configuration for compilations) when it comes to a source distribution.  There is even a simple way to control specific USE flags for specific packages (For those moments when "I generally don't want to use the QT library, but for this program, I do.").

---

### Post by aeto on 2007-05-02
Why do you compare a **distribution** to a **kit**? LFS **is not a distribution**. Rather it is a thorough **guide** and tool to help one build a custom Linux operating system. Arch itself was initially an LFS project by Judd Vinet, who based his ideas on CRUX, Slackware and Gentoo. LFS should be followed if one is interested in learning, studying, or is heavily involved in developing Linux systems.

A Linux OS involves the following:

Compiler for a Compiler
Compiler for Software
Kernel
Software

Consider crafting a very simple wooden stool. You need a saw/chainsaw, hammer, nails, a big block of wood. That is the base set of variables. The saw is the compiler for a compiler, you have to craft out the wooden pieces out of the block. The nail is then the compiler for software, it gets things attached. After that you varnish the material, brush off scraps, add refinements, paint, etc.

One can basically set up an environment through any medium, be it an already-running distribution or a Thumbdrive. LFS, as well as Gentoo, provides you with a CD containing the base packages and essential requirements for bootstrapping. LFS also tells you that any other medium is fine as you just need the packages and a root environment to get started.

Go for a stage 1 Gentoo if you want to get as close to the LFS steps as possible.

---

### Post by public_void on 2007-05-04
I installed Gentoo on an old machine. It really teaches you alot, and after a couple of goes (yes I ended up with a machine that didn't boot twice) you should understand linux a bit better. Having said that, it was quite a hassle, and really I wouldn't do it again unless I had alot of free time.

As for LFS, reading the instructions kinda put me off. However again if I had a loads of free time (which I doubt) then I might try it, just to learn.

---

