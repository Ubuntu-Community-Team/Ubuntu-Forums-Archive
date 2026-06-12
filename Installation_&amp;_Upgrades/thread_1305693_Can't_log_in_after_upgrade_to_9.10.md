---
title: "Can't log in after upgrade to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by wmcbrine on 2009-10-30
After a flawless experience upgrading to Jaunty, I'm back to having serious problems with the Karmic upgrade.

What happens is, I get as far as the gdm login screen, enter my info, get a brief flash, and am promptly returned to the login screen again. No error message; nothing.

I have a little-used second account (for another user) that I decided to test. That one worked fine! I also was able to log in at the command line with no problem.

I tried looking for errors in log files, and the best I could do was this -- my ~/.xsession-errors:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
No protocol specified
No protocol specified
XOpenDisplay() failed
Failure: Module initalization failed
No protocol specified

** (gnome-session:2717): WARNING **: Cannot open display:
```

(This is repeatable -- .xsession-errors.old is the same, apart from the number.) I feel unenlightened. An .xsession-errors file from a successful login is much longer.

---

### Post by wmcbrine on 2009-10-30
I managed to log in using "Failsafe GNOME". Not sure what the difference is between this and regular GNOME (it looks no different), but perhaps from this, someone can point me towards the problem?

---

### Post by wmcbrine on 2009-10-30
Ah, another data point: I get the same messages, "No protocol specified" and "XOpenDisplay() failed", when I try to run mpg123. I also get no sound...

Scratch that -- there's sound, it was just turned really low. But, turning it up, it's completely garbled.

---

### Post by wmcbrine on 2009-10-31
OK, I found out I couldn't start any X apps from the Terminal while logged into my main account in "Failsafe GNOME". So I did an "xhost +". After that, the "No protocol specified" message went away. At first I guessed that the restriction was related to the failsafe mode, but then I tried logging into the alternate account in failsafe mode, and it didn't have the problem.

So... what the heck? Anybody?

---

### Post by BuayaGuy on 2009-10-31
Same thing's happening to me...when I first installed (fresh install under VMWare Fusion 3), it worked great - then after about a day, it started where it would only login after trying 3-4 times...now I can't login at all through the normal GNOME interface.

Logging in through the xterm and Failsafe GNOME work fine, but Failsafe mode doesn't allow you to access any administrative functions (that I can see, anyway.)

---

### Post by wmcbrine on 2009-10-31
I turned off everything in Startup, with no change...

---

### Post by inearlygaveup on 2009-10-31
keep punching your details into the login screen - I get in after about the fifth attempt (Not a good start)

---

### Post by BuayaGuy on 2009-10-31
I finally gave up and reinstalled Ubuntu - since it's through VMWare Fusion, it wasn't a big deal to do and I didn't have to sit and wait for it to finish.

After setting up a few things, I then saved a snapshot being able to login, so hopefully if it DOES happen again, I can just revert to that time.

---

### Post by wmcbrine on 2009-11-05
OK, progress -- I traced the problem to my .profile, and from there, to this line:

export XAUTHORITY=$HOME/.Xauthority

Now, I still don't know *why* this kept me from logging in, but there it is. (And yeah, I do actually have an .Xauthority file.)

---

### Post by Hyo on 2009-11-08
I too have that same problem. I have install reinstall and the problem will not go away. I hope i can get this done tonight.

---

### Post by kubilus1 on 2010-01-13
Same exact issue, different solution for me.  I had a ton of entries under ~/.metacity/sessions.  I cleared these out, and now I can login. 

Now onto the many other 9.10 upgrade issues.   *sigh*

---

### Post by et1ssgmiller on 2010-01-14
I have seen the problem twice with 9.10.  I reinstalled the first time it happened.  After the reinstall it's been working okay until the latest round of updates ( last night 1-14-10 ).  It took me numerous reboots and attempts before it mysteriously decided to complete the log in.  I tried the Failsafe Gnome login a few times with no luck.

---

### Post by ridgerunner57 on 2010-01-29
Hello,

Me too, this problem with fusion 3 and Ubuntu 9.10. Using the failsafe Gnome login I changed my monitor res to 800x600 in Ubuntu. I am now able to login normally. Currently, it is working at 1366x768. It seems that folks who use Parallels are also having some similar problems.

HTH
James

---

### Post by pauljwells on 2010-02-19
I find that if I just switch the view in Fusion to 'Window' rather than 'Full Screen' I can login without any problems.

---

### Post by docdross on 2010-03-12
Thanks pauljwells! This worked. 
I had Ubuntu 64 working and it just would not let me login. I thought I had done something stupid, I am a linux nube, so I re-installed with the same problem. 
Your fix works. I start and login in single window then go full screen after login.
I had not done any recent update to guest or host os???
Very weird problem. Anyone know what is going on?????

---

