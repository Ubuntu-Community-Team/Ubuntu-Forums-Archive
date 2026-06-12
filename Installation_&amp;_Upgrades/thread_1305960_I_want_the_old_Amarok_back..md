---
title: "I want the old Amarok back."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by kjkrum on 2009-10-30
Is there a 9.10 package for the old (ca. 8.04) Amarok, or will I have to build it myself?

The new Amarok is complete garbage. Among its offenses:

- Indiscriminately moving and renaming my files!!! (!!!!!!)
- Refusing to acknowledge that I've told it NOT to scan several subfolders in ~/Music
- Playlist display makes no sense whatsoever

Amarok was KDE's killer app.  It's a shame they had to ruin it...

---

### Post by PorkyPie on 2009-10-30
You'll have to build it yourself. I believe this was discussed in another thread a few ears ago.

---

### Post by kjkrum on 2009-10-30
Ugh.  It utterly destroyed my music collection.  I had thousands of tracks organized in folders by artist and album, and hundreds of unsorted files, including some in folders I told it not to scan.  It moved every single audio file it could find into one folder and created its own organizational system for them, putting many in folders with garbage names like '(Disc'.  FRACK!  Way to piss all over 9.10's nearly flawless user experience.

---

### Post by PorkyPie on 2009-10-30
You can actually installl the old Amarok, without having to build it.

Add this ppa to your Software Sources list

```
ppa:bogdanb/ppa
```Then run this in the terminal:

```
sudo apt-get remove amarok && sudo apt-get install amarok14
```

---

### Post by Lars Noodén on 2009-10-30
You can 'pin' an application to a specific version or repository:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

I would agree that some of the changes seem out of control and perhaps unwarranted.  I'm still recommending 8.04 for enterprise environments, because of so much missing from the newer versions.

---

### Post by kjkrum on 2009-10-30
Thanks for the tips.  Those 1.4 binaries installed without a hitch.

Now to start moving all my files back where they belong...

---

### Post by PorkyPie on 2009-10-30
> **kjkrum said:**
> Thanks for the tips.  Those 1.4 binaries installed without a hitch.

Now to start moving all my files back where they belong...

You're welcome :)

---

### Post by skotos on 2009-10-30
> **PorkyPie said:**
> You'll have to build it yourself.
No, luckily this is unnecessary.
On 9.04 I added these two lines to my /etc/apt/sources.list

deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main

as suggested somewhere in the forums and, after refreshing the packages info, Amarok 1.4 was ready to be installed.
Now, changing jaunty to karmic does not work, but I suggest you to investigate/search the forums.

---

### Post by george1984 on 2009-10-30
I am gratefully running Amarok 1.4 in Karmic using Bogdan's ppa, but as Skotos says above the sources list must be set to "jaunty main" and not "karmic main" as you might think. In fact I only just did this on my other box.

---

### Post by -siGGi- on 2009-11-01
i get the following error message after adding bogdanb ppa:

