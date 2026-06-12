---
title: "new install and new to ubuntu"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by solarys on 2009-06-24
I just installed ubuntu on a pc that currently has Vista on it.  The install appeared to be successful.  When I login to ubuntu, I get a desktop with no icons.   The system does not appear to me hung.  I can right click on the desktop and select options off of the menu. What am I doing wrong here?  Any/all suggestions are welcomed!!
 
solarys

---

### Post by Therion on 2009-06-24
As I recall a default desktop in Ubuntu IS clear of any icons.  That's not indicative of a problem...

You can find your applications and utiliites and such under the menus (**Applications - Places - System**) on the top Gnome panel and PUT icons on your desktop if you'd like to though (drag and drop).

Does that help, or am I not understanding the problem?

---

### Post by solarys on 2009-06-24
Thanks for yoyr response.  There is nothing on my desktop to click on.  It just has an orange wallpaper.

---

### Post by scrooge_74 on 2009-06-24
Cheer up, welcome to Ubuntu and Linux in general.

Don't worry you can put icons in there if you want, you should have a bar on top that has the Ubuntu logo and says applications Places and System

---

### Post by solarys on 2009-06-24
> **scrooge_74 said:**
> Cheer up, welcome to Ubuntu and Linux in general.
 
Don't worry you can put icons in there if you want, you should have a bar on top that has the Ubuntu logo and says applications Places and System
There is nothing on the screen to click on, wallpaper only.  No logo, no nothing.

---

### Post by scrooge_74 on 2009-06-24
press ALT + F2 to get a command prompt style window, then there is a list below find the terminal and open a console window.

Maybe some parts of gnome did not load properly, or log out and log back in

---

### Post by solarys on 2009-06-24
I was able to bring up terminal window.  Yet, I still can not see icons.  What should I do next?

---

### Post by scrooge_74 on 2009-06-24
Well at least you know the system is not hanged :D

Check [here]("http://www.yolinux.com/TUTORIALS/GNOME.html") 

I think you can type gnome-session-properties

If you do a ps -ax you will see a list of apps running, probably the gnome-panels or some others did not load

---

### Post by jlc0204 on 2009-06-24
I'm new and need help as well. This seems to be very frustrating for something that is supposed to be better than Windows!
I have installed the latest version of Ubuntu, via Wubi on my Dell Deminsion 4500 (I know I'm out of date).
I am able to choose Ubuntu to load the OS, but after I log in I'm done. There are no icons (which I've read that the screen starts off blank), but there is nothing. The computer appears to be done running and I've left the screen alone for several minutes. I don't get any type of menu if I right click, either.
Please help. I hate to do an unistall before I am even able to give it a try. My wife is already going to be upset that I've made changes to her routine on the computer/ :(

---

### Post by scrooge_74 on 2009-06-24
The best I can say is that wubi is not supported and I read somewhere is not actually the best choice. I rather do the old fashion way (old like 2 years now): use a live CD and install it.

I'm not well verse in the problems you have, but it seems some parts of Gnome are not not running. Try CTRL+ALT+BackSpace and try to log in again, maybe it will restart all those services that are not running at present

---

### Post by jlc0204 on 2009-06-24
Previously I restarted 4 or 5 times with the same results. I had to hold the power button down to get the PC to shut off so I could restart. There was just nothing I could do once I logged on. It appeared my login and password were accepted.

---

### Post by scrooge_74 on 2009-06-24
How did you installed Ubuntu in the first place? Is really odd you are having this kind of problems.

hope someone more savy comes along soon yo help you out

---

### Post by solarys on 2009-06-25
Is there a log file that records the bootup process?  If so, where is it located?  Any/all suggestions are welcomed.

---

### Post by scrooge_74 on 2009-06-25
/var/log/

there you have dmesg and syslog those files have the info

---

### Post by abn91c on 2009-06-25
> **solarys said:**
> There is nothing on the screen to click on, wallpaper only.  No logo, no nothing.
alt+f2 then type **gnome-display-properties** and change the screen resolution, see if that helps
this may help you also [http://www.yolinux.com/TUTORIALS/GNOME.html](http://www.yolinux.com/TUTORIALS/GNOME.html)

---

### Post by solarys on 2009-06-25
Issue resolved!  i re-installed Ubuntu all by itself.  Initial install was a dual boot with MS Vista. I now have a a task bar at the top and bottom, where I can select options without a problem.  Thanks for everyones help and input.

---

