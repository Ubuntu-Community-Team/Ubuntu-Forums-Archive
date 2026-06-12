---
title: "How will Ubuntu work on my old PC?"
date: 2008-08-07
forum: General Help
---

### Post by jras20 on 2008-08-07
I have a 900mhz computer with 96mb of Ram.  I have windows XP on it, I'm thinking of putting Ubuntu on it.
I already installed Ubuntu on my laptop and my Dell.

---

### Post by HermanAB on 2008-08-07
It will run OK if you install Xubuntu, since you don't have much RAM in that one.

---

### Post by cybrsaylr on 2008-08-08
You need more ram.

I'm running XP & Ubuntu 8.04 on a 400Mhz Pent2 PC with 384MB ram and they both run fine.

---

### Post by swisscow on 2008-08-08
More ram would certainly help and xubuntu is still a little heavy. You could do a command line install and then build a "minimal" system on top using open box or such like.

Have a look through

[HTML]https://help.ubuntu.com/community/Installation/LowMemorySystems[/HTML]

---

### Post by LitusMayol on 2008-08-08
Hey man!

I've and old laptop (and HP I think it is...) I know **Ubuntu** was too heavy to get on it, so I tried **Xubuntu**. It was so slowly despite it was running better than the **Win**installed before. 

> **swisscow said:**
> You could do a command line install and then build a "minimal" system on top using open box or such like.


I haven't really understand this sentence, but I think it would help my laptop! :P Can you explain it further...? 

Thanks!
And pardon the newbie!

---

### Post by s3a on 2008-08-08
Try out Debian Xfce, Debian uses less system resources compared to Ubuntu and since Ubuntu is based on Debian, the operating systems are very much alike. So I would think it would be better for you to go for Debian Xfce over Xubuntu. If you would really like to use something in the Ubuntu family, add more RAM, or ask about the fluxbox GUI.

