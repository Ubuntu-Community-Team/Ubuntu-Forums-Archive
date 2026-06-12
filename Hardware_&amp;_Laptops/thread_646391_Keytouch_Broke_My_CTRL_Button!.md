---
title: "Keytouch Broke My CTRL Button!"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by insertnewsn on 2007-12-21
I'll try and make this short and sweet..I was trying to fix my Dell E1705's global shortcuts, and I was reffered to keytouch..

After installing keytouch, it messed up my keyboard layout to the point where the left and right CTRL buttons won't work, and the ALT key is messed up as well (ALT+A now selects all..CTRL+A is supposed to do that!)

I've tried uninstalling keytouch, deleting the .keytouch folder in my Home directory, resetting my keyboard layout and keyboard types, all while restarting my computer after every change...but to no avail, the problem is still there.

Is there any way I can just get rid of the problems that keytouch has caused me?

Note: when checking xev for the leftt CTRL button, I get the following...

left:

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

Any help you could give would be really appreciated!!

thanks guys!

---

### Post by BaroldGene on 2008-02-28
I'm having the same issue!  For me its only the left control.  When I killed the keytouch deamon the keycode came through as 0x00 from XEV.  Now its coming through properly, but having the effect of the up key!  Its broken on the TTYs too!  


Anyone know what's going on?

---

### Post by Iceman512 on 2008-04-02
bump, I too am suffering from this problem! Please advise. Thanks in advance.

---

### Post by warp99 on 2008-04-02
Are these by chance USB keyboards because according to the developer there is a problem:

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

As far as the keys not working the keytouch dameon must still be loading. Check the /etc/init.d directory for keytouch. If it's there delete it, then check to see that all of the files were removed per the package list:

[http://packages.ubuntu.com/gutsy/i386/keytouch/filelist](http://packages.ubuntu.com/gutsy/i386/keytouch/filelist)

Edit:
At the worse email the developer. I've dealt with him before, nice person. He should be willing to help.

---

### Post by Iceman512 on 2008-04-02
Actually, I'm not sure if it's a USB or PS/2 keyboard; in my case, it is my notebook, the HP DV2550SE (a derivative of dv2000 lineup). Thanks again for the reply. I tried out your suggestions but to no avail so I emailed the developer. I will definitely post the email(s) here for the benefit of others (hopefully I will remember to do so!).

Thanks again.

EDIT: My CTRL key is back from the dead! Not sure what I did tough, just removed Keytouch via Synaptic Package Manager, double-checked to make sure that all associated files were deleted, changed the keyboard layout and restarted the machine (not just logout and login again, that didn't work for me). I figured that makes sense because, and I'm guessing here, that when you logout, the computer still needs a keyboard configured to enable you to enter your username and passwor d at the login screen, so the keyboard layout file or whatever was never taken out of memory, if that makes any sense. 

Anywho, thank you for helping us solve this problem.

---

### Post by Guinness70 on 2008-04-11
im using a Logitech G15 v1 keyboard (not USB)

yesterday i installed keyTouch in yet another attempt to get the extra buttons working (unsuccessfully).
apart from the extra buttons everything worked fine yesterday.
this morning CTRL and ALT and some other keys are not working but only when in a game (GuildWars) running with Wine.

story of my short Ubuntu life so far :**[COLOR="Red"][SIZE="3"] try fix something = break somethingelse[/SIZE][/COLOR]** ](*,)

---

