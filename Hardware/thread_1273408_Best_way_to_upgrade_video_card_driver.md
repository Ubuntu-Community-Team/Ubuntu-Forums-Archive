---
title: "Best way to upgrade video card driver?"
date: 2009-09-23
forum: Hardware
---

### Post by kanehbosm on 2009-09-23
On my dell vostro 1400 laptop I run Ubuntu 9.04, freshly installed.  I like to play the BZFlag game.  It is very "jumpy" on linux.  I suspect I need a better driver for my graphics card.

To get the game to run smoothly in windows I had to go to 'computer manager', identify my video card, then download and install the latest driver for the card from the manufacturer.  The driver came in a .exe file that I double clicked.  Now BZflag is very smooth in windows.

The problem is that I don't know how to upgrade the driver in Ubuntu.  To discover what video card I had I read somewhere to do "~$ lspci" at the terminal.
The result was:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

If I go to system-->administration-->hardware drivers, there is no driver listed.  

I'm a total newbie here.  What is the best way for me to upgrade my laptop to the latest manufacturor's driver in Ubuntu?

---

### Post by beastrace91 on 2009-09-23
For the Intel integrated card the only gfx driver available on Ubuntu is the open source one that is installed by default. The jumpy-ness odds are is simply due to the fact that intel cards aren't that great to begin with.

Sorry,
~Jeff

---

