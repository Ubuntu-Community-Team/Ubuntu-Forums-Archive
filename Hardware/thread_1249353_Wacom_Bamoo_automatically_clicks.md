---
title: "Wacom Bamoo automatically clicks"
date: 2009-08-25
forum: Hardware
---

### Post by timmevandermeer on 2009-08-25
Hello,

I run Linux Mint 7 32bit
I have a problem with my wacom bamboo tablet. It should work out of box, but when I´m moving the pen above the tablet it thinks I´m clicking. For example, on the desktop it creates a selection-square, while I'm not touching the tablet at all. The back of the pen(eraser) works well.
So I think the problem has something to do with the mapping of the functions. Anyone knows how to fix it? I also tested it on an Ubuntu 9.04 pc. I had the same problem with windows 7, but there are no official drivers for win 7. I will also try to test on windows xp.

sorry for my bad English

thanks
Timme

---

### Post by Favux on 2009-08-25
Hi timmevandermeer,

It sounds like you may have the stylus set to "hover" mode.  Type 'wacomcpl' in a terminal.  When the gui pops up select 'stylus' and then 'Tool Buttons'.  In 'Tool Buttons' change 'Side Switch Mode' from "Side Switch Only" to "Side Switch + Tip".

You have to have 'wacom-tools' installed from Synaptic Package Manager.  It has to be the same version, 0.8.2-2 linuxwacom I think, as the already installed xserver-xorg-input-wacom.  If not install it and reboot.

If there is still no response from 'wacomcpl' in a terminal try entering:
```
xsetwacom list
```
The output should be stylus, eraser, cursor (if you have the Wacom mouse), and pad.  If it is blank that's why 'wacomcpl' won't work.

That's a problem with how the 10-wacom.fdi is parsing the names being returned by HAL.  To see what HAL is calling things enter:
```
xinput --list
```

A modified 10-wacom.fdi that parses the names correctly is in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

---

### Post by timmevandermeer on 2009-08-26
Thanks for the help, but after following the instructions, the problem still appeared. Also the hover settings already were correct. The tablet has worked well for a few minutes before I followed the instructions, and the same problem occured in Win7. I think it´s broken since it works sometimes. I will return it to the store. I bought it only a few weeks ago, but my sister smashed on it, no too hard, but it might have been anough to break it.

thanks for helping me
Timme

---

### Post by KolorGuild on 2009-12-11
I have the same issue with my Genius Mousepen. How can I fix this problem?

---

