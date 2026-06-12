---
title: "upgrade of sorts?"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by segascream on 2009-06-25
I'm hoping that someome may be able to help me with this, although I'm afraid I know what the answer will be.

I'm currently running Ubuntu Studio 8.10.  Of course, since I just recently got internet access at my house, my computer keeps reminding me that Ubuntu 9.whatever is out now.  I'd love to upgrade, but the thing is, I don't use the features of Studio nearly as much as I thought I would.  I still wind up doing the majority of my audio and video editing in Windows, because it works.

So, while I want to upgrade, I also want to switch to a different flavor of Ubuntu.  Preferably something lighter than Studio is.  I really don't need anything as memory-intensive as Studio, since I basically use Ubuntu for all my light-weight work/fun: reading, writing, music, internet.

So, is it possible to upgrade to 9, and switch to something like Kubuntu?  (And before anyone suggests a liveCD or anything of that nature, I can't boot from USB on this laptop, and my CD-Rom is non-working)

Any help would be great.  Thanks.

---

### Post by abn91c on 2009-06-25
> **segascream said:**
> I'm hoping that someome may be able to help me with this, although I'm afraid I know what the answer will be.

I'm currently running Ubuntu Studio 8.10.  Of course, since I just recently got internet access at my house, my computer keeps reminding me that Ubuntu 9.whatever is out now.  I'd love to upgrade, but the thing is, I don't use the features of Studio nearly as much as I thought I would.  I still wind up doing the majority of my audio and video editing in Windows, because it works.

So, while I want to upgrade, I also want to switch to a different flavor of Ubuntu.  Preferably something lighter than Studio is.  I really don't need anything as memory-intensive as Studio, since I basically use Ubuntu for all my light-weight work/fun: reading, writing, music, internet.

So, is it possible to upgrade to 9, and switch to something like Kubuntu?  (And before anyone suggests a liveCD or anything of that nature, I can't boot from USB on this laptop, and my CD-Rom is non-working)

Any help would be great.  Thanks.
if you have a fast internet connection you can install the kubuntu desktop
**sudo apt-get install kubuntu-desktop**, try it and if you like it then run the distro upgrade. you must log out and select **KDE **under sessions, at the log in screen

---

### Post by segascream on 2009-06-26
Did the apt-get, Kubuntu downloaded onto my system like a dream.  After rebooting, though, I had no wireless internet.  Wicd didn't work, and though I tried, I wasn't able to find a suitable KDE replacement.

Worse is the reason why- somehow, somewhere along the way, trying to find a wireless network manager, my internet stopped working entirely on my laptop.  It's not an ISP issue, as both my Wii and my wife's Asus eeepc are online.  (Wii by wireless, eeepc by wired.)

Figuring I had somehow hosed my system, I started digging around trying to find old liveCDs that I might be able to somehow use to reinstall.

Ironically, I've now gotten my CD drive working again (it was a physical issue- the drive would not open), and have done a fresh reinstall of Ubuntu Studio, but I still have no internet.

Driver for my wireless card is installed, and in fact I have one solid green light on my card right now.  Ethernet cable doesn't seem to do the trick, either, although I'm not sure if I have to somehow enable a wired commection on there or not (I'd always just used wireless, and it always just worked.  That was one thing that made me love Ubuntu.)

Can someone please help?!?!?!

[enable: panic mode]

[/panic mode enabled, frustration level rising]

---

### Post by abn91c on 2009-06-27
1. go to applications.system>hardware drivers and see if your card drivers are listed to "activate"
2. kubuntu network manager widget need to be added, see attached pic.
you may need to remove wicd

---

