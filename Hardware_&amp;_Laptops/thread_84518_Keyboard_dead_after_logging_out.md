---
title: "Keyboard dead after logging out"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by oliwally on 2005-10-31
I've noticed that if I log out of Kubuntu Breezy, it frequently happens that my keyboard does not respond at all when I try to log back in. I cannot type in my password and therefore have to reboot. Any ideas anyone?

---

### Post by LorenzoD on 2005-10-31
Odd. Not happening here, but I'm running Ubuntu with KDE 3.5 beta 2 packages. 

A few questions: first of all, what type of keyboard do you have? Second, is the entire keyboard dead, or can you CTRL+ALT+Backspace? In that case you may want to try CTRL+ALT+F1, log in (assuming the keyboard works there) and do some snooping around in places like dmesg.

---

### Post by oliwally on 2005-11-01
[QUOTE=LorenzoD]Odd. Not happening here, but I'm running Ubuntu with KDE 3.5 beta 2 packages. 

A few questions: first of all, what type of keyboard do you have? Second, is the entire keyboard dead, or can you CTRL+ALT+Backspace? In that case you may want to try CTRL+ALT+F1, log in (assuming the keyboard works there) and do some snooping around in places like dmesg.[/QUOTE]
Thanks for helping out LorenzoD.
> what type of keyboard 
It's an Xsonic keyboard. Hasn't let me down so far. Logging in and out worked fine in Hoary.
> is the entire keyboard dead
Yes, the entire keyboard is dead. None of the keys produce an input in the password field, nor do the Tab or arrow keys allow any navigation. I can still turn NumLock and CapsLock on and off on the keyboard, but it has affect other than the lights coming on and off on the keyboard. The CTRL+ALT+Backspace and CTRL+ALT+F1 don't work either.

I have to restart the computer to log back in - then the keyboard works.
> snooping around in places like dmesg
I have no experience with dmesg and would need some help please to further diagnose and fix the problem.

---

### Post by oliwally on 2005-11-02
bump

---

### Post by teaker1s on 2005-11-02
have you tried changing the keyboard type in settings I'm running a wireless keyboard and had various problems until I tried the options similar to the keyboard and found that my keyboard is nearest to a microsoft internet keyboard and customised the buttons that didn't work with shortcuts.
other than that maybe someone else can suggest something

---

### Post by oliwally on 2005-11-02
[QUOTE=teaker1s]have you tried changing the keyboard type in settings I'm running a wireless keyboard and had various problems until I tried the options similar to the keyboard and found that my keyboard is nearest to a microsoft internet keyboard and customised the buttons that didn't work with shortcuts.
other than that maybe someone else can suggest something[/QUOTE]

Hmm....I can't find any options to configure the type of keyboard I have. Isn't there a hardware browser in KDE that lets you fiddle with choosing specific brands/types of hardware? 
I'm still not convinced that this is the problem since it was fine in Hoary.

---

### Post by oliwally on 2005-11-04
bump ;)

---

### Post by oliwally on 2005-12-10
> I've noticed that if I log out of Kubuntu Breezy, it frequently happens that my keyboard does not respond at all when I try to log back in. I cannot type in my password and therefore have to reboot. Any ideas anyone?
Does anyone have a solution to this problem?

---

### Post by oliwally on 2005-12-13
[QUOTE=oliwally]I've noticed that if I log out of Kubuntu Breezy, it frequently happens that my keyboard does not respond at all when I try to log back in. I cannot type in my password and therefore have to reboot. Any ideas anyone?[/QUOTE]


I have just upgraded to kde 3.5 and the problem seems to have disappeared.

---

