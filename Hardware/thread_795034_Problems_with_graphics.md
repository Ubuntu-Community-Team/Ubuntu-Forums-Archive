---
title: "Problems with graphics"
date: 2008-05-15
forum: Hardware
---

### Post by vvule on 2008-05-15
Few days ago I've bought a new Monitor - Samsung 943N (LCD 1280x1024), and changed the monitor setting at the nearest match to my new Monitor (940 N) as there was no option to choose the exact model. After this stupid move, I'am experiencing some wierd problems. First the picture was a real mess, that I couldn't see anything on te screen. Than I followed the advice the one member of this forums gave me. I've entered 
**sudo dpkg-reconfigure xserver-xorg -phigh **and choose the VGA option, even though the default option was VESA. Afterwards, I got the message UBUNTU IS RUNNING IN LOW GRAPHICS MODE just before the loging screen. Well now I could see the desktop clearly, but the resolution was 800x600, and the higher one couldn't be chosed from Change Resolution option in Preferences menu. Then I've upgraded my distro from 7.10 to 8.04, and run again  sudo dpkg-reconfigure xserver-xorg -phigh, and the xserver was automaticaly reconfigured. Now the screen resolution is O.K but the scrolling of documents, web pages ,.. is so damn slow, it takes eternity to scroll down to the bottom of the page. I also see some black flashes on shut down,... 

And to mention I've enabled ATI restricted driver, but computer states that IT IS NOT CURRENTLY IN USE

Does anyone know the solution to this mess?

My actual prefix is ubuntu!

---

### Post by MatusZ on 2008-05-15
Hmm...try to run Screen and Graphics under system and there try Generic not Samsung from menu on the left, model LCD panel 1280*1024 at 60Hz

---

### Post by vvule on 2008-05-15
Actually there is no Screen and Graphics under System (there is no in Preferences neither in Administration)

Very messy! And the scrolling is sooooooo sloooooow!

---

### Post by windowskilla on 2008-05-15
> **vvule said:**
> Actually there is no Screen and Graphics under System (there is no in Preferences neither in Administration)

Very messy! And the scrolling is sooooooo sloooooow!

Slow Scrolling is a possible sign of an incorrect driver.

---

