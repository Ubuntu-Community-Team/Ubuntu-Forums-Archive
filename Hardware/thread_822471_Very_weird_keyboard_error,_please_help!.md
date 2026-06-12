---
title: "Very weird keyboard error, please help!"
date: 2008-06-08
forum: Hardware
---

### Post by picpak on 2008-06-08
For some reason lately, my computer won't correctly type the number 3...each time, it comes up as 32 or 23. I make very sure that I'm not hitting the 2 button, but it still happens. Here's the kicker, however: my password has a 3 in it, and it's impossible to correct what I typed!

I uninstalled scim a while back; would that have anything to do with it? How do I reinstall it if I can't use my password?

---

### Post by bwhite82 on 2008-06-08
Firstly, are you able to narrow it down to hardware or software? Do you have a Windows installation on the same machine? Does the keyboard do the same in Windows?

---

### Post by picpak on 2008-06-08
It's a keyboard that's worked perfectly for the past 8 years. It happens in every program. I have Windows XP installed under VirtualBox, but the VirtualBox service isn't running. And I can't get it running because I CAN'T TYPE IN MY PASSWORD. Ugh!

---

### Post by picpak on 2008-06-08
Well, thanks to [this guide](https://help.ubuntu.com/community/LostPassword), I managed to get a new password. However, I ending up breaking VirtualBox trying to see if it worked (found the XP ISO file, didn't think I needed it, deleted it and emptied trash), so no help there. And now, out of nowhere, my sound quits working. I swear, it's like 2005 all over again.

---

### Post by chochem on 2008-06-08
Uhm first off... Couldn't you change the password by booting into recovery mode , then changing your primary user's password with 'passwd [name of primary user]' ? At least you'd be able to use sudo while fixing the main problem :)

EDIT: Dammit, beat me to it... No cookie then, I guess? ;)

---

### Post by picpak on 2008-06-08
> **chochem said:**
> Uhm first off... Couldn't you change the password by booting into recovery mode , then changing your primary user's password with 'passwd [name of primary user]' ? At least you'd be able to use sudo while fixing the main problem :)

EDIT: Dammit, beat me to it... No cookie then, I guess? ;)

That's fine and dandy for my password and all..but I still can't type 3 correctly.
.

---

### Post by chochem on 2008-06-08
Right... Maybe delineating whether it's an X or not an X thing might be good? Have you tried outside of X, e.g. the text terminals (ctrl+alt+F1-6)?

---

### Post by picpak on 2008-06-08
> **chochem said:**
> Right... Maybe delineating whether it's an X or not an X thing might be good? Have you tried outside of X, e.g. the text terminals (ctrl+alt+F1-6)?

It happens in the consoles, too. I know that because when I followed that guide I had to fix up typing "init 3", lol.

---

### Post by chochem on 2008-06-08
Dang :| Well then it certainly soudsn liek a hardware issue... I spilt a bowl of cereal into my old laptop once and it took a lot of typing before the keys started working independently again... But to test if it is your system why not just shove in an installation cd and boot using that?

---

### Post by picpak on 2008-06-08
Well, I found a psuedo-solution: turn on Numlock and use the 3 on the side. :mrgreen:

---

### Post by chochem on 2008-06-08
Haha... I actually thought of that but figured you would have dismissed it with "Don't you think I've tried that!!!????" :D

---

### Post by picpak on 2008-06-08
LOL, well now I know it's the keyboard's problem...I thought maybe the kernel upgrade or something else may have screwed it up.

Thanks for dealing with my stupidity! :lolflag:

---

### Post by chochem on 2008-06-08
Don't mention it :)

---

