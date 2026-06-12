---
title: "Help configuring monitor"
date: 2008-11-25
forum: Hardware
---

### Post by rv53705 on 2008-11-25
My monitor got crashed, so i friend gave me his old one, but when i started Ubuntu 8.10, it told me that the monitor profile (or something like that) was wrong, i clicked on reconfigure, but nothing happens, the screen gets black and i gotta restart.

This doesn't happen on Windows (i have Ubuntu with Wubi).

---

### Post by upchucky on 2008-11-25
if it is nvidia look here

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)


if card is others try envy.

you may be able to use the xorg.conf backup it created on the original install this should get you up with a bare bones display

if you have the disk you used to install put it in and see if the new monitor works, if it works then editing the xorg file will fix the problem.

if you do not have the install disk for your system, booting with the live Knoppix disk will let you edit the file

search here for xorg file you can probably find a copy of one that will work for your sys.

---

### Post by rv53705 on 2008-11-25
I run the Ubuntu 8.10 LiveCD, and started but gave me the same error:

```

Ubuntu is running in low-graphics mode.

The following errors was encountered. You may need to update your configuration to solve this.

(EE) SAVAGE(O): No valid modes found
(EE) Screen(s) found, but none have a usable configuration

[RIGHT][AN OK BUTTON, PRESSED BY ME][/RIGHT]


```

```

What would you like to do?

[LIST]
[*]Run Ubuntu in low-graphics mode for just this session
[*]Reconfigure graphics
[*]Troubleshoot the error
[/LIST]
[RIGHT][TWO BUTTONS, CANCEL AND OK, I CHOSE #1 AND PRESSED OK]
[BEFORE (NO LIVE CD, ON MY INSTALATION) I CHOSE #2 AND THAT'S THE PROBLEM I HAVE NOW][/RIGHT]

```

```

Stand by one minute while the display restarts...
[RIGHT]
[AN OK BUTTON, PRESSED BY ME][/RIGHT]

```

At this point, screen gets black and nothing happens, i gotta restart and come back to Windows.

I've not tried xorg.conf.

---

