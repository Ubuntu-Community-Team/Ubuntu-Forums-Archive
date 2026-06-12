---
title: "Hard time writing CD images on DVDs using K3B"
date: 2008-07-13
forum: General Help
---

### Post by bogdanbiv on 2008-07-13
Writing CD images on DVDs is hard to do (one has to follow a specific workflow):
What works (even if buggy and may produce a broken DVD disk):
Insert blank DVD,
Choose to write an image to it using K3b
Choose image;
Burn;
(Two differnt errors appear here:
one at the begining of writing, that breaks the writing process and the disk,
the other, less harmful, appears at verifying the output written to the disk)

what does not work (for me):
Choose iso image
open it in K3b
from the pop-up selecting the output medium I can only choose CD mediums, even though I have inserted a DVD in the writer drive.

This is quite annoying, as I buy only DVD blanks these days and most Linux distributions I try out issue (mostly) CD images.


I have Kubuntu 8.04, KDE 3.5.9

$ uname -a
Linux bog-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by logos34 on 2008-07-13
You might want to save and post the k3b debug output--it'll give us a better idea what exactly is happening.

As far as the failed verification, if you're using like 8x or 16x dvd_+_r and just burning at the default speed, sometimes turning it down lower (to say 4x) will result in a successful verified burn

---

### Post by bogdanbiv on 2008-07-13
Maybe next time I'll be more carefull to save the log/& error message.

Letting errors aside, how about the other problem? Am I the only one that cannot write a CD image on a DVD because there is no option in the drop down list?

In the attached picture:
I have inserted a blank DVD in the unit, but the drop down list won't let me select it: I have to insert a blank CD-R(W).
So I can't waste my DVDs on what could be written on a CD?

---

### Post by coffeecat on 2008-07-13
Have you tried Brasero? I know you're using Kubuntu and that Brasero is a Gnome app, but it should run OK. It might drag in a lot of Gnome dependencies if you try to install it, but if you don't mind that it's worth looking at. It's got an easy-to-use user interface. I'm beginning to prefer it to k3b.

---

### Post by bogdanbiv on 2008-07-15
I installed Brasero, although it's not a long term solution as it depends on libbeagle1 which is a library of the Mono project and I try to erase all traces of Mono from my computer. 

My issues with Mono come from a licensing paranoia (patents and all the other leagal stuff).

---

