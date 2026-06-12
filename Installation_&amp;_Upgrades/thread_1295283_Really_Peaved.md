---
title: "Really Peaved"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2009-10-19
All,

I know the web site designers thought the simplification of the download site to the current version was best for the user community, but in their wisdom to do so rushed ahead and forgot all us more serious users, developers and machine builders that for various reasons have to be able to see and get all older versions/distros, to support certain platforms, software releases, etc. that just will not allow the acceptance of the latest release.

The simple thing they overlooked, that really peaves me in a link, on the download page to all other versions.  Even the search tool does not produce the list and one must go looking for it.

I have attempted to keep on my master server all the versions since 7.04, but can not find the "alternate" versions and the "powerpc" versions for many of these releases.  Also I have 3 download threads that got interrupted, so 3 of my versions code are incomplete.  When I search for the file (EX: "ubuntu-8.10-server-i386.iso") it does not come up as the in the search and it should and should be the first item in the results.

This make me have to waste valuable time to get up here on the forum, explain what I need, and wait hours to get a response on something that should be 2 clicks away from the download site.

Please help me get the web designers attention and fix this!  Submitting a bug-fix doesn't seem to help!

Thanks!

OMR

---

### Post by OldManRiver on 2009-10-20
All,

The distros I'm missing are:

ubuntu-7.04-alternate-amd64.iso
ubuntu-7.04-alternate-i386.iso
ubuntu-7.04-desktop-amd64.iso
ubuntu-7.04-desktop-powerpc.iso
ubuntu-7.04-server-amd64.iso
ubuntu-7.04-server-powerpc.iso
ubuntu-7.04-textonly-amd64.iso
ubuntu-7.04-textonly-i386.iso

ubuntu-7.10-alternate-amd64.iso
ubuntu-7.10-alternate-i386.iso
ubuntu-7.10-desktop-amd64.iso
ubuntu-7.10-desktop-powerpc.iso
ubuntu-7.10-server-amd64.iso
ubuntu-7.10-server-powerpc.iso
ubuntu-7.10-textonly-amd64.iso
ubuntu-7.10-textonly-i386.iso

ubuntu-8.10-alternate-amd64.iso
ubuntu-8.10-alternate-i386.iso
ubuntu-8.10-desktop-amd64.iso
ubuntu-8.10-desktop-i386.iso
ubuntu-8.10-desktop-powerpc.iso
ubuntu-8.10-server-amd64.iso
ubuntu-8.10-server-i386.iso
ubuntu-8.10-server-powerpc.iso
ubuntu-8.10-textonly-amd64.iso
ubuntu-8.10-textonly-i386.iso

ubuntu-9.04-server-powerpc.iso
ubuntu-9.04-textonly-amd64.iso
ubuntu-9.04-textonly-i386.iso

OMR

---

### Post by howefield on 2009-10-20
> **OldManRiver said:**
> This make me have to waste valuable time to get up here on the forum, explain what I need, and wait hours to get a response on something that should be 2 clicks away from the download site.

You think that is bad, have pity on us who waste valuable time reading and responding to such whines... ;)

Many of your "missing" downloads may be found at 

[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

---

### Post by jefelex on 2009-10-23
What I have to ask is how do you change the /etc/apt/sources.list to ensure that if you have to reinstall an older version (7.10), how then can you get all the updates from the old-releases archive?  it would be nice if there were some step by step directions for an old fart like me to follow!

---

### Post by howefield on 2009-10-23
> **jefelex said:**
> What I have to ask is how do you change the /etc/apt/sources.list to ensure that if you have to reinstall an older version (7.10), how then can you get all the updates from the old-releases archive?

Would you really want to install an unsupported system ?

7.10 went end of life last April.

Don't think there is a way to do what you want easily, if at all.

Don't let that put you off though, usually when I say something can't done, someone comes along to prove the exact opposite :)

---

### Post by OldManRiver on 2011-05-21
All,

Had not been back to look at this for a while.  Still peaved but different reason this time.  The last post here explains why.  "End of Life", man you knotheads,

Do you not know there are servers still out there running RH1!

Reason:
Hardware is not compatible with newer releases and/or had to have custom drivers built, so:

**"If it's not Broken, Don't fix it!!!"**

See if I have a box working doing what I need it to do and it has been happy doing that for me for 10-15 years, why change it or mess with it.  That means if the box is still running the #@#$%^$# OS must still be supported!

Sorry working boxes trump any of your: "Don't feel like it" answers.

Just my Thoughts!

Cheers!

OMR

---

### Post by tgalati4 on 2011-05-22
I actually agree with OMR.  It would be nice to have community-supported LTS releases.  Backports provides some of this, but a more thorough, community-supported framework would be helpful to keep the LTS releases around for a while.

---

### Post by Hedgehog1 on 2011-05-22
Well, I give **OMR** 2 gold stars for finally responding to the 2009 post, even if it is 2011 now. :D

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-22
> **tgalati4 said:**
> I actually agree with OMR.  It would be nice to have community-supported LTS releases.  Backports provides some of this, but a more thorough, community-supported framework would be helpful to keep the LTS releases around for a while.

