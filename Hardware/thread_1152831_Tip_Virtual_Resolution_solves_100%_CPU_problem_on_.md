---
title: "Tip: Virtual Resolution solves 100% CPU problem on IBM T40 (9.04)"
date: 2009-05-08
forum: Hardware
---

### Post by Qreeek on 2009-05-08
After installing 9.04 on my T40 laptop I had problems with CPU running at 95-100% load while idling at the desktop.

If I left system Monitor running and let the screen fade, I could see that it did not use 100% CPU when the screen was off.

I lowered my resolution to 800x600 while playing with a live user login and it solved the problem. To my surprise I found that when I changed back to the native 1400x1050 it no longer burns my CPU.
It now hovers around 40-50% load in idle.

I believe this has something to do with the virtual resolution it asked me to enable, but I am not a hardcore techie so I stopped worrying about it when I got it to work.

In any case, owners of T40s (and possibly other setups with ATI cards) might get a significant performance improvement by trying the below:

It is probably not the most efficient way to enable the virtual resolution, but it worked for me and requires no knowledge of linux terminal inputs. Sort of quick'n'dirty:
1) Open display settings
2) Change resolution to 800x600 and apply
3) Change resolution to something else (I changed to 1024x768), it should now ask if you want to enable virtual resolution. If not try another resolution until you get the message.
4) Click yes to enable and you will have to log out of X
5) Log back in.
6) Change your resolution to what you want to use.
7) Open System Monitor and check CPU load.

Hope this can help others that got disappointed when they upgraded to 9.04 after having run flawlessly on 8.xx.

---

