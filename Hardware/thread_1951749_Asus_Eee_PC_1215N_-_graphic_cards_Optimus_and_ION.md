---
title: "Asus Eee PC 1215N - graphic cards: Optimus and ION"
date: 2012-04-03
forum: Hardware
---

### Post by NeedALotOfHelpXD on 2012-04-03
I have a problem with nvidia ion in ubuntu 12.04
I found some solutions for another eee pc here:
[http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)
and [http://ubuntuforums.org/showpost.php?p=11748295&postcount=301](http://ubuntuforums.org/showpost.php?p=11748295&postcount=301)
but are strictly for another model of asus eee pc. 

My problem is:

nvidia-settings says: You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

sudo nvidia-xconfig 
WARNING: Unable to locate/open X configuration file.
New X configuration file written to '/etc/X11/xorg.conf'
and after restart i get a very low resolution and nvidia clearly isn't enabled.

jockey-gtk doesn't recognize the nvidia-ion

glxgears
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't get an RGB, Double-buffered visual

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
05:00.0 VGA compatible controller: NVIDIA Corporation Device 0a76 (rev a2)

so how can i get nvidia to work, and how can i revert to intel integrated graphics like they did?

---

### Post by Millis on 2012-05-15
I'm having the exact same problems with the same model of netbook.  I was just trying to get the VGA connector to support changing displays in ubuntu, and now I'm stuck in low resolution with nvidia driver not being used. 

Been looking and not getting a clear answer that works.  

I'm still learning how terminal works, I just recently retried these steps in terminal: Removing the Nouveau driver, then installing kernel headers, then installing the latest nvidia driver, trying to select it (not sure if the commands worked) and then doing nvidia-xconfig and restarting the computer.  No luck. :-\

---

### Post by ItalOz on 2012-06-09
same problem here
Tried just recently to connect a second monitor and found out was not working fine with the standard driver.
So I tried to install the Nvidia  ones and got same problems as you.
I'll keep you posted if I find something

EDIT:
[check this out]("http://askubuntu.com/questions/70031/how-to-use-3d-graphics-on-asus-eee-pc-1215n")

---

