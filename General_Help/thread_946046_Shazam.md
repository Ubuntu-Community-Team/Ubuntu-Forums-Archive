---
title: "Shazam"
date: 2008-10-12
forum: General Help
---

### Post by Forbees on 2008-10-12
looking for a program like the iphone's SHAZAM

it detects the artist/album/title of a song it hears with the iphones mic

i'd like to have a program that does that by loading the audio file into it

i tried musicbrain picard, but it failed unless you know anything about the song to help it


i have tons of songs given to me by friends on cd's with no title, album, or artist info

help?

---

### Post by jamesrl on 2008-10-13
I would stay with MusicBrainz as most likely to work.  Quod Libet worked pretty good for me.
For a list of software to try with musicbrainz if picard doesn't do it for you:
[http://musicbrainz.org/doc/MusicBrainzTagger](http://musicbrainz.org/doc/MusicBrainzTagger)
[http://en.wikipedia.org/wiki/Musicbrainz](http://en.wikipedia.org/wiki/Musicbrainz)

---

### Post by Forbees on 2008-10-13
picard couldn't find anything . . . the ones it did find . .  were still labled as track 1 track 2 etc

i tried installing Jaikoz,. but i need a java update, and i can only find .bin to install with . . . . and i have no idea how to use those

---

### Post by jamesrl on 2008-10-13
a .bin is a binary executable, so you can install just going to the directory you downloaded it, and then typing

```
./java-installer.bin
```
(if the binary is named java-installer).  May have to give your self executing permissions, if so just type:
```
 chmod u+x java-installer.bin

``` and then do the previous line.

It is easier to install/uninstall/update java by installing via package manager (packages in multiverse repo):

```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by Forbees on 2008-10-13
it says i'm already the latest version >,<

---

### Post by jamesrl on 2008-10-14
First, check your java version.
```

java -version

```
should see something like:

> java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Server VM (build 10.0-b23, mixed mode)


According to the jaikoz website you need 1.6 or greater, which I presume is what sun-java6 gives you (as opposed to sun-java5 which is 1.5).

On my system, java runs /usr/bin/java (run the command "which java" to find out) which going to /usr/bin and doing "ls -l ja*" tells me it is a symbolic link to /etc/alternatives/java which is itself just a link to /usr/lib/jvm/java-6-sun/jre/bin/java which is installed as part of the multiverse package sun-java6-bin (and i have version 6-07-3ubuntu2 installed).

Maybe you have sun-java6 installed but for some reason the command java isn't going to sun-java6, as you have other java versions also installed?

For me Jaikoz installed without need of a java upgrade (I'm running 8.04 [hardy]).

I just downloaded it to a directory called ~/jaikoz
then
```

unzip jaikoz-linux.sh
sudo sh jaikoz-install.sh

```
and after installing it to /usr/local/Jaikoz it runs by typing in 
```

/usr/local/Jaikoz/jaikoz.sh

```

It seems to do what you want (I'm running an autocorrector as we speak; gone through about 140 songs so far) generating all the acoustic ids.

---

### Post by Forbees on 2008-10-14
well i'm running java 1.5.0 so there is some problem with my updater than  . . . . >,< i'm running hardy as well

---

### Post by starplex on 2010-10-05
There is a really good online music recognition service at midomi.com

---

### Post by ubunkoop on 2012-01-22
[http://www.midomi.com/](http://www.midomi.com/)

uses your mic to identify tunes. connected to soundhound (a shazam alternative:)

---

### Post by sffvba[e0rt on 2012-01-22
Thanks for the input.

*Thread **closed**.*



404

---

