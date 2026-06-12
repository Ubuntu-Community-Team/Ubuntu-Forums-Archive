---
title: "Toshiba C655D acpi issue 10.10 beta"
date: 2010-09-05
forum: Hardware
---

### Post by DrJohn999 on 2010-09-05
Toshiba C655D-S5041 (AMD V120, 2 GB RAM. ATI Graphics 1366x768 ) fails to boot at all with CD or USB drive using 10.04 desktop, live, UNR, or 10.10 beta with same variants. Crashes after ~ 0.4 - 0.5 s with startup log entries on text-mode screen in all cases. 

Using the 10.10-beta alternate on CD, however, I was able to install onto an attached USB drive (didn't want to hose the Win-7 image on the built-in drive), after setting acpi=off for the CD boot and subsequent  off the USB HDD post-installation.

With acpi=off then wireless and wired lan work, but no screen brightness or volume fn-key combos, no suspend/hibernate/resume functionality (not surprising given the circumstances). Ran out of patience at this point.

Nice inexpensive laptop, but its going back tomorrow 'untouched' for exchange w/something else.

---

### Post by Moorthy on 2010-10-12
As noted [here]("http://kerneltrap.org/mailarchive/git-commits-head/2010/5/20/34989"), install with acpi=off and boot with acpi=copy_dsdt to resolve the problem.

---

### Post by nfrootloop on 2011-04-08
I am having the same issue, and I am very new to linux...How do I even go about making these changes? After installing Ubuntu (with acpi=off) and restarting and attempting to access ubuntu, I dont see where I would have time to apply any change, or patch a kernel, before the above listed problem occurs...:confused:

---

### Post by nfrootloop on 2011-04-08
eureka, i have found it. just in case any other complete and total beginners are having the same issue with the toshiba satellite c655d-s5014, what i did was:

created ubuntu live disc using readily available instructions on ubuntu.org

inserted said disc into drive, restarted computer

press f12 while restarting

select the cd drive

when purple screen came up, hit esc, which brought up a language menu

selected english

hit esc again to arrive at a command prompt

entered:

live-install acpi=off

went through the installation

when restarting and trying to boot ubuntu, i got a bunch of text, so...

when i booted back up and had the option of going into ubuntu or 7, i highlighted ubuntu

hit e

this will bring up another string of text. find where it says splash, and before splash, type acpi=off

there needs to be a space between the word preceding splash
acpi=off splash

and then my friend...then, you hit ctrl+x


sorry if this simplicity bothers anyone. i had no idea what i was doing through any of this. im completely new, and just dont want anyone else to have to suffer for days as i did.
:D

---

