---
title: "Mouse works only after logging out and back in again"
date: 2012-05-26
forum: Hardware
---

### Post by Oromis32 on 2012-05-26
Hi all,

I just installed Ubuntu 12.04 LTS on my desktop PC. Then I installed KDE because I prefer KDE to the default Desktop. 

But then my mouse started to behave strangely:
When I initially log into my account after system startup, I can onky use some of the UI controls (for instance, I can click the K-Menu button but I cannot use any of the elements in the K-Menu, rendering it completely useless. Pretty much all I can do is pressing [Ctrl]+[Alt]+[Del] and wait the 30 seconds to log out since the dialog's controls are also unclickable.

When I log back in again (without rebooting), everything is back to normal. All UI controls work as expected.

Hardware information:
Mouse is a Cyborg R.A.T.5 Mouse. I already set it's button mapping in the xorg.conf file:
```
Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitec Cyborg R.A.T.5 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 0 0 0"
EndSection
```

It obviously has something to do with this particular mouse. When I attach any other mouse, everything works normally without logging-out and back in again.
This problem also appeared on a previous KUbuntu installation (Was the reason to abandon it). 

Thanks in advance for any advice

Oromis

PS: Sry for my english, it's not my native language.

---

### Post by Shelty on 2012-07-03
Hello, Oromis!

I should say that you're non alone :)

I have absolutely the same issue. My mouse is a little bit different - Cyborg R.A.T.9 (wireless)

After the first load it only able to move the cursor.

Then, it start working only when I do "KDM service stop/start". After that it works just perfectly, even additional buttons... but still, after every system start I need to do the same thing.

A little bit annoying, especially if keep in mind that I have a Saitek keyboard, which is also able to switch "Ctrl+Alt+F1" only after 6-7 attempts.

So I'm really interested as well in how to deal with the problem.

Any help would be appreciated!

P.S. I want to appologize for my grammar, English is not my native language as well

---

