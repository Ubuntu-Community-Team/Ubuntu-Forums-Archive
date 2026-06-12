---
title: "Multiple Update Dialogs Force Logout"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Scott M. Sanders on 2009-06-23
Lately when my Ubuntu 9 gets updates, I get a dialog box that says, "Updates are being installed..." with four buttons. That's okay, however seconds later spawns another dialog that's identical to this first one, and another, and another... to the infinite degree, forcing me to logout. 

If I try clicking any of those four buttons, it doesn't help. 

Using Update Manager manually helps of course only in the sense that it will bypass these dialog boxes from having to come up again, at least until next time, as this has happened twice now.

Also I maintain three Ubuntu installations, but this only happens on the one where I have all updates download and install automatically.

---

### Post by Scott M. Sanders on 2009-07-02
Bump: I just got back to see 303 of them in my taskbar. I was able to close them all at once without logging out, however this is still a big nuisance...

---

### Post by Scott M. Sanders on 2009-07-11
Every time is something different. I just want it to show an icon when there's updates so I can click and start them, like my Ubuntu server. Instead I must run Update Manager manually daily (or when I remember), and today in the middle of downloading updates, I get hammered with multiple dialog boxes from the following three entities (while downloading a samba update):
[LIST]
[*]gpk-update-icon, saying that updates are being installed, with the four button options, none of which actually work;
[*]notify-osd, telling me that another package manager is running; and
[*]Package Manager error details, saying I can only run one package manager program at a time (no kidding).
[/LIST]
Oddly when the samba update stops downloading, so does the spawning of these windows. 

Clearly there is a conflict, but what is the solution? Where are the settings for gpk-update-icon that I once set to auto-install updates, and is this not a very good app or what?

---

### Post by Scott M. Sanders on 2009-07-21
:-\"

---

### Post by Scott M. Sanders on 2009-07-28
I found if I launch System Monitor and end the process gpk-update-icon, that seems to solve the problem without forcing a logout, albeit temporarily of course. I suppose that should be a no-brainer though. 

Anyway still happening...

---

### Post by Scott M. Sanders on 2009-08-02
Today I did a manual update with Update Manager, walked away to do other things (it happens), came back to 550+ gpk-update-icon/notify-osd dialog windows, and was ultimately forced to do a hard reboot as my desktop would no longer respond to user input... :(

---

### Post by Scott M. Sanders on 2009-08-19
Hey guys! gpk-prefs: This is what caused this mess and is under System > Prefs > Software Updates apparently. And somehow mine has no pretty orange star icon for it anymore like on my Fedora (yes, I've had to resort to Fedora just to figure this out). 

I would suggest to others that you leave gpk at its defaults, simply because well 
[LIST]
[*]gpk will likely cause you hell for you otherwise, and 
[*]this could be the worst linux app ever written. 
[/LIST]

Anyway thanks for all you guys' help! :p

---

