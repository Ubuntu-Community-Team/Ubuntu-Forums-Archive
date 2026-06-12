---
title: "no shutdown option"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by gary_emms on 2009-10-31
Hi
Iv'e just upgraded to Kubuntu 9.10, All seems Ok except that I no longer have an option to shutdown or reboot in the 'Leave' section of the menu. As I am in the habit of shutting my PC down when I'm not using it, this is a nuisance to me - I know that I can log off and shutdown from the log on screne but its not the same.
Any one got any ideas as to how I add these options?
thanks
Gaz:confused:

---

### Post by SuperSonic4 on 2009-10-31
Have you checked for the *kshutdown* package? Don't know if it will work.

Also there is a Lock/Logout plasmoid on my install - perhaps that will work. If push comes to shove you can shut down from the command line ```
sudo shutdown -hP now
``` or ```
sudo shutdown hh:mm
``` for a certain time

---

### Post by gary_emms on 2009-11-01
Thanks, Kshutdown does the job. 
:popcorn:

---

### Post by drumz on 2009-11-03
Why doesn't the lock/logout widget have a shutdown option anymore?  I find this really annoying - i have to log out first, then do a shutdown.  Even on the KDE menu there's no shutdown option on the Leave menu item - I can hibernate and sleep but not shutdown.

---

### Post by froghopper on 2009-11-03
System Settings -> Advanced -> Session Manager -> Offer shutdown options

---

### Post by drumz on 2009-11-03
The checkbox for 'offer shutdown options' is checked already.

This is on a laptop that has both gnome and kde installed.  I've even moved my ~/.kde to ~/.kde-old so I had a fresh directory...

---

### Post by froghopper on 2009-11-03
Hmmm if you have both kde and gnome are you logging into kde from kdm or gdm? I think if you log into kde from gdm (or gnome from kde) you can only return to the login manager not shutdown from the window manager (without some hacks)

You can try:

> sudo dpkg-reconfigure gdm

or kdm to switch between them

---

### Post by drumz on 2009-11-03
Ok, tried the 'sudo dpkg-reconfigure kdm' and still the same thing.  When I click on the 'leave' button in the lock/logout applet the only option shown is logout.

---

### Post by Zillode on 2009-11-15
I have the same problem on my laptop.

---

### Post by drumz on 2009-11-16
Got it working:  Despite following one of the previous poster's instructions on switching from gdm to kdm to handle the login process, IT NEVER SWITCHED!

```
ps -ef | grep gdm
``` showed it was running.

Running the command ```
sudo dpkg-reconfigure gdm
``` and then selecting kdm did the trick after I rebooted.

Now when I use the logout/lock widget I get the shutdown option!  Yeah!!!

(But it sounds like a bug!)

EDIT:

I opened bug 484522 on this today.  I don't really care whether I use gdm/kdm, but with kdm evolution keeps prompting me to unlock the keyring on login and with gdm the shutdown/restart option disappears so I need at least one of them work work cleanly ;-)

---

