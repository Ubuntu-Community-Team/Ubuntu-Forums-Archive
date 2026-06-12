---
title: "MadCatz R.A.T 7 MMO Gaming Mouse"
date: 2012-12-06
forum: Hardware
---

### Post by Barsoianu Radu on 2012-12-06
Hello,

I've recently bought MadCatz R.A.T 7 MMO Gaming Mouse, seeing that there are allot of sites that offer support for linux for this product. However i was not carefull about the "MMO" thingy in the forums, the device is pretty much new and i couldn't find anywhere on the internet a guide to install the mouse and to make all the buttons work. Here is a link to all the other series xorg.conf hack for R.A.T 3/5/7/9 [http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/) and here is a link to my mouse [http://www.cyborggaming.com/prod/mmo.htm](http://www.cyborggaming.com/prod/mmo.htm). Can someone please help ? i switched to windows meanwhile and i hate it , but i hate even more not beeing able to use my mouse inside my OS. Normal click get's locked or simply donsn't work. I also posted this on OpenSuse forums but somehow i managed to get only a "sell it" reply and "i got a 56k modem who has native linux driver", i really hope to find a more mature responce here. I ussualy use Ubuntu, Mint and/or OpenSuse, however like i sad i am currently back to windows since i don't have a mouse under Linux :).

---

### Post by surfjdh on 2012-12-18
feel your pain, just got a rat7 and been playing with X11/conf.d crap for 5 hours to no avail....

---

### Post by Barsoianu Radu on 2013-01-02
hopefully 2013 will bring more ppl to help me solve this issue. Currently switched back to win and i hate it :(

---

### Post by kuoxiaorong on 2013-02-16
I would assume that it's the mode/profile change button that's causing the problem on the MMO mouse, since that was the issue with the other R.A.T. mice. (See: [http://ubuntuforums.org/showthread.php?t=1528982](http://ubuntuforums.org/showthread.php?t=1528982) and [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892))

I would venture a guess that the xorg.conf tweak ([http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/01/cyborg-rat-7-mouse-under-linux/)) will work if you add a few modifications for the extra buttons that the MMO mouse has. What I would suggest is running xev to find out the numbers assigned to the various mouse buttons (especially the mode/profile change button, which will probably have three numbers). For the ButtonMapping option, replace each of the three numbers you got from xev for the mode switching with 0. After that, you'll want to do xinput -list to find the correct name for your mouse and put that name in the MatchProduct line. I'm not sure what to do with all those extra buttons, but I might try adding the numbers you got for those buttons to the ButtonMapping list of numbers.

Unfortunately, I can't test this out, since I have a R.A.T. 5. You might want to try a less "permanent" tweak first just to make sure you have the button mappings correct by trying the Xmodmap change (from the first two links).

ETA: Ignore the above wall of text! Just found a post that looks like it will work: [http://ubuntuforums.org/showthread.php?p=12395500#post12395500](http://ubuntuforums.org/showthread.php?p=12395500#post12395500)!

---

