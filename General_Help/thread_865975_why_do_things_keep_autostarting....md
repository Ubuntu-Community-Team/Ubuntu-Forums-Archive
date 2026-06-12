---
title: "why do things keep autostarting..."
date: 2008-07-21
forum: General Help
---

### Post by evencoil on 2008-07-21
I don't think I have my sessions being saved. My ~/.config/xfce4-session/xfce4-session.rc file has the properties SaveonExit=false and AutoSave=false. And yet whenever I log into my main account in Xubuntu I get amarok loading (minimized in the taskbar) and Orage (the calendar program) popping up on the main screen. Also, in my 2nd desktop I get a copy of gftp open and an old Thunar browser pointed to a directory I use often. So it looks like the session is being saved, right? But also, if I close all these things and log in again they will open back up. Also, my ~/.config/autostart/ directory doesn't have anything in it except an amouse config. So any idea what gives?

---

### Post by sisco311 on 2008-07-21
The config files are in the ~/.cache/sessions/ folder.


Rename the folder and log out and log in.
If this works remove the folder, if not restore it.

---

### Post by Cheesehead on 2008-07-21
You don't need to save your session every time. 

If you save [COLOR="Red"]once[/COLOR] on logout, you will get that session back every time until you save differently.

So set up your system as you wish it to be upon startup, then logout/save session. Upon restart, your system should be as you wish.

---

### Post by evencoil on 2008-07-21
> **sisco311 said:**
> The config files are in the ~/.cache/sessions/ folder.


Rename the folder and log out and log in.
If this works remove the folder, if not restore it.

This worked, thanks!

And thanks to Cheesehead for clarifying for me how sessions work. I think I had it all wrong.

---

