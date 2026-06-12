---
title: "Ctrl+Alt+F7 to see the graphical login screen"
date: 2008-11-03
forum: Hardware
---

### Post by cool_penguin on 2008-11-03
Hi Everyone,

I recently upgraded to Ubuntu 8.10. While at the first impression everything looked good, I was very disappointed to see a Blank Black Screen at GDM login after the first re-start (following fresh installation using Live USB). When I am greeted by a Blank Black Screen, I hit Ctrl+Alt+F6 and then I am taken to a text based command line login console. Then at this point if I type nothing and instead hit Ctrl+Alt+F7, then I am taken to the graphical GDM login screen. The same problem occurs also when I log out and try to log in. I am forced to follow the same sequence of hitting Ctrl+Alt+F6 first and then hitting Ctrl+Alt+F7 to see the graphical login screen.

I was looking up various blogs and forums, where one guy advised adding the line Driver "vesa" to the xorg.conf under the section "device". When I do that I can see the graphical GMD at start up and also when I log out and try to log in. But then the problem is that the max screen resolution that I get is only 800x600 while my notebook supports a max of 1024x768.

BTW, when I follow the sequence of hitting Ctrl+Alt+F6 first and then hitting Ctrl+Alt+F7 to see the graphical login screen, the screen resolution even at login is 1024x768. But only after adding vesa to xorg.conf, the login screen and the normal desktop screen all scale down to 800x600

Could anybody please help me with this? I am using an Acer Travelmate 2310 notebook which has an integrated SiS Graphics card. Not the best, I know, but its a 4 year old notebook and all version of Ubuntu until Hardy worked perfectly like a charm.

Thanks a lot in advance.

Cheers,
Harry

---

### Post by cool_penguin on 2008-11-03
This blog here also suggest a similar fix but my resolution won't play well then.

[http://www.heise-online.co.uk/open/Ubuntu-8-10-first-tryout--/features/111823/4](http://www.heise-online.co.uk/open/Ubuntu-8-10-first-tryout--/features/111823/4)

---

