---
title: "Random Full System Crashes"
date: 2008-05-11
forum: Hardware
---

### Post by Wish4Me on 2008-05-11
Ubuntu: Hardy Heron 8:04
Both Gnome/KDE

**Bug**
A crash occurs after usage normally with some graphical input. Highlighting seems to be the cause of some error but I am uncertain of the full extent. (ex. Firefox URL bar, or highlighting of text) I say random but its not really random because if i let the system sit there idle it doesn't crash.

**Background**
It appears to be a bug in a cross platform utility such as compiz or the kernel itself. Both Kubuntu(KDE4)/Ubuntu 8.04 have the crashes for me. Also, the I received a crash on a live CD of Fedora 9. However after some usage I received no crash in Fedora 8 KDE. The older version of some software in the version seems not to have a problem with my computer. Ive become a fan of Ubuntu through the usage that I have been able to use. I would like to help identify the source of this bug but it really has baffled me.

**The Crash**
If the crash occurs with Firefox upfront its a plain white screen with nothing and no way to do anything. With Amarok(The second program that the crash most often occurs with, but these are the two I use the most) there is vertical lines. The command Ctrl+Alt+f1 doesnt work. I have to hold my computers power shutoff switch.

**Hardware**
AMD Athlon 64 Processor 3200+
160 GB ATA Hard Drive
512MB DDR SDRAM Dual Channel
ATI RADEON XPRESS 200 Series

**Notes**
I have been wanting to use Ubuntu as I find it far superior to my Windows XP boot but its quite frustrating to have a crash kill in the middle of anything. Windows XP is very stable for me and my RAM passed a MEM test with no errors. Also, no Hard disk errors appear. It apears to be a very graphical error.

---

### Post by hallgeirl on 2008-05-11
Maybe the crash has something to do with network activity? That might also explain why it doesn't crash while idling. A couple of things you could try:
- Turn off Compiz.
- Try disconnecting from the network (maybe even remove the network driver).

Try out if that makes it..not crash. It's easier to fix erros when you know what they are. :P

---

### Post by Wish4Me on 2008-05-11
How do I turn of compiz?

---

### Post by hallgeirl on 2008-05-11
Go to System->Preferences->Appearance->visual effects->set to None.

---

### Post by Wish4Me on 2008-05-11
Not Networking, Not Compiz. Crashed with KDE4 which doesnt use compiz and when i started in Failsafe Gnome and in normal gnome with it off. Networking I unchecked the Enable Networking at top Right in normal ubuntu. Also, as I was typing everything before this sentence it crashed with seemingly no normal data transfer.

It just crashed as I was typing but as I am typing again it doesnt crash. This is crazy... I have no clue what could be causing these crashes. I just surf around firefox and eventually it crashes. Or when firefox isnt even loaded i just use the computer and it crashes at some point.

---

### Post by hallgeirl on 2008-05-11
It sure sounds like some faulty driver to me. If you have installed some third-party drivers (proprietary or otherwise), have you tried turning them off? For instance graphics drivers.

---

### Post by Yannick Le Saint kyncani on 2008-05-11
> **hallgeirl said:**
> It sure sounds like some faulty driver to me. If you have installed some third-party drivers (proprietary or otherwise), have you tried turning them off? For instance graphics drivers.

+1 for turning off proprietary drivers.

---

### Post by Wish4Me on 2008-05-11
I cant log in without Proprietary ATI driver. Its some bug that may or not be related to this. But it would seem unrelated because others had the login problem but not the crashing problem. I have to use Failsafe GNOME to login at all. Also, It still crashes without it on so i just have it on. Otherwise no proprietary driver is used.

---

