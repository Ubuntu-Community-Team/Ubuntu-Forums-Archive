---
title: "lms data keyboard k9014 - I can't find get a pound sign"
date: 2016-09-14
forum: Hardware
---

### Post by naomibrown on 2016-09-14
Hi,

I've just bought a lms data keyboard k9014 and I'm trying to type the British pound sign, but am unable to do so. I can see it on the keyboard with the number 3 but can't get it to work.

I've tried:

ctrl alt 3
shift 3
alt gr 3

Any ideas?

Thanks,
Naomi

---

### Post by him610 on 2016-09-14
Recommend you refer to an ASCII Code Table [http://www.ascii-code.com/]("http://www.ascii-code.com/")
Find the code that represents the British Pound sign and Euro sign.
Put them both on separate lines in a text (use Gedit, nano, etc)  file, save it, remember where you saved it.
Whenever you need it in the future, just open the file, and copy & paste the ASCII code for your sign.

I have not used this method for British pound, but I have used this method for other symbols in the past.

You might try this site also... [http://superuser.com/questions/293119/how-to-type-pound-sign%C2%A3-using-us-keyboard-in-windows-linux-and-mac]("http://superuser.com/questions/293119/how-to-type-pound-sign%C2%A3-using-us-keyboard-in-windows-linux-and-mac")

Another link... [https://ubuntuforums.org/showthread.php?t=1964422]("https://ubuntuforums.org/showthread.php?t=1964422")

Good luck.

---

### Post by ajgreeny on 2016-09-14
Which keyboard layout are you using? You may be able to find the normal keypress needed for the £ with a search of "us keyboard layout GB Pound" or whatever layout you use.

Google suggests "control-shift (hold down) type u00a3" which works for me even though I don't need it (using UK layout here in UK) but it does add two superfluous )) before the £.  I think that unicode  system is totally independent of your layout.

---

### Post by naomibrown on 2016-09-14
Hurrah! I've got a pound sign!!! £ :) 

I found that I have to use NumLock first and use just the numbers on the number pad when I'm typing in u00a3. I hadn't realised that was the case :D

Under input sources it says English(UK). On the keyboard I do have the @' the wrong way around when I'm typing compared to the key I'm pressing, which is confusing me.

---

### Post by ajgreeny on 2016-09-14
If you are using a UK keyboard layout you should have Shift+3 (along the top of the keyboard, not numpad 3) for the £; that is where it is on UK layout.

---

### Post by naomibrown on 2016-09-16
When I press Shift+3 I get a #. This is the case for both Shift keys. On the physical keyboard there is a £ sign above the 3 (along the top of the keyboard). 

That's what started confusing me in the first place :(

---

### Post by ajgreeny on 2016-09-16
> **naomibrown said:**
> When I press Shift+3 I get a #. This is the case for both Shift keys. On the physical keyboard there is a £ sign above the 3 (along the top of the keyboard). 

That's what started confusing me in the first place :(
That suggests you have a US keyboard layout but the hardware is not US but something else.
Where is your @ sign shown on the keyboard and what keys actually produce it for you?

---

### Post by naomibrown on 2016-09-16
The @ sign on the physical keyboard is next to Return but in order to get an @ symbol I have to use Shift-2 which on the physical keyboard has ".

---

### Post by ajgreeny on 2016-09-16
Yes, it seems you have a UK keyboard (ie, the hardware) but are using the US keyboard layout in spite of the system showing the UK layout.

Somewhere in system settings you should find a way to change the layout you are using, if that is what you want to do. As it is not conforming with the settings shown it may be worth changing it to something else and then back again to UK to see if that changes it for you.

Of course, if you only needed the £ sign that one time, you may not need to change anything; it's your choice.

---

### Post by naomibrown on 2016-09-17
Fixed :) 

I changed it to US layout, typed a few things then changed it back to UK layout and it now has a UK layout as normal (i.e. I can get a £ sign by pressing Shift-3).

I thought I'd done this before to try to fix it, but obviously not ...

---

