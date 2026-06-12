---
title: "Radeon Mobility 7500 Display Issues"
date: 2009-11-21
forum: Hardware
---

### Post by balmont on 2009-11-21
I just installed Xubuntu 9.04 and then upgraded to the newest version (9.10, I think).  

Anyways, when I was running Xubuntu off the CD I wasn't having any problems.  
After installing (before the update) I was getting vertical pink lines being displayed on certain menus (some of them seem to flicker/move).  After the update I'm still getting the vertical pink lines, however, now I'm also getting a weird window when I open the system monitor page.

I am suspecting it's the installed driver.  Radeon doesn't support my video card (01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500])

I am searching the forums and will continue to look.  Any help would be appreciated.

p.s. Attachments are screenshots from my computer.

---

### Post by Troken on 2009-11-22
I am having the exact same problem (installed Xubuntu 9.10). I ran compiz-check ([http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)) and got the following result, but as a Linux newbie, I have no clue what to do with that information. Any help would be appreciated!

Distribution: Ubuntu 9.10
Desktop environment: Xfce
Graphics chip: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
Driver in use: radeon
Rendering method: None

Checking if it's possible to run Compiz on your system...  [SKIP]
Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by Troken on 2009-11-22
Hey again, I found a solution.

Seems that there are some problems with some old ATI cards, among them of course the Radeon Mobility 7500 - see the last post of the release notes here:
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

To put it short: in xorg.conf under "Device", add
Option "RenderAccel" "off"
But I advice you to read the release note first.

It worked for me!

---

### Post by louieb on 2009-11-22
> **balmont said:**
> p.s. Attachments are screenshots from my computer.

Its a bug. screen shot looks like you have the system monitor opened up.

Heres where I found my fix maybe it will work for you too
[SOLVED]                          [Notifications and some windows show up black hashed??]("http://ubuntuforums.org/showthread.php?t=1312300&highlight=t30")

> 
The problem seems to be related to this bug [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001") and this one in freedesktop [https://bugs.freedesktop.org/show_bug.cgi?id=23668](https://bugs.freedesktop.org/show_bug.cgi?id=23668).

A potential fix is to edit your xorg.conf as in the Launchpad comment by Grant Bowman. I'm about to try this now.


---

