---
title: "Annoying display behavior after upgrade from 9.04 to 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by rkannan on 2009-11-06
After I upgraded from 9.04 to 9.10, I am getting a strange display behavior. All my windows start out as maximized. I have to go to the toolbar at the bottom and do a "unmaximize". Also, if I click on the display, all my open windows get minimized. 
I think it is some window manager setting. I tried removing .gnome .gnome2 .gconf .gconfd directories but that doesn't seem to have helped. I have gone through the System preferences but cannot identify any relevant setting. I tried switching window manager between kde and metacity and that also did not help.

This is really irritating. I will be grateful for any help.

I have a nvidia 8800GTX and a dual monitor twinview display which was working fine before the upgrade. 

Thanks,
--Kannan.

---

### Post by unamanic on 2009-11-06
Sounds like the behaviour that maximus provides on purpose for the netbook remix.  You could see if it's installed and remove it if it is.

---

### Post by rkannan on 2009-11-09
Thanks. Removing the maximus package with synaptic resolved the issue. 

--Kannan.

---

