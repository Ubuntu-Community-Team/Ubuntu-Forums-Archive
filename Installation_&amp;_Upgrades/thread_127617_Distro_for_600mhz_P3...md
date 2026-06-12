---
title: "Distro for 600mhz P3.."
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2006-02-09
Hey guys..
I recently got a free 600mhz P3 and plan to use it for Folding @ home and hosting files..

My question is. What is a good small distro of Linux I could use for this?
Even the earliest version of Ubuntu is too much for this system..

I was thinking DamSmallLinux, or somehting along those lines.
Maybe a early version of a current distro like Mandrake?
Any opinions would be great.
thanx again..

---

### Post by engla on 2006-02-09
Why do you think Ubuntu is too much?
Ubuntu is fine but a bit slow on a 300MHz for me.

If you don't like ubuntu's speed, try xubuntu (with the xfce desktop), it's quite fast/effective.

Anyway I think you should go for anything based on debian, the package management system is great.

---

### Post by aysiu on 2006-02-09
Use Ubuntu.

Do a server install (when you boot up the installer disk, just type *server*).

Then after you've installed everything, you'll get a black screen with a login.

Log in.

Then, type ```
sudo nano /etc/apt/sources.list
```

Comment out (put a # sign in front of) the line that has a CD-ROM in it.
Uncomment (remove the # sign from the front of) all the lines that look like web addresses.

Then, save (control-x), confirm (y), and exit (Enter).

Finally ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` When it's all done, type ```
startx
```

512 MB of RAM is a lot, but a 600 MHz processor is a bit slow, so that's why I'm suggesting XFCE.

---

### Post by byen on 2006-02-09
Hey floyd27. You never mentioned the amount of ram you have?
But in any case I would suggest using Ubuntu with XFCE,Fluxbox or IceWM. They are pretty decent and do not need as many resources as Gnome or KDE.
If you are looking for other distributions I suggest DamnSmallLinux or Puppy linux. But I strongly suggest using Ubuntu with lighter desktops/window mangers!!!

---

### Post by az on 2006-02-09
Your box must not have a lot of ram if Warty runs slowly on it.

Less than a 400 MHz pentium will start to slow desktop responsiveness to clicks.  More than 600 MHz will not have that much of a diffrerence with a realy modern processor in regards to the desktop.  Opening a document in Openoffice is another deal....

---

### Post by floyd27 on 2006-02-09
This system im looking to get setup only has 128mb ram..
the sys in my sig is my main Kubuntu box..

I tried the 5.10 live cd in it but after 45 min and still loading the desktop, I figiured the systme could not handle it..

I am going to try DSL to see what its like. If I dont like it ill go with a hoary or breezy server install with xubuntu..
thanx for the info guys. It was exactally what I was looking for.
cheers

---

### Post by z_diver on 2006-02-09
I have a P3 600 with Hoary and 512mb RAM -- it runs great.  I've often thought of upgrading but it runs SO WELL that I don't want to change a thing.

---

### Post by orev on 2006-02-09
I have one computer with 600mhz and 128mb ram.  It works fine with either ubuntu or kubuntu.

It is not fast at loading programs...but is pretty good for internet surfing and the basics.

---

### Post by Dragonbite on 2006-02-09
I've been running Ubuntu Live Cd on my P3 500MHz machine (maxxed out with a blazing 256MB of Ram mind you! ;)  ) and it was surprisingly usable (for a live CD).

I've been using Gentoo with KDE for a few years and even that was right around the speed of the Windows 98 it CAME with!  (Except for the file manager, I would use Xfce 99.9% of the time.) 

Once I get everything working on my "new" (used) machine I plan on wiping this one out and installing Ubuntu (or rather, Xubuntu) alone!\\:D/

---

### Post by engla on 2006-02-09
[QUOTE=floyd27]This system im looking to get setup only has 128mb ram..
the sys in my sig is my main Kubuntu box..

I tried the 5.10 live cd in it but after 45 min and still loading the desktop, I figiured the systme could not handle it..

I am going to try DSL to see what its like. If I dont like it ill go with a hoary or breezy server install with xubuntu..
thanx for the info guys. It was exactally what I was looking for.
cheers[/QUOTE]
The Live CD is much worse than the installed version regarding performace.. did you note that the CD says that 128M is the lowest recommendation for the Live CD, and 32M is the corresponding number for the installed version?
The Live CD uses quite a bit of your RAM to get a writable filesystem so linux can boot.

---

### Post by floyd27 on 2006-02-09
Well I went striaght to a server install of ubuntu with Xfce..
I must say its running sweet. 
the only thing I dont like is the file manager..
WOW its horrible.. :)

Can I use natalius or konqueror instaed of whats there?
What are you guys that are using xfce using as a file manager.
You cant be using the stock one.. come on'...

---

### Post by hw-tph on 2006-02-10
You can use Nautilus. Launch it using **nautilus --no-desktop** to prevent it from trying to take over your XFCE/whatever desktop.


Håkan

---

### Post by BobSongs on 2006-02-12
[QUOTE=floyd27]Well I went striaght to a server install of ubuntu with Xfce..
I must say its running sweet. 
the only thing I dont like is the file manager..
WOW its horrible.. :)

Can I use natalius or konqueror instaed of whats there?
What are you guys that are using xfce using as a file manager.
You cant be using the stock one.. come on'...[/QUOTE]
Dunno if "Thunar" would work with your setup. See if it does. [Here's the thread]("http://www.ubuntuforums.org/showthread.php?t=95934")

---

### Post by djmaxmalta on 2008-02-11
hey guys i know i done a topic befe called mayday  on linux, but i got to say that blag 6000 on my p3 500mhz with 320mb ram works good but the problem i have is that my screen is good at 1280 by 1024 wich ubuntu 7.04 tends to bug up on and so dos most linux's    i like the gnome/debian look is like a bit of mac and win, but i wanna know will ubuntu 6.06.01 work as good? and i need to know how to restart x server in general since blag and ubuntu are based from gnome

---

### Post by djmaxmalta on 2008-02-12
> **djmaxmalta said:**
> hey guys i know i done a topic befe called mayday  on linux, but i got to say that blag 6000 on my p3 500mhz with 320mb ram works good but the problem i have is that my screen is good at 1280 by 1024 wich ubuntu 7.04 tends to bug up on and so dos most linux's    i like the gnome/debian look is like a bit of mac and win, but i wanna know will ubuntu 6.06.01 work as good? and i need to know how to restart x server in general since blag and ubuntu are based from gnome

hey guys i need help ubuntu 6.06 works just had a dodgy 10gb hdd that i wanted to install it on, but the problem i really need help in is that xfce,kde,gnome versions of ubuntu dont look good ont he 19" they are to big on a 1024 x768 but i want it on 1280 x 1024 which i was on windows xp on 16bit instead of 32

---

### Post by kerry_s on 2008-02-12
> **djmaxmalta said:**
> hey guys i need help ubuntu 6.06 works just had a dodgy 10gb hdd that i wanted to install it on, but the problem i really need help in is that xfce,kde,gnome versions of ubuntu dont look good ont he 19" they are to big on a 1024 x768 but i want it on 1280 x 1024 which i was on windows xp on 16bit instead of 32

change /etc/X11/xorg.conf to your driver and the mode to 16. then restartx.

info i need for detailed instruction:
your editor
vid card

---

### Post by djmaxmalta on 2008-02-13
> **kerry_s said:**
> change /etc/X11/xorg.conf to your driver and the mode to 16. then restartx.

info i need for detailed instruction:
your editor
vid card

well my grapihcs card is a sis (silicon) v300

and then i have a spare which is sis 6326 agb it used to work wonders on a p2 with 128mb ram but i scraped it, kept hdd, graphics, usb card, sound and moniter.


ps i have been with ubuntu for like 2 years as a normal user i kinda know nothing on how to restart x or anything else that has a command... still a windows user for gaming, and ubuntu for office and linux experiments....

people that can provide a linux cert course in Malta are really expensive u need atleast E100,000 euros and well windows is at 100 euros what a big price difference!


oh and i forgot to say that after i install with live cd i don't get the root priveleges of editing some of the system file (i mean copy and paste some extras) i have a friend who is kinda building his system based on ubuntu and he gave me some themes and all that work in root section of themes and not user.

and an another thing i installed ubuntu on 10gb but i have a slave drive with 40gb how can i make ubuntu work with both and not with 1 hdd?

---

### Post by kerry_s on 2008-02-13
okay, i'm going to assume your running gnome.

press> **alt+f2** <that will call up a launch bar.
in that type> **gksudo gedit /etc/X11/xorg.conf**
type your password
that will open the file for editing.
see pic's 1 & 2
for the mode see pic 3 

logout and press> **ctrl+alt+backspace** <that will restart X

that should take care of your resolution.

---

### Post by djmaxmalta on 2008-02-14
> **kerry_s said:**
> okay, i'm going to assume your running gnome.

press> **alt+f2** <that will call up a launch bar.
in that type> **gksudo gedit /etc/X11/xorg.conf**
type your password
that will open the file for editing.
see pic's 1 & 2
for the mode see pic 3 

logout and press> **ctrl+alt+backspace** <that will restart X

that should take care of your resolution.

thanks but as it seems ubuntu did detect my sis but it was on 24 and not 16 and thanks it worked, you don't mind if i use ur explanation on my website [www.linuxmalta.tk](www.linuxmalta.tk) (its still in beta mode)

---

### Post by kerry_s on 2008-02-14
go for it. :)

---

### Post by djmaxmalta on 2008-03-18
> **kerry_s said:**
> okay, i'm going to assume your running gnome.

press> **alt+f2** <that will call up a launch bar.
in that type> **gksudo gedit /etc/X11/xorg.conf**
type your password
that will open the file for editing.
see pic's 1 & 2
for the mode see pic 3 

logout and press> **ctrl+alt+backspace** <that will restart X

that should take care of your resolution.

i just installed kubuntu on my pc the p3 is it the same command for kde or xfce?

---

### Post by Tomatz on 2008-03-21
MSDOS :lolflag:


But seriously fluxbuntu may run ok :)

---

### Post by djmaxmalta on 2008-05-14
> **kerry_s said:**
> okay, i'm going to assume your running gnome.

press> **alt+f2** <that will call up a launch bar.
in that type> **gksudo gedit /etc/X11/xorg.conf**
type your password
that will open the file for editing.
see pic's 1 & 2
for the mode see pic 3 

logout and press> **ctrl+alt+backspace** <that will restart X

that should take care of your resolution.

hey guys i tried this in Ubuntu 8.04 and it didn't bring me the info as in 7.10 alot of unknowns and one of my network cards didn't wanna work.

so did the code change? or is 8.04 still a beta release and i downloaded it like last week

---

