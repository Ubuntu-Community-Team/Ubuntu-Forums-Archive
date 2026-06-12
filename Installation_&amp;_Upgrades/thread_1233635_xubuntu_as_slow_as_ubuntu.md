---
title: "xubuntu as slow as ubuntu?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by Krallus on 2009-08-06
I recently upgraded (i.e. formatted and re-installed) Ubuntu on my seven-year-old 1GHz Pentium III w/ 512 MB of RAM from Feisty Fawn to Jaunty Jackalope.  I spent some time working all the kinks out, but I find that Jaunty's just too slow on my system.  Hoping to stick with a recent and supported distro, I decided to give Xubuntu a whirl by installing the xubuntu-desktop package.

I logged into Xfce and, unfortunately, I found that there was very little (not noticeable) improvement in performance.  Scrolling in most applications like FireFox, Thunderbird, or GnuCash still is choppy.  Rhythmbox skips when switching which application has focus.  Switching focus or launching an app requires a significant degree of patience.

My question is that if I were to re-format the drive and install Xubuntu from its own disk, can I expect a difference?  My impression from anything I've read is that the only difference between installing xubuntu-desktop on top of Ubuntu and using a Xubuntu CD is that the former will have Gnome packages taking up HD space -- not something that will affect performance on my two 80 GB HDs.  So... does a Xubuntu-from-CD install configure things differently?  (e.g. fewer daemons loaded on every boot?)

Thanks for your advice.

---

### Post by TheNosh on 2009-08-06
xubuntu is a poor implementation of Xfce. you could try another distro if you really want good Xfce, or i've heard you can get a bit of a performance boost by installing the Xfce4 package instead of Xubuntu-desktop.

---

### Post by magmon on 2009-08-06
I am currently wrighting to ya from an emachines laptop with 512 megabytes of ram and an 80 gig hd running xubuntu. It runs incredibly fast, and after some customization, is very good looking. It is a fresh install from a disk.

---

### Post by kerry_s on 2009-08-06
try debian it's faster, i'm using xfce4 on 450mhz 256mb ram.
net install:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/)

a straight install is gnome, use the advanced options for the other desktops. you might want to try that lxde desktop, i played with it a couple of days ago & it seemed to be working very good, i just prefer xfce4.

---

### Post by Mighty_Joe on 2009-08-07
Xubuntu is a good choice if the bottleneck on one's system is the display controller or memory.  In your case, I think that P3 CPU is holding you back.  You're not going to get it to go fast unless you drop it from a tall building.;)
Try [Puppy Linux]("http://www.puppylinux.org/").  It's made for slow systems.

---

### Post by Cheesemill on 2009-08-07
Take a look at [#!]("http://crunchbanglinux.org/") (Crunchbang Linux)

---

### Post by Mighty_Joe on 2009-08-07
> **Cheesemill said:**
> Take a look at [#!]("http://crunchbanglinux.org/") (Crunchbang Linux)

I run crunchbang on some virtual machines and I like it a lot, but under the covers, there's a whole lot of Ubuntu. The main difference is the window manager. Our friend has a very slow CPU and needs a distro that addresses that shortfall.

---

### Post by Jose Catre-Vandis on 2009-08-07
You are getting the same performance because you still have all the underlying ubuntu/gnome bloat underneath your xfce/xubuntu interface.

Yes, xubuntu is getting a bit heavy in places, but it is much more streamlined that the full scale ubuntu. Give it a try from its own disk. why not make some space on your HDD so you can run it side by side for comparision.

Alternatively, get the ALT CD, do a command line install, and build up your system from there. This cuts out even more bloat.

I run xubuntu on a variety of PCs from a 333mhz laptop to a 1.4 mhz desktop, no speed or video problems.

---

### Post by snowpine on 2009-08-07
Don't think of xubuntu as "a faster ubuntu" but rather as "ubuntu for users who prefer xfce to gnome."

On slightly different topic, here is some enlightening reading material:
[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

ps there is no speed advantage to re-installing xubuntu from scratch, if you have already installed xubuntu-desktop, it is the exact same thing. (assuming you stay away from ubuntu applications like nautilus, openoffice, etc.)

---

### Post by Jose Catre-Vandis on 2009-08-07
> **snowpine said:**
> Don't think of xubuntu as "a faster ubuntu" but rather as "ubuntu for users who prefer xfce to gnome."

Here is some enlightening reading material:
[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)
[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

ps there is no speed advantage to re-installing xubuntu from scratch, if you have already installed xubuntu-desktop, it is the exact same thing. (assuming you stay away from ubuntu applications like nautilus, openoffice, etc.)

To be fair snowpine, those two articles are comparing xubuntu with Debian xfce, not Xubuntu & Ubuntu. What they do say is that by building up from a command line install can achieve memory savings and more "speed"

---

### Post by snowpine on 2009-08-07
> **Jose Catre-Vandis said:**
> To be fair snowpine, those two articles are comparing xubuntu with Debian xfce, not Xubuntu & Ubuntu. What they do say is that by building up from a command line install can achieve memory savings and more "speed"

Good point; I've edited my previous post. :)

---

### Post by Krallus on 2009-08-10
Thank you for all the advice, everyone.  I did try the LXDE/OpenBox desktops by adding the packages to Ubuntu and loading them from the GDM, but no noticeable improvement in performance.  I've also removed a number of packages that I saw were loading daemons I felt were unnecessary (e.g. all the bluetooth stuff).  I hesitate to move to another distro since I'm not convinced it will solve my problem -- especially if I'm determined to continue to use the apps that I'm used to: Firefox, Thunderbird, Totem Player, Rhythmbox, OpenOffice, GnuCash, etc.  Same goes for installing Xubuntu from scratch.  Frankly, I'm also just plain used to the look and feel of Ubuntu.

I believe I'm stuck with the almost inevitable conclusion that it's time to upgrade.  I think what disturbs me most about this is that my system was more than fine for browsing the web, email, watching video, and word processing a few years ago -- but now I can't *happily* do those simple things with the latest versions of my favourite apps without a hardware upgrade.  I guess that's partly to do with the ever-increasing sophistication of some apps, especially web browsers, but I think it's also that more inefficiencies are built into them due to developer reliance on latest hardware capabilities.  Oh well, that's the way of these things, I guess.

So.. now I get to do research to try to find the best and most compatible latest hardware for building a kick-*** Ubuntu home PC.  Suggestions?  Anyone know some sites that do reviews on such things (a quick Google search didn't find much on h/w reviews related specifically to Ubuntu or Linux)?

Thanks again!

---

### Post by Jose Catre-Vandis on 2009-08-10
You have done well to get this far on your PIII :)

Before you give up, at least give Xubuntu or Debian + xfce a try.

You'll need a fresh install to really see any benefits, as just installing new display/window managers is still making use of all the underlying Ubuntu stuff.

If you really want to play, try installing Arch-Linux, and build up from scratch, much more work, but might generate the result you are looking for.

---

### Post by robert shearer on 2009-08-10
Ulite is an unofficial remix of Ubuntu Hardy LTS and integrates the LXDE desktop very well.
I found it surprisingly fast on My P3/512Mb.
[http://u-lite.org/](http://u-lite.org/)

---

