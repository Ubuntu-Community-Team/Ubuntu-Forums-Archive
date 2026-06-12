---
title: "Aborted, partial upgrade"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2009-03-13
Maybe I'm foolhardy, but everything seemed to be going so well. I was updated, and running smoothly when I realised a lot of ubunteros were on intrepid and well, I was with hardy, so I did the silly thing and okayed the upgrade. It did something and stopped. Then it suggested a partial upgrade. Then after about 6 hours, it aborted and now I get this message:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.


This is now happening everytime I boot, and I keep getting requests for authentication on my internal harddrives which no longer authenticate properly so I am having difficulty accessing two of my partitions from within my Ubuntu installation. What should I do? Any advice for my poor gnome?:(:(:(:(

---

### Post by afrodeity on 2009-03-13
Okay, my faith is restored, I let the update manager update again and it seems to have updated correctely this time. It listed and installed some 1500 different components and then asked me to reboot, which I have done. I now get this:

afrodeity@afrodeity-desktop:~$ cat /etc/issue
Ubuntu 8.10 \n \l

Which could mean I've updated to Intrepid, or my update manager thinks the system is Intrepid. Will do some tests. Right now the machine is downloading Linux headers and source for hardy so not sure what it's thinking. This is a bit like going through birth process, and wish there was more actual support from ubuntu midwives to keep us ubunterized and ubuntified.

---

### Post by afrodeity on 2009-03-13
Okay so I ran a check to see which kernal I am running
afrodeity@afrodeity-desktop:~$ uname -a
Linux afrodeity-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

Which would appear to be my old Hardy kernal as far as I can tell. So this is not a real upgrade, only a partial upgrade which has completed sans kernal. I am now probably going to be upgraded to kernal 2.6.24-23-generic which is a bit different of a numerical improvement. I am still in the dark since online specs for Intrepid 

 · GNOME 2.24.1 With Tabbed File Browser
· Linux kernel 2.6.27
· Guest session/Switch User
· DKMS (Dynamic Kernel Module Support,)
· X.org 7.4
· Network Manager 0.7
· PAM authentication framework
· Totem BBC plugin
· Private (encrypted) Directory
· nVidia &#8220;legacy&#8221; video support
· Create Bootable USB drive at the time of installation

i.e kernal 2.6.27.

The 2.6.24 kernal is a restricted kernal, not sure what this is or why I am upgrading to a restricted kernal, please help.

---

### Post by Mgiacchetti on 2009-03-13
sudo update-manager -d

---

### Post by afrodeity on 2009-03-13
The seriously intelligent updater, interrupted by an electrical storm, failed dsl link or lack of bandwidth, went and did this:

It proposed a partial upgrade, upgraded, installed "Intrepid" and then tried to download kernal 2.6.23-24.

It then suggested I reboot, and also another partial upgrade. 

I was forced to enter my password to run the upgrade. It then came up with this amazing solution:

"This updater does not support upgrade from Intrepid to Hardy."

Seriously topsy turvy. Next, the Updater is going to start cracking one-liners like

"This updater does not support upgrade from Intrepid to Hedgehog". I can just see the look on Mark Shuttleworths face as he upgrades his Jaunty Jackalope to Dapper Drake.

With upgrades like this, I am fast on the track to becoming an Atari running Minix server.

Look, guys, surely this is a bug, and surely it could be solved by an inventory that has some kind of knowledge scheme of what part goes where in the invent that some of the parts arrive before or after, or in the wrong timezone. 

This is relativity, and you could plan around the possibility that a 14 hour flight from Joburg to NY might entail upgrades occurring over time, and servers getting upset along the way. Please suggest a way of getting out of here. BTW I like the intrepid keeness, but its a seriously outdated look, more KDE than the old Gnome.

---

### Post by afrodeity on 2009-03-13
> **Mgiacchetti said:**
> sudo update-manager -d

Updater runs, and says

Not all updates can be installed, Then it gives 4 reasons:

This can be caused by 

* a previous upgrade which didn't complete
* problems with some of the installed software
* unofficial packages not provided by ubuntu
* normal changes of a pre-release version of Ubuntu

ditto #1 and #3

Yes the upgrade didn't complete - what would the solution be?:P

Yes, I have unofficial software, I could remove, but is there a way of determining what the problem is?:o

---

### Post by afrodeity on 2009-03-14
Well, I guess nothing is going to run properly on a Hardy Ibex. Software sources is not running. If I download anything, there is bound to be some conflict since the sofware will not know that its a Hardy Ibex or Intrepid Heron. What to do, is it possible to downgrade? Surely there is a blueprint app that could propose a downgrade and figure out which parts of the system to change?

---

