---
title: "Blank screen on when resuming from suspend"
date: 2008-04-25
forum: Hardware
---

### Post by FreakyT on 2008-04-25
I'm using an HP tx1000z, and, while almost everything works, suspend only partially works.

While the laptop suspends properly, when it is woken up, the screen stays black.  (The backlight turns on, however.)  Interestingly, while Caps-lock still responds, nothing else does, and I can't Ctrl-alt-backspace or console-switch my way out.

I also tried this:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Any ideas?

Thanks!


I posted about this sort of issue once before:
[http://ubuntuforums.org/showthread.php?p=4776365](http://ubuntuforums.org/showthread.php?p=4776365) (though the forum it was in is now closed) but didn't really get anywhere.

---

### Post by EricDB on 2008-04-27
I get the same thing, but it's only about 1 in 10 resumes.  Otherwise it works.  But when I get the BSOD (Black Screen Of Death), the computer doesn't respond to anything--Ctrl-F1, Ctrl-F7, Ctrl-Alt-Backspace, or the power button (unless I hold it 4 seconds to turn the computer off).

---

### Post by acron1 on 2008-04-27
> **FreakyT said:**
> I'm using an HP tx1000z, and, while almost everything works, suspend only partially works.

While the laptop suspends properly, when it is woken up, the screen stays black.  (The backlight turns on, however.)  Interestingly, while Caps-lock still responds, nothing else does, and I can't Ctrl-alt-backspace or console-switch my way out.

I also tried this:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Any ideas?

Thanks!


I posted about this sort of issue once before:
[http://ubuntuforums.org/showthread.php?p=4776365](http://ubuntuforums.org/showthread.php?p=4776365) (though the forum it was in is now closed) but didn't really get anywhere.

Try Ctrl-Alt-F1 followed by Ctrl-Alt-F7 and if that helps.
Good luck.

---

### Post by NastyT23 on 2009-08-27
has anyone found a fix for this issue yet? I'm running jaunty and this still happens to me every now and then...

---

### Post by JohnFr on 2009-12-11
> **FreakyT said:**
> I'm using an HP tx1000z, and, while almost everything works, suspend only partially works.

While the laptop suspends properly, when it is woken up, the screen stays black.  (The backlight turns on, however.)  Interestingly, while Caps-lock still responds, nothing else does,


I have a similar issue with Ubuntu NBR on a HP 110-1125. 

BUT, I have discovered it is only the screen which has been totally
dimmed.  If I press the screen brightness key (fn F4 for me) it fixes
the problem. I also think one can wait a few seconds for the dialog box
asking for a password to come up and then enter the password

---

