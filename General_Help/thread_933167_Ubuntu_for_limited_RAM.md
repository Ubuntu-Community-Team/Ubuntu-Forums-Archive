---
title: "Ubuntu for limited RAM"
date: 2008-09-29
forum: General Help
---

### Post by Peter09 on 2008-09-29
I was hoping to install a Linux operating system on my friends Laptop.

He is running Win95 on a laptop with 64MB of Ram and 8GB of disk. :confused:

Many small Linux's (DSL for instance) are based around a small footprint (low disk space) whereas I am not so bothered so much about disk space as RAM and CPU.

Anyone any suggestions - is there a small Ubuntu flavour that could do this?

---

### Post by Uchiha_madara on 2008-09-29
> by Peter09
ing Win95 on a laptop with 64MB of Ram and 8GB of disk.

Ubuntu at least need 256 Ram and 512 Mbyte Swap , 20 GB for ubuntu Application's and update ..... so i don't guess it works with him..

if he still need to use ubuntu 
try yo ask about XUbuntu, goUbuntu, and fluxUbuntu.....

---

### Post by kpkeerthi on 2008-09-29
[http://crunchbang.org/](http://crunchbang.org/)
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by snowpine on 2008-09-29
I would not recommend Crunchbang, Fluxbuntu, Xubuntu, or any type of 'Buntu with 64mb of ram. Windows 95 is 13 years old; the first version of Ubuntu came out in 2004. The system requirements aren't even close.

DSL is a fine choice for those system specs. Good luck!

---

### Post by snowpine on 2008-09-29
(Sorry, double post)

---

### Post by Uchiha_madara on 2008-09-29
you right and i agree with you .. i dont think so it works

---

### Post by kerry_s on 2008-09-29
> **Peter09 said:**
> I was hoping to install a Linux operating system on my friends Laptop.

He is running Win95 on a laptop with 64MB of Ram and 8GB of disk. :confused:

Many small Linux's (DSL for instance) are based around a small footprint (low disk space) whereas I am not so bothered so much about disk space as RAM and CPU.

Anyone any suggestions - is there a small Ubuntu flavour that could do this?


anything with 64mb of ram or less DSL is king, you can go custom debian if you want a particular setup, but it's pretty hard to do what dsl does out of the box.

if it has to be ubuntu, you can try the custom install with that.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

if your still wrapping your head around linux, i did see a ubuntu project, but haven't tried it myself.

[http://ubuntulite.tuxfamily.org/](http://ubuntulite.tuxfamily.org/)

---

### Post by snowpine on 2008-09-29
> **kerry_s said:**
> 
if it has to be ubuntu, you can try the custom install with that.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)



I would not recommend even a command-line-only install of Ubuntu 8.04 for a 13 year old computer with 64mb of ram. Read this bug report: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

DSL will use less resources and give you a GUI, browser, and lots of other apps instead of just a command line interface.

---

### Post by spongedaddy on 2008-09-29
I've used Puppy Linux on ancient PCs in the past successfully. It may be worth a try for you.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by kerry_s on 2008-09-29
> **snowpine said:**
> I would not recommend even a command-line-only install of Ubuntu 8.04 for a 13 year old computer with 64mb of ram. Read this bug report: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

DSL will use less resources and give you a GUI, browser, and lots of other apps instead of just a command line interface.

that bug is for vmware, were talking real hardware here.
i do agree though DSL would be the better choice since it can run on 16mb ram and up.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Peter09 on 2008-09-29
Thanks everyone for your replies....

**DSL**
I thought DSL looked really good, the only problem I have it that it seems to suggest that its not so good being installed, it sort of suggests that it runs best from a usb drive or CD (In the end that may be the only option - although I suspect this machine won't boot from USB).

**Puppy**
Puppy looks OK and may be a candidate. The main issue I had is that the technological age of my friend involves examining two stones to see if a sharp edge can be developed through mechanical brutality. I thought the puppy menus' looked confusing, and as this is going to be supported over a 200 mile gap simplicity will be good.

**ARCH**
Arch could have been ok but installation was confusing and would be difficult over the telephone.

**fluxbuntu**

Downloading now, I will run it up in a VM with 64MB. Not a good test as my machine has dual CPU's etc and his is more abacus like.

----------------------------

I am hoping to get remote support working for him, but this has been a bag of worms. He has just got a broadband package with a wireless router --- into the future here... however his Laptop has no wired connection, but he does have a wireless card :D --- which I think he has working in 95 but it doesn't connect to his router ....:(

All this over the telephone ....

Why not something easy like Brain Surgery, no one asks you to do anything just off-the-cuff for them in that field.

---

### Post by Flynn555 on 2008-09-29
so is fluxbuntu just ubuntu with fluxbox as the desktop enviroment or is there more lightwieght things happening behind the scenes??

---

### Post by snowpine on 2008-09-29
> **kerry_s said:**
> that bug is for vmware, were talking real hardware here.
i do agree though DSL would be the better choice since it can run on 16mb ram and up.
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

True, the initial bug was posted on VMware but if you keep reading other users replicated the bug on actual old hardware. Are you speculating, or have you yourself successfully installed Hardy on "real hardware" with only 64mb?

---

### Post by LowSky on 2008-09-29
it Fluxbox on ubuntu... it wont work on 64MB (192MB maybe). Tell your friend he is better off saving $400-$500 for  new laptop or use DSL/Puppy, but if he isn't so technologically inclined he'll be up a certain creek without a paddle.

---

### Post by snowpine on 2008-09-29
> **Flynn555 said:**
> so is fluxbuntu just ubuntu with fluxbox as the desktop enviroment or is there more lightwieght things happening behind the scenes??

Fluxbuntu is Ubuntu 7.10 with Fluxbox and a light-weight applications suite: Kazekahase instead of Firefox, Rox-filer instead of Nautilus/Thunar, Xmms instead of Rhythmbox, Slim instead of GDM, etc. The lightweight applications are at least as important as the windows manager as far as building a lightweight system.

I would not recommend Fluxbuntu on 64mb machines due to the following bug I have discovered: [http://ubuntuforums.org/showthread.php?t=882096](http://ubuntuforums.org/showthread.php?t=882096)

---

### Post by snowpine on 2008-09-29
> **LowSky said:**
> it Fluxbox on ubuntu... it wont work on 64MB (192MB maybe). Tell your friend he is better off saving $400-$500 for  new laptop or use DSL/Puppy, but if he isn't so technologically inclined he'll be up a certain creek without a paddle.

This is probably the best advice in this thread. :)
And if your friend is tight on money for a new laptop (we are all feeling the pinch these days), he can probably find a used pentium 4 for under $100 that will still be light years ahead of what he has now. Your friend needs user-friendly, and user-friendly needs processing power and ram. :)

---

### Post by Peter09 on 2008-09-29
Thats why he's talking to me, I'm the user friendly bit :(

---

### Post by Sycron on 2008-09-29
Well my 486 DX2 66mhz is happy because he's running the latest version of DamnSmallLinux.

---

### Post by snowpine on 2008-09-29
DeLi Linux is another option. It is perhaps a better choice than DSL for an inexperienced user who just wants web browser, word processor, etc.

---

### Post by C.S.Cameron on 2008-09-29
FYI
Installs on USB flash can be booted on older machines using a boot CD.
A bit of a hassle but it works.

---

### Post by Mulenmar on 2008-09-29
> **spongedaddy said:**
> I've used Puppy Linux on ancient PCs in the past successfully. It may be worth a try for you.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

Bad idea, only has root level user. Major security problems possible.

Puppy is best for rescue CDs, from what I understand.

---

### Post by -Zeus- on 2008-09-29
> **Uchiha_madara said:**
> Ubuntu at least need 256 Ram and 512 Mbyte Swap , 20 GB for ubuntu Application's and update ..... so i don't guess it works with him..

if he still need to use ubuntu 
try yo ask about XUbuntu, goUbuntu, and fluxUbuntu.....

Ubuntu needs 20GB??? absurd, the install only needs 4GB and applications might take up another GB, definately NOT 20GB

---

### Post by jf812 on 2008-09-29
I think xububtu is the best.

---

### Post by snowpine on 2008-09-29
> **Mulenmar said:**
> Bad idea, only has root level user. Major security problems possible.

Puppy is best for rescue CDs, from what I understand.

I agree, however, one could argue that many new users do not understand/like the Linux system of having a separate root account. A non-technical user transitioning to Puppy from Windows 95 would not likely be concerned about the potential security tradeoff. :)

---

### Post by liquidfunk on 2008-09-29
Why not a custom Debian with Flux/Black/Open Box.

 If not, I second Crunchbang!

---

### Post by Sycron on 2008-09-30
I recommend too crunchbang.

---

### Post by snowpine on 2008-09-30
I am a big Crunchbang fan too, but if you are seriously thinking about installing it on your 64mb Windows 95 computer, please read my post here: [http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

To summarize, Crunchbang itself is 64mb-friendly, but installing the base Ubuntu system on which it depends is a horrible experience with that tiny amount of ram. (And you certainly would not be able to install using the Crunchbang Live CD; you would have to use the alternate method.)

My advice is do not listen to anyone telling you to use an Ubuntu derivative unless they themselves have actually installed it on a laptop with the same specs. If your friend can get a slightly more modern computer, these are all good suggestions. :)

---

### Post by Sycron on 2008-09-30
Well Distros like puppy, DSL, DeLi Linux will just work. I'm not sure, I never tried but CrunchBang may work too also.

---

### Post by snowpine on 2008-09-30
> **Sycron said:**
> Well Distros like puppy, DSL, DeLi Linux will just work. I'm not sure, I never tried but CrunchBang may work too also.

Yes what I like best about Crunchbang is the applications that are included. I've only installed one or two applications since I started using it--it's like he thought of everything! A very nice distro. My only complaint so far is I don't like editing the menu when I do add an application. :(

---

### Post by Sycron on 2008-09-30
> **snowpine said:**
> Yes what I like best about Crunchbang is the applications that are included. I've only installed one or two applications since I started using it--it's like he thought of everything! A very nice distro. My only complaint so far is I don't like editing the menu when I do add an application. :(

I run programs from terminal, so i don't need the menu. As far as I know you have your icon placed automatically somewhere at System, but i'm not sure.

---

