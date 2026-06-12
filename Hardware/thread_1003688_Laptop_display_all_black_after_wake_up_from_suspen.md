---
title: "Laptop display all black after wake up from suspend"
date: 2008-12-06
forum: Hardware
---

### Post by Fzang on 2008-12-06
Laptop on 8.10 suspends just fine but when I wake it up again all I get is a black display and I have to hard reset...

Any solutions? Graphics drivers are installed and works and it also detects my battery

---

### Post by utnubuuser on 2008-12-06
Did you try any of the F1- F15 buttons to wake up the screen?  How about ctrl+F1 - F15,
or similar?  ctrl+alt+F1-F15?
Isn't hybernate/suspend usually Funtion+F4 or something along those lines?

---

### Post by Fzang on 2008-12-06
My suspend shortcut is Fn+F1

I'll try those things tomorrow

---

### Post by Fzang on 2008-12-07
Bump!

Tried pressing everything in every possible way but it ain't starting!

Is there really nothing I can do?

---

### Post by Fzang on 2008-12-07
Bump! This is very important as I want to use this laptop for school and suspend is a must

---

### Post by raul_ on 2008-12-07
Maybe it's not supported. 

Check 
[https://wiki.ubuntu.com/LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam")

---

### Post by Coombabah on 2008-12-07
> **Fzang said:**
> Laptop on 8.10 suspends just fine but when I wake it up again all I get is a black display and I have to hard reset...

Any solutions? Graphics drivers are installed and works and it also detects my battery

Suspend was working well on 8.10 until a recent update.

I now get the same black screen.

Using Ctl+Alt+Backspace to restart xwindows is quicker than rebooting for now.

edit: Rebooted to the previous kernel 2.6.27-7-generic

The issue is still there. 

I tried Ctl+Alt+F7 and this wakes up xwindows so there is a better workaround than killing X or rebooting.

---

### Post by Fzang on 2008-12-08
So I can kill X to get screen back?

Also, the manufacturer (Zepto) states that the computer is fully supporting 8.04 with the exception of webcam..

Would it be wise to downgrade?

---

### Post by Coombabah on 2008-12-09
> **Fzang said:**
> So I can kill X to get screen back?

Also, the manufacturer (Zepto) states that the computer is fully supporting 8.04 with the exception of webcam..

Would it be wise to downgrade?

Killing X puts you back at the login screen.

I've had varying wake from suspend issues in the last few days.

Today it was hard to wake and when it finally woke from suspend there wasn't the usual password prompt to unlock the screensaver.

When I try switching with ctrl+alt+F2 ctrl+alt+F7 etc I can't get back to X without ctrl+alt+backspace.

When I installed 8.10 suspend was one of the things that impressed me as working well.

I don't which update killed suspend but it was fairly recent.

booting an earlier kernel didn't make any difference

Until this bug is fixed a quick and nasty workaround might be to save your work before suspending and just killing X with ctrl+alt+backspace if it's sleeping so soundly that it won't wake up again.

Wonder if there is anything in launchpad about this?

---

### Post by eldragon on 2008-12-09
if only your backlight isnt working...... (capslock led still works)..

then switch to a virtual terminal and back, that should bring your laptop back to life..

to do that: CTRL ALT F1
then: CTRL ALT F7

good luck

---

### Post by Coombabah on 2008-12-09
> **eldragon said:**
> if only your backlight isnt working...... (capslock led still works)..

then switch to a virtual terminal and back, that should bring your laptop back to life..

to do that: CTRL ALT F1
then: CTRL ALT F7

good luck

That worked for me yesterday but not today and I've noticed some more bugs.

Just tried CTRL ALT F1
then: CTRL ALT F7

After CTRL ALT F1 the usual login prompt

After CTRL ALT F7 There was an underscore at the top left of the screen

ctrl+alt+backspace just echoed some characters on the screen instead of killing X

ctrl+alt+del rebooted

Something has upset X recently and X's behaviour is a bit unpredictable even without trying to suspend.

I wonder if this affects everyone or just a combination of hardware or software?

---

### Post by Fzang on 2008-12-10
If I kill X my screen flickers a bit and goes even more black than before and I still have to hard reset :o

---

