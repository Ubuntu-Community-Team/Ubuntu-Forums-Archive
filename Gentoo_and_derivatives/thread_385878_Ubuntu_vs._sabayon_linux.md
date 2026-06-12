---
title: "Ubuntu vs. sabayon linux"
date: 2007-03-16
forum: Gentoo and derivatives
---

### Post by ajmannen on 2007-03-16
Hi, i have just found sabayon linux, it comes with Beryl as default. I am thinking about having this next to my Ubuntu egdy eft, anny one know if it's good?

---

### Post by EndPerform on 2007-03-16
> **ajmannen said:**
> Hi, i have just found sabayon linux, it comes with Beryl as default. I am thinking about having this next to my Ubuntu egdy eft, anny one know if it's good?

I've played around with it.  It's based off of Gentoo and comes preloaded with a ton of different software, although I think they may have some stripped-down versions now.  Being that it's based off of Gentoo, updating might take a bit longer than you're used to since software will be compiled.  It is pretty nice, though.

---

### Post by ajmannen on 2007-03-16
It looks real cool on YouTube, How big partition do i need?

---

### Post by EndPerform on 2007-03-16
> **ajmannen said:**
> It looks real cool on YouTube, How big partition do i need?

I think something along the lines of 5 gig at least.  Check out their website to be certain, though.

---

### Post by mips on 2007-03-16
> **ajmannen said:**
> It looks real cool on YouTube, How big partition do i need?

For the DVD just over 10GB.

I just checked now with Gparted and I'm using 10.02GB for the DVD install. This excludes my /home partition which I have seperate to the OS.

So work on about 15GB if you are gonna install lots more stuff.

---

### Post by forcesofhabit on 2007-03-18
I installed Sabayon 3.3, and it was quickly removed. Despite users stating that the OS is very fast, this was not the case. The PC I was running has 1 gig of ram, and 2.0ghz processor speed. Along with an Nvidia 256mb card... I thought for sure it'd be alright.

I like the project and its goals. If only it worked for me.

I'm sticking with Ubuntu.

---

### Post by Rodneyck on 2007-03-18
I was going to download the new 3.3 dvd via bittorrent, but the speed is so slow I decided to wait for the mini cd release Lots of users have reported the same slow speeds on the Sabayon forum.

On closer examination of the threads, users are also reporting lots of problems with the new 3.3 install, upgrading and broken apps after install.  

I decided to wait for the issues to subside.  I am very happy with Sidux, but just wanted to see if there were any major improvements over Sabayon's 3.2. Gentoo is to fragile for my taste and I have always found issues with Sabayon, mostly Kuroo and the portage system.

---

### Post by rai4shu2 on 2007-03-19
I just tried out 3.3 on my box here, and it's great. :)  Beryl is a little better (though still buggy), and lots of stuff just works a lot better.

The install was fast: about 35 minutes from start to finish. I ran into that issue of the installer in the boot menu not working, but if you boot like normal and run the Installer Updater it fixes that problem. At least this time I didn't run into a grub error for the Windows partition. Still get that error for the Ubuntu partition (so I had to reinstall grub from the Ubuntu live CD).

The xorg.conf was still a bit off. Basically, it ran my monitor at 60 Hz instead of my preferred 75 by default (easily fixed).

I don't like KDE so I switched over to Gnome after a while. It's the latest stable Gnome (2.16.3), so it's very familiar. Everything I tried there seemed to work okay. I'm getting a little weary of Gnome and its perpetual "low" severity bugs, though. I don't really get why they keep piling on new features while ignoring bugs that have been in there for years. KDE is a lot better in that department, but for all its features I can never seem to find the ones that *I* want. And no precompiled XFCE, so...

It seems a bit faster than the latest Ubuntu Feisty, though Feisty is still in testing so that might change. I didn't like how it rendered fonts in Firefox on certain sites like The Register or certain other forums. I'm also not crazy about how much you have to download when you emerge --sync (about 80 MBs in my case). Seems a little odd to me. There are some other cosmetic quirks too, but I think they were too trivial to remember now.

Overall, Sabayon is definitely catching up to Ubuntu in ease of installation and use.

---

### Post by mips on 2007-03-19
> **rai4shu2 said:**
> I'm also not crazy about how much you have to download when you emerge --sync (about 80 MBs in my case). Seems a little odd to me. 

It's only the first time that is so big. Next time is much smaller/faster.

---

