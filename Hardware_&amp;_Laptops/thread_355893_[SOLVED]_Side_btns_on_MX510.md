---
title: "[SOLVED] Side btns on MX510"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by iamstretchypanda on 2007-02-07
Hi, i followed _[color="blue"][this](ubuntuguide.org/wiki/Ubuntu_Edgy#Mice)[/color]_ guide to get the side buttons on my mouse working.  I completed the sections: " Activate side-mouse-buttons in FireFox" and  "Install & Configure IMWheel"

All of my buttons work, except scrolling up on my scroll wheel takes me back a page, and scrolling down on my scroll wheel takes me forward.  Also, hitting the browser forward (front-side btn) scrolls down and browser back (back-side btn) scrolls up.

It just appears that they are flip-flopped and will be an easy fix.  Any ideas?

Thanks much,
James

---

### Post by iamstretchypanda on 2007-02-11
Is there any sort of information you'd like me to post to help get this worked out?

---

### Post by AnRkey on 2007-02-23
To get this working in Firefox on Feisty I added this 2 line script to my startup in system>prefs>sessions

```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 " &
```

My mouse is a Logitech MX510

That works just fine for me now.

This mouse setup headache is very tricky and changes with each mouse that logitech brings out. I found this spec for a Gui on launchpad. I am sure if we get enough people interested in the idea the Devs will make it happen.

The link >> [https://blueprints.launchpad.net/ubuntu/+spec/gui-mouse-configuration/](https://blueprints.launchpad.net/ubuntu/+spec/gui-mouse-configuration/)

Subscribe to it and if they start work on it, help to test the packages.

R

---

### Post by iamstretchypanda on 2007-02-27
Thanks for your advice, that worked well for me.  A reboot actually fixed most of my problems but still couldn't get firefox to work.  Your script was sufficient for that.  Kudos :]

---

### Post by AnRkey on 2007-02-27
In the part...

```
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "67" &
exec $REALSTARTUP
``` 
... of the howto, try switching 6 7 with 4 5 around so that it shows 
exec xmodmap -e "pointer = 1 2 3 6 4 5 6 7" &

you can try this first by running 
exec xmodmap -e "pointer = 1 2 3 6 4 5 6 7" &
from the command line
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
to switch back if it doesn't work.

Let me know if it works

---

### Post by iamstretchypanda on 2007-06-26
Interesting.  It worked on my old setup (edgy) but after a re-install/upgrade to feisty its back the way it was.  I'm not having any luck fixing it this time around.

---

### Post by BobLand on 2007-06-26
Try this.  [http://ubuntuforums.org/showthread.php?t=485175](http://ubuntuforums.org/showthread.php?t=485175)
This works on my system - fiesty MX510

bobland

---

### Post by iamstretchypanda on 2007-07-07
Followed posted guide, perfect fix. thanks :]

---

