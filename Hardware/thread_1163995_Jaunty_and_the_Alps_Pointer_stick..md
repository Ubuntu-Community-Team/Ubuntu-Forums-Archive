---
title: "Jaunty and the Alps Pointer stick."
date: 2009-05-19
forum: Hardware
---

### Post by Johnny &quot;V&quot; on 2009-05-19
Hello, this is my first post here on the forums. I am a noob when it comes to linux and am in need of some help. I am a windows admin and am learning linux because I am tired of the windows restrictions.
 
I loaded ubuntu 9.04 on a sony vaio ux 390 umpc. Everything is working great except for the Alps touch stick. It is extremely sensitive. I have tried everything to get it to stop clicking when moving the pointer on the screen. I have researched this for the last 3 days and have come up dry.
 
I followed the directions on here....
 
[http://ubuntuforums.org/archive/index.php/t-76585.html](http://ubuntuforums.org/archive/index.php/t-76585.html)
 
but still any settings that I have in the xorg.conf do not work. I have tried loading gsynaptics and none of the settings in there do anything. When I run synclient -m 100 and move the mouse all values are at zero and do not change. 
 
The only thing that I can think of is it is not using the xorg.conf for anything or the settings that I have are not pointing to the proper driver.
 
I am temporarily using a mouse to get around when doing 'heavy' stuff as selecting several icons or madly scrolling accross screens is driving me insane.
 
Any files you need to see please let me know.
 
TIA
 
Johnny "V"

---

### Post by Johnny &quot;V&quot; on 2009-05-19
I did want to add while following the directions on that earlier post they mention to check /proc/bus/input/devices file and they list that they have information in there. Mine is empty. No entries.

---

### Post by Johnny &quot;V&quot; on 2009-05-20
No one???

---

### Post by shyce on 2009-07-16
I have this same problem. Would really like a solution.

---

### Post by shyce on 2009-07-16
Found a solution: 

[Configure ALPS Touchpad in Ubuntu 9.04 - Jaunty Jackalope]("http://bhagwad.com/blog/2009/04/configure-alps-touchpad-in-ubuntu-904-jaunty-jackalope.html")

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

