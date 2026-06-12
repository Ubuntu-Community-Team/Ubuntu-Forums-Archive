---
title: "x crashes when loading any game or video"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by corstar on 2006-04-19
Hiya, 

I have managed to get ubuntu to recognise my ati card and now displays the correct "fglrxinfo"

corstar@toshiba:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9000/9100 IGP Series DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

But, every time I start any basic game that doesn't require accelleration, the whole system crashes. I can't even ctr+alt+backspace. I have to restart the laptop, which really gets me.

Is there a driver missing or a command I should enter to fix this problem??

---

### Post by gondilon on 2006-04-20
check your xorg.conf file in /etc/x11 to see if in the section that id's your card the option noaccel is in there. if it is not, add it at the end of the section.

---

