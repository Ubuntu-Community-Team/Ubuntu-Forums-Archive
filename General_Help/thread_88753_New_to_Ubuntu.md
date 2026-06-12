---
title: "New to Ubuntu"
date: 2005-11-11
forum: General Help
---

### Post by vishnumrao on 2005-11-11
Hello,

I am new to Ubuntu, and trying to move from Fedora. I am very comfortable with FC4, though it was my first linux experience. Its been very exiting and loved it. But some issues with FC make me want to try out other distros, and thus chose Ubuntu because I like the "earthy" desktop feel of GNOME in Ubuntu screenshots. I have a few questions before I try out Ubuntu.

1. How do I play music in Ubuntu? Does Ubuntu have support for mp3. Been using xmms in FC but mp3 support sucks in FC. How is the support for sound in Ubuntu? Got my card working in FC after a couple of months of fiddling. Dont want to be doing that with Untu.

2. I am aware ubuntu uses apt-get for software installation from repos. Are there any third party repos where I can get  more stuff or are all the stuff already there in the official repos? 

3. I find most third party sotware released (example vmware) are released only as rpms or .tar.gz.  Rpm makes it very easy in FC. Are .deb files released? Not seen too many. 

Looking forward to trying Ubuntu,
vishnumrao.

---

### Post by RAOF on 2005-11-11
Check out the [new user guide]("http://help.ubuntu.com/starterguide/C/").  That should walk you through the initial setup (multimedia, DVD, etc).

There's a lot of stuff in the repos, especially once you've enabled the universe/multiverse repos.  3rd party repos do exist, and you can expect a semi-official Dapper-backports repo with the coolest stuff from Dapper packaged for Breezy sometime.

Some people do release .deb files (the Wine project springs to mind).  You can use alien to convert from .rpm (or other package formats) to .deb files, with variable success.  It will certainly convert, but it may not install in the right place(s), dependencies might have different names, etc (Of course, this actuall applies to just .rpm packages on different distro's.  Notice how, for example, mono has different rpm files for each version of Suse & Fedora ;))

---

### Post by invalid on 2005-11-11
Hi

1) Sound is handled for *most* systems right out of the box. I would recommend searching the forum for your specific card to see if anyone else has had problems with it. As far as players, you have your choice of numerous ones including xmms, beep, kaffeine, amarok, etc. Codecs are readily accessable if you need them, through synaptic.

2) Nearly everything you want is available in the "universe" and "multiuniverse" repos available through ubuntu. If you are unsatisfied with these, you can use numerous others, including Debian and more.

3) If you can only find something as an rpm, you can easily convert it into a debian package, and then install it. Alien is very helpful in doing this. (alien -d package.rpm)

Cheers,
Cb

---

### Post by Buffalo Soldier on 2005-11-11
Another source is the **Unofficial** UbuntuGuide at [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by RAOF on 2005-11-11
[QUOTE=Buffalo Soldier]Another source is the **Unofficial** UbuntuGuide at [http://ubuntuguide.org/](http://ubuntuguide.org/)[/QUOTE]
...which is sadly out of date.  Much of it works, but some of it doesn't, and some of it explains how to do things the wrong way(tm).

---

### Post by gw90se on 2005-11-11
Have you tried a Live CD yet? It might answer some questions, such as the sound card and give you a good feel for the distro.

---

### Post by vishnumrao on 2005-11-11
Yes I have tried the Live cd for the 5.04 Warty. BTW I have a AMD64 machine. Any really bothersome issues with the 5.10 Breezy with AMD 64 machines? 

Please let me know. And thanks for those replies. 

Vishnu Rao.

---

### Post by BoneyOne on 2005-11-11
I haven't seen any issues with AMD64. I'm running it myself (3200+) and have yet to have any serious issues.

Only issue I had is due to my ATI X800XL (PCI-E) not being recognized properly.
An updated driver fixed that issue. Not sure what sort of sound you have, but if your on an AMD64 it's a good chance you have a NForce board (maybe).

Once again, I can verify no issues with sound on my NForce4 board (using onboard sound).

---