```
Wähle vormals abgewähltes Paket amarok14.
Entpacke amarok14 (aus .../amarok14_2%3a1.4.10-0ubuntu3~ppa4_i386.deb) ...
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/amarok14_2%3a1.4.10-0ubuntu3~ppa4_i386.deb (--unpack):
 Versuche, »/usr/share/man/man1/amarokcollectionscanner.1.gz« zu überschreiben, welches auch in Paket amarok-utils 2:2.2.0-0ubuntu2 ist
dpkg-deb: Unterprozess paste mit Signal (Broken pipe) getötet
Verarbeite Trigger für man-db ...
Verarbeite Trigger für hicolor-icon-theme ...
Verarbeite Trigger für desktop-file-utils ...
Verarbeite Trigger für hal ...
Regenerating hal fdi cache ...
hal start/running, process 4464
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/amarok14_2%3a1.4.10-0ubuntu3~ppa4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

does anybody know how to solve this?

edit: nvm found out how to solve it, i didnt removed all the packages of amarok 2

---

### Post by dontgetshocked on 2009-11-03
Amen to that brother.Seems like a lot of that is in the new 9.10, you cant edit stuff and so  on.

---

### Post by Niko Johnson on 2009-11-03
> **PorkyPie said:**
> You'll have to build it yourself. I believe this was discussed in another thread a few ears ago. i Like the simplicity of your website... it will make new users happy to make the linux switch.

---

### Post by Doctor-No on 2009-11-06
Do you have icons in Amarok 1.4?  On my system (Kubuntu 9.10 amd64) there are no icons after installing Amarok 1.4 via PPA (and after compiling it by myself, too).  I suppose there is missing an icon pack.  Does anybody know how to solve this?

---

### Post by skotos on 2009-11-06
I know that 2.2 is here. I have tried it once again and now it works on some of my computers, but... hey... we were used at having 1.4 simply running out of the box on gnome too... no check, no audio device configuration/troubleshooting...

It is really a pity that a so great app is facing such a bad luck...

I think that 1.4 is probably the best/most advanced audio player ever developed/deployed.
It should be available by default as an alternate option to 2.2, at least up to when 2.2 will have reached the same affordability and maturity.

---

### Post by skotos on 2009-11-06
> **Doctor-No said:**
> Do you have icons in Amarok 1.4?  On my system (Kubuntu 9.10 amd64) there are no icons after installing Amarok 1.4 via PPA (and after compiling it by myself, too).  I suppose there is missing an icon pack.  Does anybody know how to solve this?

Just completely removed 2.2 and reinstalled 1.4 on Karmic 64 with```
deb [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/bogdanb/amarok14/ubuntu](http://ppa.launchpad.net/bogdanb/amarok14/ubuntu) jaunty main
```and
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AE74AE63
```and I had no issue at all.

Try the re-install option of Synaptic for

[LIST=1]
[*]amarok14
[*]amarok14-common
[*]amarok14-engine-xine
[/LIST]

---

### Post by wkulecz on 2009-11-06
Armarok 2.2 is garbage, even if it worked, (test palys a sound, but none of my mp3s play, although they play fine in totum) the user interface is just plain obnoxious!

Armarok 1.4 is my wife's favorite application on 8.04, if I'd "upgraded" her to this abnomination I'd be in the dog house forever!

Armarok 1.4 needs to be elevated to at least equal status in the main repos, its a disservice to foist this 2.2 crap on the unsuspecting!

--wally.

---

### Post by dontgetshocked on 2009-11-06
> **Doctor-No said:**
> Do you have icons in Amarok 1.4?  On my system (Kubuntu 9.10 amd64) there are no icons after installing Amarok 1.4 via PPA (and after compiling it by myself, too).  I suppose there is missing an icon pack.  Does anybody know how to solve this?

use this link
[http://www.dwasifar.com/?p=849](http://www.dwasifar.com/?p=849)

---

### Post by DrinkTheBlackCoffee on 2009-11-11
I'm glad I found this thread while Amarok was still scanning my collection, I cancelled and no files have been changed. That kind of arrogance is something I can't stand for.

Any tips for Gnome users running KDE apps? I love coding in Kate and Amarok 1.4 is the best but all those extra KDE libraries and updates trouble me...


EDIT : I let out a big howl when I saw that old splash screen :)

---

### Post by seeker5528 on 2009-11-11
> **DrinkTheBlackCoffee said:**
> I'm glad I found this thread while Amarok was still scanning my collection, I cancelled and no files have been changed. That kind of arrogance is something I can't stand for.

Don't believe *everything* you read without having some confirmation.

I have never had any version of Amarok old or new re-organize or rename my music files without telling it to do so somewhere.

There was some discussion about the ~/Music thing, which doesn't necessarilly have to be ~/Music, the location of the Music directory is relative to what is specified in $XDG_DATA_HOME, [Link](http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html),  [Link](http://www.freedesktop.org/wiki/Software/xdg-user-dirs).

Response to the ~/Music situation in the Amarok forum [here](http://forum.kde.org/viewtopic.php?f=116&t=79595&hilit=%7E%2FMusic+xdg&start=20#p129393)

> Not a bug, but a feature. We deliberately decided to scan this directory by default, as it's the Freedesktop default location for music. So it exists on most distros, and many people will use it.

However, if you can't disable the scanning of it, this would count as a bug (and I think we have a report for it).

Don't know what the current status is, I never noticed this behavior, but that may just be because I never use it for anything.

How you feel about the display of the play lists is a pretty subjective thing, the situation is much better than in the earlier 2.x releases, but I think is still a little bit of a work in progress.

Later, Seeker

---

### Post by doug-M on 2009-11-24
> **wkulecz said:**
> Armarok 2.2 is garbage, even if it worked, (test palys a sound, but none of my mp3s play, although they play fine in totum) the user interface is just plain obnoxious!

You might try adding the below package to get 2.2 to work, why it doesn't have this as a required package baffles me. From everything I've seen 2.2 is a huge step backwards from 1.4 though. The thing that made me love Amarok was showing the newest songs added to the collection, was fabulous in 1.4, if it exists in 2.2 I can't find it. 

sudo apt-get install libxine1-ffmpeg

---

### Post by kjkrum on 2010-08-22
Still using and loving Amarok 1.4 on Xubuntu 10.04. :D

I gave 2.2 another chance since I posted this, and couldn't get used to it.  The most important feature of 1.4 that is missing from 2.2 (or at least, I can't figure out how to enable it) and all other music players I've tried is the way 1.4 *filters the current playlist* when you start typing in the search bar.

---