### Post by rai4shu2 on 2007-03-21
That's a relief. Too bad they can't spare you that, but I guess it's a Portage thing. Must be a big pain for dialup users.

---

### Post by tubasoldier on 2007-03-21
I gave sabayon a shot. I like the idea of a source based distro. Compiling and building from source always seems snappier to me. Always argued by many people however.

The biggest issue I had with Sabayon is the length of time it takes to install anything! I selected a few minor programs from thier graphical package manager and it took nearly 15 minuites to install them. It also took half that time to remove a program. I just don't have that much time to waste on package management. Even though I believe source based distros are superior, I just haven't found one that is easy to setup and maintain. So for now its Ubuntu.

---

### Post by igknighted on 2007-03-21
> **tubasoldier said:**
> I gave sabayon a shot. I like the idea of a source based distro. Compiling and building from source always seems snappier to me. Always argued by many people however.

The biggest issue I had with Sabayon is the length of time it takes to install anything! I selected a few minor programs from thier graphical package manager and it took nearly 15 minuites to install them. It also took half that time to remove a program. I just don't have that much time to waste on package management. Even though I believe source based distros are superior, I just haven't found one that is easy to setup and maintain. So for now its Ubuntu.

Keep in mind that when Sabayon installs anything it is compiling the source code, not installing a package.  They are working on a binary package installer (called Entropy), but it is only in an alpha stage right now.  A 15 minute install is quite normal in a source based distro.  If you had tried to install OpenOffice.org then it could easily have taken several hours, as that is a huge program.  Once installed, the program should be snappier if you set the compiler flags properly, but the actual install will take a long time.

---

### Post by igknighted on 2007-03-21
> **rai4shu2 said:**
> That's a relief. Too bad they can't spare you that, but I guess it's a Portage thing. Must be a big pain for dialup users.

I suppose they could include the latest portage snapshot on the DVD, perhaps they should now that I think about it...

---

### Post by zaratustra on 2007-03-22
portage snapshot is updated more than once a day... so if you want to be up-to-date, that isn't good idea. I think they say not to use sabayon unless you have good computer and good connection

---

### Post by igknighted on 2007-03-22
> **zaratustra said:**
> portage snapshot is updated more than once a day... so if you want to be up-to-date, that isn't good idea. I think they say not to use sabayon unless you have good computer and good connection

True, but if it was included the "emerge --sync" would only have to fill in the changes.  After a while it would lose value, but especially around the release it would be awesome.

Also, I think if you wget the tarball of the latest snapshot from [www.gentoo.org](www.gentoo.org), and extract it without the -v option you could cut down the time considerably.

---

### Post by zaratustra on 2007-03-22
> **igknighted said:**
> 
Also, I think if you wget the tarball of the latest snapshot from [www.gentoo.org](www.gentoo.org), and extract it without the -v option you could cut down the time considerably.I agree with that completly

---

### Post by Cannonade on 2007-03-29
Sabayon was the third distro I tried, the first being Ubuntu 5.10 and the second Gentoo. I like Sabayon, because I like Beryl, but I dislike Gentoo. I loved the cool 3D affect from Beryl, and I thought Sabayon was quite smart. However, I'd be much happier when Beryl becomes offical, with all the bugs cleared and can be easily installed onto Ubuntu.

I find Sabayon very buggy and very unstable. From the Live DVD I had, often, I would boot into Sabayon and my keyboard wouldn't work, not even the caps light would come on. I found a lot of programs either took ages to load or didn't load at all. Also, a hell of a lot of programs crashed the OS. Compared the Ubuntu, the booting time is also extremely long.

I think I'll be sticking with Ubuntu and Windows. Although I will keep looking at Sabayon, and I will consider trying to triple boot Ubuntu, Sabayon and Windows if Sabayon becomes more stable.

---

### Post by igknighted on 2007-03-29
> **Cannonade said:**
> Sabayon was the third distro I tried, the first being Ubuntu 5.10 and the second Gentoo. I like Sabayon, because I like Beryl, but I dislike Gentoo. I loved the cool 3D affect from Beryl, and I thought Sabayon was quite smart. However, I'd be much happier when Beryl becomes offical, with all the bugs cleared and can be easily installed onto Ubuntu.

I find Sabayon very buggy and very unstable. From the Live DVD I had, often, I would boot into Sabayon and my keyboard wouldn't work, not even the caps light would come on. I found a lot of programs either took ages to load or didn't load at all. Also, a hell of a lot of programs crashed the OS. Compared the Ubuntu, the booting time is also extremely long.

