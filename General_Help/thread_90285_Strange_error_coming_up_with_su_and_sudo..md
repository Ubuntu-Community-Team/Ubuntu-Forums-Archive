---
title: "Strange error coming up with su and sudo."
date: 2005-11-14
forum: General Help
---

### Post by TeraDyne on 2005-11-14
Ok, I just installed klik to try it out, and after trying to get a few apps for burning to CD, I'm getting this error when trying to do anything with su or sudo:

```
shawn@ubuntu:~$ sudo apt-get update
sudo: timestamp too far in the future: Nov 14 18:14:34 2005
shawn@ubuntu:~$

```

I downloaded the following:
KOffice
Kaffeine
Kate
amaroK

Anyone know what caused this, or how to fix it?

---

### Post by aysiu on 2005-11-14
Maybe your clock is set to the wrong time?

---

### Post by TeraDyne on 2005-11-14
It's the current time in US Central time as far as I know. I can't change it, anyway. If I try ti, it says "su returned with an error." [Edit]Fixed. I rebooted and it set my time to UCT instead of CST, like I originally had it. Now I can use my root pass and everything. Wow, I never thought something I learned in windows (if it's borked, reboot) might come in handy here. Thanks anyway.[/Edit]

[edit] New problem. Now it's stuck on UTC and won't switch to CST, even if I try to edit it from the "Configure Time & Date" dialouge. This is frusturating. Any ideas?[/edit]

---

### Post by shakin on 2005-11-14
[QUOTE=TeraDyne]It's the current time in US Central time as far as I know. I can't change it, anyway. If I try ti, it says "su returned with an error." [Edit]Fixed. I rebooted and it set my time to UCT instead of CST, like I originally had it. Now I can use my root pass and everything. Wow, I never thought something I learned in windows (if it's borked, reboot) might come in handy here. Thanks anyway.[/Edit]

[edit] New problem. Now it's stuck on UTC and won't switch to CST, even if I try to edit it from the "Configure Time & Date" dialouge. This is frusturating. Any ideas?[/edit][/QUOTE]

Try changing your time in the BIOS. You also may be configured to sync time with an Ubuntu NTP server, which would give you UTC. You can setup your timezone to have the KDE clock automatically adjust.

---

### Post by TeraDyne on 2005-11-14
[QUOTE=shakin]Try changing your time in the BIOS. You also may be configured to sync time with an Ubuntu NTP server, which would give you UTC. You can setup your timezone to have the KDE clock automatically adjust.[/QUOTE]

I changed the timezone and nothing happens. Then I tried changing the time in the BIOS, but it went right back to UTC time. It's still showing UTC.

---

### Post by randcoop on 2005-11-14
Try

sudo tzconfig

That should walk you through the process.

---

### Post by sciurus on 2005-11-14
I'm experiencing a similiar problem. I want my BIOS set to local time, and I selected that option during the Kubntu install. In /etc/default/rcS, UTC is set equal to no. However, in KDE's Adjust Date and Time control module, the current time zone says UTC, although below it America/New_York is selected. When I run the command *date +%z* it says +0000, instead of the -0500 it should say for EST. What can I do to change this?

---

### Post by sciurus on 2005-11-14
[QUOTE=randcoop]Try

sudo tzconfig

That should walk you through the process.[/QUOTE]

This says America/New York is selected.

---

### Post by TeraDyne on 2005-11-14
I actually fixed it by upgrading to KDE 3.5-rc1.

As for "sudo tzconfig", it showed up as "America/North Dakota/Center", which is what I was trying to set it, but it never changed to it until I updated KDE.

---

