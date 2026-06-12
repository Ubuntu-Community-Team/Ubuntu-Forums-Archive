---
title: "Total noob, probably in the wrong forum section :)"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by ambidextrousone on 2009-02-03
Hi,

Ive been using ubuntu for 6 months, have not looked back, nor plan on returning to windows - unless windows 7 is absolutely mind blowing, which im sure microsoft will ensure by the final release, is not the case.

within 6 month, ive done some things i never thought myself capable of, although simple to most, installing some of my favourite windows software proved tricky, but as most things here, the community got me through it. thing is, i seek a new challenge, i want to get a little more handy with bash :)

i was wondering if one of you guys could point me into the right direction of how i can duel-boot another flavour of linux, preferably one that will require a lot of time and effort to set up, but hopefully give me a greater insight to whats going on in the backseat of this lovely OS :) any suggestions of where i can go about getting this, please, do respond!

---

### Post by binbash on 2009-02-03
If you are going to install windows7, it destroys the grub.There are some howtos written at this forumm (also you can google it) for how to getting  back the grub and dual boot : 

[http://blog.lokonopa.com/grub-up-windows-7/](http://blog.lokonopa.com/grub-up-windows-7/)

---

### Post by ambidextrousone on 2009-02-03
no no, its not windows 7 i want, i want a difficult to set up version of linux that i can duel boot through grub, purpose being of getting a greater knowledge of linux, because as much as i love it, ubuntu didnt require me to know much about its inner workings, but to be quite honest, i dont know how to use grub, how embarrassing. its a greater knowledge of linux i seek, and i feel a difficult manual set-up would be a good place to start.

---

### Post by pbpersson on 2009-02-03
Grub should be something that just works behind the scenes that you will not need to "learn" - sort of when you used Windows and you relied on the MBR, it is all behind the scenes.

Typically if you install a new version of Linux it will co-exist with the version of Linux you already have on your machine.  I THINK you can have several versions of Linux on one machine although it is required that each version have it's own / partition.

I just read that several versions of Linux will share the same /home and /swap mount points on a machine which I think is awesome.

As for which Linux version is more difficult, I will leave that question for someone else.  I prefer things to be easy so I can be productive with my other tasks.  :)

---

### Post by ambidextrousone on 2009-02-03
thank you pbpersson, i think i want to basically encounter more problems :D so i can repay the community here with a little knowledge of my own! with that in mind, do you or anyone else know of a 'ground up' install version of linux i can setup alongside ubuntu to share my home?

its mainly the terminal i want to gain a greater feel for, but getting comfortable with grub along the way is a bonus.

im sorry im so vague, but thats exactly how i am when it comes to the more technical prospects of this operating system, lol :D

---

### Post by Sorivenul on 2009-02-03
There are many ways to go about this. I would suggesting setting up Arch or Slackware. Both of these distributions do things differently from Ubuntu regarding setup, startup, and package management, but will increase your general understanding quite a bit.

