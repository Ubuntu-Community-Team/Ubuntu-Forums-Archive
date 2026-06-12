---
title: "Numerical keypad doesn't work w/8.04"
date: 2008-04-24
forum: Hardware
---

### Post by bcardarella on 2008-04-24
Just upgraded. Everything seems to work fine with the exception of my numerical keypad. The hardware is OK, I can see that it is producing output with the xev command, an it's not the numlock key.

I checked my xorg.conf file and that didn't seem to change for my keyboard layout. I'm guessing that the new version of Gnome is overriding something. (as Gnome LOVES to do... but I could be wrong) Any ideas?

---

### Post by bcardarella on 2008-04-24
Nevermind, I guess the accessibility option got turned on that had the numerical keypad control the mouse. I shut it off and everything works perfectly.

For those looking:

System/Preferences/Assistive Technologies/Keyboard Accessibility/Mouse Keys

and just turn it off

---

### Post by msegmx on 2008-06-17
thanks for ur answer man, i was pretty dissapointed until i found ur thread. thanks 2 google too :D

---

### Post by abazoskib on 2009-07-17
just posting because the same thing happened to me. this is a bug in one of the updates because i definitely didn't turn this option on.

---

### Post by Giggity on 2009-07-21
Thanks for sharing your experience.  Same thing happened to me with 9.04, but knowing what happened helped me solve it quickly.

---

### Post by Trylmand on 2009-07-30
Thank you, solved my problem !

---

### Post by stolsvik on 2010-01-13
(Too bad there aren't any "Thanks!" button here)

Thanks!

I know for absolute certain that I have never consciously enabled this - so either it have happened "by itself" for some stupid reason, or I have hit some stupid key-combo ******** that enabled it. In any case, it is completely absurd, and such a feature should not turn itself on by chance, and there should not be a key-combo enabled by default. Basically if such a key combo exists and is enabled by default, it boils down to being a "destroy numeric keypad without user knowing what the **** happened" hidden hotkey.

---

### Post by pararoly on 2010-01-15
same prob. fixed. thanks :-)
roland

---

### Post by jayshomebrew on 2010-01-29
Fixed my problem too in ubuntu 8.04. one of the updates must have changed it. I thought it was my MS Office keyboard..


[IMG]http://img46.imageshack.us/img46/3558/screenshotkeyboardprefe.png[/IMG]

---

### Post by angelot on 2010-02-21
I had this issue with 9.10 too. Thanks for the tip - it solved my problem.

---

### Post by meklu on 2010-03-02
Thank you very much! Same happened to me in Karmic.

---

### Post by HunkTB on 2010-03-05
Same happened when I upgraded from Karmic 09.10 to alpha lucid 10.04; the update must somehow  change the configuration.
Thanks: this post show me how to solve it

---

### Post by TakensM on 2010-04-14
Thanks a lot , i had this problem too in version 9 , i almost got used to it but now it is solved ! thanks a lot for this post

---

### Post by gabrielqs on 2010-05-28
Same happened here, on lucid lynx.

---

### Post by emecas on 2010-06-03
Thanks for your post.... it also works for 10.04 , problem solved

EmeCas

---

### Post by mobidyc on 2010-06-20
Thanks,

you made my day :popcorn:

---

### Post by The Minder on 2010-10-09
Dude... you are brilliant.

I was playing poker online and some idiot cracked my AA with K9... I got frustrated and hit the keyboard/keypad a couple of time.   Moments later my keypad stopped working and I assumed I had broken something.   Quick trip to the store, buy a new keyboard, home and reboot my computer and the damn keypad STILL didn't work.

A quick Google and I found this thread.   Somehow, the combination of keystrokes I triggered when I stomped the keyboard turned this function on.

Thanks heaps mate. :)

---

### Post by bonesTdog on 2010-10-09
> **bcardarella said:**
> Nevermind, I guess the accessibility option got turned on that had the numerical keypad control the mouse. I shut it off and everything works perfectly.

For those looking:

System/Preferences/Assistive Technologies/Keyboard Accessibility/Mouse Keys

and just turn it off
Worked perfectly for Lucid Lynx.  Thanks!  An easy quick solution for an annoying problem!

---

### Post by zelalem on 2010-10-25
Thanks a lot. It solved my problem as well.

---

### Post by shoualacoder on 2010-10-27
Thanks lot for sharing your experience, i had the same issue since months.
My problem is solved on Ubuntu 10.04.

---

### Post by allxk on 2011-02-21
> **bcardarella said:**
> Nevermind, I guess the accessibility option got turned on that had the numerical keypad control the mouse. I shut it off and everything works perfectly.

For those looking:

System/Preferences/Assistive Technologies/Keyboard Accessibility/Mouse Keys

and just turn it off


Thank you! Its working!

---

### Post by ctothej on 2011-05-21
I am still having this issue with 10.10! It reverts back to mousekeys enabled every now and then all by itself. Soo frustrating.

---

### Post by schmoe76 on 2011-05-26
> **ctothej said:**
> I am still having this issue with 10.10! It reverts back to mousekeys enabled every now and then all by itself. Soo frustrating.

Yes, me too.  I never remember the fix.  I always have to google for this thread.

My question is - what is causing Ubuntu to continually revert back to "Pointer can be used to control the keypad" mode?  

I have a hard time believing that Canonical would purposefully and continually set the keypad to a mode that is non optimal for the vast majority of users.  That would be like continually resetting the keyboard layout to dvorak.

There must be some combination of keys that is triggering this mode.  Something that we all are unintentionally typing.

---

### Post by MrHara on 2011-10-24
Thx, This helps also for me (10.04). Questions is really why/ how this happend? I'm 100% sure I have never set numpad be like mouse control? could it be some apps which do so?

---

