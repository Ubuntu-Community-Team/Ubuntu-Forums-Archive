---
title: "[SOLVED] XKB Configuration Error"
date: 2008-06-04
forum: Hardware
---

### Post by mr_boo1711 on 2008-06-04
Hey peeps,

Hope someone can help.  I've recently reinstalled my ubunutu on to another harddrive after playing about with it now for 2 years - the idea being a clean slate, and to remove some of the rubbish that's been buried in my system.  Got pretty much everything sorted apart from one or two things - the major one being my keyboard....

Its a Logitech Dinovo Edge, which previously have never gave me any problems - but now my super/win key isn't recognised.. :confused:  I did used to have my media buttons working with Amarok too, and now they're not anymore.  I've tried the keyboard settings - but everytime I change the slightest thing I get this error...

Error activating XKB Configuration
It can happen under various circumstances:
- a bug in the libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X Server with incompatible libxkbfile implementation

X Server version data:
The X.Org Foundation
10400090

If you report this situation as a bug please include:
- The result of xprop -root|grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


....so here are what the commands return in terminal....

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", ""

...and....

 layouts = []
 model = 
 options = []
 overrideSettings = true


Anyone got any ideas?? :confused: :confused:

Cheers,
Steve

---

### Post by imog on 2008-06-04
I have resolved this for myself after reading many unanswered threads, much like yours.

The results of the xprop command look good.  Your solution is to make the results of the gconftool match.

To do this, you will want to open gconf-editor and modify those settings.  You want to specify pc105 for model, and uk for layout.  Once that is done, logout and log back which will restart x, and you should no longer receive the error message.

This worked for me, if it does not work for you post back and maybe we can figure out a slight variation which will also work for you.

My results look like this now, I use a different keyboard layout than you tho:

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "dv", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "dv", "", ""

....

layouts = [dv]
 model = pc105
 overrideSettings = false
 options = []

---

### Post by mr_boo1711 on 2008-06-04
Hey imog! - thanks for the reply.

Nice idea - makes perfect sense infact.  However I give it a perfect bash and the only thing that changed was that I didnt get the warning message when I booted back up.  I still get it when I go into the keyboard settings and play about with ANY of the options.

The super/win key didnt work either when I booted back up.....  :confused:

Darn it!

---

### Post by imog on 2008-06-06
> **mr_boo1711 said:**
> Hey imog! - thanks for the reply.

Nice idea - makes perfect sense infact.  However I give it a perfect bash and the only thing that changed was that I didnt get the warning message when I booted back up.  I still get it when I go into the keyboard settings and play about with ANY of the options.

The super/win key didnt work either when I booted back up.....  :confused:

Darn it!

Ya, my understanding is that the way this works is a bug of some sort.  I mean, I don't know that I did anything to break the Keyboard settings - you should be able to modify the keyboard settings at will and not have these problems.

Assuming its a bug, if you go to change anything in the keyboard config, you will probably want to change it in both places - when you get it right, you won't immediately get the xkb configuration error message.

If I were you I'd play with the options available and try to find something that works best for you - the answer I came to myself is the best info I've seen on this issue thus far.  I was not able to find much info worth anything, though I found a lot of people having issues.

---

### Post by Zsola on 2008-06-06
Thank You! I was looking for a solution for this. Had this problem with one of my user account, but the others were just perfect...
That account just needed some tweaking with gconf-editor. Adding the keyboard layout solved the problem.

---

### Post by mr_boo1711 on 2008-06-07
> **imog said:**
> If I were you I'd play with the options available and try to find something that works best for you 

Yeah, I'm going to keep tweaking things and see what happens - trial and error. :)  Its the only real issue i've got with my Ubunutu just now so I'm keen to resolve it.

I dont remember doing anything to break mine either though - It was an error that came immediately after a clean install. :confused:

Anyways - Thanks for your help imog - much appreciated. :D

---

### Post by mr_boo1711 on 2008-06-15
I nearly forgot to mention to anyone who stumbles on the above post - This worked for me, but I needed to change the layout to 'GB', not 'UK' like it says above....  :)

---

### Post by Bloemetjesgordijn on 2008-09-03
Hi guys,

I am using this keyboard also, but somehow neither my mouse nor the keys are responding. Do you have issues with this??

---

