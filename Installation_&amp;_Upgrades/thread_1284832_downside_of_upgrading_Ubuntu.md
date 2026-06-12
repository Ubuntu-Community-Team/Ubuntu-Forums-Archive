---
title: "downside of upgrading Ubuntu"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by corkscrew on 2009-10-07
I am currently running Jaunty Jackalope. As a convert from windows I am really pleased with the stability of my system.
When Karmic comes out at end of october does that mean that there will be no more updates / security fixes for Jaunty?
I would like to continue running Jaunty whats the downside of doing this?

---

### Post by Elfy on 2009-10-07
Jaunty will reach end of life in October 2010 so you are fine to stay with that for the time being.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by bruno9779 on 2009-10-07
Advantages of upgrading to 9.10:

- Grub2, new look, several little improvements etc...

Disadvantages:

- I did some 10 upgrades as an ubuntu user so far: 80% of the times flawlessly, 20% ... so and so. I have found it easier to reinstall sometimes (especially if you have a separate /home partition).

- I have also had better luck upgrading, after 3-4 weeks from the release. Many bugs get fixed the first weeks of release

---

### Post by earthpigg on 2009-10-07
the downside of upgrading immediately is that you place your system's stability at risk. every new Ubuntu release, there are many people who's install broke when they did an in-place upgrade (instead of clean install)... maybe this figure is 1%, maybe it is 10%... who knows?

ubuntu 9.04 is only 6 months old. many peopl are still using Windows XP, which is pushing a decade old, and are quite happy with it.

if you are completely satisfied with 9.04 and not interested in any of the new features of 9.10, then i'd go ahead and stick with what works. 9.04 will continue to recieve security updates for 18 months after the _4_th month of 200_9_.

if 18 month's isn't long enough to make you happy, you could consider sticking with the Long Term Releases.

8.04 will have 3 years of support from the 4th month of 2008.
10.04, when it comes out, will have 3 years of support from the 4th month of 2010.
12.04... etc. you get the idea :D


the downside, of course, is that 9.04 will mostly only have the latest-and-greatest of programs that where out when 9.04 was released. Firefox 4.0, for example, may not be officially backported to ubuntu 9.04 when it comes out.

---

### Post by corkscrew on 2009-10-07
I do have a seperate home partition, so what will happen to all the applications I already have installed under Jaunty if i do a clean install?

---

### Post by Mighty_Joe on 2009-10-07
> **earthpigg said:**
> the downside of upgrading immediately is that you place your system's stability at risk. every new Ubuntu release, there are many people who's install broke when they did an in-place upgrade (instead of clean install)

This, this, this!
I got burned big time when upgrading to 8.04. My system would lock up within minutes and there was no way to downgrade (it turned out to be a bug in [Xwindows]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227882")).  After a few days of ripping my hair out, I ended up using GParted to create a new partition, install 7.04 there and mount my "upgraded" partition as /home.  
At the very least, run the Live CD for a day or two to make sure the new version works.  Install it to a flash drive and run it from there.  Install 9.10 to a new partition or new hard drive. Back up your data somewhere.  Anything but an upgrade!

---

### Post by earthpigg on 2009-10-07
> **corkscrew said:**
> I do have a seperate home partition, so what will happen to all the applications I already have installed under Jaunty if i do a clean install?

you will need to install the apps again, but once you do they will use your existing settings and whatnot.

---

