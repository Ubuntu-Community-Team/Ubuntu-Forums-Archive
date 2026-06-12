---
title: "Odd bug - Two &quot;apps&quot; are autostarted each login"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by maximilion on 2009-08-20
Just installed Xubuntu 8.04.1, and after adjusting the GUI to my liking, I started the settings for the calendar on a whim. I thought I could make it dock to some corner of the desktop on boot, but I didn't make any changes to any settings.

I went on to customize further, and I had to re-login to see some changes. When I did, the calendar (Ograf or something) AND the settings panel for it, launched automatically.

I check the autostart, but there's nothing but the basic defaults there. Session saving is turned off when I shut down/log out.

Somehow Xubuntu decided to put those two launches in some startup file, I guess - but how do I get rid of them?

---

### Post by spcwingo on 2009-08-20
Look under /home/your_user_name/.config/autostart.

---

### Post by maximilion on 2009-08-27
no autostart file or folder in the .config dir. I'm logged in as admin and did a "sudo thunar". Any other suggestions?

---

### Post by spcwingo on 2009-08-27
The only other place I can think of is /usr/share/autostart.  If not there, hopefully someone else will swing by with a solution.

---

### Post by maximilion on 2009-09-18
No autostart folder there either...

---

