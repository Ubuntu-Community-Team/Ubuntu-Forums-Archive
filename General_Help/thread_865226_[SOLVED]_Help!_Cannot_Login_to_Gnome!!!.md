---
title: "[SOLVED] Help! Cannot Login to Gnome!!!"
date: 2008-07-20
forum: General Help
---

### Post by MatthewPlanchard on 2008-07-20
:confused:

Okay, so yesterday I installed Enlightenment, Xubuntu, and Fluxbox, to play around with a little bit.

I logged into:
1. enlightenment
2. E-Gnome
3. Fluxbox
4. Xfce Session

After satiating my curiosity and messing with settings, I wanted to go back to my familiar Gnome Ubuntu desktop. But now I cannot log in.

From the login screen, which appears as normal, I type my user name and password.
X starts, the usplash screen appears, and the startup sound plays. Nothing else happens. 
None of the messages appear on the splash screen (starting nautilus, etc.), and there is a weird white or black box in the top left that looks like some kind of graphical glitch. 
It does not proceed any further, even in failsafe mode.

I am able to log in to Xfce, which is what I am using now.
However, GNOME is unreachable.

Here is what I've tried so far:
1. Uninstall Fluxbox and Enlightenment (I am currently using Xfce to post this)
2. Login to Failsafe GNOME - same problem
3. Reinstall Ubuntu-Desktop, GDM, and most Ubuntu and Gnome related core apps.
4. Reconfigure X - No success
5. Log in to recovery mode - Tried it, no success

I have searched the forums and have not found the same problem anywhere. I'll keep working, but I was feeling despair struggling onward without assistance. So anything you think would be totally helpful and welcome.

Thanks, and Blessings.
Matthew

---

### Post by lordadi on 2008-07-20
Hi Mathew,

If you can see the login screen, you may want to click on sessions and then choose gnome. It "might" help else try the xclient script option.

Let me know if reconfiguring X worked.

Lordadi

---

### Post by MatthewPlanchard on 2008-07-20
Okay, update Number 1:

What I just tried:
1. Reconfigure X - Did not work
2. Recovery Boot - Repair X, Repair Damaged Packages - Did not work

Clicking gnome does not help, but I will go try the XClient script now.

Thanks!

Update:
Okay, the Xclient script just brings me back here to Xfce. GNOME is still hanging at the usplash screen. I'll keep searching the nets. Let me know if you have any thoughts.

---

### Post by songshu on 2008-07-20
i never use Gnome but it sounds there is something wrong in the user department and not the general system itself, basically i guess it could be a single small config .file in your home directory giving you problems.

does the same thing happen if you create another user and log in??
this would prove the theory

---

### Post by MatthewPlanchard on 2008-07-20
Okay, Songshu, you are officially a genius. *hug*

I am logged in now with a new user account. I am now looking through my config files to see if I can get my original account fixed.

Please let me know if there's anything you can think of specifically that I could try.

Thanks!

---

### Post by songshu on 2008-07-20
what you could do is simply move all the .configfiles in your /home to a save place (just make a /home/you/backup folder/ and then copy them back in if you need them.

new .configfiles will be automatically created like the first time you ever logged in and then you can always copy the /backup files back one by one to see where the problem is.

p.s.
Yes i'm a genius indeed, but the fact i asked the same question on linuxquestions.org 8 years ago also helped ;)

---

### Post by MatthewPlanchard on 2008-07-20
Ahhhh, thank you sooooo much Songshu.

I'm back in my own home space now and totally happy. Now I'll work on figuring out which config file was causing problems. I'll post it up here when I figure it out.

Thank yoooou!

:guitar:

---

### Post by songshu on 2008-07-20
i'm just glad i could help Alice

---