I think I'll be sticking with Ubuntu and Windows. Although I will keep looking at Sabayon, and I will consider trying to triple boot Ubuntu, Sabayon and Windows if Sabayon becomes more stable.

Try the mini edition.  Boot times are comparable to Ubuntu, and the system as a whole is much more snappy.  Also, I haven't had any stability issues with it.  What kind of keyboard do you have?  That seems like a really odd error.

---

### Post by tchoklat on 2007-04-10
On a new system with gigabyte SLI mobo I cannot get ANY ubuntu version to run or install. Sabayon 3.3 mini is the only one that does and it runs well. A few little glitches that I cannot resolve;
 
Acceleration manager wont change from 'no acceleration' option
GuardDog wont set up - reports iptables problem
Cannot get my OKI 10ex printer to print
 
 
Tony

---

### Post by mips on 2007-04-10
> **tchoklat said:**
> On a new system with gigabyte SLI mobo I cannot get ANY ubuntu version to run or install.

Weird thing is the 04/9 Feisty build had GFX problems on my PC and it is a bog standard nvidia 6600 that has never been an issue. The defult 'nv' driver would not work, had to install nvidia-glx.

I know Feisty is Beta but it is only a few days away from release this should at least work.

---

### Post by Nomearod on 2007-04-11
> **tchoklat said:**
> On a new system with gigabyte SLI mobo I cannot get ANY ubuntu version to run or install. Sabayon 3.3 mini is the only one that does and it runs well. A few little glitches that I cannot resolve;
 
Acceleration manager wont change from 'no acceleration' option
GuardDog wont set up - reports iptables problem
Cannot get my OKI 10ex printer to print
 
 
Tony

About the "Acceleration manager", I'm not sure but I think that it doesn't matter. If you select the second option and reboot the PC it will use it but if you open acceleration manager it will show always the first option.

---

### Post by tchoklat on 2007-04-14
HI,
 
If you are right, then my system must be OK.
 
I have ditched Guard-dog.
 
I have got the printer working so all is well.
 
thakns

---

### Post by Ariccanfly on 2007-04-16
my bcm4311wirelss card works for the first time!!!

Linux  2.6.21-rc5-sabayon #1 SMP Mon Apr 9 00:14:45 UTC 2007 x86_64 AMD Turion(tm) 64 X2 AuthenticAMD GNU/Linux

So if you want a "works out of the box" linux os that is bleeding edge.. than sabayon wins...
but keep in mind that bleeding edge also = unstable, ubuntu does not equall unstable,

but for my wireless to work in ubuntu i have only one kernel  2.6.17.10 .. and now that the wireless git development stack is in this and all new kernels... i can switch back to ubuntu when it catches up.. like a year i bet...

---

### Post by mips on 2007-04-16
> **Ariccanfly said:**
> 
but keep in mind that bleeding edge also = unstable, ubuntu does not equall unstable,


FUD, Edgy was a POS, on my PC anyways. Feisty is much better.

---

### Post by igknighted on 2007-04-16
> **mips said:**
> FUD, Edgy was a POS, on my PC anyways. Feisty is much better.

Well, take that with a grain of salt... as new versions come out, support for more (see: newer) hardware comes with it.  However, if you constantly live on the edge of new software, you are going to run into bugs and breakages unless you are very lucky, in which case please buy me a lottery ticket :).  So yes, newer software can = better hardware support, but it also can = fewer bug fixes, more chance of breakage.  Look at Slack and Debian, the two most stable Linux OS's... their package selection is ANCIENT (I haven't looked at Etch, so don't count that).  But even though they are benchmarks for stability, many newer pieces of hardware don't work.  Hardware support != stability, but they are both important.

---

### Post by mips on 2007-04-16
> **igknighted said:**
> Well, take that with a grain of salt... 

Well with Dapper everything was great. Edgy was one big headache. Feisty is fine though.

---

### Post by RebounD11 on 2007-07-12
Sabayon - Bad first impression... errors on first installation attempt... way too many stuff like both ati and nvidia drivers preinstalled, and lots of that starts up at boot (CPU 100% - AMD64 3500+,1.5 out of 2 GB of RAM constantly used). A little better but still bad second impression - minimal install is too minimal... I had to wait forever to install everything I wanted and after all was finished it wouldn't start up at next reboot.

