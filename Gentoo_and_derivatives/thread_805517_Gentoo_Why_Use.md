---
title: "Gentoo Why Use?"
date: 2008-05-24
forum: Gentoo and derivatives
---

### Post by HunterThomson on 2008-05-24
I have always thought of Gentoo as the 133t Linux system. But, what are the real benefits over using Ubuntu i.e. PaX PIE/SSP.... sound really cool but can I just install them on my Ubuntu system? I know the Gentoo system I would  end up with would have a smaller Kernel and such but dose this really matter in the long run? Is this negated by the time it takes to do other things in Gentoo that are faster to do in Ubuntu? I am reading the install docs and am planing to do a duel boot gentoo/Ubuntu.

What are your thoughs?

---

### Post by regomodo on 2008-05-24
I use it because i want a very customised system for my needs. Speed increase is not an aim and is largely not noticeable or a key issue. If it improves speeds by 1% then it's not going to make a difference for me, however, if you are into doing simulations/rendering/modelling/computations then that 1% can be quite significant.

Additionally, i wanted to **learn** Linux without having to use Linux From Scratch.

---

### Post by Cap'n Skyler on 2008-05-26
i can install sabayon...easy....
gentoo?
nothing but trouble.cant even get it to install....
live cds
dvd from linux mags from the UK
nothing...failed install every time.:confused:

---

### Post by regomodo on 2008-05-26
> **Cap'n Skyler said:**
> i can install sabayon...easy....
gentoo?
nothing but trouble.cant even get it to install....
live cds
dvd from linux mags from the UK
nothing...failed install every time.:confused:

let me guess. Kernel problems? For me that is the hardest part.

---

### Post by sujoy on 2008-05-26
follow the wiki to every word, install the gen kernel and get the system to boot first,  then you can take time and compile your own custom one. its not that difficult really, with the wiki printed out or on another terminal.

as for its benefit, well besides being a great learning experience, its also a bloat free distro like arch, as whatever you have are the things you would use, nothing extra. you can keep it as stable or as bleeding edge as you want, along with all the benefits of being a rolling distro.

no reason why anyone with patience shouldn't use it :) although i am not patient enough and hence like the binary system of arch better than gentoo's compile stuffs.

---

### Post by marty1011 on 2008-05-26
For learning linux. But I am stuck at adding gentoo to my Ubuntu grub.
I am planning to keep trying until I get a working system though.

---

### Post by LinuxGuy1234 on 2008-06-13
For l33t stuff. Really I'm using it to create my own custom environment.

Right Now:
Gentoo base system
CVS, SVN, Git
X + GNOME
Some other things :)

I also have Sabayon Linux. (3.4e from Linux Magazine (and not a UK reader))

---

### Post by M_the_C on 2008-06-14
Two reasons:

1)  As people have said already, customisability.  If you follow the Gentoo Handbook the system you get has hardly any extras to what you need (in comparison to most distros), it doesn't even have X.  From that you can create the best system for you.

2)  Learning.  Even after just one run through of the Gentoo handbook I had learnt so much.  Now, providing I have a little assistance from guides, I have no problem compiling my own kernel.

I would recommend, as sujoy said, using the handbook rather than the Installer on the LiveCD.  Apart from the fact that you learn more, I have never got the installer working on my computer.

I also agree with regomodo, I have never noticed the speed improvement you are supposedly meant to get.  A stripped down install would give more tangible benefits, but that can be done with most distros.  Although it is easier building up, sometimes it can be hard deciding what to take out of a standard install.

---

### Post by regomodo on 2008-06-15
> **sujoy said:**
> follow the wiki to every word, install the gen kernel and get the system to boot first,  then you can take time and compile your own custom one. 

If the "genkernel all" command is supposed to be a trouble-free method of getting a working kernel, then it isn't. 

In my  1st experience with it it for some reason compiled the nvidia sata/pata controllers as modules and i could never get my system to boot. After compiling them into the kernel directly (the non-automatic route) and i was in.

---

### Post by trimeta on 2008-06-15
> **regomodo said:**
> If the "genkernel all" command is supposed to be a trouble-free method of getting a working kernel, then it isn't. 

In my  1st experience with it it for some reason compiled the nvidia sata/pata controllers as modules and i could never get my system to boot. After compiling them into the kernel directly (the non-automatic route) and i was in.
I've never actually used genkernel, to be fair; still, how long ago was your failed attempt? Maybe it's improved since then...

---

