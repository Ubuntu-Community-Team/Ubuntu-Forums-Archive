---
title: "How do I get rid of Evolution on Gnome?"
date: 2008-08-07
forum: General Help
---

### Post by softtower on 2008-08-07
I am sick and tired of endless updates that come from evolution-related packages: evolution-data-server, evolution-data-server-common, etc.

I don't use Evolution, I've never even seen it. So I tried to get rid of these annoying packages:

```
sudo aptitude remove evolution-data-server evolution-data-server-common
```

But it claims that half of Gnome itself and even (!) Metacity window manager depend on Evolution! 

WTF? Is there a way I can get rid of Evolution-smelling packages?

Here is the output:

```

The following packages have unmet dependencies:
  ekiga: Depends: evolution-data-server but it is not installable
  libedataserverui1.2-8: Depends: evolution-data-server-common (>= 1.12.0) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
alacarte
ekiga
fast-user-switch-applet
gnome-applets
gnome-panel
gnome-panel-data
gnome-session
libedataserverui1.2-8
metacity

Downgrade the following packages:
capplets-data [1:2.22.1-0ubuntu4.1 (hardy-updates, now) -> 1:2.22.1-0ubuntu4 (hardy)]
gnome-control-center [1:2.22.1-0ubuntu4.1 (hardy-updates, now) -> 1:2.22.1-0ubuntu4 (hardy)]
libgnome-window-settings1 [1:2.22.1-0ubuntu4.1 (hardy-updates, now) -> 1:2.22.1-0ubuntu4 (hardy)]

Leave the following dependencies unresolved:
gnome-control-center recommends evolution-data-server
gnome-control-center recommends gnome-session

```

---

### Post by silkstone on 2008-08-07
As far as I know, Evolution and gnome-desktop are intertwined and you cannot get rid of Evolution completely. I did see somewhere that you could remove some of it, but certain packages have to remain.

I think it's something that need fixing, since I guess most people use Thunderbird - and at least you should have the choice without needing to keep Evolution.

---

### Post by softtower on 2008-08-07
Jesus... this is terrible, why on Earth would anything depend on Evolution? Why is it even installed by default?

---

### Post by silkstone on 2008-08-07
It just is, I'm afraid. Smacks a bit of Windows and IE. I seem to remember that the packages you were trying to get rid of were ones that had to remain. Sorry!

---

### Post by rbmorse on 2008-08-07
From a terminal:

sudo apt-get purge evolution

Look at the message BEFORE you enter "Y" and press the <enter> key.  Does that look like what you want?  If not, just press "n"

---

### Post by anselm on 2008-08-07
I wish there was a option to get rid of evolution also.

Maybe something the gnome devs could work on??

---

### Post by mb_webguy on 2008-08-07
Ditto.  I have a few email accounts, but they're all forwarded to my Yahoo account, so I don't use Evolution *or* Thuderbird.  I can uninstall nearly every other program that comes packaged with Ubuntu, and in many cases *have* (e.g. Tomboy and F-Spot to get rid of Mono, Totem in favor of VLC, Transmission in favor of Deluge, and Rhythmbox in favor of Amarok).  I don't see why Evolution should or would be a requirement for the entire distribution...

---

### Post by cariboo on 2008-08-07
See here why evolution is a part of Ubuntu:

[https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution)

Jim

---

### Post by sameerds on 2008-08-07
> **cariboo907 said:**
> See here why evolution is a part of Ubuntu:

[https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution)



Visited that link ... still can't "see" why evolution is built into Ubuntu! 

I tried to remove it too, but some packages are dependencies for the Gnome package. I think this is a packaging problem rather than a software problem. The Gnome Desktop probably doesn't need all of evolution, except maybe a few libraries to parse certain formats. But the gnome packages are built with evolution as a dependency.

---

### Post by sameerds on 2008-08-08
Someone had filed a bug on launchpad which got closed as "Invalid". 

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/240097](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/240097)

I think this is a rather stupid dependency problem, and should indeed be removed. How do we get the right people to hear about this?

---

### Post by webaake on 2008-08-08
Count me in! Just received some useless updates to a useless program suite!

Evolution should really be completely removable, without any hazzle.

---

### Post by DeMus on 2009-02-01
> **webaake said:**
> Evolution should really be completely removable, without any hazzle.

I fully agree with this. Now it looks like Windows and IE, Windows and Mediplayer. I thought Linux was different. What was I thinking?

