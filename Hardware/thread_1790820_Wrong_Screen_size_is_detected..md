---
title: "Wrong Screen size is detected."
date: 2011-06-25
forum: Hardware
---

### Post by deviao on 2011-06-25
Hi All,

I have a mini ITX system that is connected to my 32 inch TV via HDMI.  The installation of ubuntu went smoothly but when i log in there is a slight issue.

Basically, the system is detecting my monitor as a 48inch one when i use both the standard display drivers and the Nvidia ones.  screen res is  1920 x 1080 and seems to be fine but i can't see the whole desktop.  When i move my mouse off the screen in every direction the cursor vanishes but is out of range.  If i right click i get half a menu so it is as if i have a 32inch screen window on an overall 48inch desktop.

I am not very ubuntu savy so if you need any extra info please give me exact steps (puts on stupid hat) :)

I think i may need to force the system so it realizes its 32inch?  Help is greatly appreciated.

The board i am using is a ASUS AT510MT-I with onboard NVIDIA Next Gen ION graphics with 512MB dedicated video memory. (Nvidia ION 2010).

Thanks in advance.

---

### Post by JK1103 on 2012-01-26
I am having a similar problem with my first-ever linux installation that I jumped head-first into.

Actual (TV) screen size is 42", being shown as 52".  As you have mentioned, this is not a resolution issue (as far as i can tell)  

I just installed all updates and the issue is still here.

I will keep playing around, but was just curious if you had any luck and could pass along what worked.

Thanks!

---

### Post by JK1103 on 2012-01-26
Solution was actually not related to Ubuntu.  When I changed the input name on the HDMI2 port of my TV from nothing to "PC" it automatically reset the size of the screen.  Everything is working now.

1 hurdle down, many more to go...

---

