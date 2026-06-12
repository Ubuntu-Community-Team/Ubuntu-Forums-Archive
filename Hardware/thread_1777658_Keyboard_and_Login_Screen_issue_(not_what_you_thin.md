---
title: "Keyboard and Login Screen issue (not what you think)"
date: 2011-06-08
forum: Hardware
---

### Post by Remshot on 2011-06-08
Hi, recently I migrated Wubi to its own partition, everything worked fine, couldn't have been more satisfied.

This morning I boot up my computer, and when I get to the Ubuntu login screen, there is no input from the keyboard, and I cannot enter the password. All the lights such caps lock work, I can use the keyboard in the BIOS, Grub, and Windows 7.

I have read all other threads relating to this topic and:
[LIST]
[*]I have tired the USB legacy thing in the bios, does not work.
[*]I have tried the on screen keyboard, does not work.
[*]I have tried switching languages and keyboad layouts, does not work.
[*]I have rebooted my computer many times, also does not work.
[/LIST]

I am running 11.04 64 bit on an HP G62. Any help would be greatly appreciated, I would really like to continue using Ubuntu, but if I can't login, I'm not sure I can do that.

---

### Post by Remshot on 2011-06-08
Some further information:

I can still use the keyboard in recovery mode. Is there anything I can do there to fix it?

---

### Post by Rei_Theta on 2011-06-10
Im having the same problem :/, with no luck. Have you tried other keyboards?

---

### Post by chiefrocka on 2011-06-25
Same here just stopped working yesterday after a reboot. Keyboard works perfect on other operating systems. If I boot into recovery mode, keyboard works fine too. It's only during the normal boot process at the login screen that the keyboard stops working. If I smash all the keys, sometimes I'll get one or two characters to come out but I don't really know a good way to reproduce it. I've applied all of the recent package updates but still same problem.

On-screen keyboard doesn't work either.

I'm running Ubuntu 11.04 64-bit.

---

### Post by chiefrocka on 2011-06-25
I've discovered something weird for my case: long key presses work. If I hold the 'e' key for example, I see the character being printed. If I only press the 'e' key once, nothing happens.

---

### Post by chiefrocka on 2011-06-25
Update:

After long pressing the characters of my password (even shift requires a long press) I was able to log in. Once logged in everything works fine. Typing in any application works normally.

So it seems that the issue concerns only the login screen. Long pressing the keys (even modifier keys) works.

To those more familiar with the login application: is a different keyboard layout used to take input from the keyboard or something?

---

### Post by grahammechanical on 2011-06-25
Have you tried loading the Keyboard utility? There is an Accessibility tab with a tick box called Only accept long keypresses. Perhaps it got checked somehow.

Regards.

---

### Post by chiefrocka on 2011-06-25
You nailed it! I probably was trying to wake the computer by clicking randomly and somehow got all three clicks to turn on this feature.

Not sure if a UI improvement can be made here. Perhaps visual indication that some accessibility feature is enabled or something?

---

