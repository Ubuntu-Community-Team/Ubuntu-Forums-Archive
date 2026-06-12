---
title: "915resolution"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by ericsp on 2006-06-01
I installed Dapper on my Dell Latitude D410. Everything works OK appart from the screen resolution. It should be at 1240x1024, but I get stuck with 1024x768. I figured that 915resolution might help out in these cases, but I cannot get it to work. Anyone here who knowhs how?

Eric

---

### Post by Muffe on 2006-06-01
Yes. As standard 915resolution starts after GDM. It has to be started before to have anny effect. Try restarting X and see if that helps. If that helps, make 915resolution start before GDM.

Feel free to ask if you need any furtehr help.

---

### Post by ericsp on 2006-06-02
Thanks. The issue is a bit more complicated than I noticed initially. My labtop has a 1024x768 screen, but I dock on a system with a 1240x1024 screen. When docked, I can only get the 1024x768 resolution. I probably have to make changes to xorg.conf . Any suggestions?

---

### Post by fast1 on 2006-06-02
I have a similar problem. My laptop (Dell D620) has a 1440x900 screen.  The external monitor (Philips 20") has a 1680x1050. I managed to get this resolution option with 915resolution. However, when I select it, the screen is screwed up and I have to go back to the previous resolution. Note that I can have both 1440x900 and 1680x1050 on the laptop. What about you?

---

### Post by macbuff on 2006-06-02
I have a DELL D610 with a 1400x1050 display and as standard it come up with 1280x1024.  I used 915resolution to patch the video settings to reassign one of the unused to 1400x1050 and the system now boots up as 1400x1050 but on return from sleep it reverts to 1280x1024.

Have a look on [http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

John

---