Third time's the charm... finally a DVD install of Sabayon 3.3 without errors... to bad it has no package selector I had to remove a lot of apps after installation (see first impression to find out why) - although an improved installer was promised in the 3.4 release :D

A couple of reboots later:
- CPU never gone above 75% (running beryl, Parallels workstation with 512 MB reserved RAM and a WinXP installation, and while installing NFS: Carbon in Cedega)
- no errors or crashes  - probably the most stable KDE distro ever (so far)
- everything that worked under Ubuntu on this computer now works better, and what didn't work under Ubuntu now works (as well as anything else)

Ubuntu wins a round at hard drive management : somehow Sabayon doesn't detect my partitions or the partitions of other hard drives I connect to my computer correctly (it only happened once or twice - never for my personal hard drive) - sometimes sees my ATA hard disks or CD/DVD-ROM drives as SCSI or SATA drives (again isolated incidents)

Winner: Sabayon for its stability,speed, productivity (has everything you could think of and still installs in about 15-20 minutes tops) and feel (looks and sounds great - it's artwork) - 3.4 promises improvements - can't wait :D

---

### Post by maxrisc on 2007-07-31
I am on Sabayon 3.3 mini install.

Compiz just works...right out of the box.  No fooling with ATI drivers or screen resolutions.

All of the software I want and need is already on Sabayon and it simply works.

*buntu's you can't even get k9copy or k3b to work correclty.

*buntu is a dumbed up newbie distro that is good for introducing people from Windows to the OS.  It's a great philosophy but the ability to tweak it is just too minimal.  Any time I try to change something under the hood it breaks something else.  Not to mention trying to install ATI drivers is a big pita.  

On the other hand the Ubunut LiveCD is quite the savior when it comes to needing a live box in a moment's notice.  I have to give you all props there.

I am a long time Unix user and I have used linux full time since the RH  Halloween release and I have to say that Sabayon is by far the best distro I have ever seen and heard :0)

Both distros have their place.  I like them both but prefer Sabayon to get my work done.  Yes it is true that Sabayon had some growing pains in the beginning.  But today I won't even think about installing anything else...

---

### Post by Lord Illidan on 2007-07-31
I tried Sabayon 3.4 recently.

The live dvd was v. nice.

however, installation was a different matter. It seemed as fast as Ubuntu, no speed gains..in fact it was a bit slower, sometimes with all the things starting up.

Gnome was a p.o.s. on Sabayon. Most KDE apps wouldn't show up in the Notification Area, I finished re-emerging most of Gnome and KDE, before I finally gave up. Even metacity was broken.

---

### Post by viking777 on 2007-07-31
Ive been using Sabayon for a year or so and liked it a lot with one grave exception. Their download servers are complete crap, they are so slow that the quickest I have ever succeeded in getting a dvd version is 12 hours and then it was corrupted (the torrents are even worse, more like 12 days there!) . It was right after that that I switched to Kubuntu and as soon as you learn how to install a root account and a root version of konqueror it is very good (although compiz doesn't work at all and beryl is not available on the repos for gutsy, not that that bothers me, both Sabayon and PClinux have working beryl effects and I never use them.) So if you are going to use it go for the mini version and be prepared to wait for ages for downloads and program installations (because they are compiled by the OS not precompiled as in other distros. I don't pretend to know much about this, but I do know how long it takes to install Mozilla Thunderbird!)

PS. If you are tempted to reply to this telling me how bad it is of me to circumvent Ubuntu's marvellous sudo system DONT!!!:mad::mad::mad:

---

### Post by buntunub on 2007-07-31
LOL sudo is complete crap! I understand fully the reasons for its ubuntu implementation, but its just overkill. Nothing wrong with working in #. Either way, you can still accomplish the same thing by typing sudo rm -RF *, as rm -RF *, its just an extra switch.

---

### Post by maxrisc on 2007-07-31
The very first command I always run is "sudo passwd" :)

I've been thinking about reducing the Sabayon DVD to about half it's size and seeding that.  Gnome is garbage in my general opinion.  Even Linus thinks so.

I was able to pull the Sabayon x86_64 3.4a DVD from Europe this morning.  It took about 4 hours to grab the whole thing.

All in all though I am a power user and programmer.  After using Compiz for many months I find it almost impossible to get any work done on a regular desktop.

But like I said before I really like the Ubuntu philosophy.  I am already thinking about the next latest greatest release...Cubuntu3D

---

