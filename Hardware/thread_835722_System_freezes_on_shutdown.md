---
title: "System freezes on shutdown"
date: 2008-06-20
forum: Hardware
---

### Post by transkinetic on 2008-06-20
This happens about half the time;
When ever I shut down or reboot my computer, I get a black screen and all the indicator lights stay on. What's worse is that the hdd access light stays on and I can hear my hard drive make a sickening noise when I power of manually by holding the button down for thirty seconds.

Help, what do I do? I'm scared I'm going to blow out my HDD!

---

### Post by xnid on 2008-06-20
Have you tried pressing ctrl-alt-backspace? 

On my computer (a dell XPS M1530 running Ubuntu 8.04) it seems like the Xserver is not shutting down, unless i press ctrl-alt-backspace.

---

### Post by transkinetic on 2008-06-20
ctrl-alt-bcksp causes x to restart on my system and sometimes it hangs but without the hdd being perpetually accessed.

---

### Post by Odrodzona-Sarmacja on 2008-06-21
"gksudo gedit /etc/gamin/gaminrc" (gedit/mousepad/kate)
and make following changes
"
fsset ext2 poll 10
fsset ext3 poll 10
fsset vfat poll 10
fsset ntfs poll 10
"
See if that helps you with that frenzy of hd access somehow.

---

