---
title: "Gentoo is a monster that kills CD-drives"
date: 2007-08-12
forum: Gentoo and derivatives
---

### Post by Steveway on 2007-08-12
Well, just want to tell a little story.
I have an Acer-Laptop with one of those stupid tsst-CD/DVD-drives.
It works pretty well and reads about anything but that is not what I want to tell.
While searching for more experience and having a second free partition I decided to try out the Gentoo Live-CD.
Pretty nice, works ok emerge is nice too.
So up to the install, the gtk-installer is pretty straightforward if you know your hardware.
Ok installing...needs some time, compiles some things, then nothing...
My drive stopped to work, I had to reboot and it took me to grub, Gentoo seemed to have reached up to the point where it installs grub and I can boot into Gentoo.
But the install seems not to be finished really and the drive gets mounted read-only , dang.
Ok, then let's try it again! CD in, choose to boot from Cd, ok, booting...Grub. What? Why?
I check the CD, the drive, nothing.
Another CD, nothing.
So I can only boot into a broken grub and not install something different? That sucks.
Ok, I have to rescue that Laptop, it's my main machine, I only have a 166MHZ machine her functioning as a server without a monitor attached to it.
Ok, in my Bios I saw that I could choose to boot from my external USB-Harddrive.
I went to my sisters Pc, dropped in a Xubuntu CD (I first defragmented my external Harddrive using her Windows), made the Partition smaller, added an ext3 Partition and installed it. Worked like a charm.
I plugged it into my Laptop and booted from it, Grub showed up and showed Xubuntu but it didn't want to boot.
I edited hd(1,1) to hd(0,1) and it worked.
Pheew, that saved me, thank god. CD-drive doesn't work but I can use my Laptop.
But today, several days later, I randomly dropped a Myst 3 CD into it, surfed a little, looked to my Desktop and saw a CD icon entitled Exile DVD.
Whoow, freaking awesome, the drive fixed itself somehow.
Thanks Ubuntu!
I'm not gonna try Gentoo another time on this Laptop, curse you Gentoo.
(I know that Gentoo didn't really kill my drive, it's just badly designed, all those tsst-drives show failures on Windows and on Linux.)

---

### Post by kellemes on 2007-08-12
You better install the Gentoo-way next time.. so forget the automatic installer.
Installing the Gentoo the Gentoo-way you should see as lesson no.1

---

### Post by Darkhack on 2007-08-12
I know that I might get flamed to a black crisp for saying this, but I would never let Gentoo touch my primary machine.  Compiling an application to install it takes way too long and it is too easy to break one's system with emerge.  If you are not careful, doing a system wide upgrade could cause a lot of breakage.  There is nothing wrong with Gentoo for those who like a custom compiled system that is fully customized to meet their needs with certain changes that can only be made at compile time, but to me, it is still a hobbiest distro.  I love Ubuntu on the desktop and I seriously think that once Canonical gets to be more well known and trusted as a company, that eventually enterprise users might consider the server version of Ubuntu as an alternative to SUSE or RHEL.

---

### Post by kellemes on 2007-08-12
I must disagree I'm afraid.
Dists like Gentoo are much much easier and safer to maintain and upgrade as *buntu's, as long as you know what you're doing..

Being an Archer myself I know every upgrade will give me all the control I need to maintain my system, this is the same with Gentoo and other rolling -release-distro's.
It's all about the knowledge of the administrator.

---

### Post by SunnyRabbiera on 2007-08-12
yeh but compiling is a pain

---

### Post by kellemes on 2007-08-12
> **SunnyRabbiera said:**
> yeh but compiling is a pain

There is nothing to it.. Just accepting the defaults gives you a working system.
USE-flags give you the freedom to influence the result.
It's about freedom to get things done the way **you** want it.
You want a system "that **just** works" or you want the best of performance and stability possible..
There are a lot of things you'r not able to do using Ubuntu without having to hack the system, where in Gentoo it's one emerge away.

---

### Post by macogw on 2007-08-12
If I knew the USE-flags, I could probably get a faster system on my old Pentium II, but that thing takes 20 minutes to an hour to compile each thing (I should know, it took 2 days to do Enlightenment).  If the point is to make the thing faster, why waste all that time compiling?  Then if you have a computer fast enough to compile in 5 minuts, why do you even need USE-flags?  Are you going to notice that it took 2 clock cycles less?

