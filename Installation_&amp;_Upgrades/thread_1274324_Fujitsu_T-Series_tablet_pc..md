---
title: "Fujitsu T-Series tablet pc."
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by prophetking on 2009-09-24
Hey all. I've come across a Fujitsu T4020D Lifebook tablet PC for cheap.

Anyone installed ubuntu (any flavor) on one before? I'd like to see if it's likely to work before I buy the thing.

---

### Post by Favux on 2009-09-24
Hi prophetking,

Looks like folks have been able to get it working.  Some links:

[http://ubuntuforums.org/showthread.php?t=110050](http://ubuntuforums.org/showthread.php?t=110050)

[http://ubuntuforums.org/showthread.php?t=1075239](http://ubuntuforums.org/showthread.php?t=1075239)

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D)

[http://ubuntuforums.org/showthread.php?t=1136848](http://ubuntuforums.org/showthread.php?t=1136848)

[http://ubuntuforums.org/showthread.php?t=1259154](http://ubuntuforums.org/showthread.php?t=1259154)

Hope this is helpful.

---

### Post by prophetking on 2009-09-25
infinitely so! Thanks, my forum search fu was evidently weak. :)

---

### Post by Favux on 2009-09-25
Hi prophetking,

You're welcome.

Have fun setting it up.  Good luck!

---

### Post by Mark Phelps on 2009-09-26
I have a T4020 and it was working fine in 8.04.  Ever since then, though, Ubuntu has changed how it senses the bezel keys -- and nothing I have done with the newer Ubuntu versions senses those keys anymore.  This includes 8.10 through the latest alpha of Karmic.

The stylus works by default in 9.04 but I had problems getting the rotation scipt to rotate the stylus along with the screen.  never was able to find a way to fix it.

Autorotate (sensing the orientation of the tablet and changing the display from landscape to portait and back) does NOT work.  There are scripts you can write to do the rotation, but without the bezel keys working, you will not be able to do that in Tablet mode.

No version of LM-sensors detects anything useful,so stuff like conky and gkrellm are a waste of time for monitoring CPU temps.

However, what does work includes the display, the stylus (pen), and the wired and wireless internet connections.

---

### Post by Favux on 2009-09-26
Hi Mark,

Regarding fjbtndrv I found a couple of links:

[https://launchpad.net/~khnz/+archive...-archive-extra](https://launchpad.net/~khnz/+archive...-archive-extra)

[http://ubuntuforums.org/showthread.p...54#post7318554](http://ubuntuforums.org/showthread.p...54#post7318554)

Major progress with the bezel buttons.

added these two lines to software sources:
deb [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) jaunty main
then ran this in konsole:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F
sudo apt-get install fjbtndrv
```
reboot

The buttons work. I haven't noticed that all of them actually do anything yet, but the ones I'm most interested in do. The alt button puts the word alt on-screen in green letters, the screen rotate button rotates the screen 90 degrees CCVW every time I press it, the page up/down do, indeed, page up and down and the line up/down moved the page up and down one line at a time. In an openoffice doc, it pages up/down & moves one line up/down, moving the cursor, just like using the page up/down and arrow up/down keys on the keyboard.

From posts 15 and 16 on the last link I gave prophetking.

---

### Post by Mark Phelps on 2009-10-01
Favux:

They must have changed some stuff, then, because the last time I tried those drivers, all they appeared to do was put an object on the desktop that you could then click.

What I am able to do in 8.04 is use keymappings to program specific activities for the bezel keys -- to do essentially the same actions as happens by default in MS Windows.

However, thanks for the links.  I will look them over.

---

### Post by adummy on 2010-10-10
Any recent update on this subject? In particular TH700? Thanks!

---

### Post by Favux on 2010-10-10
Hi adummy,

[https://sourceforge.net/projects/fjbtndrv/](https://sourceforge.net/projects/fjbtndrv/)

[https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa)

---

