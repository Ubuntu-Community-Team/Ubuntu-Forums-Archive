---
title: "Desktop Menu Bar top and Bottom MISSING!"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by BITstate on 2007-12-28
I was playing around with my screen resulotion on laptop and know I have lost the top and bottom bars from the desktop.:(

Please could some kind person explain to a ubuntu/linux beginner what I have done wrong.:confused:

Linux is a SLC (Steep Learning Curve), My brain is recovering from years of misguilded MS Windows usage.  Please Forgive me.

---

### Post by georider on 2007-12-28
No forgiveness necessary. You're simply learning.

I wonder if you set your desktop bigger than your screen.

At any rate, you can get to your settings by pressing and holding <ALT>  and pressing <F2>. This should bring up the "run command" box in both KDE and Gnome; whichever you might be using. 

For Gnome, just type in "gnome-control-center". Then find the screen resolution under the hardware section.

For KDE,  type in "systemsettings". Under Computer Administration, you will find the monitor & display option.

That should get you back to a familiar place and you can change your settings back.

If not, write back with more info such as:

Which are you running: KDE or Gnome or ???

How were you changing the resolution: editing xorg.conf, systemsettings, gnome-control-center??

Good Luck and let us know how it goes!!

-g

---

### Post by BITstate on 2007-12-29
ALT f2, not working, I tried this first, Nothing works, the only menu I can get is the mouse Right Click menu.  I cant get a CL, nothing but a leathery Desktop background.

I am using ubuntu 7.10 as is I'm not sure if it is K this or G that.

I was thinking about:- 
sudo cp /etc/x11/xorg.conf /etc/x11/xorg.orig
sudo dpkg-reconfigure xserver-xorg
startx

But I don't have the CL in order to do this.

Problem History:- What happened was; screen was set to 640*480 and I was trying to set it to 800*600 by changing the screen option.

---

### Post by georider on 2007-12-29
Ok. Did you try to break out of X into one of the other sessions? You can do <CTRL><ALT><F1 through F6> to reach the other sessions. Log in and you'll have your CL. This does not affect your X session that is default to <CTRL><ALT><F7>.

Check your /etc/X11 directory before changing anything. You may already have some backup xorg files in there you can use. Look at the dates and see if you have one around the time you KNOW it was working. Then copy it into xorg.conf. 

When working with these files, it is wise to ALWAYS make a backup copy before modifying them.

Write back if no resolution. There are more tricks. :)

Good luck!

-g

---

### Post by BITstate on 2007-12-29
Result Negative

CTRL ALT F1 to F6:- No Result:(

---

### Post by Yellow Pasque on 2007-12-29
Can you just add those panels back by right clicking and adding panels, or do you really believe they're floating offscreen somewhere?

Here is a cool power tool to help you with Gnome. Run:
```
sudo apt-get install gconf2 gconf2-common gconf-editor libgconf2-4
```

Now you should have something called "Configuration Editor" under the Applications -> System Tools menu. Look under /apps/panel/default_setup and you should see settings for your panels.
 I have other suggestios if needed, nut let's hope they're not required.

Good luck.

---

### Post by BITstate on 2007-12-29
No right click add panels and noway to get CL to enter your command, I am Totally Stuck

---

### Post by georider on 2007-12-29
You can try <CTRL><ALT><BKSP> to break out of your current X session.

Do you have another machine you can ssh into this machine with?

Have you been able to reboot in any way? If you can get rebooted and get to the login the <CTRL><ALT><F1> should work there as well.

If not you may need to force a reboot which **could cause data loss** and is **not recommended**.

---

### Post by BITstate on 2007-12-29
Control Alt BackSpace has worked, :)

I know get a warning window with:

Nautilus can't be used now
due to unexpected error.
show more detail:
Nautilus can't be used now, due to an
unexpected error from Bonobo when 
attempting to locate the factory. Killing
bonobo-activation server and
restarting Nautilus may help fix the
problem.

Whats that all about? :confused:

One more thing, harddisk is working overtime!!!!

I have my desktop back!, Thank you for all your Helps Everyone!!!!

---

### Post by georider on 2007-12-29
Good to hear.

I should have explained that <CTRL><ALT><BKSP> dumps your current session and restarts the X server. I have never had any issues with doing this as a last resort but it should be used sparingly as it could leave some programs in a bad state as they are not exited properly.

As far as your HD working hard. If it does not go away, you should probably investigate as it could easily degrade your system performance considerably. And on a laptop, we don't need that! It also uses more battery power than it should. Start with a proper shutdown and boot to see if it is a process that was hung due to the resolution issues you were having.

You should also verify your system is set to proper resolution for your monitor and video card. I have seen some damage to monitors and a toasted graphics card caused by improper video settings. See your manufacturers recomendations for the info as each one is different.

Good luck and happy hacking!

-g

---

### Post by BITstate on 2007-12-29
I have set the resolution to 800*600

The hard disk drive has been working overtime since I installed ubuntu.

I think maybe I make the /Swap far to big, I have 64MB system RAM and I think I should have double that for Swap space, but I have a feeling that the Swap area is several hundred MB's!

---

### Post by georider on 2007-12-29
I use the same general rule: swap is twice actual ram. 

This could be an issue. I believe you can resize your swap without reinstalling. At least I know it can be done in Solaris. I have not had to experience that in Linux yet so maybe some reading is necessary here.

Good luck!

---

### Post by Kougaiji on 2008-01-04
I have the same exact problem... someone please help

---

### Post by georider on 2008-01-05
Which issue, Kougaiji? Hard drive working overtime or desktop bars missing?

---

