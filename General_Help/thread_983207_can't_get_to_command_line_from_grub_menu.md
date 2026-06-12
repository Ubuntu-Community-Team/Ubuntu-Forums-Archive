---
title: "can't get to command line from grub menu"
date: 2008-11-15
forum: General Help
---

### Post by Cyan_Fire on 2008-11-15
Hey guys,

I was thinking about upgrading to Intrepid today, but I've had this problem with my grub menu for a while which I'd like to resolve first.

The problem is that on the grub menu, I can select an OS using the arrow keys and boot one using ENTER, but pressing 'e' or 'c' to edit an entry or drop to a commandline has no effect. I do not use a grub password.

Here is everything I have tried:
[LIST=1]
[*]Reinstalling grub.
[*]Manually recreating a menu.lst using update-grub.
[*]Setting a grub password. The grub menu said "press p to enter a password" but pressing p had no effect.
[/LIST]
None of these worked.

One more consideration, I use dvorak and have set my ttys to use dvorak as well as X, but I don't see how this would affect grub.

Any ideas?

---

### Post by LateNiteTV on 2008-11-15
specify runlevel 3 when booting.

---

### Post by Cyan_Fire on 2008-11-15
Huh? Do you mean by changing menu.lst? The problem isn't that I can't boot, it's that I can't edit the command line from the grub menu.

---

### Post by caljohnsmith on 2008-11-15
Do you maybe have your caps lock on? Also when you say you reinstalled Grub, did you just reinstall the Grub package? If so, you also need to run the grub-install command to update all the Grub boot files in /boot/grub. If your drive is sda for example, you would do:
```
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
And do that while you are booted into Ubuntu (not from a Live CD). That should update your Grub files and reinstall Grub to the MBR (Master Boot Record), and that might fix your problem. Let me know how it goes. :)

---

### Post by Cyan_Fire on 2008-11-15
Well, this is weird. I didn't have caps lock on, but I tried it *with* caps lock on and guess what... it worked! Thanks for your help!

So, new problem: why is caps lock "reversed" for my grub?

---

### Post by caljohnsmith on 2008-11-15
> **Cyan_Fire said:**
> Well, this is weird. I didn't have caps lock on, but I tried it *with* caps lock on and guess what... it worked! Thanks for your help!

So, new problem: why is caps lock "reversed" for my grub?
If your keyboard functions normally after you boot into Ubuntu, I'm not sure why it wouldn't function normally on start up. My only guess might be if you can some how configure your keyboard differently in your BIOS, but that's not likely. At least you found a workaround though; cheers and have fun. :)

---