---

### Post by SunnyRabbiera on 2007-08-12
> **kellemes said:**
> There is nothing to it.. Just accepting the defaults gives you a working system.
USE-flags give you the freedom to influence the result.
It's about freedom to get things done the way **you** want it.
You want a system "that **just** works" or you want the best of performance and stability possible..
There are a lot of things you'r not able to do using Ubuntu without having to hack the system, where in Gentoo it's one emerge away.

yeh but you know the average user wont really like having to compile the endless amounts of software and stuff that goes along with linux.
This is why package mangaers like debian and RPM are good, as the average user wont have the patience to compile stuff

---

### Post by WishingWell on 2007-08-12
In every benchmark i've ever seen Gentoo is equal or slightly slower when compared to Debian.

Compiling on an old PIII wouldn't be fun, as soon as you get an update of Gnome or KDE your system will hardly be usable for the hours it takes to compile it.

---

### Post by Bachstelze on 2007-08-12
Moved to Gentoo Talk.

---

### Post by Steveway on 2007-08-12
> yeh but you know the average user wont really like having to compile the endless amounts of software and stuff that goes along with linux.
This is why package mangaers like debian and RPM are good, as the average user wont have the patience to compile stuff
On Gentoo if you want to install a programm you just have to do a emerge programname.
So $emerge thunar will download and compile thunar for you.
It's like apt-get only that it compiles the programs instead of using precompiled ones.
And Gentoo is not thought to be used by the average user.

---

### Post by cobrn1 on 2007-08-12
> **SunnyRabbiera said:**
> yeh but you know the average user wont really like having to compile the endless amounts of software and stuff that goes along with linux.
This is why package mangaers like debian and RPM are good, as the average user wont have the patience to compile stuff

The 'average user' doesn't usually use gentoo though, do they? ;)

Personally, neither do I ,but I appreciate what kellemes is saying... with gentoo you build the system (literally) exactly how you want it...

Personally, i'm more attracted to arch as my "bleeding-edge" distro - I like that balance between latest features but ease of install and speed of install (you can't deny that even if compiling is easy, it *does* take longer).

---

### Post by kellemes on 2007-08-13
> **WishingWell said:**
> In every benchmark i've ever seen Gentoo is equal or slightly slower when compared to Debian.

Compiling on an old PIII wouldn't be fun, as soon as you get an update of Gnome or KDE your system will hardly be usable for the hours it takes to compile it.

There are binary packages for situations like this..I've never compiled KDE on Gentoo.
Debian isn't made for performance in speed so these benchmarks I want to see.. :popcorn:

---

### Post by Steveway on 2007-08-13
This is strange.
So after playing some Myst3 with the DVD-version I decided to burn the new KDE4life-version.
Ok, it was allready downloaded, I eject my DVD insert a CD from wich I burnt many before, it gets recognized.
Fired up Brasero selected the iso, pressed burn, whoops that was the wrong one, I was still downloading the iso I choosed and Brasero spit out a failure of unkown format and ejects my CD.
Ok then insert the CD again and choose the right iso, the drive slides in and ... nothing!
Ok, I press the eject button, check the CD and insert it again... nothing again.
I take another CD (luckily I have plenty), insert it...nothing!
What is this kind of wizardry?
Ok, then just to test it out I inserted the MystDVD again and... it gets recognized!
What the...? How...? Why...?
I get a DVD I burned some weeks ago, insert it... recognized!
I try a CD...nothing!
The self-burned DVD again...recognized!
Now while I'm writing this I tried a CD again...recognized!
What the heck it happening here?
Percentage of propability of recognizing a DVD 99%
Percentage of propability of recognizing a CD 5%
How can a CD/DVD-Combidrive fail so hard at reading CDs but has no problem with DVDs? There is just one Laser in it, I could imagine it the other way around but not like this.
I'm gonna burn now before it fails again.
It calls itself TSSTcorpCD/DVDW TS-L532A in hardinfo.

---

### Post by HardcoreLinux on 2007-10-16
Yeah you do not install gentoo via live CD you install using chroot and all that other good stuff.

---

