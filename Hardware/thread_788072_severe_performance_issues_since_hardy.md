---
title: "severe performance issues since hardy"
date: 2008-05-09
forum: Hardware
---

### Post by mriedel on 2008-05-09
I recently upgraded my Laptop from Gutsy to Hardy. Since then I'm having severe performance problems. When it runs, firefox takes up about 70% cpu. when it doesn't Xgl/compiz are at the top.

The laptop is a compaq nx8220. graphics card is an ATIX600 mobility.

Performance issues:
- compiz effects are all but smooth
- with compiz turned off, moving windows around on the desk is very slow
- accessing the filesystem, writing to the filesystem
- opening/running programs etc
- animations of all kinds
- the more i run the more issues

-> so just general and horrible slowness

did not experience any similar issues with gutsy.

---

### Post by mriedel on 2008-05-11
bump

---

### Post by mriedel on 2008-05-12
bump

---

### Post by argosreality on 2008-05-12
The problem with firefox is probably related to a caching issue [Fix here]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/"). I too have had issues with Compiz speed on my desktop running an X1900GT. Haven't had a chance to test with the latest 8.4 drivers that I snagged through EnvyNG last night

---

### Post by GnuSense on 2008-05-12
Firefox-3 is a beta, I can't believe they chose it as the default for a LTS release.  Many of my favorite extensions don't work and it is simply buggy. The bogs that finally got me to revert to Firefox-2 was that FF3 wouldn't remember my previous session and would always start in Offline Mode. Canonical should have made Firefox-2 the default with an option to install Firefox-3, in my opinion. 

But I've noticed at least 2 other processes in Hardy that have maxed out my CPU to no visible effect that had to be stopped by "sudo kill."  I guess a regular release schedule is a nice thing, but I prefer the Debian you'll-get-it-when-its-ready approach.

---

### Post by mriedel on 2008-05-14
The problem doesn't seem to be directly related to firefox. When i run top (without ff running), the cpu is far from being at 100%. Still my system is extremely laggy.

---

### Post by tewald on 2008-05-15
I was having this performance issues with Hardy and reinstalled Gutsy.
Just to prove that I wasn't paranoid, I downloaded gtkperf and run it with 1000 iterations using clearlooks engine. Result time on Hardy: ~350 seconds ( avg of 5 runs ).
With Gutsy I manage to obtain ~220 seconds in 5 runs.
That proved ( at least on my machine ) that Hardy is indeed slow.
And I installed all correct drivers for my vga card ( NVidia GeForce 6200 ).
Stangely the 3D wasn't affected ( ~1500 fps on glxgears ):confused:
This problem occurs alson with a coworker machine, using a intel 845GL card. Gusty for him was also much faster.
Maybe later I try Hardy again, when some updates are released.

---

### Post by mriedel on 2008-05-17
I get about 190fps with glxgears so together with the compiz issue it sounds like a 3D related problem.

---

### Post by mriedel on 2008-05-21
bump

---

