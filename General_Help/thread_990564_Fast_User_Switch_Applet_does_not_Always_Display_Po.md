---
title: "Fast User Switch Applet does not Always Display Power Options"
date: 2008-11-22
forum: General Help
---

### Post by brainiac8008 on 2008-11-22
When I use Intrepid, I don't always see the power options (Suspend, Hibernate, Restart, Shut down) in the Fast User Switch Applet. The user options (Guest session, Lock screen, Log out) are always visible.

I have tried clicking on the desktop and closing all windows, but to no avail. It seems as though it *might* be a function of how long the computer has been on before the applet displays the power options.  The first attached picture was taken after the computer was on for a few hours, and the second was taken as soon as the computer started up. It has now been 2 hours since I have taken that second screenshot and there still aren't any power options.

---

### Post by brainiac8008 on 2008-11-23
Anyone? I don't want to have multiple applets just for some user and power options!

---

### Post by brainiac8008 on 2008-11-25
*bump*

---

### Post by edd07 on 2008-11-25
I'm having a similar problem, but in my case only "Suspend" and "Hibernate" disappear. Does anyone have an answer to this?

Thanks

---

### Post by brainiac8008 on 2008-11-25
> **edd07 said:**
> I'm having a similar problem, but in my case only "Suspend" and "Hibernate" disappear. Does anyone have an answer to this?

Thanks

[Here]("http://ubuntuforums.org/showthread.php?p=1010022#post1010022") is what I've found to enable Suspend/Hibernate. On the second page, one person mentions that GNOME and KDE were conflicting, and that by uninstalling KDE, he/she was able to get all of the power options.

I wonder if [this]("https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/282613") is related to my problem?

---

### Post by edd07 on 2008-11-25
> **brainiac8008 said:**
> [Here]("http://ubuntuforums.org/showthread.php?p=1010022#post1010022") is what I've found to enable Suspend/Hibernate. On the second page, one person mentions that GNOME and KDE were conflicting, and that by uninstalling KDE, he/she was able to get all of the power options.

I wonder if [this]("https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/282613") is related to my problem?

No, hibernate and suspend work all right, it's just those options sometimes disappear from the new user-changer/shutdown-menu/pidgin-status changer thingy. I can still use the options if I press the power button of my laptop. It's not really a very serious problem (for me, at least), but it would be nice to be able to fix it.

Oh, and I don't have KDE. I tried KDE 4, but I uninstalled it before I even upgraded to Intrepid.

Thanks

---

### Post by brainiac8008 on 2008-11-25
I see. My problem is not that big a deal either, but it is sort of annoying. I guess I would not be satisfied with the Fast User Switch Applet anyways because you can't access user/power options when using Pidgin. What were the devs thinking with that one? I can't lock my screen or switch users while set to "away" in Pidgin.

Well, I'm just trying to keep this thread alive now. If we can't get any answers, I'm gonna let the thread die out. ](*,)

---

### Post by edd07 on 2008-11-26
> **brainiac8008 said:**
> I see. My problem is not that big a deal either, but it is sort of annoying. I guess I would not be satisfied with the Fast User Switch Applet anyways because you can't access user/power options when using Pidgin. What were the devs thinking with that one? I can't lock my screen or switch users while set to "away" in Pidgin.

Huh? That's strange, I can see the power options when using Pidgin, they appear beneath the Pidgin options.

Weird problem :)

---

### Post by joshzam on 2009-02-06
I found that whenever those Suspend, Hybernate, Shut Down, etc. options weren't visible in my FUSA, it was because my Power Management wasn't running. Try going to System > Preferences > Power Management. After opening this, I found those options had returned to my FUSA. To make sure they are always there, check your System > Preferences > Sessions and make sure Power Manager is checked to run at startup. Worked for me, I hope it works for you.

---

### Post by brainiac8008 on 2009-02-25
joshzam, I would try that if I could, but I just wiped out my Ubuntu installation to try out Windows 7 Beta. If I have the same problems when I install Jaunty over Win7, I will try what you have suggested and post my results here.

---

### Post by pallinger on 2009-04-14
Joshzam, your solution worked for me! 
Thanks!

---

### Post by tsb47 on 2009-07-26
Worked for me too. 

Thanks!

---