### Post by HunterThomson on 2008-06-16
Yes, wile reading through the Gentoo handbook I have learned a lot. I think that is what makes installing Gentoo a good thing to do and what also makes it the l33t Linux i.e. once you get a Gentoo sys installed and configured you know quite a bit about Linux:)


However, I never did install Gentoo... I am now reading quite a bit about Debian. I like it for the same reasons I liked Gentoo... Correct me if I am wrong:

Rolling distro.... No more distro upgrade hell ((I am still using 7.10 because 8.04 has so many problems with my laptop HW))

Custom... only the programs I use and no nvidia driver (( I don't have a nvidia GPU so I don't need it))

Still cool l33t self made Linux system:)

But with Debian I don't have to compile everything. I still have all the packages and the install seems a bit simpler. I plan to install it with Ubuntu in the shell.

But the best part is no more distro upgrades:guitar: 
I just want my system to work and "Stay" working not brake with the next release. Not that there is anything wrong with Ubuntu. It is a vary good distro and vary simple to use. There are so many laptops and different hardware it is hare to make one OS to run it all out of box:)

---

### Post by M_the_C on 2008-06-16
Providing you don't pick to install any of the pre-set configurations (e.g. Dekstop) then yes, Debian is a good choice.

The main drawback of Debian is that unless you go to the unstable repos (i.e. like Ubuntu) then the packages are quite a bit behind.

Gentoo however can be accused of the opposite, the packages can be so up-to-date that they break things.

There is no perfect distro, just choose which suits you best.

---

### Post by HunterThomson on 2008-06-21
WEll,

I just installed Arch Linux:)

After, a hell of a time getting it up and running with a sudoer, xorg, kdebase, some apps. I am loving it:) 

wasted a lot of time trying to install a custom 2.6.23 kernel (do to mis-information about cd drive not working with 2.6.25 kernel... Only had to add hal to demons... I need to tell that guy on the archlinux forums...)

The FTP ISOCD didn't work so I had to boot into UBS Backtrack and download/burn coreISO CD.

It would have been a whole lot simpler to install if I had a printer or a second computer to read the instructions. I had to do it all form memory:lolflag:

I had my ALSA driver module running last night no problem but now it will not work??? "-Module Not Found"

BUT, in the end it is all I hoped it would be i.e. FAST>>>, only the apps I installed and use, I know how to configure 'most' everything(because I had to:), Rolling distro up to date and will stay that way\\:D/, AND still simple/fast to install new programs.

---

### Post by sujoy on 2008-06-23
for the problem, go to the IRC channel at freenode, there are some really helpful people.

as for arch, well, thats the beauty of it.
you need binaries --> repos
you need source   --> ABS

Edit: gees almost missed out on the lovely AUR :)

---

### Post by spupy on 2008-10-11
Addition to things people already said:

I love the Gentoo packaging system - Portage. First, because it uses soft dependencies. Hard ones always gave me troubles in Ubuntu/Debian. 
Revdep-rebuild. Awesome. If for some reason an upgrade breaks programs in your system, revdep-rebuild scans libraries and programs, finds the problems, and fixes them.
And many more little cool features.


Oh, yeah, Ubuntu and Debian don't like my touchpad. :-|

---

### Post by crimesaucer on 2008-10-11
Why I would use Gentoo is for the custom CFLAGS/CXXFLAGS/MFLAGS being used for compiling everything from source on an Authentic AMD64 kernel.....


I gave the install a try, spent a solid 2 days at it, failed the first attempt because I did it wrong in the beginning..... then for the second try I know that I followed every step in the AMD64 handbook for a stage 3 install.... but when I was done and rebooted, I was unable to log into my new Gentoo partiton, and not even my Vista partition.


So I gave up for now and will try again latter when I have time....


For now, I'll just stay with my Archlinux, custom compiled zen2 patched kernel, and pacbuilder to compile my entire system using the same custom flags..... basically as close to a Gentoo system as I can get on Arch.

---

### Post by chris200x9 on 2008-10-11
use flags! get rid of unneeded stuffs :)

---

### Post by ippokratis on 2008-10-11
> **spupy said:**
>  
Revdep-rebuild. Awesome. If for some reason an upgrade breaks programs in your system, revdep-rebuild scans libraries and programs, finds the problems, and fixes them.
And many more little cool features.



Yeah! That's a fine reason too!  I love Gentoo because is fast, with only necessary packages, no upgrades, perfect!  A little difficult to install it, but after... :guitar:

---

