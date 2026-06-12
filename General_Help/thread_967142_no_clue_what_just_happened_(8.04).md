---
title: "no clue what just happened (8.04)"
date: 2008-11-01
forum: General Help
---

### Post by heddleston on 2008-11-01
so for the 2nd time in 2 days, i have gotten some type of black screen of death. both times, multiple applications open, using firefox, when suddenly the whole screen goes kinda shaky for about 5 seconds and then it all goes black and goes non responsive, have to manually turn it off and reboot.

is it an X problem? nvidia? third thing here?

---

### Post by jerrylamos on 2008-11-01
Well, on 8.10 the "black screen of death" is caused by compiz.

Try System Preferences Appearance Visual Effects None

or in terminal type

matacity --replace &

If it seems you are on to something, then try removing compiz with synaptic or else in terminal:
sudo apt-get remove compiz
sudo apt-get remove compiz-core

Jerry

---

### Post by heddleston on 2008-11-02
im not on my machine right now, but ill give that a shot. its weird, though, because i installed 8.04 and have been running compiz & emerald since june, but have never had this happen until the past few days. trying to remember if ive done anything to significant to compiz lately to make it do this.

---

### Post by 3rdalbum on 2008-11-02
If you can get to a text terminal through pressing Control-Alt-F2, and then run the "dmesg" command, you might get an error message that explains something.

From personal experience of problems with Nvidia drivers, I'd recommend disabling them and seeing if the problem persists.

---

### Post by heddleston on 2008-11-03
so i disabled compiz last night, and everything seemed to be working ok. then this morning, my computer wont boot. not even BIOS. what the mess, and furthermore, why is this just now happening? ive been running compiz for a while without any problems.

---

### Post by skydiver|goose on 2008-11-03
try booting off a live CD, then go into your /etc/X11/ dir and change your most recent xorg.conf backup to xorg.conf and delete the current one. that should at least let you get booted back up and be able to see your screen again

---

