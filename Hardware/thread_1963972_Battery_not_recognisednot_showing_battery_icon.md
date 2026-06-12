---
title: "Battery not recognised/not showing battery icon"
date: 2012-04-23
forum: Hardware
---

### Post by carys on 2012-04-23
My battery is in perfect working order. It charges as it should and the laptop runs fine when the laptop runs off the battery. I've had Ubuntu 11.10 since it was launched and the battery icon has always been on the top bar.
However, yesterday it disappeared. I cannot tell what percentage battery I have left anymore. Even when I open up the power application in the system settings no information is displayed.
I've tried uninstalling/installing the battery icon with[INDENT]   sudo apt-get purge indicator-power
      sudo apt-get install indicator-power


 [/INDENT]..but it doesnt solve the problem.

I've also downloaded a battery monitor called barmon from the software centre and that doesn't show any information about the battery.
Changing the theme does nothing either.

I have a samsung rv510 laptop running a dual boot of ubuntu 11.10

Also, the battery display works perfectly in windows by showing the percentage power left and whether its charging or not.

Please help if you can


SOLVED

Realised that the last thing I changed on ubuntu was an issue with changing the screen brightness. I undid my last action and the laptop returned to normal. Then found another solution to the brightness issue here
[http://linuxon1001p.blogspot.co.uk/2010/03/fixing-brightness-controls.html](http://linuxon1001p.blogspot.co.uk/2010/03/fixing-brightness-controls.html)
Everything works perfectly now :)

---

### Post by carys on 2012-04-23
Ha now the sound doesn't work..lovely.

---

