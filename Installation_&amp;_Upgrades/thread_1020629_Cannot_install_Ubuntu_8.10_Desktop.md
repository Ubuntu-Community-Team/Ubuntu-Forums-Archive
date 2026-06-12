---
title: "Cannot install Ubuntu 8.10 Desktop"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by andygegg on 2008-12-24
(I know, me and a zillion others...).  This is a 1997 era Pentium, 200 MHz, 328MB, 2x4GB SCSI discs, Matrox Millenium graphics board, Iiyama 17" CRT (a sensible m/c when I bought it...).  Bought the official Desktop CD (and I've run the check).  Selecting Install or Live Run do the same thing, Normal or Safe Mode graphics.  Lots of writing appears, down to Starting Ubiquity..., I get a back screen with a little 'x' icon then a splodgey beige wall paper, black screen, more writing, down to Checking battery state [OK] (it's not a laptop).  Then the screen goes black, the monitor makes some clicking noises (which suggests it's trying to set a video mode), then back to the writing - this happens 3 or 4 times then it just sits there.  I've tried again and at the first screen I've deleted 'splash' and 'quiet' options and added 'debian-installer/framebuffer=false'.  It gets to the same point but now I see an input prompt 'ubuntu@ubuntu:~$'  If I type ls it replies Desktop.  Any ideas?
I have previously installed an old (2003) copy of Fedora which came with a book.

---

### Post by logos34 on 2008-12-24
I'd look into DSL or Puppy linux...Or even Xubuntu (use a wm lighter than xfce, like icewm, flux or openbox)

---

### Post by 2hot6ft2 on 2008-12-24
Not enough RAM to run a livecd of ubuntu. Might try xubuntu with the alternate cd for the install or go with those suggested above.

---

### Post by andygegg on 2008-12-28
Thanks, people.  The CD wrapper claims I've enough RAM, maybe someone should tell them it's not enough...  I'm not sure I'll bother anymore - so far Windows 98 knocks Linux into a cocked hat (it installs, it runs, it has a decent screen resolution, it's easy to use...).  Downloading stuff is not an option with my internet connection and I feel I'm throwing good money after bad buying stuff that probably won't even install.  So long, and thanks again.

---

### Post by linux_tech on 2008-12-28
with 384mb RAM you should be able to run xubuntu, but you should set up a swap file.  You should also do the alternate cd install-

PC (Intel x86) alternate install CD-
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.10/release/)
see this also for some tips-
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Info on how to swap file-
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

