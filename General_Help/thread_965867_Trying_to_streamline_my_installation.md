---
title: "Trying to streamline my installation"
date: 2008-10-31
forum: General Help
---

### Post by SteinbergerNate on 2008-10-31
Ok, so I've decided to do a reinstall sometime in the future on my laptop. I don't currently have access to my desktop computer (which runs quite nice) which is usually my primary computer. This laptop is an old Sony Vaio I inherited from my father. To give you an idea of how old it is, it was the first thing in our house that could play dvds. My dad even went out and bought a couple movies to try it out. So, you can imagine that it's sluggish to say the least. As a bonus though, I figured out how to use the graphics accelerator that I didn't even know existed until yesterday.

I may wait to do this until I have access to the desktop as my primary computer since what I'm shooting for is more of a slick web notebook. Not something that can do it all but something to keep me connected and to type up documents on the go. I'm also a musician and use MuseScore to write music scores. This would be nice to have

I'm asking for advice on what to install from a minimal installation to get this as streamlined as possible. The machine is a 800Mhz processor with 256MB of ram and the video chipset has 8MB. I'm currently using a standard install of Ubuntu. 

I've read a bit about FluxBox and OpenBox. They both sound like they would be good candidates for windowmanagers. I have also looked at the OLPC "Sugar" distribution and like the simplicity but need something more flexible which is why I'm shooting for a Debian based distro as there's already a huge library of easily installable software.

So, throw your thoughts out there. I'm in brainstorming mode and will seriously consider any reasonable ideas on starting fresh.

---

### Post by RedSquirrel on 2008-10-31
If you plan to stick with Ubuntu, the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") is very handy.

