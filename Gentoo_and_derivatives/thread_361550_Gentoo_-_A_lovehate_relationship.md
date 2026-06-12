---
title: "Gentoo - A love/hate relationship"
date: 2007-02-14
forum: Gentoo and derivatives
---

### Post by Rodneyck on 2007-02-14
Ok, I have this love/hate relationship with Gentoo and Gentoo-based distros. I love many of its features, but mostly, I love it for its lightening fast speed as compared to other distros. I assume this has to do with everything being compiled and dependencies configured into one big mashed potato that works, for the most part.  I really want to love it. I do, envious of people who report good things, really.

However, after several failed attempts at Sabayonlinux, the most recent a few days ago trying the bloated 3.26 DVD... again, I always seem to run into something that makes it either so frustratingly complex to make work or something that makes the distro to unreliable to have as a main working environment. 

I finally gave up on Sabayon, at least until the next version. I instead, searched for another distro that was Gentoo-based in hopes this would provide better results and less frustration. Surprisingly, I have only found one other, Kororaa. 

Kororra comes in two flavors, the livecd (which was not so live for me, ie it did not boot up, no matter what I tried) and the install cd (2 cds to be exact.) After installing, I was met with a lovely KDE system that like Sabayon, was lightening fast, maybe even faster as this version installed without beryl or any 3D desktop. After I started to dig around a bit, I noticed that everything was a bit outdated. It seems there is only one developer working on Kororaa and updates leapfrog several months at a time. Actually, correction, years to be more exact, as the non-livecd version was released in 2005. This is the version I used and we are talking way outdated. 

To update, meant I had to basically update KDE, x server, then everything else. In theory, or in Debian world, this would not be such an odious task, but in Gentoo, this meant headache(s) and ambiguous instructions. I started to do this but immediately, as has happened in Sabayon, the user is met with masked dependencies and tons of questionable errors in part due to...dependent apps. After reading through their forum, the general consenses was "...well, it's not going to be easy to update, so good luck with that."  I concluded that it would be easier to just install pure Gentoo and start anew, than to go through all the trouble updating everything in Kororaa and deal with things being broken in the end, which was very likely from their forum topics.

So this brought me to the question of, should I Gentoo or not Gentoo?  I find it strange that there are not a lot of distros based off of Gentoo and the two I have found, most users of Sabayon and Koraraa do not update their systems through Gentoo repos themselves, but instead wait for the developers to release a new upgrade (CD/DVD) to obtain main features of their system. Sure, adding amule might be easy, but just try and update to KDE 3.5.6 for all its bugfixes. OUCH!! 

As I have pointed out, Kororaa has too slow of a release cycle, for me, and Sabayon has recently lost half of its developers, reporting that their next release will be slowed down as a result. Again, more waiting for functions that could be a click away in a Debian-based world.

I then found this piece written by a longtime Gentoo user that addresses many of the problems and questions I have and have found in both Sabayon and Kororra. If you are wondering about this distro or have bludgeoned you head into the wall asking, "Is it just me?", then give this a read and decide for yourself.

[http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/](http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/)

---

### Post by mips on 2007-02-14
> **Rodneyck said:**
> 

So this brought me to the question of, should I Gentoo or not Gentoo?  

Strange as I have for the last two days asked myself the same question. I'm keen to try Gentoo but I'm not that big on customising things things. I like installing things and they just work.

I really do like Sabayon and find it stable as hell but there is one or two things that I'm battling with. Besides that I'm happy as pig in poo.

The thing I really appreciate is the speed. I also love the Gentoo documentation. If you follow the docs things are bound to work.

Maybe FreeBSD ?

---

### Post by zaratustra on 2007-02-14
For me, there is no sabayon or anything else that could replace true flavour of gentoo. Just because it is closest to LFS and it gives you control and does only what you say. Thing which I don't like with sabayon is that it installs so many stuff. Why the *uck I need every available media player? Gentoo made by your hand is so custom and it is reason why it is so beautiful. And if you are hardcore geek and control phreak, there is no doubt.:) You should gentoo:)