Arch, by default, does not come with a GUI, giving you a clean command-line base to build to suit your personal needs and preferences. Configuration is handled manually. This may seems frightening, but the excellent [Arch Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") should get you started. Arch has "pacman" for package management, which is a different, and arguably better system than Ubuntu/Debian's dpkg/apt. You also have a different init (startup) system. The big plus with Arch is that the Ubuntu forums offer great Arch support as well as many of us have or do use Arch.

Slackware will give you a KDE (KDE 3) desktop by default, and will not hold your hand. You can also opt not to install a desktop by default, leaving you with a command line system. Package management is done, by design, manually, including dependency resolution. This can be remedied with applications like slapt-get and gslapt (think apt-get and Synaptic for Slackware). Packages are also "vanilla" or unmodified by default, leaving the user to configure them. Configuration is done by hand in Slackware, as with Arch, using the configuration files in /etc and other locations as needed.

Either distribution will teach you more than just a new package manager. I probably learned the most from my time spent with Slackware, but Arch is a great "next step" after Ubuntu.

Hope this helps you on your journey! Good luck!

---

### Post by ambidextrousone on 2009-02-03
thank you Sorivenul, that should keep me entertained for a few days :D

ambi out!

---

### Post by boof1988 on 2009-02-03
Are you wanting to install a linux version (using CLI only) and then build it up to what you want?

What are the minimum requirements you want in the initial install?

A couple options (amoung innumerable ones):
[LIST=1]
[*]Install Ubuntu server and build onto it.  This will give good internet functionality from the start as well as some familiarity from the start.
[*]Install the core Debian system and then build on it.  This option will use many of the same CLI commands since Ubuntu is based on Debian.
[*]Try any of the other linux dists.  Fedora, OpenSUSE, ZenWalk, Mint, Fluxbox, SliTaz, Puppy, DSL, CrunchBang.  And play around with trying to get them to work.
[/LIST]

---

### Post by boof1988 on 2009-02-03
> **Sorivenul said:**
> There are many ways to go about this. I would suggesting setting up Arch or Slackware. Both of these distributions do things differently from Ubuntu regarding setup, startup, and package management, but will increase your general understanding quite a bit.

Arch, by default, does not come with a GUI, giving you a clean command-line base to build to suit your personal needs and preferences. Configuration is handled manually. This may seems frightening, but the excellent [Arch Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") should get you started. Arch has "pacman" for package management, which is a different, and arguably better system than Ubuntu/Debian's dpkg/apt. You also have a different init (startup) system. The big plus with Arch is that the Ubuntu forums offer great Arch support as well as many of us have or do use Arch.

Slackware will give you a KDE (KDE 3) desktop by default, and will not hold your hand. You can also opt not to install a desktop by default, leaving you with a command line system. Package management is done, by design, manually, including dependency resolution. This can be remedied with applications like slapt-get and glapt (think apt-get and Synaptic for Slackware). Packages are also "vanilla" or unmodified by default, leaving the user to configure them. Configuration is done by hand in Slackware, as with Arch, using the configuration files in /etc and other locations as needed.

Either distribution will teach you more than just a new package manager. I probably learned the most from my time spent with Slackware, but Arch is a great "next step" after Ubuntu.

Hope this helps you on your journey! Good luck!

Thanks for this info.

---

### Post by Sorivenul on 2009-02-03
> **boof1988 said:**
> [LIST=1][*]Install Ubuntu server and build onto it.
[*]Install the core Debian system and then build on it.
[*]Try any of the other linux dists.
[/LIST]
While these are all great options, which I have suggested in other threads, I don't think they suit the OP. 

Ubuntu Server, is Ubuntu minus GUI with a server-oriented kernel. It doesn't require much manual configuration and running apt-get a few times will not teach the user much about the CLI or Linux. The same goes with Debian, though there is slightly more manual work to do than Ubuntu, depending on your hardware. Other Linux distributions don't do "CLI-only" installs as easily or need as much manual configuration, which the OP wants. 

Just my two cents. 

Cheers!

EDIT:
> **boof1988 said:**
> Thanks for this info.
You're welcome! :D

---

### Post by boof1988 on 2009-02-03
> **Sorivenul said:**
> The same goes with Debian, though there is slightly more manual work to do than Ubuntu, depending on your hardware. Other Linux distributions don't do "CLI-only" installs as easily or need as much manual configuration, which the OP wants.

Just de-select the "standard" and "desktop" options on the Debian install.  And you have a very basic install.

Also choose "manual network configure"

---

### Post by Sorivenul on 2009-02-03
> **boof1988 said:**
> Just de-select the "standard" and "desktop" options on the Debian install.  And you have a very basic install.

Also choose "manual network configure"
Or do a netinstall without being connected to the network. This is my quick way to get a Debian-base, as without the connection it will only install the base system. It saves on download time to only get the netinst ISO. ;)

However, I stand by my original suggestions of Arch or Slackware.

---

### Post by boof1988 on 2009-02-03
> **Sorivenul said:**
> Or do a netinstall without being connected to the network. This is my quick way to get a Debian-base, as without the connection it will only install the base system. It saves on download time to only get the netinst ISO. ;)

However, I stand by my original suggestions of Arch or Slackware.

However, I didn't dispute your suggestions.  Why do you dispute the recommendation of Debian, when you (now) give another way to install a base system with Debian?  Are you trying to argue?

---

### Post by Sorivenul on 2009-02-03
> **boof1988 said:**
> However, I didn't dispute your suggestions.  Why do you dispute the recommendation of Debian, when you (now) give another way to install a base system with Debian?  Are you trying to argue?
I'm not trying to argue. 

I was just providing another way to do the install you suggested, in what is, IMO, an easier (or at least quicker) manner, for others who may be interested. I'm a big proponent of comprehensive education, and since you mentioned the method of deselecting application categories, I thought I would mention another proven method. 

No hard feelings. :D

---

### Post by boof1988 on 2009-02-03
> **Sorivenul said:**
> I'm not trying to argue. 

I was just providing another way to do the install you suggested, in what is, IMO, an easier (or at least quicker) manner, for others who may be interested. I'm a big proponent of comprehensive education, and since you mentioned the method of deselecting application categories, I thought I would mention another proven method. 

No hard feelings. :D

Peace...

---

