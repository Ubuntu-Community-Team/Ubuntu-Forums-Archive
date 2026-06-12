---
title: "Screen Resolution"
date: 2008-11-05
forum: General Help
---

### Post by talking Llama on 2008-11-05
Hey.
My screen resolution is 1024x768 although I want it to display as 1280x1024. I know my screen can display this resolution though the option isn't available in the System>>Preferences>>Screen Resolution option. It also says my refresh rate is 50hz when I can get 75hz on my monitor.
Any help would be great thanks.
Using Ubuntu 8.04 (hardy)

---

### Post by wnaBsd8d on 2008-11-05
make sure that your graphics driver is updated

---

### Post by aeronotix on 2008-11-05
[http://ubuntuforums.org/archive/index.php/t-83973.html](http://ubuntuforums.org/archive/index.php/t-83973.html)

That might be of some help to you.

---

### Post by wgrant on 2008-11-05
That's *very* old. Try [the new X resolution fix documentation](https://wiki.ubuntu.com/X/Config/Resolution).

---

### Post by madtagar on 2008-11-05
I just solved my resolution issue. Try Ctrl+Alt+Backspace. It was so easy I just about started lol... it just reset x. Thats it. I went from a dead end, 640x480 resolution to a 1024x768 just like that.

Credit goes to here:[http://www.ubuntu1501.com/2008/04/restart-x-server.html](http://www.ubuntu1501.com/2008/04/restart-x-server.html)

---

### Post by Chunky Dunk on 2008-11-05
I have this problem as well. I have to manually edit the /etc/X11/xorg.conf file to fix it. What I did was add "1280x1024" to the beginning of the "Modes" line in the "Display" Subsection under "Screen". wgrant's link shows an example of the relevant section from xorg.conf

---

### Post by Nylo on 2008-11-11
> **madtagar said:**
> I just solved my resolution issue. Try Ctrl+Alt+Backspace. It was so easy I just about started lol... it just reset x. Thats it. I went from a dead end, 640x480 resolution to a 1024x768 just like that.

Credit goes to here:[http://www.ubuntu1501.com/2008/04/restart-x-server.html](http://www.ubuntu1501.com/2008/04/restart-x-server.html)


I tried this and nothing happened.  I might have the keyboard short cuts disabled.  Where would I go to enable?

---

