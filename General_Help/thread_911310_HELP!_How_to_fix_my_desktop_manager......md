---
title: "HELP! How to fix my desktop manager.....???"
date: 2008-09-05
forum: General Help
---

### Post by shgadwa on 2008-09-05
I updated my Nvidia Driver, installed the 3D accelerator and installed Compiz, and Emerald. I did compiz --replace and emerald --replace.

For a while, it worked nicely, till I restarted and found that the windows do not have a border around them... or anything like that. No panels on the top and bottom like there ought to be, or any such thing.....

I tried compiz --replace --indirect-rendering, but that did not help....  I removed compiz... And I reinstalled xubuntu-desktop, I reconfigured the xserver... STILL, same thing.

Any help would be appreciated.

---

### Post by Predator106 on 2008-09-05
Well with compiz, what I do is install compiz-fusion (believe thats the full package name), or fusion-icon, one of those... anyways, the icon, when started provides useful context-menu items like reloading the window manager, which will fix this problem. You can also set up fusion-icon to run at start up, fixing the border problem... you do have to do this manually once, but it's so easy with Ubuntu's startup manager, no registry hassles...

Oh, it's fusion-icon by the way, compiz-fusion is a dependency of it.

---

### Post by gjoellee on 2008-09-05
it is a common bug. It is usually solved by logging in and out or restarting the machine

---

### Post by shgadwa on 2008-09-05
I did install compiz fusion... not plain compiz, sorry for the mixup.

To try to fix my problem, I uninstalled it... I also uninstalled xubuntu-desktop, then reinstalled it. I reconfigured the xserver.conf file, none of this helped. I tried to install the gnome desktop but it said that their were broken dependencies.

If I HAVE to... I will install the KDE desktop in hopes that it will fix my problem. But I think I kind of like xfce better, and the KDE one comes with a lot of apps that you either use them or you dont, if you knwo what I mean.

Any other suggestions.

Also, mind you, all my configuring and changing in attenpts to fix it, has been from the command line... I cannot do anything with the computer after I log into XFCE as it does not allow me to move the windows at all or anything.

---

### Post by Predator106 on 2008-09-05
Uhm, I must've explained something wrong, hang on....

Okay, if you want to try compiz, and to get it to work... do the replace command, yada yada yada, install the fusion-icon package.

If you still have GNOME(don't know what to do in KDE, never tried it), in the terminal type in 'gnome-session-properties'

Click add, put in a description, called something like compiz fusion or something to that degree, for the Command, put in 'fusion-icon' this will startup the fusion icon, this way you can also-if compiz crashes or something (rarely have it happen), then you can just right click and hit reload. Or if it just acting funny, like sometimes after resume from sleep I will have weird things being drawn, almost like artifacts...except more like an object. Anyways, that comes in handy...

I hope I explained it clearly now, sometimes I tend to be bad at explaining things to anyone but myself :).


Oh and since the windows have no borders, hold alt+click to drag them around anywhere(it's easier than other ways IMO).

---

### Post by shgadwa on 2008-09-05
I think that you are not understanding me correctly....

After enabling Compiz and Emerald, it worked until I rebooted. I am guessing its a problem with the emerald manager.

Now, I have a COMPLETELY Unusable system. The ONLY thing I can do is type in commands from the command line (Ctrl+Alt+F1).

Again, I uninstalled compiz, I uninstalled Emerald, I tried to change back to the old xfce manager but I do not know how...

I changed my xserver-xorg settings (which not does not use the current NVIDIA driver anymore. I uninstalled and reinstalled the xubuntu-desktop package. I tried to installed GNOME (again, I am using xfce, xubuntu) but it said that there was broken packages....

I think what I really need to know, is how can I get the system back the way it was BEFORE I put compiz on it?? I want a working computer.... Then I can try to get compiz working.


Thanks!

Shawn

---

### Post by shgadwa on 2008-09-05
By it being unusable... 

It goes like this:

I log in, and windows open up (from my last saved log in)... These windows do not have any borders around them, I cannot move them, enlarge them, or shrink them. I have nothing on my desktop (though I have a desktop photo), I have no panels (how ubuntu has a panel on the top, and on the bottom). My computer is unusable.

I think what I need to do is undo the compiz --replace and emerald --replace.... for now.

---

### Post by shgadwa on 2008-09-06
Heloo...........................


HELP?

---

### Post by Predator106 on 2008-09-06
> **shgadwa said:**
> Heloo...........................


HELP?

Be patient, I had to go to bed, I can't just take every minute out of my day to read every post you have, you have to understand that people are in different time zones, and thus different schedules.

Anyways, you could try 'metacity --replace' followed by 'gtk-window-decorator --replace'

Just out of curiosity, type in 'sudo gdm' and tell me what it says.

It said there were broken packages when you tried to install GNOME?

Hmm.

Also try 'apt-get -f' To fix the broken dependencies(hopefully).

I am unfamiliar with any window manager but GNOME, but hopefully I can still help you.

---

### Post by shgadwa on 2008-09-06
Thank you....

No, that was just my way of 'bumping' it as I know that threads can get LOST in no time.

I will try what you suggested.

Until then, I have installed KDE....

Really, I think I might just Do a reinstall of Xubuntu... as now I have SO MANY KDE apps I will never use... I have more confusion in my system form so many tries and such.....

Furthermore, I have a install of Windows XP PRO that will not boot as it is not in the boot loader and I do not know how to fix it (I also found out I do not have the registration numbers for the CD)...

I will just do a reinstall. Thanks for the help!

---

### Post by overdrank on 2008-09-06
> **shgadwa said:**
> Thank you....

No, that was just my way of 'bumping' it as I know that threads can get LOST in no time.


Furthermore, I have a install of Windows XP PRO that will not boot as it is not in the boot loader and I do not know how to fix it (I also found out I do not have the registration numbers for the CD)...



Firstly there is no need to bump in  Desktop Effects & Customization as you can see the last thread on the first page is 10 hours old. It is not like the ABT or general help.
Second we can not help with the windows cd keys :o

---

