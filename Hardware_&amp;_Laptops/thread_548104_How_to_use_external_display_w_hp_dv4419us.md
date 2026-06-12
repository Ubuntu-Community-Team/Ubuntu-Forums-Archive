---
title: "How to use external display w/ hp dv4419us"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by bas1 on 2007-09-10
Hi. I have an HP Pavilion dv4419us laptop and I have been wondering on how to use an external display with it. I have no clue as to how to use it and the laptop's built-in screen at once (or one at a time). I am quite experienced with linux, and am not afraid to edit xorg.conf (I just have not done it much). But, I am a total graphics card newb. My card/chipset is the intel 915 gms. The target resolution of the display I'm trying to hook up is 1600x1280.

Attached is my current xorg.conf file.

---

### Post by bas1 on 2007-09-11
I have had some success getting the display to work. I installed i810switch. this got the screen to work, but I need to be able to set a different resolution and refresh frequency. How do I do this?

Thanks for the help!

---

### Post by bas1 on 2007-09-11
Ok, I think I've almost got it figured out. My goal is to set up my laptop in a Multi-head configuration. I Just need help on how to set up the external monitor. Attached is my current xorg.conf file. Note the "Device" sections with the graphics card info. That's where I need help. I have the screen numbers set up right, but I am not sure about anything else. I have been following the directions here > [http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86) to the best of my abilities, but since I'm new to it, I need help.

Thanks!


P.S. Sorry for the large amount of posts, I just wanted everyone to know exactly what I was doing.
P.P.S. The external monitor I'm trying to hook up is a Samsung SyncMaster 204B.

---

