---
title: "Problem detecting Hardware on old compaq Pentium 2"
date: 2008-11-04
forum: Hardware
---

### Post by digdugdiggy on 2008-11-04
So I got this ancient computer, a Compaq Armada 7400.
266 Mhz processor, 256MB of ram nothing too great. (Heres the specs [http://www.server-unit.ru/!guard/html/1556.html](http://www.server-unit.ru/!guard/html/1556.html) )

I decided to try out Ubuntu, and put it on there.

Now I'm having alot of problems. The native resolution is 1024X768 and Its stuck at 800X600. This is making it very hard to read things and such due to the bad resolution.

I cant change it either. Ive googled my brain out. 
Tried Changing my Xorg file:
I added the submenu in there under display to include the correct resolutions. No fix. I used /etc/init.d/gdm stop to try to do it from command line, still no fix.

Tried the sudo dkpg-reconfigure xserver-xorg but that only gives me options about my keyboard, and nothing about video card or monitor.

Any help here at all? Im really stumped and this is my first attempt at Linux.

---

### Post by nixscripter on 2008-11-04
It sounds like there is something going on in the graphics driver.

Try changing resolution, and then see if there are errors in /var/log/Xorg.0.log. There may be an error in its attempt to switch resolution, which is why it's refusing to operate at 1024x768.

If you're not sure, post that file. Make sure to put [code] forum tags around the posted file so it is readable.

---

