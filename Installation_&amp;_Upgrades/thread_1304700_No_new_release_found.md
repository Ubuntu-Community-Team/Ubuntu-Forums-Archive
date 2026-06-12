---
title: "No new release found"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Tinieblas on 2009-10-29
I excitedly opened the update manager and checked for updates today hoping to upgrade from 9.04 to 9.10, but the update manager just says "your system is up-to-date". I opened the terminal and attempted to do a forced upgrade and this is what I got:

alan@Alan-Laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

Why does my computer not see the upgrade? I looked up and followed the step-by-step upgrade guide in System->About Ubuntu and I still don't see the upgrade... Any help would be greatly appreciated!

---

### Post by hwttdz on 2009-10-29
Try, "sudo apt-get update", "sudo apt-get upgrade", "sudo update-manager -c" and let me know if you see it.

---

### Post by Tinieblas on 2009-10-29
It worked! It's upgrading right now. Thanks so much!

---

### Post by Rocket2DMn on 2009-10-29
Glad to hear, it's possible that your local mirror either was not up to date, or you tried too early :)

---

### Post by ar-grig on 2010-03-06
> **hwttdz said:**
> Try, "sudo apt-get update", "sudo apt-get upgrade", "sudo update-manager -c" and let me know if you see it.

I have done the things and internet connection is ok, but 'no new release found' again ...

---

### Post by vipseixas on 2011-04-28
Old thread still helping people, it worked for me updating from Maverick to Natty.

Thanx!

---

