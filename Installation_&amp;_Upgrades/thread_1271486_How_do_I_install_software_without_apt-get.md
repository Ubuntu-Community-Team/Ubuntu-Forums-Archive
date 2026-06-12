---
title: "How do I install software without apt-get?"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by Pawprint on 2009-09-20
I have an Ubuntu 8.10 installation on a machine that has no network connection (and therefore no Internet access) and never will. I need to install a hex editor on that machine since apparently one didn't come with the installation.

Everything I've read says "Use a package manager like apt-get." Well, I know that this requires an Internet connection, so what do I have to do to gather ALL the libraries I need from some other machine and cart them over to this one? Manually seems really difficult, because you needs this, which depends on that, which depends on that, which depends on that, which depends on that, AAGGGHHHH!!!

(You might have guessed that I'm not a power user.)

One really cool thing about Slax is that there's a Web site which can build a package for you. You select the software you want and it will add all the dependent libraries and give you a nice little file to download. Does anything like that exist for Ubuntu?

---

### Post by Partyboi2 on 2009-09-21
You could give [[COLOR=Blue]Keryx[/COLOR]]("http://keryxproject.org/") ago, it allows you to get the packages using a machine that is connected to the Internet, it will also pull in all the dependencies so you don't have to manually do it. 

> One really cool thing about Slax is that there's a Web site which can build a package for you. You select the software you want and it will add all the dependent libraries and give you a nice little file to download. Does anything like that exist for Ubuntu?
Not that I am aware of, but it sounds  interesting, can you provide a link to it?

---

### Post by oboedad55 on 2009-09-21
Take a look at aptoncd here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Bartender on 2009-09-21
Keryx shows potential, but it's still not ready for prime time.  I've been following Keryx for a while.  It was unable to keep track of dependencies when I tried it a year ago.  Took another shot at it a few weeks ago, with help from Keryx Forums.  This was done with two Linux PC's - a laptop running Ub 9.04 which I could take to the library for the connection, and a fresh install of 9.04 on a desktop PC at home.  
Keryx appeared to work the first time, but failed to install scrollkeeper.  I went back to the library a week later and asked Keryx to get all updates for the desktop.  It got a bunch more.  I took the thumb drive home and installed.  At the end of the installation there were now two programs that failed to install, scrollkeeper and something else, and a little red circle with the line thru it appeared in the upper panel.  When i click on that icon it says Synaptic is tied up in knots, can't install any more packages, and needs to reload from repositories.

Linux on the desktop has improved by leaps and bounds in the last few years, but managing an "offline PC" is still a nightmare.  Best solution is to buy a laptop and take it to a broadband connection, even if that takes all day.

---

### Post by snowpine on 2009-09-21
If you have a .deb, you can use dpkg... if you have the source, you can compile it... you can even use apt-get to install from a CD (apt-cdrom). It's not a showstopper. :)

---

### Post by arcull on 2009-09-21
> One really cool thing about Slax is that there's a Web site which can build a package for you. You select the software you want and it will add all the dependent libraries and give you a nice little file to download. Does anything like that exist for Ubuntu? check this for info [http://en.opensuse.org/Build_Service](http://en.opensuse.org/Build_Service) and this is the actual web interface to download files [http://software.opensuse.org/search](http://software.opensuse.org/search)

---

### Post by mac9416 on 2009-09-21
> **Bartender said:**
> Keryx shows potential, but it's still not ready for prime time.  I've been following Keryx for a while.  It was unable to keep track of dependencies when I tried it a year ago...
Linux on the desktop has improved by leaps and bounds in the last few years, but managing an "offline PC" is still a nightmare.  Best solution is to buy a laptop and take it to a broadband connection, even if that takes all day.

I believe the problem with dependency calculation that Bartender is referring to has been fixed.  I suggest that he download the latest version and test it.  If you still encounter problems please contact the development team and let us know.

---

### Post by Pawprint on 2009-09-28
Sorry it took so long to reply. I grabbed Keryx and it did the trick. I did, however, have to alter the source path to get it to pull packages for 8.10 instead of 9.04. I think it could be a little friendlier in letting you go back to older versions, but other than that it worked well.

**Paryboi2**, that site is simply [www.slax.org](www.slax.org).

---

### Post by EXCiD3 on 2009-09-28
Glad to hear Keryx worked for you. Were you using one of the default projects? This would be why you had to change the sources.

---