### Post by darksong on 2007-07-31
Sabayon is the best linux distro i have used. The sheer amount of work that is gone into the Disto is astounding and the amount of changes per realaise is hudge. From last realase it has gone from a buggy OS which didn't detect most of my hardware, to fully working - it works much better than gentoo did on this system. 

It looks, feels and sounds good - If it continues like it will replace windows vista fully on my h/d,

---

### Post by syxbit on 2007-07-31
if it wasn't for apt, i'd switch.
however, nothing beats debian package managment

---

### Post by handy on 2007-08-09
I'm on 3.4a, & loving it.  I'm not the sort of user that can find much wrong with Gnome, & this release 2.18 suits me much better than the one I use in Dapper.

So many pieces of software are available to install from the DVD, that there are only a few things I needed to add:  NeroLinux3, DVDshrink, Cedega, a couple of games I could just drag out of /home/.cedega from my Dapper.  

The portage system won't bother me due to it being hardly ever used.  When a new version comes out in 4 or so months I'll download the DVD & upgrade from that, or I'll do the xDelta thing.

The display is easier to read in Sabayon than Ubuntu, it is crisper.  Is this due to a later version of xorg ?  My eyes love it! 

The [***_Sabayon forum_***]("http://www.sabayonlinux.org/forum/index.php?sid=047657046af43f34d1dce6b9e7287aab") is a nice place, & it works pretty fast too.

---

### Post by mips on 2007-08-09
> **handy said:**
> 
The display is easier to read in Sabayon than Ubuntu, it is crisper.  Is this due to a later version of xorg ?  My eyes love it! 



My eyes love it as well. Maybe they did something to the font rendering, never seen fonts this good before.

---

### Post by handy on 2007-08-09
> **mips said:**
> My eyes love it as well. Maybe they did something to the font rendering, never seen fonts this good before.

You & I both spend a lot of time looking at our monitors, & I have to agree with you, I've never seen a display work so well!

---

### Post by vexorian on 2007-08-09
something is making me think of the word "overrated" here.

---

### Post by mips on 2007-08-09
> **vexorian said:**
> something is making me think of the word "overrated" here.

If you have something to say then why dont you just say it ?

---

### Post by WishingWell on 2007-08-09
Sabayon trashed my partition table once, i had to fix it manually via a Slax cd and fdisk, it wasn't really all that much fun, so i went to their forums and they said it's a known problem and no, they are not going to tell anyone about it on installation but the new version has fixed that problem, so i try the new version, this time it was easier to fix the trashed partition table and i went back to the forums and they said yet again that it is a known problem and it will be fixed in the next version.

So i tried the next version, trashed my partition table again and since then, i've just not bothered.

Compiling for the sake of compiling is just daft, in numerous benchmarks Debian has proven that it is as fast and sometimes faster than specifically compiled code, if you are going to bother with compiling, compile the kernel and just use a decent package manager for the rest (and while emerge does work, unlike debian the repositories and the code within them is not subjected to the scrutiny that Debians packages are)

Sabayon may have nice fonts but it's a horrible distro.

---

### Post by handy on 2007-08-09
***@WishingWell:*** That's how it is with Linux, some hardware configurations work really well with one distro' & are nothing but trouble in another, that's the luck of the draw.  It's nice to have so many choices don't you think? :-)

It is more than just great fonts, the entire display is crisp, like I have never seen before on a monitor.

As far as speed goes, that is not what I use an OS for.  They are all fast enough these days, unless you are after more speed for sound & graphics work, or a particular game that has got your hardware on the ropes.

---

### Post by Chymera on 2007-08-30
I recently gave sabayon a try and must say i'm VERY impressed. If i wouldn't be such a gnome fan i think i really would have given it a thought to make it my primary os....

Anyway its one of the best distros i've seen so far....  and i believe that a sabayon vs. gentoo thread is in order.... i havnt inslatted gentoo on my machine, but have worked a bit with a gentoo install at school, i feel sabayon offers all the advantages of gentoo, but is a lot more accessible to newer linux users.

---

### Post by mips on 2007-08-30
[QUOTE=Chymera;3279719]If i wouldn't be such a gnome fan i think i really would have given it a thought to make it my primary os....
/QUOTE]

handy above runs Gnome on his Sabayon install as far as i know. Gnome is one of the install options you have from the DVD. Never looked at it as I never install Gnome although I currently have Ubuntu on my laptop but it is purely there for support purposes because I recently installed it on a friends notebook.

---

