---
title: "Sound Card SB X-Fi Extreme Audio finally working in Ubuntu  7.10 Gutsy gibbon"
date: 2008-05-07
forum: Hardware
---

### Post by DocBob on 2008-05-07
For those who may have encountered problems with no sound coming from this card
under ubuntu Gutsy-Gibbon 7.10 (kernel 2.6.22-14-generic), here's the solution
that worked for me (could work with other distros as well, but i can't test them
all)

Download the latest version here:[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

After that, do the following in a terminal:
to make sure all will operate correctly, do the following, before any install

$ sudo apt-get install build-essential

and after that you do that:

$ cd
$$ tar xvzf alsa-driver-1.0.16.tar.bz2
$$ cd alsa-driver-1.0.16
$$ sudo ./configure
$$ make
$$ sudo make install

reboot, and it should work

Another thing, you must deactivate in the volume panel EC958, if it is
activated, and use only analog settings (front/center/side/rear, depending on
your speaker setup, chose only analog front for 2.0 speaker system). You may
have to go into edit-->preferences (into the volume panel) to have the volume
sliders enabled for analog. You may use (although not tested) the digital
settings, if you connect your card to a digital sound system through the digital
output of your soundcard.

That's the way it worked for me. So don't throw your soundcard out the window,
there is a possible solution.=D>:guitar:****

---

