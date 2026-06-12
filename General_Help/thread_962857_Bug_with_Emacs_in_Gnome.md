---
title: "Bug with Emacs in Gnome"
date: 2008-10-29
forum: General Help
---

### Post by Helge on 2008-10-29
After upgrading to Ubuntu 8.10 (Intrepid), I've got a weird error with Emacs 22. If Emacs 22 is on screen, and I either change window using alt-TAB, or if I resize the Emacs window, the desktop becomes totally unresponsive to mouse clicks. Focus doesn't follow the mouse. No mouse clicks are recognized. The CPU meter and clock works OK.

There is a workaround: get out of Gnome (and X) using ctrl-alt-F2, then back into Gnome using alt-F7. Usually, the desktop now gets responsive.

If I just start Emacs, without changing its size, and if I change focus using the mouse, Emacs will work as usual.

There is no problem with Emacs 22 in KDE.

Weird. Did anybody else see this? I don't know where to report the bug.

---

### Post by pierrer on 2008-10-31
I have the exact same problem ... Eventually if you wait long enough (a minute or two) you will get the desired behaviour (switch virtual desktop, resize, ...)

The problem does not happen if I use emacs in terminal mode.

To try to solve it, I made the following unsuccessful attempts:

- reinstall emacs
- remove and reinstall emacs
- try with emacs-snapshot
- remove my custom .emacs file in case some settings are troublesome.

It is so annoying that I cannot work with emacs (window mode) on Ubuntu anymore ... I can confirm this is happening with Ubuntu 8.10 (Intrepid). I am a Arch linux user and on Arch linux, the problem does not exist.

The only solution I can think about is: 
- install another window manager and try
- use Vim instead of emacs and wait and hope for an update
- use emacs in terminal mode  

I have no idea why this is happening.

Thanks for any help. Maybe we should file a bug ?

---

### Post by nkv on 2008-11-15
Exactly the same problem here as well. I have been seeing this only with Metacity. If I use compiz (with all the effects enabled), it doesn't happen. The behaviour is the same with emacs22 and emacs-snapshot.

I have opened a question about this here. If anyone has further information, please provide it. 
[https://answers.launchpad.net/ubuntu/+question/51449](https://answers.launchpad.net/ubuntu/+question/51449)

---

### Post by durb on 2008-11-24
For what its worth I think I may have a related problem, sometimes when I open an rdp connection with the terminal services client I get the same symptoms.  First time was with a few clients open then after I logged in again it was the only window I had open.  That second time I was able to get out of it easily because I had the wrong conection options and was able to click cancel on the reconnect try but I still couldnt move the window.  It may be a completely different issue but I thought I would put in my 2 cents.  And for the record this is a fairly clean install.

---

### Post by andy22286 on 2010-03-30
I am not sure how much it will help, but killing all running instances of Google Chrome seemed to fix it for me.  This is on ArchLinux with the dev version of Chrome.

---

### Post by eraaij on 2010-05-18
I have a similar problem here with emacs under a minimal Gnome (no compiz) setup. 

- Ubuntu 10.04 (sorry for the 'Karmic' typo)
- GNU Emacs 23.1.50.1 (i486-pc-linux-gnu, GTK+ Version 2.18.0)
- Gnome 2.30

Reproduction: 
- Do some work in emacs (mode irrelevant) 
- Switch focus to some other windows, f.e. Firefox
- Do stuff there
- Bring emacs into focus again
- If you had a blinking cursor - it won't blink anymore
- No keyboard input seems to work, but the emacs menus can be manipulated from the main menubar. 
- You get the focus back after selecting f.e. the same or another buffer from the buffer menu.

-Emile

---

### Post by vili7 on 2010-05-26
> **eraaij said:**
> I have a similar problem here with emacs under a minimal Gnome (no compiz) setup. 

- Ubuntu 10.04 (sorry for the 'Karmic' typo)
- GNU Emacs 23.1.50.1 (i486-pc-linux-gnu, GTK+ Version 2.18.0)
- Gnome 2.30

Reproduction: 
- Do some work in emacs (mode irrelevant) 
- Switch focus to some other windows, f.e. Firefox
- Do stuff there
- Bring emacs into focus again
- If you had a blinking cursor - it won't blink anymore
- No keyboard input seems to work, but the emacs menus can be manipulated from the main menubar. 
- You get the focus back after selecting f.e. the same or another buffer from the buffer menu.

-Emile
Having this exact same problem and if I do something like saving the current file it seems to unfreeze it.

---

### Post by eToIPiIsMinus1 on 2010-05-31
I'm having the same problem. I find that activating anything on the menubar clears the issue. I don't even need to select a menu item, I can click on a menu and then dismiss it.

---

### Post by yazirian on 2010-07-12
Also experiencing this bug in a fresh 10.04 install.

My usage:
1) Edit something with emacs,
2) alt-tab to something else,
3) alt-tab back to emacs. Cursor will now be unresponsive.

Choosing a menu item works, and releases the cursor.

Frequency: often, but not always.

---

### Post by dyltman on 2010-08-04
> **yazirian said:**
> Also experiencing this bug in a fresh 10.04 install.

My usage:
1) Edit something with emacs,
2) alt-tab to something else,
3) alt-tab back to emacs. Cursor will now be unresponsive.

Choosing a menu item works, and releases the cursor.

Frequency: often, but not always.

My dad seems to have exactly the same problem, I was thinking it could be something gtk related.

---

### Post by R_Lopez on 2010-08-20
I have the exact same problem.

---

### Post by R_Lopez on 2010-08-20
I have the same problem.
10.4 and emacs 23.1+1-4ubuntu7

Have it on both an upgraded desktop and a new install of 10.4 on laptop.

---

### Post by eraaij on 2010-09-28
In follow-up to this, I did the following and this seems to have solved it so far: 

+ in ~/.gconf, rename or backup/  delete recursively all stuff here. This will effectively remove your desktop configuration.
+ Logout and Login again - new desktop config will be created.
+ Tweak as desired.

Coming from 8.x I have done a couple of updates over time. (always amazed that it all works relatively well), so this has perhaps introduced some config clutter over time. 

Can anyone confirm this ?

-Emile

---

### Post by David_rr on 2011-02-19
It doesn't work for me. I am having the exact same problem.
Ubuntu 10.10 with GNU Emacs 23.2.1 (i686-pc-linux-gnu, GTK+ Version 2.22.0).

Any other suggestions? I searched for a solution everywhere and can't find one...

---

### Post by David_rr on 2011-02-20
Bump :confused:

---

### Post by robobart on 2011-02-28
Having exactly the same problem...

I will try deleting my .gconf and report back.

---

### Post by robobart on 2011-03-01
Ah - 

deleting .gconf did not help. (It seemed to fix the problem for 10 min or so, but then the issue came back)

---