But, the way I see it; Ubuntu is for people who just want to stay up to date all the time and/or have lots of GUIs while Debian focuses more on perfecting everything and therefore is always behind when it comes to having the latest software (assuming you're using the stable version).

But again assuming you want to stay within the Ubuntu family and always be up to date (since you're posting this in ubuntuforums), I guess Xubuntu would do anyway with a large swap file. Xubuntu needs 64 MB minimum to operate (recommended 128 MB RAM) last time I read its requirements. And it would save you the hassle of trying to manually install the Fluxbox GUI.

---

### Post by LitusMayol on 2008-08-08
> **s3a said:**
> Try out Debian Xfce, Debian uses less system resources compared to Ubuntu and since Ubuntu is based on Debian, the operating systems are very much alike. So I would think it would be better for you to go for Debian Xfce over Xubuntu. If you would really like to use something in the Ubuntu family, add more RAM, or ask about the fluxbox GUI.

But, the way I see it; Ubuntu is for people who just want to stay up to date all the time and/or have lots of GUIs while Debian focuses more on perfecting everything and therefore is always behind when it comes to having the latest software (assuming you're using the stable version).

But again assuming you want to stay within the Ubuntu family and always be up to date (since you're posting this in ubuntuforums), I guess Xubuntu would do anyway with a large swap file. Xubuntu needs 64 MB minimum to operate (recommended 128 MB RAM) last time I read its requirements. And it would save you the hassle of trying to manually install the Fluxbox GUI.

Oh my god, man!

One of the best post that I've read ever! Perfect: gives me diferent options and way do you consider one better than other, but getting deeper in the one I've asked for. 
So, first of all: THANKS!

I'll try **Xubuntu** again, this time with a larger swap (I've never used Debian... So the further more I can still using the "*family*", the better). If it stills running slowly, I'll try **Debien Xfce**! ;)

Anyway, I'll say in which way I've solved it! 
So wait to hear more about me.

Thanks, thanks and thanks.

---

### Post by kerry_s on 2008-08-08
> **jras20 said:**
> I have a 900mhz computer with 96mb of Ram.  I have windows XP on it, I'm thinking of putting Ubuntu on it.
I already installed Ubuntu on my laptop and my Dell.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by s3a on 2008-08-08
@kerry_s: Doesn't DSL look very bad? He might be able to pull off better looks and still have reasonable performance ;). Anyway it's up to him.

@LitusMayol: In addition to the link kerry_s provided check out [http://en.wikipedia.org/wiki/Damn_small_linux](http://en.wikipedia.org/wiki/Damn_small_linux) for information as well as a screenshot. I think Damn Small Linux (DSL) is also based on Debian. And I keep mentioning that because going to another kind of distro such as a .rpm distro as opposed to a debian based distro (.deb) might feel different although this could be false since I haven't actually ever left the Debian world.

---

### Post by LitusMayol on 2008-08-08
Thanks both!

So... Which one will performance and improve the better my labtop?

I'll see what I'll do when I arribe home! ;) Thanks anyway, I'll say you something!
(Debian seems to be the Real World! :):lolflag:)

---

### Post by swisscow on 2008-08-08
> **LitusMayol said:**
> Hey man!

I've and old laptop (and HP I think it is...) I know **Ubuntu** was too heavy to get on it, so I tried **Xubuntu**. It was so slowly despite it was running better than the **Win**installed before. 



I haven't really understand this sentence, but I think it would help my laptop! :P Can you explain it further...? 

Thanks!
And pardon the newbie!

What this means is you just install the core part of linux (the essential stuff) then add the bells and whistles on top as you need it. It's like building a house, start with the foundations (you have to have them) then add the bits you want. A full blown Ubuntu installation is like buying a finished house, fully furnished and decorated. It's great everything is there but a lot of stuff you don't want or ever need.

In normal ubuntu, the core is installed then the extras (gnome or kde or xfce) are added on top - these are the heavy bits. Lighter options are available. Add the core (command line install) then add a window manager (similar concept to gnome etc) which doesn't require as much memory (e.g. openbox, fluxbox) and then add the software you actually want.

Have a read of that link - it tells it better than I can

Good luck

---

### Post by LitusMayol on 2008-08-08
> **swisscow said:**
> What this means is you just install the core part of linux (the essential stuff) then add the bells and whistles on top as you need it. It's like building a house, start with the foundations (you have to have them) then add the bits you want. A full blown Ubuntu installation is like buying a finished house, fully furnished and decorated. It's great everything is there but a lot of stuff you don't want or ever need.

In normal ubuntu, the core is installed then the extras (gnome or kde or xfce) are added on top - these are the heavy bits. Lighter options are available. Add the core (command line install) then add a window manager (similar concept to gnome etc) which doesn't require as much memory (e.g. openbox, fluxbox) and then add the software you actually want.

Have a read of that link - it tells it better than I can

Good luck

Another option to my problem! :) Thanks man! 

(where's the link?)

---

### Post by mikjp on 2008-08-08
> **LitusMayol said:**
> Another option to my problem! :) Thanks man! 

(where's the link?)

[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

---

### Post by jocko on 2008-08-08
> **mikjp said:**
> [http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

That link is for the server edition, which is not what you want to run on a "normal" laptop or desktop (it installs a kernel optimized for servers, and probably a lot of server software that a normal user doesn't want/need).
Get the alternate install cd from [ubuntu.com]("http://www.ubuntu.com/getubuntu/download") (check the little box where it says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer").
One of the options in the alternate cd is to install a command-line system (don't remember the exact words in the menu, but it should be obvious).
But do some research before you start, so you know how to install and start a window manager.
And it's a good idea to have an extra computer on the side to be able to search for help.

---

### Post by dai_vernon on 2008-08-08
To give my two cents, I would recommend Fluxbuntu.  Fluxbuntu is essentially ubuntu, with fluxbox as the x window manager; fluxbox, from what I understand, uses significantly fewer resources than even Xfce, and would thus be quite good for a computer with <100 Megs of RAM.

It takes a bit of getting used to but I, still a linux freshman, was able to get the hang of it quite well when using it on a friend's machine.  I do very much like fluxbox.  In addition to being extremely lightweight, it is very very pretty in my opinion; an advantage I think it has over Xfce.

Some reading material:

[http://en.wikipedia.org/wiki/Fluxbox](http://en.wikipedia.org/wiki/Fluxbox)
[http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by Sycron on 2008-08-08
> **jras20 said:**
> I have a 900mhz computer with 96mb of Ram.  I have windows XP on it, I'm thinking of putting Ubuntu on it.
I already installed Ubuntu on my laptop and my Dell.

I have too a 900Mhz computer with ubuntu an 2GB RAM and it works very fine. You may try Zenwalk , Fluxbuntu or #! CrunchBang linux... personaly i'm using CrunchBang linux now... it's Ubuntu with openbox&xfce. :)

---

### Post by snowpine on 2008-08-08
If you want to keep it in the *Buntu family, my suggestions would be:

1. Get more RAM and try Xubuntu. Xubuntu is "like Ubuntu but a bit faster." It is an "official" Ubuntu derivative and has excellent support on these forums. The experience of using Xubuntu is about 90% the same as Ubuntu.
2. Fluxbuntu will be noticably faster than Xubuntu. It is not "official" and it hasn't been updated since last year (it's based on 7.10 instead of 8.04), so it doesn't have much support or an active community like Xubuntu or Ubuntu. It uses lightweight applications instead of the standard firefox/openoffice/etc. Some people find it to be "not user friendly." (I like it.)
3. Crunchbang is a more up-to-date "unofficial" release. I find it has a more useful and beginner-friendly "suite" of applications than Fluxbuntu, plus it has things like Flash support installed from the get-go. The alternative install method ([http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)) is perfect for old computers.
4. Start with a bare-bones minimal install and build it up from there ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)). Recommended only if you enjoy DIY projects! It should be the fastest and lightest of all these options if properly configured (indeed, Fluxbuntu and Crunchbang were basically constructed using this method).

Then of course if you leave the *Buntu family, there are many options, but I'm not an expert (yet). :)

---

### Post by jras20 on 2008-08-08
Thanks for the suggestions!  Its really a "weekend" PC so I don't really care about how fast it is I can only have dialup on it.  I don't think broadband will ever be out there.  :mad:

---

### Post by snowpine on 2008-08-08
> **jras20 said:**
> Thanks for the suggestions!  Its really a "weekend" PC so I don't really care about how fast it is I can only have dialup on it.  I don't think broadband will ever be out there.  :mad:

Dialup limits your options... you should avoid any minimal/alternate/net install that downloads a lot of packages, in favor of something that has a self-contained live CD. Unless you can bring the computer someplace with broadband for the initial installation.

Fluxbuntu will definitely install with 96mb and the install CD is self-contained. I am not sure if Crunchbang will install from the Live CD with only 96mb, but if it does, that would be preferable to the alternate install link I gave you in my last post, since you have dialup.

---

### Post by mikjp on 2008-08-08
Zenwalk and VectorLinux have basically everything one needs on one CD and both are designed to be lightweight. Both of them are based on Slackware. Slackware itself has a bigger selection of packages (including KDE)on three CDs.

Greetings,

mikko

---

### Post by LitusMayol on 2008-08-09
Thank you everyone!


But finally, I've install ***Flux*buntu**. Thanks anyway to everyone! ;)

My computer is working allright! Faster than before! ;)




(does anyone, knows why ***Flux*buntu** is not an official  **Ubuntu** flavour?)

---

### Post by dai_vernon on 2008-08-09
> **LitusMayol said:**
> Thank you everyone!


But finally, I've install ***Flux*buntu**. Thanks anyway to everyone! ;)

My computer is working allright! Faster than before! ;)




(does anyone, knows why ***Flux*buntu** is not an official  **Ubuntu** flavour?)


The short answer is that it just hasn't been adopted by the ubuntu community as an official derivative.  I'd love to see it done, because I think fluxbox is as important as Xfce in terms of getting modern linux to run on minimalist systems.  Fluxbuntu is definitely a labor of love for the small group that works on it, and I'm sure they'd love to see their project gain scope.

I'm glad you like Fluxbuntu; it's definitely a good introduction to fluxbox and is every bit as pretty as a more laden X window system.

---

### Post by mikjp on 2008-08-09
> **LitusMayol said:**
> But finally, I've install ***Flux*buntu**. Thanks anyway to everyone! ;)

My computer is working allright! Faster than before! ;)

Great! Fluxbox is really nice WM when you take your time to configure it. 

Mikko

---

### Post by snowpine on 2008-08-09
> **LitusMayol said:**
> Thank you everyone!


But finally, I've install ***Flux*buntu**. Thanks anyway to everyone! ;)

My computer is working allright! Faster than before! ;)

(does anyone, knows why ***Flux*buntu** is not an official  **Ubuntu** flavour?)

Good choice--I think you will enjoy Fluxbuntu. Let us know if you have any questions/problems, because there is a small but enthusiastic group here that uses it. :)

I agree with you, it would be great if Fluxbuntu (or some other *Boxbuntu) became an official flavor, with full support...

---

### Post by LitusMayol on 2008-08-10
> **snowpine said:**
> Good choice--I think you will enjoy Fluxbuntu. Let us know if you have any questions/problems, because there is a small but enthusiastic group here that uses it. :)

I agree with you, it would be great if Fluxbuntu (or some other *Boxbuntu) became an official flavor, with full support...


So, are there somebody out there that uses ***Flux*buntu**!? 

Perfect, so now I join this little community! If I've any doubt/problem, don't worry: I'll ask it!


Thanks again!

---

