---
title: "keypad issues"
date: 2010-01-12
forum: Hardware
---

### Post by Korwynz on 2010-01-12
I have a Dell Inspiron 1501 and i just installed Ubuntu 9.10 a few days ago with not a single problem.  but now all of a sudden i am having issues where when i type something with the laptop keyboard it spits out numbers where letters should be.  right now i have a usb keyboard hooked in and it seems to obviously do the trick.  but i cant cart around a large keyboard with me everywhere.. please help :)

---------------------------------------------------------
[COLOR="Red"]Problem has been solved.  I'm such an idiot... somehow my number lock function was activated and never noticed.  but if anyone else with a laptop ever gets this issue.  check to make sure your number lock is off because on laptops the number pad is function on the letter keys :)[/COLOR]

---

### Post by quixote on 2010-01-13
That's classic, and it's happened to *everybody*.  Don't feel bad. :D

(By the way, as the original poster, you can mark this "solved" on the dropdown menu under "Thread Tools")

---

### Post by JosephGarrison on 2010-01-13
My keyboard is having issues too, not this one though. The up,down, and right arrows do not work like they should. For example, in open office, if I type the word moo, then go left behind the last "o", that works but trying to go back to the right of it, or moving up or down a line does not. How do I configure that? I know the keys work because I can still control the volume and screen brightness with them when I hold Fn.

---

### Post by garvint on 2010-04-14
OpenOffice.org Writer Doesn't Respond to Arrow Keys, Others
Hello,

I'm having a problem with OpenOffice.org Writer and Crossover MS word. While I was typing, many of the keys on the keyboard suddenly stopped working.

The keys that don't work now are Backspace, the arrow keys, Insert, Home, End, Page Up, and Page Down. Neither the dedicated keys nor the switched keys on the numeric keypad function.

These keys all work everywhere else in Ubuntu - the other OpenOffice.org modules, Firefox, gEdit, and even the menus and dialogs in OpenOffice.org Writer. The keys don't work in any document, and rebooting doesn't solve the problem.

In a previous post some suggest to remove the profile, how is this done?

---

### Post by quixote on 2010-04-14
That's a hidden directory in your home directory, which you can see in Nautilus (=file manager) by going to View and ticking "Show hidden files".  Reload (Ctrl-R).

The openoffice settings are in .openoffice.org3 (assuming you're using OOo3).  I don't know if it's being suggested that you have to delete the whole thing.  That would mean you have to re-do every single setting you've changed.  If it's the only way to fix the keyboard, it's worth it.  But otherwise....

If you look around in that directory, there's some subdirs that look directly keyboard related.  (Eg.: /home/quixote/.openoffice.org3/user/config/soffice.cfg/global/accelerator/en-US)  If you have a lot of customized settings, it might be worth just deleting some of those and see if that deals with it??

---

