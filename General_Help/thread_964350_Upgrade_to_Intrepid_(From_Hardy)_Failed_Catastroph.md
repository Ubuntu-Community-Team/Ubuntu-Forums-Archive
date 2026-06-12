---
title: "Upgrade to Intrepid (From Hardy) Failed Catastrophically"
date: 2008-10-30
forum: General Help
---

### Post by FRIEDjellyWALNUT on 2008-10-30
Please help!!

This afternoon, I started the update process to Intrepid from Hardy on an AMD64 setup. It downloaded all the package files, and was ALMOST done installing...

But then it started installing the new network manager (the progress bar was about 95% full, it now longer showed a Time Remaining estimate), and suddenly, everything just crashed. My mouse was no longer responsive, neither was my keyboard. I couldn't Ctrl-Alt-Esc or Ctrl-Alt-Backspace. Thinking that this was normal, I let it sit for about 2 hours.

It was still frozen. I did a hard reset, and when my computer booted, everything seemed normal until I got past the login screen. Now, I'm greeted with an error that says "HAL Cannot Be Initialized". My entire desktop is black, there is no taskbar, and no keyboard shortcuts work. However, my two programs that I have enabled at startup, Thunderbird and Pidgin, open and run fine. Other than that, nothing.

Please help!! There were no other applications running beside Update Manager when I was updating.

---

### Post by monkeyking on 2008-10-30
I experienced the same when opgrading from 7.4 to 7.10.

It might not be the best solution, but try finishing the update.

When I did this, it kept on going, for some time, started complaining again, and then crashed.
I then tried again,
after some times, it actually worked out.

I had to change my xorg config, and my /etc/network/interfaces.

But otherwise it worked.

---

### Post by FRIEDjellyWALNUT on 2008-10-30
Okay, so I rebooted into the machine, then logged in in the terminal using Ctrl-Alt-Esc.

At this point, I've tried everything to no avail. I've done sudo dpkg --configure -a, sudo apt-get update, sudo apt-get upgrade, sudo apt-get dist-upgrade, sudo do-release-upgrade -d.

Everything that was returned by those commands seemed to indicate that my Intrepid install is perfect. But obviously, it isn't. I think my Gnome is broken. How do I go about fixing this?

Internet and everything is working fine, and my resolution is correct, I just have absolutely nothing on my desktop. No wallpaper, no taskbars, nothing. Even Compiz works, I can activate the cube, but all 4 sides are pitch black.

I really need to revive this system, I have a virtual version of XP on here that I can't afford to lose. If in the case that I can't revive this system, how would I go about transferring the virtual drive to a clean install of 8.10? It's in Virtualbox.

---

### Post by monkeyking on 2008-10-30
Hmm,
try making a new "fresh" user.
and login as this user.

If this works, then it's your settings, or more likely the permissions.

Actually I had a problem like this quite recently alos.
It occured after I tried to make a kubuntu to a ubuntu.
It had to do with setting the default menu's to gtk style instead of qt.

---

