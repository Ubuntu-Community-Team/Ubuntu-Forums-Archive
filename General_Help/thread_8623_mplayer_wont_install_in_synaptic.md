---
title: "mplayer wont install in synaptic"
date: 2004-12-19
forum: General Help
---

### Post by neighborlee on 2004-12-19
hi..

  I am trying to install mplayer-586 ( which IS on the repositories I just checked) but getting several dependencies errors as such:
---------
mplayer-586:
  Depends: libartsc0 but 1.2.3-1 is to be installed
  Depends: libfribidi0 but 0.10.4-3 is to be installed
  Depends: libggi2 but 1:2.0.4-3 is to be installed
  Depends: libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libungif4g but 4.1.0b1-6 is to be installed


I checked and those libraries are definitely not on the same repository as mplayer nor on any of my other ones I have so Im left wondering why mplayer is there but thats it ?

thx
--

---

### Post by Ste on 2004-12-19
[QUOTE=neighborlee]hi..

  I am trying to install mplayer-586 ( which IS on the repositories I just checked) but getting several dependencies errors as such:
---------
mplayer-586:
  Depends: libartsc0 but 1.2.3-1 is to be installed
  Depends: libfribidi0 but 0.10.4-3 is to be installed
  Depends: libggi2 but 1:2.0.4-3 is to be installed
  Depends: libpng12-0 but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libungif4g but 4.1.0b1-6 is to be installed


I checked and those libraries are definitely not on the same repository as mplayer nor on any of my other ones I have so Im left wondering why mplayer is there but thats it ?

thx
--[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

At the top of the page is a great howto. 
Dosn't use synaptic but it still installs mplayer which is the important thing.

---

### Post by neighborlee on 2004-12-19
[QUOTE=Ste][http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

At the top of the page is a great howto. 
Dosn't use synaptic but it still installs mplayer which is the important thing.[/QUOTE]
--------
I appreciate the effort but i'm not about to install it from SOURCE...thats lunacy in my books albeit no offense i'm just stating my opinion ..I thought ubuntu was suppose to be about  ease of use not  having to drop-to-terminal just to install a simple media player..at this rate we will NEVER catch up to windows ....I love ubuntu but I"m not about to be forced into compiling because I prefer ease of use mentality ( and yes I am a developer ) ..I'll just use totem thx ...<<<<<

thx for info im just adament about such things...


cheers
---

---

### Post by scuba on 2005-01-02
Try VideoLan (vlc) media player if you don't like to install sources. It fills all my needs and I consider it equal to mplayer, I am really glad it was among the sources since I'm used to it on my windows machine and has brought me joy even though it was on windows ;)

---

### Post by Sensebend on 2005-01-03
I use XINE-UI and VLC, they serve my video needs quite well :D

---

### Post by fng on 2005-01-04
mplayer on the marillat-stable repository is here broken 2.

```
fng@butters:~ $ cat /etc/apt/sources.list | grep marillat
deb ftp://ftp.nerim.net/debian-marillat/ stable main
fng@butters:~ $ sudo apt-get install mplayer-k6
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-k6: Depends: libarts (>= 4:2.2.2-1) but it is not installable or
                       libarts-alsa (>= 4:2.2.2-1) but it is not installable
              Depends: libavcodeccvs (>= 2:20041227-woody0.1) but it is not going to be installed
              Depends: libdvdread2 but it is not installable
              Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
E: Broken packages
fng@butters:~ $
```

---

### Post by macewan on 2005-01-04
I'll second the xine response. grab codecs
[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/)

---

### Post by Domecq on 2005-03-08
I found a simple solution in Synaptics that worked for me.

First of all, it's necessary to have the following repositories added and enabled in Synaptics:
Marillat
-----------
URI:            [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
Distribution:   testing (use unstable here if you are using hoary)
Section(s):     main

and

Crimsun
------------
URI:            [http://sh.nu/~crimsun/](http://sh.nu/~crimsun/)
Distribution:   ./
Section(s):     (leave blank)

Next step...

Just highlight the mlpayer package that you want to be installed (i.e. i386, i588... K6 etc.)

In Synaptics menu, go to "package", then "force version", then, in the new window, choose the version 1.0-pre6a-0.0 (sh.nu)

---

