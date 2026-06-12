---
title: "Odd shutdown problems"
date: 2008-08-13
forum: Hardware
---

### Post by eleifsp on 2008-08-13
After my desktop crashed, burned, and died entirely (more or less), I got a new laptop.  If anyone cares, or it helps at all, it is an HP Special Edition Verve imprint finish, DV2000 series, model number DV2840SE.

It came with Vista, of course.  Actually, it's not THAT bad of an operating system.  I mean, of course it doesn't compare to Linux, but it's not as bad as people make it sound.  My new computer cuts through Vista like a hot knife through butter, even with ALL the bells and whistles enabled, including Aero.  Which, of course, means that it runs Ubuntu Linux 8.04 64-bit edition like nobody's business.

Except for a few issues.  Mainly it has to do with controlling the power.  First, within the last few days when I press the power button, the shutdown and restart options are missing from the menu.  Hibernate and Standby are there, but they act funny.

Standby, which I should also note is supposed to happen when I shut it's lid on battery power, doesn't actually standby.  Instead, it seems to do a hard shutdown (no Ubuntu shutdown bar, anyway), and since I stop giving it instructions, I come back to find it's booted into Vista (because I NEED Windows to do certain things, I set up the Vista boot loader to load Ubuntu).  

Hibernate usually works, but not before acting funny.  Maybe it's just me, but first when I put Ubuntu into hibernate, it takes longer than it did on my desktop (which had 1/8 the RAM this computer has), and I remember there being the shutdown bar when I tried to hibernate it.  This computer only shows a blank screen.  Then maybe, just maybe, it'll turn the power off by itself.  If not, I have to hold the button down.

I'm not an expert in Linux at all, so I'm not sure if there are any diagnostic programs I can run to help you.  If there is, let me know.  All I know is that it's kind of annoying to have to keep opening new terminals and navigating to the folder I need (I've been using the same folder from day to day).

--Eleifsp

---

### Post by eleifsp on 2008-08-19
Bump/Update

I've fixed the actual shutdown issue.  When I installed KDE 4, KDM overwrote my init.d and the rc*.d files so that gdm was in S30gdm, but the kill process for it was still K01gdm.  I switched everything around and forced GDM to be my default manager.

However, I'm still having issues with my standby and hibernate.  If anyone can help...

---

### Post by finito on 2008-08-19
I am not sure what you mean, first of all are you using kubuntu or ubuntu,

to get the shutdown panel just right click on any panel and click add to panel and add Quit.

for standby have you tried clicking on standby, does that work? or are you only trying by closing the lid.

---

### Post by eleifsp on 2008-08-20
I've been using Ubuntu since December, so I know how to shutdown with and without the buttons.  I've actually fixed the problems I'm having with shutting down (mostly, I still get a few bugs) by forcing GDM as my default display manager and changing my rc0.d through rc6.d folders.

With standby (or sleep, whatever you prefer), I have the problem both when I press the button and when I close the lid.  Ubuntu will, instead of sleeping, do a hard restart (it crashes in a way, although most of my configuration is saved, such as what pages I had open in FireFox), and Hibernate is all messed up.

How about this, could someone point me in the direction of an article, preferably in internet resource form, that describes how sleep and hibernate work?  I'll figure it out myself, but I don't know where to start.  I don't see what I'm looking for in my /etc/init.d file.

---

### Post by finito on 2008-08-20
Hibernate:
[http://ubuntuforums.org/showthread.php?p=2875529](http://ubuntuforums.org/showthread.php?p=2875529)

Suspend:
[http://ubuntuforums.org/archive/index.php/t-438299.html](http://ubuntuforums.org/archive/index.php/t-438299.html)

---