---

### Post by manmower on 2007-02-14
If you have to have Gentoo I would recommend using Gentoo itself and not one of its derivates. If you just want speed without the hassle, you should consider giving Arch Linux a try, using one of the new 0.8 alpha iso's. This will take a while to set up but once you know how it's done you will be able to repeat the whole thing in < 30 minutes the next time, if there ever is a next time, because Arch is always up to date. When the occasional tricky update comes along they are well anounced and how-tos are provided in the Arch news.

If you really don't want to start from just a base and get your hands dirty, maybe you could try [Underground Desktop](http://underground.geekcode.info/portal/posts/), one of the Arch Linux based LiveCDs. As far as I know upgrading (doing a pacman -Syu) from Underground Desktop as it is WILL break a few things (most notably you'll have to edit your grub configuration to accomodate the new name for the kernel image, and watch your fstab because devices might change names from hda* to sda*) but as I said these are well documented in the News on Arch's homepage.

---

### Post by mickbuntu on 2007-02-14
Hello,

I have been using gentoo since about 2004 after slackware and know some ins of it.  It has portage, gentoolkit bunch of other  good things. Also that one does not need to compile parts of programs that they do not want. That is a central make.conf file exists in /etc/make.conf. The "-" says not to add that feature to the program  and nothing at all says to compile it. Example:  -qt -gtk says  you  do not  want  those   to be part of the   program build. If the program  supports  another toolkit. It will use that instead to function normally. Also  one can set  number of  parallel  builds with  MAKEOPT="-J2" as an example.  

emerge  <package>   is  a  simple  command  to run and it  runs  its  build.

emerge --unmerge <package> removes the package.

You can use  shortcuts: emerge -uvad world  as an example.

That says  to upgrade  verbose  ask  and  do it  deep. To not just  upgrade  but  do something like  apt-get dist-upgrade.

emerge --ask  will just   obviously  ask you if you want to merge the  update.
emerge --pretend will obviously pretend what it would do and list it instead of asking. But it will not begin until you tell it to. You can use combination of  various commands and  use  emerge --help to see them all.
emerge --newuse  for instance will totally  check and recompile packages with the new use  flag.
emerge --emptytree  will start as if you had nothing.

Emerge --sync  will  sync with the  server against  your computer. To see if  your  software information is  outdated. After it  syncs  you can upgrade.  My  how can forget  revdep-rebuild  part of gentoolkit. It helps you if you  broken a package. It  works  about  85% of the  time  which think is  good. But  it  can go into  loop  sometimes. portage is nice too, but it   can cause  "upgrade" "downgrade" syndrome. 


You  can mask  packages too and unmask  unstable ones in  /etc/portage. Such files as  package.use (to  make a  specific  package  drop optional   compile  time   programs not a  worldwide file as make.conf)  package.keywords and package.unmask  allows you to add unstable  apps. Some ackages are hard masked as well.  Of  course  this is just  the  surface what you can do. Pages and pages of  things. 

I  have  been toying  around with ubuntu since   "Warty" came out. Received my   first   "3" disks  of  warty, followed by "3" more of  "Hoary" , Breezy, Dapper.  Forgot  but one  version they did not ship out burned it too.   Likely  made my  full switch to Debian based  operating system.  I am running a  server now, Gentoo makes a  good server.  But  just out of   personal like  of  the  cool apt  and   less  fiddling  needs now  decided to go with  ubuntu. Also for  something that  cost  absolutely  nothing  volunteer  work one  of a  good  job! Will I stay with ubuntu? Likely.   If it  can  prove to me  that it does not need  all the time  attention.

---

### Post by Rodneyck on 2007-02-14
Thanks mickbuntu, I found a wiki on both Kororra and Gentoo that covered a lot of what you suggest, but a great all-in-one guide for those in question. Great effort.  

