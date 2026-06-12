---
title: "getting online from gentoo live cd"
date: 2008-07-30
forum: Gentoo and derivatives
---

### Post by SteveNorman on 2008-07-30
I use ubuntu/xp now, but would like to learn some more "pure" forms of linux. I downloaded the gentoo install/live iso and burned it to dvd. When booting from the DVD It sees my NIC, and /sbin/ifconfig shows it as eth0, but I cannot get online with it. Should I be able to get online from the live cd? or do I need to install it first? Also, it seems that a lot of commands that the install guide do not work in the live cd environment. I am used to the Ubuntu live cd, in which ubuntu runs almost as well as when booted of the HD. Is the gentoo live cd not the same?

---

### Post by Bachstelze on 2008-07-30
The Gentoo Live CD is not so great, and not needed anyway. You can just as well install Gentoo from your Ubuntu system.

---

### Post by coffeecat on 2008-07-30
> **SteveNorman said:**
> Is the gentoo live cd not the same?

No, it isn't. If you look around Gentoo forums, you'll see a lot of - ahem - debate ( :wink: ) about the live CD. Out of interest I tried the latest live CD on a spare partition. I got myself a basic install easily enough, but thereafter I encountered all sorts of strange issues that nearly had me stumped. And I've installed Gentoo a few times before and have been using it for a couple of years. 

Personally I'd recommend a stage 3 install from another distro as HymnToLife says. This will work if you are installing to another partition on the same machine as Ubuntu but if you want to install to a dedicated machine, you do need a live CD to work from. Unfortunately you cannot use the Ubuntu live CD because it doesn't come with the developer tools you need - gcc and make - (would someone please correct me if I'm wrong). Gentoo-ists seem to favour Knoppix.

[Read the handbook]("http://www.gentoo.org/doc/en/handbook/index.xml") before you attempt anything. Did I say to read the handbook? :)

Be warned that with a stage 3 installation you end up having to boot into a console and constructing a GUI from that. And be warned that there's a very steep learning curve.

---

### Post by SteveNorman on 2008-07-30
> **coffeecat said:**
>  And be warned that there's a very steep learning curve.


thats what I am hoping for really,,If I can pull it off I think it will advance my knowledge more. I will read the handbook again, but does it cover how to install from within ubuntu or knoppix?

---

### Post by coffeecat on 2008-07-30
> **SteveNorman said:**
> does it cover how to install from within ubuntu or knoppix?

It's telling you how to install from within the Gentoo live CD environment or the Gentoo minimal installation CD, but you can apply the same procedure to any suitable live CD or another distro on another partition. Whether you use a Gentoo CD, A Knoppix CD, or Ubuntu on another partition, the principle is the same. You format the partition(s) on which you are going to install Gentoo, mount them from the live CD/other distro, unpack the stage 3 tarball, install portage, configure compile options, chroot into the new environment, and so on and so on.

It's a lot to take in at first, but it makes sense - usually after you've done it a couple of times. :? The beauty of it is that if you get tired, you can close everything down and resume where you left off. For instance, if you've chrooted into the new environment and compiled a kernel, you can leave it there. Then, so long as you go through the chroot procedure again, you can resume at the creating /etc/fstab stage.

Good luck!

Oh, and: [http://forums.gentoo.org/](http://forums.gentoo.org/)

They're actually quite friendly in there. (And the coffeecat there isn't me.)

---

### Post by SteveNorman on 2008-07-30
Pretty scary,,,I may lurk in the forums a bit before I make a go of it. Thanks for your help!

---

### Post by SteveNorman on 2008-08-01
So I hope I am on the right track here, I am downloading the stage3 i686 from here:

[ftp://ftp.wallawalla.edu/pub/mirrors/ftp.gentoo.org/releases/x86/current/stages/](ftp://ftp.wallawalla.edu/pub/mirrors/ftp.gentoo.org/releases/x86/current/stages/)

I am a bit unclear what to do with the tar ball tho,,do I unpack it on my desktop? Not really seeing much info on the tarball method. And I am a bit slow at times....

---

### Post by coffeecat on 2008-08-01
You unpack the tarball within the root partition you have prepared for Gentoo. It's basically a skeleton system with some utilities and bits of gnu precompiled. When you've unpacked it you'll see (if memory serves me correct) /usr, /etc and so on with some contents.

By the way, if you want a **really** steep learning curve, try [Linux from Scratch](http://www.linuxfromscratch.org/) :twisted: You start by compiling your own tool-chain, package by package. :|

---

### Post by SteveNorman on 2008-08-01
oh man,,I may wait a bit for that. I get gentoo running and usable I'll give that a shot. The handbook for gentoo should be required reading for noobs like me,,it really goes into a lot detail about formating and mounting. As soon as I can get a successful tarball downloaded I will give gentoo a go. I appreciate your help!

---

### Post by regomodo on 2008-08-02
> **SteveNorman said:**
> 
I am a bit unclear what to do with the tar ball tho,,do I unpack it on my desktop? Not really seeing much info on the tarball method. And I am a bit slow at times....
 here you go. [link]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=5")

---

### Post by SteveNorman on 2008-08-02
Got it,,thanks!

---

