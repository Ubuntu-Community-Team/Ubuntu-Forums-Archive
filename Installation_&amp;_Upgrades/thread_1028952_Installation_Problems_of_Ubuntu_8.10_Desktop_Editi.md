---
title: "Installation Problems of Ubuntu 8.10 Desktop Edition"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by ps_20080 on 2009-01-02
I have
Microsoft Windows XP
Professional
Version 2002
With Service Pack 2

My Hardware
Intel(R)
Pentium(R) 4 CPU 2.40 GHz 256 MB RAM but Gives at max 253 Ram

I installed Ubuntu Inside Windows
Windows is in C Drive And i installed Ubuntu in D Drive(9 Gb Free Space)

I entered to install 4 Gb Program of Ubuntu.Then it copied and created images and told to take out the disk and reboot automatically.

Then in dual boot i selected UBUNTU and for 2-3 mintues it was loading (The WALLPAPER was just so cool) and finally came up a window showing Checkinh installtion and when it was near 50% lights went off and My UPS had very little so i turned Computer off Directly.

Then when lights came I again selected UBUNTU,Then it checked Installation and Partation,Etc. Then I went to get water for my self and then there was a yellow background and small circle mouse pointer with 1/4 circle Darkened with line.The computer hadn't hung up as i could move mouse , then i left the computer and came after 20 mintues still the same situation.

What should i do now?

---

### Post by abn91c on 2009-01-03
press ctrl+alt+f1, at the prompt type these commands one at a time, the problem it the desktop effect that ubuntu loads by default
 sudo apt-get remove compiz
 sudo apt-get remove compiz-core
 after they are done sudo reboot

---

### Post by ps_20080 on 2009-01-03
When to press in windows XP or Ubuntu?

---

### Post by abn91c on 2009-01-03
> **ps_20080 said:**
> When to press in windows XP or Ubuntu?
ubuntu

---