Where do the Evolution parts get started? Is it easy to remove those links so they don't start at all? Or is that a bad idea and does it bring Gnome down?

---

### Post by TenPlus1 on 2009-02-01
Evolution-Data-Server and Evolution-Data-Server-Common are kinda stuck from removal because the Time/Date on the Gnome-Bar uses them for the drop-down Calendar...

As soon as someone creates a simple time/date panel we can use without the calendar, we might be able to remove Evolution completely...

---

### Post by Yellow Pasque on 2009-02-01
I've seen multiple reports for people wanting to remove all evolution packages. My suggestion is to try filing a bug on Launchpad (of course, search for pre-existing bugs with the same idea), and maybe the package maintainer will change the dependencies to "Recommend" instead of "Depend"

NOW is the time to file this type of "wishlist" bug so it can be fixed in jaunty.

I had a similar issue with gdm depending on alsa-utils and I wanted to remove everything ALSA/Pulse from my system.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/293075](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/293075)

---

### Post by neur0 on 2009-02-01
Couldn't you just lock the version of all Evolution packages (except for libraries) so it wouldn't bother you for updates?
Not a permanent solution, I know, but it should get it out of your way.
I also don't use any email client except the web browser any more, and I believe more and more people are switching to webmail for personal use, so braking the Evolution - Gnome dependency is not a bad idea.
Having it installed by default in Ubuntu is obviously fine.

---

### Post by Le-Dart on 2009-02-01
What exactly is the problem here? OK, Evolution is installed by default with Gnome whether it's Ubuntu, Debian, Fedora etc. 
So what? 
You don't want to use it? Then don't. Yes it's still there. Just ignore it like I do.
Evolution gets updated? OK that's how it should be. Do you want a possible security flaw left unfixed? Do these updates grind your system to halt? Do they take hours to download?
Are you also seriously saying that you use each and every application you have installed and don't have anything installed that you never use?
From the link in an earlier reply, [https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution), "Evolution is probably the best application for working with an Exchange server at this point."
That is probably the primary reason it's there. It allows people to connect to their office, MS based, email servers. 
That is a BIG plus for any Linux based distro. It should be supported not complained about.
Just relax. Either use it, it's good, or ignore it.

---

### Post by directhex on 2009-02-01
EDS is a hard dependency as the apps listed require it in order to gain functionality from it - i.e. if you make Ekiga better by enabling support for reading your Evo contact details, then that's a hard dependency built into the binary, not something optional or plugin-based. If it COULD be spun out, then it'd be only a Recommends: instead of a Depends: and EDS would be removable

---

### Post by webaake on 2009-10-16
All the more reason to uninstall EDS if it introduces security holes!

Or; change DE and get rid of Gnome alltogether! That's what I did.

---

### Post by Sven6210 on 2009-10-20
To be honest, I do not understand that you are so much annoyed by having Evolution on your computer? I am not using evolution and I never used it. And when I realized that uninstalling  of Evolution might bring some problems for Gnome I just decided to hide the icon on my menu.

So I still have Evolution installed but I never used it and I am not seeing it - and therefore I do not care.

[LIST]
[*]The space it takes on the hard disk? I do not mind, it is big enough. And I am talking about a 8 GB SSD...
[*]The updates that come along sometimes? I do not mind, I have a flat rate and the additional kB are fine with me. Even when being in China this is not an issue. And internet can be quite slow in China when downloading from a server outside of China...
[/LIST]

---

### Post by Rmantingh on 2009-10-25
Just leave it on the system and ignore it? You obviously don't understand people with OCD ;-)
If it's not used on my system then I want it gone - sorry.
I've used Xubuntu before which is blissfully free of Evilution.
However XFCE is not ideal either and lacks some functionality that Gnome has.
Still, these silly IE-like 'integrations' may be acceptable to some but not for me.
It's back to Xubuntu for me.
At least we are free to choose the desktop environment we want :-)

---

### Post by javabean420 on 2009-10-31
as of Karmic Koala you still can't get rid of Evolution

i am sorry i thought i fixed it by going to lubuntu.... but that STILL has evolution bindings!!!!!!! but it is still noticably faster for me to do lubuntu

[lubuntu.org]("http://lubuntu.org") ... redirected to ... [lxde.org]("http://lxde.org")

"""helpful post gone bad.... modders i am sorry"""

---