To give you the general idea:
[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

I don't bother with gdm, gksu, or synaptic.

Example:
```
sudo apt-get update
``````
sudo apt-get install xorg fluxbox
``````
sudo dpkg-reconfigure xserver-xorg
``````
startx
```OR

```
sudo apt-get update
``````
sudo apt-get install xorg openbox menu
``````
sudo dpkg-reconfigure xserver-xorg
``````
startx
```

---

### Post by SteinbergerNate on 2008-11-01
Yeah, the minimal cd is what I had in mind to build on. But as far as window managers go, what would be (in your opinion) the best choice for an older computer to get it running as fast and smooth as possible?

I'm not planning on going with a desktop environment but just sticking with a window manager to keep things slim. I want this thing to boot and shut down quickly as well as be zippy when I'm actually using it.

---

### Post by RedSquirrel on 2008-11-01
> **SteinbergerNate said:**
> Yeah, the minimal cd is what I had in mind to build on. But as far as window managers go, what would be (in your opinion) the best choice for an older computer to get it running as fast and smooth as possible?

I'm not planning on going with a desktop environment but just sticking with a window manager to keep things slim. I want this thing to boot and shut down quickly as well as be zippy when I'm actually using it.

Most window managers are light & fast. It's hard to go wrong. My current favourites are Openbox and dwm, but Fluxbox, IceWM, ratpoison, etc. are also quite nice. They're all going to result in your system being fairly responsive; the only real issue is to find the one you feel most comfortable with.

In fact, you could install a few of them right now on top of your current standard install of Ubuntu and see how that feels. It may not be as light or responsive as it would be if you built up from a minimal install, but it should give you some idea. Once they're installed, you can choose them from the login screen under "Sessions".

Have a look at:
[http://xwinman.org](http://xwinman.org)

for a list of window managers. I would suggest trying a few and seeing which one you like best.

By the way, have you tried the Xfce desktop environment? It might be fairly responsive on your system. I would recommend the **xfce4** package rather than xubuntu-desktop.

```
sudo apt-get install xfce4
```As far as keeping the system light, just be sure to look at the dependencies of anything you plan to install. I like to avoid installing anything that has dependencies connected to a desktop environment, but that's just me. In some cases, installing packages from a desktop environment may not make your system any slower. You sort of have to try it and see. For example, the thunar file manager is quite popular. It pulls in some xfce libraries, but if you want thunar, well that's just the way it is. :)

With regard to installing xorg, if you know the video driver you need, you could put that in front. This will install only the driver you need and not the whole collection of them. 

Example:

```
sudo apt-get install xserver-xorg-video-r128 xorg
```One more thing: Be aware that apt installs the "recommended" packages by default now. You can add '--no-install-recommends' (without the quotes) when you install certain packages to make sure you don't get a pile of extra stuff. Sometimes you want the recommended packages since they are useful or almost "necessary", but it pays to be a bit careful.

---

### Post by SteinbergerNate on 2008-11-01
Ok, I may try some of those on top of my installation. I've messed with xfce a bit but it really didn't seem that much different than Gnome. 

As far as keeping the dependencies down, I used to try to avoid anything linked with KDE. Of course that eliminates K3B which is the greatest cd burning utility out there IMO.

---

### Post by RedSquirrel on 2008-11-01
Since I don't burn very often, I just use the command-line tools directly. I prefer cdrtools (cdrecord), but on Ubuntu, only wodim is provided in the repositories.

---

### Post by SteinbergerNate on 2008-11-01
Ok, I'm stuck. I can't figure out how to work dwm. I can't get any menus to come up or anything. Luckily, I had Firefox opened when I switched from one to the other.

---

### Post by SteinbergerNate on 2008-11-01
Ok, I got out of it. Pressed the power button on the computer and it shut down. Let me get back into something else.

Now, while I know that just a window manager is going to slim things down a bit, what I don't know about them is how they're different from a desktop manager. Doesn't appear that I can have icons anywhere and so I have to do everything through menus. Any other usability differences I might need to know about?

---

### Post by RedSquirrel on 2008-11-02
> **SteinbergerNate said:**
> Ok, I got out of it. Pressed the power button on the computer and it shut down. Let me get back into something else.

You should also be able to get out by pressing Ctrl-Alt-Backspace. The default keyboard shortcut to quit dwm is Alt-Shift-q.



> **SteinbergerNate said:**
> Now, while I know that just a window manager is going to slim things down a bit, what I don't know about them is how they're different from a desktop manager. Doesn't appear that I can have icons anywhere and so I have to do everything through menus. Any other usability differences I might need to know about?

When you run a window manager on its own, you may have to use _separate_ programs to achieve the kind of functionality you are used to in a desktop environment. You can have icons on the desktop, but you have to use a separate program to achieve it. I don't like desktop icons, so I never do this.

You can use menus to access everything. I prefer to setup keyboard shortcuts or run programs from a terminal.

If you're at the stage of getting used to running a window manager on its own, I would suggest you stick with something like Openbox or Fluxbox at first. They are both well-documented. You have to do a bit of reading and experimentation to learn how to make them do what you want.

urukrama has a detailed guide to Openbox that you might find helpful.

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

The docs on the main Openbox site are very good as well.

[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)


For Fluxbox:

[http://fluxbox.org](http://fluxbox.org)
[http://fluxbox-wiki.org](http://fluxbox-wiki.org)


You can read about dwm here:

[http://www.suckless.org/dwm/](http://www.suckless.org/dwm/)

---

### Post by SteinbergerNate on 2008-11-02
Yeah, I seem to like Fluxbox. I'm also giving xfce another chance right now because when I installed it before, I installed it with the xubuntu-desktop package. It seems a bit more slick even with all the rest of the stuff from the normal ubuntu install. 

At the moment, I think I have it narrowed down to Fluxbox and xfce. We'll see what pans out.

---

### Post by urukrama on 2008-11-02
If you want to use Xfce on a computer with modest specs, I strongly recommend using the xfce4 package in the repositories, rather than the xubuntu-desktop package. I've found the former to be much faster and more repsonsive. The xfce4 package only gives you xfce and none of the other applications Xubuntu uses, so you will have a little more work setting everything up, but it is more than worth it.

---

### Post by SteinbergerNate on 2008-11-02
Yup! I found that package and that's how I installed it. Seems to be a bit more snappy than I remember. Of course, the last time I tried it on this computer, I didn't know I had an unused graphics chipset. Oh well. I may be using xfce after all just because of the flexibility. I supposed I could install both on my minimal install and switch back and forth to see which worked better for me.

---

### Post by RedSquirrel on 2008-11-02
Xfce is nice. The configuration is just point & click. :)

It wouldn't be a problem to have both Xfce and Fluxbox installed.

---

### Post by SteinbergerNate on 2008-11-03
Ok, one of the heaviest pieces of software that I use is Evolution. I don't know if there is a replacement out there for it or not that is lighter and, preferably, doesn't use any of the big desktop dependencies. 

What I need is an e-mail client that can connect to an imap server and synchronize with my WM5 phone. It's really quite nice to have all my contacts in my e-mail client AND my pda/phone and I don't know if I can let that go now that I've had it for so long.

I may just have to bite the bullet and keep Evolution unless someone knows of an alternative that's lighter and does all that I need.

---

### Post by SteinbergerNate on 2008-11-05
Well, I did it. I made a clean install from the minimal cd. Boy is xfce snappy without all that baggage!

Still working on finding apps that I want on here.

---

### Post by urukrama on 2008-11-06
Vanilla Xfce4 is very snappy. You can make it even more responsive and fast by disabling everything you don't use. Xfce4 is very modular, and you can easily disable parts of it (such as xfdesktop if you don't use the icons on the desktop). When I use Xfce, I generally also replace xfwin4, the window manager, with Openbox, which is not only lighter, but also more configurable.

---

### Post by SteinbergerNate on 2008-11-06
That's good. I may try lightening it up a bit more...

Right now, I have a problem with the minimal install. I can't get any audio. First, when I tried to play stuff with mplayer, it would say that it couldn't connect to the pulse audio server. So I installed pulse audio. Now it say stuff about not being able to open a jack server or openal.

Do I need jack? I can understand openal but why would I need jack for just regular desktop sound?

---

