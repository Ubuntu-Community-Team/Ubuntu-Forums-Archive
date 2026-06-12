---
title: "ACPI not updating lid state?"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by timster on 2005-05-10
First I want to ay that Ubuntu is a great distro! I've been using it on my desktop for a while now. A couple nights ago I bought a laptop (Averatec 3250H1) on an impulse buy since I got a really awesome deal on it. First thing I did was format the drive and install Hoary. Most things I have been able to configure myself, but this one has stumped me a little.

Whenever I close the laptop lid, and re-open it, it doesn't come out of the screensaver mode. I have to press Alt-F7 and move the mouse or press a key to have the screen restored.

There is a line in my /etc/acpi/lid.sh that reads:

grep -q closed /proc/acpi/button/lid/*/state

I think this is the problem. If I do a "cat /proc/acpi/button/lid/LIDD/state" it returns "state: closed" obviously this is not right, since the lid is open now. It looks like the state file isn't being updated when the lid is opened/closed.

Has anyone seen anything like this before? How does the state file get updated? Any ideas where I could look?

Thanks  :)

---

### Post by timster on 2005-05-12
No one knows?

I put Windows XP back on this laptop. It seems to work a whole lot better than Ubuntu did in many areas.

I would love to have Linux running on this laptop, but unfortunatly it doesn't look like there is a whole lot of support for laptops now. 

Oh well. I'll check back in a couple months and see if things have improved.  :)

---

