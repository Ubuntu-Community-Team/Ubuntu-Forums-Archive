---
title: "wacom or Xournal bug causes random lines"
date: 2009-06-09
forum: Hardware
---

### Post by X-Kent on 2009-06-09
Hello.
After installing ubuntu 9.04 on my toshiba m750 I get some weird behavior while using xournal. When I write something I suddenly get some random straight line in some direction. Screenshot would explain better, it is attached. (lines are not always in the same direction as it is in screenshot)

I can't figure out is it a bug in wacom driver that reads some buggy input or is it a bug in xournal. Anyway I have no problem in anything but xournal (at least I didn't notice it)

Anyone had anything like this ? Any ideas what may cause it ?
(tried disabling compiz and playing with Xinput/Core events no luck)

This bug is very annoying as it interrupts the writinng and I should undo that line all the time :-(

---

### Post by TabletUbuntu on 2009-06-15
I have the same problem, but no fix yet.  Please see [here]("http://ubuntuforums.org/showthread.php?t=1173170")

---

### Post by X-Kent on 2009-06-15
Thanks. Now I know that I am not alone in this. I will keep watching that thread too for any updates on the issue. This bug really annoys.

I used the guide from here to configure the tablet:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)

Favux saved me a lot of pain and more explanation of how to get m750 tablet working here (look for my and Favux posts):
[http://ubuntuforums.org/showthread.php?p=7294796](http://ubuntuforums.org/showthread.php?p=7294796)
[ ]("http://ubuntuforums.org/showthread.php?p=7388096#post7388096")

---

### Post by Favux on 2009-06-15
Hi X-Kent and TabletUbuntu,

There may be a fix for you.  Try disabling "Use Xinput" on the Options menu.  From this bug report:  [https://bugs.launchpad.net/ubuntu/+source/xournal/+bug/348706](https://bugs.launchpad.net/ubuntu/+source/xournal/+bug/348706)  Worth a shot anyway.

---

### Post by X-Kent on 2009-06-17
I have already tried disabling X input and all combinations with Core Events, no result.
Thanks for a tip anyway.

---

### Post by TabletUbuntu on 2009-07-08
Anyone have a fix for this?  It is *very* annoying to have to continually delete these lines.

Thanks!

---

### Post by Fc1032 on 2009-07-08
Hello again Favux and X-Kent!

I had xournal but never had the problems of random lines...

I did notice that the touch screen does not deactivate as readily as vista did when the pen is used, it is easier to make marks by touch input by accident in ubuntu.

=( sorry that im not real help

---

### Post by Favux on 2009-07-08
Hi Fc1032,

So do you use a launcher with:
```
xsetwacom set touch touch "off"
```
before you start Xournal and another when you leave Xournal?
```
xsetwacom set touch touch "on"
```
Or I guess you could just "wrapp" Xournal with both those commands.

---

### Post by Fc1032 on 2009-07-08
Hello!

I don't use any launcher to disable the touch, because im used to the "disable touch when pen is used" function in vista. It works the same in ubuntu

I just write on it. I've tested for a while to double check if i get the random lines, but i still haven't had the issue.

Edit: After i changed the pen size to "fine" i started to get the random line problem too. It never appeared when i was using the default pen size. After changing back to the default pen size random lines also appear =(

I tried to change the fine pen size as the default pen but that didn't prevent the random line issue. So, so far in order for me to not get that weird line issue is to use the default "medium" pen size

After closing and reopenning xournal, its in the default pen size and the problem does not occur, just like before. So if i do fiddle around with the pen sizes, the random lines start to appear. 

Problem is fixed if i restart xournal and use the default pen size...

---

### Post by Favux on 2009-07-08
Hi Fc1032,

Attaway!  If that works for others it's a breakthrough.

---

### Post by Fc1032 on 2009-07-09
Sure hope that this can help others =)

But even in the "thin" line pen, my line problem did not happen as frequent as it did in X-Kent's screenshot.

I usually get one or two random lines from the thin pen then afterwards it happens less frequently.

X-Kent give the thick/defualt pen a try, it might reduce the number of random lines =)

---

### Post by TabletUbuntu on 2009-07-09
That does not work for me.  I use the default pen size, and mine is set to medium.

Also, I do disable touch before starting Xournal.

---

### Post by X-Kent on 2009-07-14
I rarely change my pen size so I work with default most time and I still get lot of random lines :-(.
I will try disabling touch method and report back if I have anything.

---

### Post by Fc1032 on 2009-07-14
I think the problems is varying between us all...

---

### Post by X-Kent on 2009-07-15
Disabling touch has no effect on m750, even with touch off I still get random lines with default pen size.

---

### Post by Fc1032 on 2009-07-24
=( sorry, im no help... i have no idea where the problem is and how to fix =(

---

### Post by X-Kent on 2009-10-29
Seems to be fixed in karmic koala.

---

### Post by sanette on 2010-09-12
well it's now ubuntu 10.04
and the "spurious lines" bug is still there.

X-Kent : so I'm curious when you say it's solved in karmic.

the guys at linuxwacom say they won't try to fix this until they get a M750, so it's a bit desperate.

I have a "fix" that works *mostly*, but not always.
If anybody is interested, I can post it.
It requires recompiling the wacom_drv driver

**REMARK**: this is a bug in the driver, not in xournal: for instance it happens also in gimp

---

### Post by sanette on 2010-10-25
Here is a patched version of xf86-input-wacom 
compiled for maverick (10.10, 64 bit).

xserver-xorg-input-wacom_0.10.8-0ubuntu1-patch_amd64.deb

I believe it eliminates the bug.

---

### Post by tiger015 on 2011-06-09
This issue is certainly not solved. I have the same bug in natty. Any suggestions on how to solve it? I tried everything commented so far. I am having Thinkpad X210t. Time to log in to Windows :(

---

### Post by gauravm on 2011-06-20
I have the same problem.  The only thing I was able to do was: Uncheck Use XInput under Options in Xournal and the random lines stop happening.  Although now my writing is much more "pixelized"

FYI: On xournal 0.4.5 w/ Natty on Asus t101mt with the Asus Multitouch Screen

---

