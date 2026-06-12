---
title: "Login screen realignment problem"
date: 2005-11-12
forum: General Help
---

### Post by capcorn on 2005-11-12
How can I change the resolution of my login screen to fit into my screen?
Currently my login screen is bigger than my screen. If i move my mouse to the bottom, the login screen will move up and show the Gnome logo and reboot/shutdown option. I have adjusted the screen resolution to 1024x768 but seems like the login screen is ignoring it.

how can i resolve this issue?

Thanks for your time.

---

### Post by Ubuntist on 2005-11-12
Maybe System -> Preferences -> Screen Resolution?

---

### Post by 3dmaker on 2005-11-12
I have same problem! And  System -> Preferences -> Screen Resolution only changes your users resolution. Not login screen. Talk when you know man! You probably use a laptop and have no problem with it.

---

### Post by TimelessRogue on 2005-11-12
Hey 3dmaker ... chill, man!  Give the guy a break!  Like the rest of us, he was just trying to help out ... and without a lot of info at that!

As to laptoppers, we're a pretty common lot in Ubuntuland ... and rightfully so.  I too, have a screen problem on an older HP that I've been trying to work out.  Screen size (doesn't want to fill the entire screen ... offset to the left) though, as opposed to resolution.  And this is where I will find the answer ... if I don't figger it out for myself, that is.

So capcorn:  hang in there ... someone with give you a hand.  As a matter of fact, you might do a forum search for "screen resolution" or just "resolution" to see how others handled the problem.  Hey, you too 3dmaker.

---

### Post by capcorn on 2005-11-12
Thank you for your replies.

Hope someone can advise how to resolve the issue.

---

### Post by Qrk on 2005-11-12
reconfigure xorg (either by editing your xorg.conf file or with sudo dpkg-reconfigure xserver-xorg) and take out the resolutions above the one your monitor can use.

If you use the dpkg command, theres a nice dialog box devoted to it. 

These changes will be system wide.

---

### Post by capcorn on 2005-11-12
Qrk,  Thanks for the tip.

I have tried ur suggestion. It didnt work.
I have marked out the resolutions that are bigger than my screen can support.
And I did a change resolution to select the desired resolution. 
Still the login screen is larger than my screen resolution.

I am searching for a solution.

---

### Post by teaker1s on 2005-11-13
the settings will be in the login manager config files. have you checked
system-administration-login screen setup just in case there is a setting.
can't suggest more as kde is my login manager not gnome

---

