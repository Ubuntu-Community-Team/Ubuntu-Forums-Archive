---
title: "[SOLVED] upgrading by alternate DVD won't work!"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by mhdbnoimi on 2009-07-17
Hi All,

I've downloaded ubuntu 9.04 iso image for upgrading my ubuntu 8.10. But I failed to run upgrading process although I've read [upegrading document](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD) cafully!

[LIST]
[*]I tried to run this command:
[/LIST]
```
gksu "sh /media/cdrom0/cdromupgrade"
```
but nothing happened!

[LIST]
[*]I tried to look for **cdromupgrade** folder in the DVD but I didn't find any folder contains on **upegrade** label !!!
[/LIST]

[LIST]
[*]I tried to download the iso image once again and I faced the same problem.
[/LIST]

[LIST]
[*]I tried to install a fresh copy on the virtual machine (VirtualBox) for checking iso image validity and I didn't find any problem for fresh installation.
[/LIST]

[LIST]
[*]I tried to reboot from 9.04 DVD but it didn't show me any message point to upgrading process!
[/LIST]

[LIST]
[*]I tried to add 9.04 DVD as a third party software source but nothing happened (I don't want to update my software, I want to upgrade whole system).
[/LIST]

[COLOR="Red"]**How I can upgrade ubuntu 8.10 -> 9.04 by using alternate DVD?**[/COLOR]

Note:
I've dialup connection so I can't make network upgrading becuase it could take hundreds of hours.

---

### Post by earthpigg on 2009-07-17
hi,

are you sure it is mounted at /cdrom?

pop the cd in and enter 'mount' in a terminal. you may see something about /media/cdrom or similar.

try replacing /cdrom/cdromupgrade with /media/cdrom/cdromupgrade and/or /media/cdrom0/cdromupgrade, whatever the case may be, if that is indeed the case.


is this from a fresh install of 8.10, or did you go 7.10 -> 8.04 -> 8.10 or something to that affect? if i remember correctly, older versions of ubuntu mounted things at different places by default, and some of that residual configuration may have been left behind.

---

### Post by mhdbnoimi on 2009-07-17
> are you sure it is mounted at /cdrom?
I fixed run command as shown above. any way the screenshot show the path of the DVD-ROM (see it plz)

> is this from a fresh install of 8.10
it's a fresh installation of 8.10

---

### Post by earthpigg on 2009-07-17
you've done the 'run autorun prompt', i assume?

if you run this command, it will search the cd for the file/folder/shell script named 'cdromupgrade':

> ls -R /media/cdrom/ | grep cdromupgrade

i've never used the alternate CD, so im guessing here.... and my internet is going slow atm, so can't download myself to play with :\

any results from the command above?

edit - im off to bed, but ill check back on this thread tomorrow in case you haven't gotten sorted out by then. there may be a super-simple fix to your problem that i wouldn't be aware of since i have never tried using an alternate install cd.... you may want to look into seeing if you can find that.

---

### Post by mhdbnoimi on 2009-07-17
> any results from the command above?
I got nothing! although I tried the following
```
ls -R /media/cdrom/ | grep cdromupgrade 
```
nothing!

```
ls -R /media/cdrom0/ | grep cdromupgrade
```
nothing too!!!!

---

### Post by earthpigg on 2009-07-17
well, that certainly is annoying.

i'm going to download the alternate cd and take a look myself.

it is possible that the wiki is inaccurate or out of date.

---

### Post by earthpigg on 2009-07-17
hi, after downloading the alternate install cd myself and looking around...

...i don't think you downloaded the correct iso!

see my attached screen shot, and compare to your screenshots.

the correct alternate install .iso will have 'alternate' _in the file name_.

[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

edit: made a typo in the text on my screenshot. the alternate cd clearly _does_ have a cdromupgrade script, and does not have the other two things that are clearly visible in your screen shot. :D

---

### Post by mhdbnoimi on 2009-07-19
> ...i don't think you downloaded the correct iso!
oooh my god.... I got it, you're correct. I downloaded ubuntu-9.04-desktop-i386.iso not ubuntu-9.04-alternate-i386.iso this the problem (I think). It seems that desktop iso doesn't contain on cdromupgrade script, for that I couldn't upgrade my ubuntu.

Thanks earthpigg for help, I'll download alternate iso today and if everything go ok. I'll add [solved] prefix to title of this post, thanks again.

---

