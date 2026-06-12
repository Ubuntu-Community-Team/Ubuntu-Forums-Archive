---
title: "Where is gstreamer0.8-lame?!"
date: 2005-11-14
forum: General Help
---

### Post by Mosey on 2005-11-14
I'm attempting to get Sound Juicer to encode mp3s in breezy but I can't seem to find the gstreamer0.8-lame plugin in my repositories...is it gone for good?

The backports, when enabled, give me errors.

What should I do?

---

### Post by Remmelas on 2005-11-14
gstreamer0.8-lame is in the repos, not sure which though.
here is my current sources file

## All officially supported packages, including security- and other updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse

## The source pacakges
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
#deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

#source packages from debian-marillat
#deb-src [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

#hoary stuff
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse

#cinelerra
#deb [http://www.kiberpipa.org/~gandalf/ubuntu](http://www.kiberpipa.org/~gandalf/ubuntu) ./ .

#backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

#wine stuff
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
#plf
#deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
#deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

#freenx
deb [http://www.linux.lk/~anuradha/nx/](http://www.linux.lk/~anuradha/nx/) /

---

### Post by Mosey on 2005-11-14
It's still not showing up in my cache search...

and I'm not sure I want to alter my repositories that heavily. I'm not a expert user quite yet. Worried about irreversible damage.

---

### Post by Remmelas on 2005-11-14
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
I understand completely
When i first installed it, i just followed the instructions at the link I included.  Safe, non-destructive :cool:

---

### Post by Mosey on 2005-11-14
The only repositories I havn't enabled are the backports...and when i do enable them I get errors saying they can't be accessed...

---

### Post by Remmelas on 2005-11-14
```
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse main restricted
```
is the source line that will get you the package.  I'm not sure how to help beyond that, make sure that line is in your sources.list, ```
sudo apt-get update
```, then ```
apt-cache search gstreamer0.8 | grep lame
``` and it should be in the results

---

### Post by Mosey on 2005-11-14
THANKYOU!!!!

It worked. For some reason the multiverse wasn't even in my repository list.

THANK!!!!YOU!!!!

---

### Post by Remmelas on 2005-11-14
glad I could help ;-)

---

