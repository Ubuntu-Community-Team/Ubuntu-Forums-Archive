---
title: "visual effects problem"
date: 2008-09-16
forum: General Help
---

### Post by bradpurvis on 2008-09-16
this is the third machine i have installed UBUNTU on. i seem to keep having a visual affects problem.

when i try to enable visual effects i get this message:

composite extension not avaliable

help would be appreciated TY

---

### Post by Pro-reason on 2008-09-16
How exactly does the visual affect the problem?

(Sorry — couldn't resist.)

Run [Compiz]("http://www.ubuntugeek.com/check-compiz-will-run-on-your-ubuntu-desktop-or-not.html")-[Check]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by bradpurvis on 2008-09-16
dude not helpful. it was funny though

any other suggestions like some terminal codes i can use

---

### Post by kokkus on 2008-09-17
So you can't activate your visual effects? Ok first of all you have to enable your graphic card unde system > administrator > hardware drivers.
Restart your PC and try again.
If this doesn't help, see if your graphic card is one of the blacklisted cards.
You can use compiz-check to see if your gfx card is blacklisted and how you can fix (whitelist) it. 
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

**Note:** Blacklisted cards are not supported by Ubuntu.

Good Luck :)

---

### Post by bradpurvis on 2008-09-17
It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "0" 

i got that message when i ran compiz-check

---

### Post by Pro-reason on 2008-09-17
> **bradpurvis said:**
> It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "0" 

i got that message when i ran compiz-check

Oh yeah?  Let's look at that file.  Do this:

```
grep Composite /etc/X11/xorg.conf
```

Post the exact output.

---

### Post by bradpurvis on 2008-09-17
purvis@purvis-desktop:~$ grep Composite /etc/X11/xorg.conf
        Option          "Composite"     "0"
purvis@purvis-desktop:~$

---

### Post by Pro-reason on 2008-09-17
> **bradpurvis said:**
> purvis@purvis-desktop:~$ grep Composite /etc/X11/xorg.conf
        Option          "Composite"     "0"
purvis@purvis-desktop:~$

Do these three commands (copy and paste for maximum accuracy): ```

cd /etc/X11

sudo cp xorg.conf xorg.conf.backup

**sudo sed -i "s/\"Composite\".\".\"/\"Composite\"     \"enabled\"/" xorg.conf**

```

You can then do the previous command to check it worked.

If for some weird reason the *sed* command doesn't work, edit the file in gedit.  (That is to say, type &#8220;gksu gedit /etc/X11/xorg.conf&#8221; to open it, and then change the text yourself.  Save and close.)

---

### Post by bradpurvis on 2008-09-18
purvis@purvis-desktop:~$ cd /etc/X11
purvis@purvis-desktop:/etc/X11$ sudo cp xorg.conf xorg.conf.backup
[sudo] password for purvis:
purvis@purvis-desktop:/etc/X11$ grep Composite /etc/X11/xorg.conf
        Option          "Composite"     "0"

---

### Post by bradpurvis on 2008-10-12
yeah well i have been waiting for quite a while. so any suggestions on a quick fix?

---

### Post by bradpurvis on 2008-10-12
i have all drivers enabled i just need to know how to change the composite from 0 to what it has to be.

---

### Post by Pro-reason on 2008-10-12
> **bradpurvis said:**
> i have all drivers enabled i just need to know how to change the composite from 0 to what it has to be.

I've already told you how to do that.  I'm just waiting for you to do it!

---

### Post by bradpurvis on 2008-10-13
purvis@purvis-desktop:~$ grep Composite /etc/X11/xorg.conf
	Option		"Composite"	"0"
purvis@purvis-desktop:~$ cd /etc/X11
purvis@purvis-desktop:/etc/X11$ 
purvis@purvis-desktop:/etc/X11$ sudo cp xorg.conf xorg.conf.backup
[sudo] password for purvis: 
purvis@purvis-desktop:/etc/X11$ 

i have already posted this but i don't know what else to do.

---

### Post by bradpurvis on 2008-10-14
BUMP! still need help

---

### Post by Pro-reason on 2008-10-15
If you refuse to follow my instructions, there is nothing I can do.

I'm removing this thread from my watchlist, so I won't see any more bumps.

---

### Post by bradpurvis on 2008-10-18
wtc i did all of your instructions 
are you messing with me?

---

### Post by kokkus on 2009-05-06
GOt the same problem once. FIxed it by setting it to 1.

---

