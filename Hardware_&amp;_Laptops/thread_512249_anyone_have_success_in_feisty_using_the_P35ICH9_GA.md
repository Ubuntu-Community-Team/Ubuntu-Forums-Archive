---
title: "anyone have success in feisty using the P35/ICH9 GA-P35C-DS3R gigabyte motherboard?"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by kraymore on 2007-07-29
anyone have success in feisty using the GA-P35C-DS3R gigabyte motherboard ? P35/ICH9

thanks

it uses  P35/ICH9

---

### Post by pstate on 2007-07-31
The short answer is yes!  Amazingly, feisty worked straight out of the box including the onboard NIC and audio.  I haven't had time to go over and figure out if the choices are optimal, but so far it seems to be working!

---

### Post by nfm on 2007-08-22
Hi,

I have setup ich9r RAID0 array, when I try to partition the live-installer does not see the array, but the 2 separate hdds. Is this live-installer limitation or I need new kernel?

---

### Post by deuce868 on 2007-10-27
Did you ever get anywhere with this? I'm trying to set it up with raid 5 now, but like you, it shows 4 drives rather than the one raid disk in the installer. I guess I can always do software, but that was part of the appeal of this mobo.

---

### Post by canzi on 2007-11-10
Bump, this is still an issue, anyone got a fix?

---

### Post by deuce868 on 2007-11-10
Found that the issue is related to what's called "fakeraid". It's done in software and there are tricks to try to make it work. Search the wiki for fakeraid. 

I ended up just doing the raid 100% in software at install time.

---

### Post by canzi on 2007-11-11
cheers, think ill do the same

---

