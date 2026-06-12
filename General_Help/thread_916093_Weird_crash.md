---
title: "Weird crash?"
date: 2008-09-10
forum: General Help
---

### Post by ykcirt on 2008-09-10
I just experienced something odd. Maybe this is how Ubuntu crashes, I don't know. Either way I'd like to know what it was.

I was browsing some Wikipedia articles, reading lots of text without actually doing anything for minutes at a time, when I suddenly noticed the scroll/caps/numlock lights on my keyboard were flashing on and off in unison. I had never seen that before, not on Windows anyway. Both my keyboard and mouse didn't respond (incidentally, they're not wireless), so came to the conclusion that either something had locked me out, or Ubuntu had crashed.

I've been using Ubuntu for about a month and overall I'm very happy with it. I've seen some minor issues and programs crash, but nothing like this. I still a little green, so for all I know this happens all the time.

---

### Post by unutbu on 2008-09-10
This used to happen to me when using RedHat and an old rt2500 wireless driver to operate my wireless network adapter. The problem went away when I switched to Ubuntu. I can't say for certain that your problem is the same, but the symptom sounds exactly the same.

Perhaps if you install a different or newer wireless driver you can avoid the problem.

Until then, note that doing hard power offs on your machine is not good if you can avoid it. It is better to use the following key combinations:

```
Alt-Sysrq-h  prints out a HELP message that briefly reminds you of the functions. 
Alt-SysRq-R  turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  send a SIGTERM to all processes, except for init.
Alt-SysRq-I  send a SIGKILL to all processes, except for init.
Alt-SysRq-S  attempt to sync all mounted filesystems.
Alt-SysRq-U  attempt to remount all mounted filesystems read-only.
Alt-SysRq-B  immediately reboot the system without syncing or unmounting
Alt-SysRq-O  poweroff

```
See [http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by ykcirt on 2008-09-10
Duly noted, but the keyboard didn't respond. I doubt that would have worked.

I don't use any wireless devices, but I noticed Ubuntu comes shipped with a lot of Bluetooth related stuff. I thought I had disabled most of that.

Edit: I just remembered some techs have been working on our (wired) network today. It's well in the evening now though, they've been done for six/seven hours. I don't know. Otherwise I can't think of anything out of the ordinary. I used WINE a lot today, but not while I was reading those Wikipedia articles (with Firefox).

2nd Edit: I think I just now realized you brought up wireless because I did so. Let me clarify "*(incidentally, they're not wireless)*". It occurred to me that wireless mice/keyboards might give some kind warning signal when their batteries are low. That's why I thought I should mention they are not wireless. Not because the problem itself could be related to wireless devices or networking. It can.. but that would be some coincidence. ;)

---

