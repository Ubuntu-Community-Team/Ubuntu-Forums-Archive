---
title: "Can't get past login screen after upgrade to 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Amblikai on 2009-11-01
Hi folks,

Just upgraded xubuntu from 9.04 to 9.10. I can't get passed the login screen though. 

I click on the user, type the password, i get the fireflies and then it just goes back to the login screen.

I can ssh in from another machine (my laptop). 

Can anyone help or give me some ideas of some log files i can look at? I understand 9.10 has a new login manager (gdm?)

Thanks in advance, 

Kai.

---

### Post by Amblikai on 2009-11-02
Anyone? I'm still having this problem.

---

### Post by Amblikai on 2009-11-02
There seems to be a number of people having this problem across various forums. No one has had a reply.

Having never filed a bug before i am hesitant to do so until i know more about the situation. 

Can someone help me out here?

---

### Post by ivoshm on 2009-11-03
> **Amblikai said:**
> There seems to be a number of people having this problem across various forums. No one has had a reply.

Having never filed a bug before i am hesitant to do so until i know more about the situation. 

Can someone help me out here?

Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

If it helped ... write here [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932) "ME TOO" :(

Ivo(sh)

---

### Post by lagonie on 2009-11-04
had the same Problem with my ePC 1000h netbook and my (very old) lcd-screen pluged-in durin install and first strt of 9.10.  removed the display.xml and the problem was instantly gone..  
after that I have to say: 9.10 looks real nice :)

---

### Post by easterlingman on 2009-11-06
> **ivoshm said:**
> Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

If it helped ... write here [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932) "ME TOO" :(

Ivo(sh)

I tried this fix but after logging out and back in I got kicked back to the login screen once before being able to login properly.  Usually it happens 4 to 8 times so I guess it's an improvement, but any other ideas on what could fix this for me?

---

### Post by peyre on 2009-11-14
That seemed to do the trick for me!  Thanks Ivoshm!

> **ivoshm said:**
> Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

If it helped ... write here [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932) "ME TOO" :(

Ivo(sh)

Edit: But, on another of my Xubuntu machines, this workaround didn't do the trick.  There was no displays.xml there.  I deleted the whole .config folder, but that still didn't do it.

---

### Post by PetteriP on 2009-12-10
I had one of these today.
I could login to root desktop though.
In the .xsession-errors file there was an error stating something or other about the user rights of the .ICEauthority file. Right click on .ICEauthority and from the Permissions tab read and write rights to my user. That solved it.

---

### Post by S1gurd on 2009-12-16
Thanks for the tips guys.  This combination worked for me:

1.Login is as an alternat user with root access.
2.read the .xsession-errors file - mine was complaining about display 0.0
3. Follow ivoshm's advice here:

remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

And it worked. :P

---

### Post by azertyh on 2009-12-16
hi,
i had the same problem. i solved it by changing the displays.xml file. my post is here [http://ubuntuforums.org/showthread.php?p=8402051#post8402051](http://ubuntuforums.org/showthread.php?p=8402051#post8402051)
i can log on now and i notice that even if i change my screen resolution, i can always log on with the new resolution.
the displays.xml doesnt exist until you change your screen resolution.

---

### Post by jamppa93 on 2010-01-17
Deleting the displays.xml file worked for me. 

I logged in via xterm -session and deleted the displays.xml file via text console.

Thanks for advice.

---

### Post by TheOneBlackMage on 2010-01-25
I can confirm this fix worked for me as well.  Thanks for the tip.

---

### Post by NunyaB on 2010-01-25
Thank you for this post.  I am having the same problem and this gives me something to try!

---

### Post by Miscellaneous on 2010-02-21
> **ivoshm said:**
> Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

If it helped ... write here [http://bugzilla.xfce.org/show_bug.cgi?id=5932](http://bugzilla.xfce.org/show_bug.cgi?id=5932) "ME TOO" :(

Ivo(sh)

Thank you so much... This is not the first time it happens to me but it's the first time I got a proper answer! Thanks a million!

---

### Post by sportscliche on 2010-03-13
Thanks, this worked for me too.

---

### Post by Browser_ice on 2010-08-08
Why hasn't this been fixed so far ?

I have just experienced this bug.

---

### Post by krekon on 2011-03-11
I have the same problem in lucid lynx and there is no display.xml file in there. What can I do?

---

