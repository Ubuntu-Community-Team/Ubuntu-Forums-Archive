---
title: "Weird rendering problem in gmail after 9.04 installation"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by chudak on 2009-05-03
I'm running a T60 with an ATI mobility radeon x1400. I'm running the open source driver.

I've noticed a strange rendering problem in gmail that I never had in 8.04 using the fglrx driver.

Basically, I'm getting strange black artifacts, almost like a badly rendered underline, under the checkbox for each item in the inbox. When I move the mouse cursor over the artifact, it usually disappears but it comes back.

Here's an example:

[IMG]http://lh4.ggpht.com/_KqG6jws_Gd0/Sf26anrIgLI/AAAAAAAABSY/iCcJtg0AV_w/gmail.jpg[/IMG]

I'm also noticing red auras around some text. I used to get this with my old CRT monitor and it was usually caused by divergence in the guns but I'm now running a 24" LCD so this shouldn't be an issue.

---

### Post by OMalley on 2009-05-05
I have exactly the same problem. Turning off visual effect doesn't solve the problem.

---

### Post by apiccirilli on 2009-05-07
Having the exact same problem here - T60, X1400, fresh 9.04 installation.  Any ideas as to the cause?

---

### Post by apiccirilli on 2009-07-11
Has anyone ever determined the solution to this?  Is there any more information we can provide to help out?

EDIT: This seems to be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/366224](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/366224)
which also has no solutions :/.

---

### Post by skywarp04 on 2009-07-13
I've noticed this problem since Jaunty which is when they started using X.org 7.4.  I have a Radeon HD3850.  Besides the black lines/artifacts being annoying my system will also have to be restarted sometimes due to the frame buffer duplicated my onscreen images.  It makes the system unusable and I usually have to switch to tty1 to initiate a restart.  Then it will be fine for about 2 days.  I power my computer off every night too, so it's not just a random problem that happens if you leave you computer on too long.  I've been mad as hell at ATI/AMD lately for their lack of support.  They release driver updates every month, but not much changes between each update. They add some new features here and there, but instead of adding new features maybe they should be making it stable and usable.  I've had this same issue since Catalyst 9.4.  Now tried Catalyst 9.6 and if anything the problem seems worse.  It happens more frequently and now my CPU usage with Xorg sucks.  Using the open source driver everything works fine except I have no 3D support which means no fancy KDE4 effects for me.  I'm half considering purchasing an Nvidia card.  I have been an ATI fan for awhile, but their Linux driver support just plain sucks.

---

