---
title: "Display drivers crashing upon install..."
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Midnitewolf on 2009-03-01
"Display Server has been shutdown 6 times in 90 seconds..."

im getting this error repeatedly while trying to install ubuntu (wubi)

At first i had trouble getting past the initramfs issue, but i changed the words "quiet splash' in the menu.lst to "all_generic_ide" and got past this problem, as well as a few more.

I finally managed to reach the next step, and ubuntu started to install completely. When it reached about 90% it went to a black screen where it was all gibberish, mentioned something about starting gnome drivers, and thats where im stuck.

The screen will flash alot and return to this screen, and after about a minute or two, it says "Display Server has been shutdown 6 times in 90 seconds...".

What can i do? I read another thread about this problem, it said to try and modify the _/etc/X11/xorg.conf_ file, and then press PAGEDWN to find nvidia... only problem is that when i access this, i cant press PAGEDOWN. I just see a ton of "~" symbols over my screen, and if i try to scroll down (with PAGEDWN) all i hear are beeps from my computer, and nothing happens at all.


Any help with solving this problem???

---