Running hardware so old that it cannot run 10.04 is a very risky situation.  If the hardware goes down, there are no spare parts.

I know that to many folks it like replacing the unused spare tire on your car every 12 years - seems like a waste until you get a flat. In the desert. On a lonely road. At night. Out of cell phone service.

***The Hedge***

:KS

---

### Post by kaldor on 2011-05-22
> **tgalati4 said:**
> I actually agree with OMR.  It would be nice to have community-supported LTS releases.  Backports provides some of this, but a more thorough, community-supported framework would be helpful to keep the LTS releases around for a while.

I agree so much. The biggest issue I have is that staying with an LTS on the desktop leaves me out in the cold when I want to get new stuff, so I need to upgrade my entire OS. I always tell myself "I'll stick to the LTS", but then within a year I find a PPA or new software I could really use but am unable due to being on an unsupported OS. I think the "LTS" tag only applies to servers and specialist workstations right now.

---

### Post by OldManRiver on 2011-05-22
Kudos to all you for the really supportive responses.

At least the brainheads, with the "We know better"* mentality, they could at least leave us a nice set of repositories, with a "You are on your own" message and we "Old Farts" with working Gorrilla machines, that keep slamming the home runs, can create our own "self help" group with our own IRC Chat and all, and keep doing our jobs.

Just my thoughts!

Cheers!

OMR

*  The old IBM school of thought that almost bankrupted them and now the MicroSoft school thought, which will bankrupt them -- So what the @##$^$%$# is it doing in the Linux world?  Have we lost our thought edge?

---

### Post by tgalati4 on 2011-05-22
Well, since you have the source code for most of any distro that you are running, you can fix problems and patch vulnerabilities yourself.  It's just a pain to do so.  

And technically it's not necromancy to respond to your own thread, even if it is over 2 years old!  Some of us old timers are not happy with the pace of change in Ubuntu and it's breakage every 6 months.  Regressions are no fun, nor is patching and finding work-arounds every time we upgrade.

Dapper Drake with 6 years of bug fixes and some backports makes a fine operating system.  I can even run the latest Bitnami stacks of (statically-compiled binaries) of the latest web packages.  So it really depends on how you use the machine.  I've had a Dapper Drake machine running continuously since 6.06 (June 06) and it still runs well.  It was a desktop machine that got morphed into a server and it's bullet-proof.  One of these days I will migrate to Lucid, but I know I will have breakage and weirdness to deal with.

---

### Post by OldManRiver on 2011-06-03
> **tgalati4 said:**
> Well, since you have the source code for most of any distro that you are running, you can fix problems and patch vulnerabilities yourself.  It's just a pain to do so.  

And technically it's not necromancy to respond to your own thread, even if it is over 2 years old!  Some of us old timers are not happy with the pace of change in Ubuntu and it's breakage every 6 months.  Regressions are no fun, nor is patching and finding work-arounds every time we upgrade.

Dapper Drake with 6 years of bug fixes and some backports makes a fine operating system.  I can even run the latest Bitnami stacks of (statically-compiled binaries) of the latest web packages.  So it really depends on how you use the machine.  I've had a Dapper Drake machine running continuously since 6.06 (June 06) and it still runs well.  It was a desktop machine that got morphed into a server and it's bullet-proof.  One of these days I will migrate to Lucid, but I know I will have breakage and weirdness to deal with.

tgalati4,

You mention Dapper Drake and there are now so many flavors of Linux that I've lost count.  Soon some enterprising young geek will discover a way, as I did with "homogenous melding" (Cross Transform days - which lead to MiddleWare), that will merge, what ever base core version/flavor you have and add all the new capabilities from a central respository.  That and when we get "plug-n-play" hardware drivers, then Linux will again dominate the world, not just in numbers (which it already has) but in thought process and innovation.

Though I'm not an HP fan, I love their new hplip, that finds the driver for any of their printers and installs it on you Linux box.  Kudos HP!!

Since they are treating all their printers as a repository and using their own Linux code to address and access the repository and install drivers that way, I think that might spark the imagination of other HW OEMs to think the same way and soon all we will need is a seperate repository, with lists of the HW OEMs and the "plug-n-play" will be on it's way.  HEY!!   HEY!!  :)

Cheers!

OMR

---

### Post by tgalati4 on 2011-06-04
Well, that's already happening.  Look at [http://bitnami.org](http://bitnami.org).  This is a company that is statically compiling several popular packages that you can load on to your older machines.  It takes up more disk space since it's using bundled library files, not the old libraries that came with your aging distro (Dapper Drake in my case).  

Also, virtual machines allow you to run several linux distros on one real machine.  So you could have a machine running Dapper Drake, Hardy Heron, and Lucid Lucy--all LTS releases--and just keep running applications on each instance until they break then load them up on the latest instance.

I'm contemplating setting up a Xen hypervisor to run these LTS releases to keep them around.  For instance I have a build environment to cross-compile code on Dapper Drake for my nokia n800.  I imagine recreating that build environment will be difficult under Lucid.

---