Unfortunately for me, Kororra was so old, that I received lots of masked packages which would have taken a lot of time to investigate if the unmasking did not work. I understand Mips comment in that I want things to be a little easier and maybe that statement means I am not Gentoo material. I am not worthy...lol.  Yet, I still want to be... I'm a fringe Gentoo wanna-bee and not sure if that is good or bad. :) 

Manmower, I did try and install Arch a month back, but if memory serves me, configuring and formating the partitions left me with my head in the sand. Fortunately, I can now report due to my experience with Kororaa, I am now able to accomplish this task, AND understand it.  The Kororaa dev created a snappy pdf/howto on how to install the system with easy including instructions on how to configuring a partition. I now know about swap/boot/home, etc. the different types and how much space to allocate for each, kudos to the creator of that guide.  With this in hand, I might try Arch again.  BTW, I assume it is Gentoo-based?

---

### Post by manmower on 2007-02-14
> **Rodneyck said:**
> BTW, I assume it is Gentoo-based?

It is not in fact, I just brought it up because the one thing you really love about Gentoo seems to be its speed, and that is where Arch also excels.

[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

If you seriously want to try and install it again I suggest you use the [latest iso](http://www.archlinux.org/news/283/), this will minimize your trouble in updating to the latest and greatest. And I encourage you to examine if not print out some basic guides from the wiki, to get you to the point where you have a graphical system (WM/DE of your choice).

---

### Post by mips on 2007-02-14
> **manmower said:**
> 
[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

[I]
"This may be the most interesting competitor to Arch since it goes head to head in package modernity and has a somewhat sizable, smart, active, no nonsense community." [/I]they say about FreeBSD...

---

### Post by RAV TUX on 2007-02-14
> **mips said:**
> [I]
"This may be the most interesting competitor to Arch since it goes head to head in package modernity and has a somewhat sizable, smart, active, no nonsense community." [/I]they say about FreeBSD...

mips I was always interested in BSD...but found FreeBSD a nightmare...

I left Sabayon for a weekend, installed openSuse, KNOPPIX, and rPath...I missed Sabayon incredibly...

I understand the issue of bloat, I took a DVD to my wifes University Computer Lap popped it into and obviously low quality Dell (I didn't bother getting specs)....it loaded without fail but ran noticeably slower then my home computer

(but this was just running live and not an install)

My only solution is to develop a Gentoo based distro that is smooth and efficient with out bloat....that everybody can easily use and enjoy

give me time I am working on something...it may be a while

also I did find that simply using --unmerge to remove unnecessary programs works wonders....this may be the more immediate solution

unless you go with a pure Gentoo system

---

### Post by yabbadabbadont on 2007-02-14
Gentoo isn't really that much faster than most other distributions.  It's just that, by configuring your USE flags properly, you cut out all the crap from the packages you install that other distributions include.  In that sense, it does make the system seem faster as the programs are smaller (and generally there are less of them).

I've used (mainly) Gentoo since late 2002 but, in the last year or so, I've been mostly using Ubuntu Dapper.  I love it when I have a well configured Gentoo system, but I've reached a point where I don't want to spend any time maintaining it.  I don't care too much about having the latest and greatest package versions.  I just want a stable system that gets regular security updates.  That's what Dapper provides (usually :)).

---

### Post by rai4shu2 on 2007-02-14
[http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/](http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/)

That's an interesting article. There's a lot to think about there, especially considering GCC just upgraded to 4.1.2 recently.

---

### Post by mips on 2007-02-14
Hmm, I see DesktopBSD 1.6RC1 is out (although no anouncement to the effect). It is based on FreeBSD 6 so I might just give it a spin.

[ftp://ftp.desktopbsd.net/pub/DesktopBSD/Torrents/1.6/DesktopBSD-1.6RC1-i386-CD.iso.torrent](ftp://ftp.desktopbsd.net/pub/DesktopBSD/Torrents/1.6/DesktopBSD-1.6RC1-i386-CD.iso.torrent)

or

[ftp://ftp.allbsd.org/pub/desktopbsd/DesktopBSD/Releases/1.6](ftp://ftp.allbsd.org/pub/desktopbsd/DesktopBSD/Releases/1.6)

---

### Post by mickbuntu on 2007-02-14
> **Rodneyck said:**
> Thanks mickbuntu, I found a wiki on both Kororra and Gentoo that covered a lot of what you suggest, but a great all-in-one guide for those in question. Great effort.   

Your welcome Rod,  that is  how  guess it  works we share  knowledge on  linux with one another. 

> **mips said:**
> Hmm, I see DesktopBSD 1.6RC1 is out (although no anouncement to the effect). It is based on FreeBSD 6 so I might just give it a spin.

[ftp://ftp.desktopbsd.net/pub/DesktopBSD/Torrents/1.6/DesktopBSD-1.6RC1-i386-CD.iso.torrent](ftp://ftp.desktopbsd.net/pub/DesktopBSD/Torrents/1.6/DesktopBSD-1.6RC1-i386-CD.iso.torrent)

or

[ftp://ftp.allbsd.org/pub/desktopbsd/DesktopBSD/Releases/1.6](ftp://ftp.allbsd.org/pub/desktopbsd/DesktopBSD/Releases/1.6)

Hi Mips!! It uses  the  ports  like gentoo does  but in a  bit  different way.  Google has some interesting information  on "bsd" desktops.  Installed  the original  bsd one time. It used to come on  floppy disk as a method to install.  Doing that right now is not practical I did it  only because back then did not have a  burner, a readily fast accessible  internet   connection.   


> **rai4shu2 said:**
> [http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/](http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/)

That's an interesting article. There's a lot to think about there, especially considering GCC just upgraded to 4.1.2 recently.

Thanks for the  article rai, it  hits  home personally so going to read it right now. But it  probably will not  change my  own personal view on gentoo. As already formed my opinion of it using it long time. The Author  though started even before I did. So they might have some strong  words in that article.  Either way it will be nice to read in  someone else's mindset of the  distro! 

Thanks again.

---

### Post by pay on 2007-02-14
> **RAV TUX said:**
> My only solution is to develop a Gentoo based distro that is smooth and efficient with out bloat....that everybody can easily use and enjoy

give me time I am working on something...it may be a whileI would gladly help you test that out:) 

Gentoo's probably been the distro that I have used the most. What I end up doing is getting fed up with all the maintenance that it needs so I convert to another distro and then I start to miss things out of gentoo/portage that i wished that the new distro had. It's a vicious cycle. 

That's why I would love a simple, light Gentoo based distro that is easy to use and doesn't take forever for the initial installation... Sabayon is probably the closest thing to that but it has way too many packages installed that aren't needed and way too many proprietary packages. For example, I found that it installed the proprietary nvidia AND ati drivers as default which is sort of negative to the gentoo philosophy.

---

### Post by zaratustra on 2007-02-15
I am here for testing and maybe some coding also...:) Sabayon would be better if it had a possiblity to customize package list before install.

---

### Post by rai4shu2 on 2007-02-15
> **mickbuntu said:**
> Thanks for the  article rai, it  hits  home personally so going to read it right now.

Actually, I was reposting the link given by the OP, and it struck me how serious problems with upgrading GCC can be. The comments after the article are pretty educational as well, so make sure you read those too. :)

---

### Post by RAV TUX on 2007-02-15
> **zaratustra said:**
> I am here for testing and maybe some coding also...:) Sabayon would be better if it had a possiblity to customize package list before install.
This is exactly what I am thinking:)

---

### Post by runningwithscissors on 2007-02-15
> **rai4shu2 said:**
> [http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/](http://www.xaprb.com/blog/2006/11/21/to-gentoo-or-not-to-gentoo/)

That's an interesting article. There's a lot to think about there, especially considering GCC just upgraded to 4.1.2 recently.
A minor point GCC release usually does not cause any problems at all on Gentoo.
Downgrading your toolchain or performing an upgrade to a major revision can sometimes. (3 to 4, or so).

Yes, some things can be a bit of a hassle (my last kernel upgrade borked my SELinux policy and I haven't got around to fixing it). But for everyday desktop use, it isn't as troublesome as people say.
The only problems I can imagine are compile times (which are minimal except for larger packages like entire desktop environments or IDEs) and the old CUPS monster.

---

### Post by Rodneyck on 2007-02-16
> **manmower said:**
> It is not in fact, I just brought it up because the one thing you really love about Gentoo seems to be its speed, and that is where Arch also excels.

[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

If you seriously want to try and install it again I suggest you use the [latest iso](http://www.archlinux.org/news/283/), this will minimize your trouble in updating to the latest and greatest. And I encourage you to examine if not print out some basic guides from the wiki, to get you to the point where you have a graphical system (WM/DE of your choice).

Well I installed Arch with wiki in hand, but I must have missed something. After I rebooted, I was met with just a prompt asking for Host ID or Host Login & password. I have no idea what it wants, as none of this was asked nor set during installation.  I will look over it again and see if there is something I missed.

---

### Post by manmower on 2007-02-16
You hostname should have been set during the install when you edited /etc/hosts. But at this point that is not the most important bit. You should be able to login as root with no password. Then you can use passwd to set a root password of your choice and add a user using the useradd command.

You can get help by looking at the manual pages, e.g.
```
man useradd
man passwd
```

I suggest doing this right away and just use su or sudo (you'll have to install sudo, instructions in the wiki) whenever you need to be super-user. There will be lots of little things to configure at first, but the install guide and/or beginner's guide should get you on your way. Otherwise feel free to ask here or in their forums.

---

### Post by Rodneyck on 2007-02-16
Thanks manmower, but unfortunately, the only prompt I get is asking for the host login and password and I can not get out of it or past it. I may have to start anew.

BTW, I was doing some reading on Arch and looking over reviews. I assumed it was a compile type distro, but it turns out to be binary much like Debian (packages.)  Maybe you or someone else pointed this out previously and I missed that. Given that, my question to you is what makes it more speedier than a say a Debian based system?

For others, I have found a great review or look at the latest Gentoo distro. It contains a graphical look/step-through guide re the livecd so you know what to expect if you choose to install this way. I am still dangling my toe into the Gentoo pool trying to decide if I want to devote 18 hours to install it.  :) 

**Gentoo 2006.1**
The Gentoo release team has just announced the launch of their 2006.1 version, so we are going to take a look at what's new. Included in the updates is an improved installer/LiveCD with Networkless mode, smarter partitioner, updated compiler and more. This release also adds the addition of an AMD64 Live CD.

[http://techgage.com/article/gentoo_20061/1](http://techgage.com/article/gentoo_20061/1)

---

### Post by manmower on 2007-02-16
> **Rodneyck said:**
> Thanks manmower, but unfortunately, the only prompt I get is asking for the host login and password and I can not get out of it or past it. I may have to start anew.

I still think this is the normal behaviour. Does it look like this?

```
Arch Linux "versionnumber" ("versionname") ("yourhostnamehere") (vc/1)

"yourhostname" login:
```

If so just type root and press Return, when asked for a password just press Return again and you should be in. I thought the new 0.8 Beta iso's asked you to set up a root password in the installer now but maybe I was wrong (or did you use 0.7.2?). Either way I think your install went fine. Don't give up just yet. :)

> **Rodneyck said:**
> BTW, I was doing some reading on Arch and looking over reviews. I assumed it was a compile type distro, but it turns out to be binary much like Debian (packages.)  Maybe you or someone else pointed this out previously and I missed that. Given that, my question to you is what makes it more speedier than a say a Debian based system?

I recently pointed this out in the "is Gentoo still for me" thread, because some people were saying it was source based. The Arch Linux Vs. Others wiki page I linked to is also pretty clear on this. Anyway, what makes it fast? In my opinion:

- init system makes for very fast boot
- binary packages means quick installing as opposed to compiling from source. If the options are not to your liking or you want to optimise further you can recompile easily via the Arch Build System.
- all packages are i686 optimized as opposed to the usual i386. I think i686 is a very reasonable cutoff for machines still in use today (Pentium Pro and higher).
- 100% bloat free: You install only what you want and pacman only gets the absolutely necessary dependencies, unlike apt-get which sucks in tons of deps and sometimes even "recommendations" if you're not careful.

I think the last point is the most important one for day to day use: having only what you need installed is always going to give you a more responsive system than any of the heavyweight distros can give you. You can have this with Debian too, but I find Arch much easier to configure, and much easier to keep at the leading/bleeding edge. A Debian FTP install for instance would be very fast but harder to tweak under the hood, and you're bound to run into problems by combining stable, testing and unstable repos etc. In Arch, current repo is always pretty much up to date and you upgrade every day or every other day. You will run into small glitches now and then but I find this easier than facing a slew of new problems every six months. If you are feeling brave there is the testing repo, which contains future candidates for the current repo, and plays nice with it.

Anyway, I don't want to push it on people, but I think if you conquer the (small) initial hurdle to a fully fledged GUI system, you might just be surprised at how easy it is to maintain, and stick with it.

---

### Post by zaratustra on 2007-02-16
> **RAV TUX said:**
> This is exactly what I am thinking:)
Great minds think the same:) LOL

---

### Post by Rodneyck on 2007-02-16
> **manmower said:**
> I still think this is the normal behavior. Does it look like this?

```
Arch Linux "versionnumber" ("versionname") ("yourhostnamehere") (vc/1)

"yourhostname" login:
```

If so just type root and press Return, when asked for a password just press Return again and you should be in. I thought the new 0.8 Beta iso's asked you to set up a root password in the installer now but maybe I was wrong (or did you use 0.7.2?). Either way I think your install went fine. Don't give up just yet. :)



Not quite, it was just "hostname:" and "Password". I reinstalled it and this time (either I spaced it and missed the option initially or ???) it asked me to enter a root hostname and password. I entered these when prompted again and it then let me access the terminal-like prompt. I then downloaded KDE and configured the rc.conf to add "kdm" so KDE would start up on boot, all was well. 

You are correct, this is NOT for newbies. You are basically installing everything, and I mean everything, by hand. It does make for a great tweaking distro and very customized for the user, which I like. It is speedy, but not sure if it surpasses Gentoo in that department. Gentoo was speedy with Beryl running and I have not even gotten to that yet in Arch. I just built my first xorg.conf file from scratch, but getting there. 

I do like the idea of never installing another "update" disk to update the system. I with this were the case with more distros.  After I am done, I will compare it to Gentoo and see how it stacks up. I just need a free weekend to install Gentoo. :-k

---

### Post by mips on 2007-02-18
> **zaratustra said:**
> I am here for testing and maybe some coding also...:) Sabayon would be better if it had a possiblity to customize package list before install.

[http://www.sabayonlinux.org/forum/viewtopic.php?t=3666](http://www.sabayonlinux.org/forum/viewtopic.php?t=3666)

---

### Post by Rodneyck on 2007-02-18
> **mips said:**
> [http://www.sabayonlinux.org/forum/viewtopic.php?t=3666](http://www.sabayonlinux.org/forum/viewtopic.php?t=3666)

My feeling, I think they should bump it up to priority and not an afterthought. It seems to be the number one complaint on the Sabayon forum. It was high on my list.

---

