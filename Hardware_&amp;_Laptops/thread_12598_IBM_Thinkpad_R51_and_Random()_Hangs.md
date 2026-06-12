---
title: "IBM Thinkpad R51 and Random(?) Hangs"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by lt_kije on 2005-01-25
Hello world-

I've been running Ubuntu 4.10/Warty quite happily on an IBM Thinkpad R51; I purchased the laptop new approximately three months ago. In the last month or so, I've noticed that the laptop will inexplicably hang -- I'm sure there's a reason, but I'm not clear on how to diagnose it or what it might be. Most often, I'll be compressing a file (bzip2) or running apt-get when the screen will lock. I can't CTRL-ALT-BACKSPACE out of X or CTRL-ALT-DEL to reboot; the system appears non-responsive. All I can do is turn the power off and manually reboot.

These crashes have happened with what appears to be increasing frequency, but (IIRC) first started after a kernel upgrade (to 2.6.8.1-4, I think). I've tried booting 2.6.8.1-3, but I still experienced crashes.

I don't think this is Ubuntu's fault (I've tried running Knoppix, but that has crashed as well), but I'd like to verify that before I move on. I've also never owned a laptop before, so I'm not sure how to get support for this issue (either from IBM or someplace else). If it is a hardware problem, who do I call? I'd try to isolate hardware, but I don't have any known-goods on hand. I've tried going through IBM's diagnostic checklist, but it all involved Windows-only utilities (DiskChecker, or some such app).

Lastly, has anyone else experienced these issues on a Thinkpad R51? I went with IBM for the solid construction (and good Linux support, as mentioned on this forum), so I didn't expect to have these issues so soon. Is the R51 line significantly worse than the T line?

Thanks for your help!

lt_kije

---

### Post by hardcandy on 2005-01-26
[http://forums.gentoo.org/viewtopic.php?t=205355](http://forums.gentoo.org/viewtopic.php?t=205355) has a long thread about the laptop. It sounds like a suspend issue, does pressing the Escape key do anything? If not, maybe a video hangup. Gentoo uses the xorg X server so take that into account.

---

### Post by lt_kije on 2005-01-26
Thanks for your quick reply. I read the whole Gentoo thread (which made me want to get my laptop back and running more than ever), but I didn't see anything that seemed to help. I don't think it's a suspend issue, since it crashes even while I'm using the keyboard/trackpad. The Escape key doesn't work, either.

I tried running the Ubuntu installer, but the laptop would hang during various parts of the install process. After about 15 tries (run install->hang->hard reset->repeat) I'm giving up. Unless anyone has any better ideas, I'm going to try and get some hardware type help from IBM. Any recommendations on how to proceed? I'll post with my successes/failures as they occur.

Thanks for your help!

lt_kije

---

### Post by codemarauder on 2006-10-31
I am facing the same problem with IBM Thinkpad R51 2887 MQ6. It hangs randomly and the only option is to boot it manually.

What was the solution for your problem? I am suspecting a faulty RAM module for this.

Please let me know...

-Nishant

---

