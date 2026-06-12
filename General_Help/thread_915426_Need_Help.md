---
title: "Need Help"
date: 2008-09-09
forum: General Help
---

### Post by blackknight438 on 2008-09-09
Hey. I'm really new to using anything but Windows, and I have a few problems. First, my video card screwed up my screen settings somehow. Before the drivers were installed, I could run at 1600x1200 at 60hz. I installed the drivers and restarted so that I could play games and use visual effects. My maximum resolution is now 1280x1024. The maximum hz is 52. What happened and how do I fix it? My card is an NVIDIA 7900. On the hardware drivers screen it says I have the "NVIDIA accelerated graphics driver (latest cards)."

I don't know if I should go to other forums or not to list the other problems, but I figure I'll list them here just in case. My second problem is with sound: I have none. My card is an Audigy SB0090. I'm completely lost on the audio settings screen, and I haven't the slightest clue how to get it to work.

My third problem is with installation of a certain program. I don't know if this has to do with my ineptitude at using Ubuntu or the program itself. The program is called Wine. I download it, extract it, and click the wineinstall file in the tools folder that the site tells me to click. I get a prompt asking me if I would like to "Run in Terminal," "Display," "Cancel," or "Run." If I click run, it does nothing. If I click run in terminal, it shows a window for about a half of a second before closing.

I fail, and I'm in dire need of help. Thank you.

---

### Post by easybake on 2008-09-09
> **blackknight438 said:**
> Hey. I'm really new to using anything but Windows, and I have a few problems. First, my video card screwed up my screen settings somehow. Before the drivers were installed, I could run at 1600x1200 at 60hz. I installed the drivers and restarted so that I could play games and use visual effects. My maximum resolution is now 1280x1024. The maximum hz is 52. What happened and how do I fix it? My card is an NVIDIA 7900. On the hardware drivers screen it says I have the "NVIDIA accelerated graphics driver (latest cards)."

I don't know if I should go to other forums or not to list the other problems, but I figure I'll list them here just in case. My second problem is with sound: I have none. My card is an Audigy SB0090. I'm completely lost on the audio settings screen, and I haven't the slightest clue how to get it to work.

My third problem is with installation of a certain program. I don't know if this has to do with my ineptitude at using Ubuntu or the program itself. The program is called Wine. I download it, extract it, and click the wineinstall file in the tools folder that the site tells me to click. I get a prompt asking me if I would like to "Run in Terminal," "Display," "Cancel," or "Run." If I click run, it does nothing. If I click run in terminal, it shows a window for about a half of a second before closing.

I fail, and I'm in dire need of help. Thank you.

First, open up a terminal. Accessories>Terminal. paste ```
sudo apt-get install envyng-gtk
```

When it's done installing, in Terminal type ```
envyng-gtk
``` select nvidia. click ok. let it work its magic.

I don't know that much about sound but i'm sure someone else does.

Third, the easiest way to install wine would be to open the add/remove programs menu. Search for Wine. Check the box, click Apply.

---

### Post by blackknight438 on 2008-09-09
It gives this back when I tried that in the terminal:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envying-gtk"

I assume that means it failed?

---

### Post by blackknight438 on 2008-09-09
...Anyone?

---

### Post by easybake on 2008-09-09
> **blackknight438 said:**
> ...Anyone?

you miss typed it just copy and paste the codes.

---

### Post by blackknight438 on 2008-09-09
You're right; sorry. It installed just fine, and I restarted, but my resolution is still capped at 1280 by 1024. Any other ideas?

---

### Post by easybake on 2008-09-09
> **blackknight438 said:**
> You're right; sorry. It installed just fine, and I restarted, but my resolution is still capped at 1280 by 1024. Any other ideas?

Try running ```
nvidia-settings
``` in terminal. Install it, if it isn't already. Check the X Server Display Configurations.

---

### Post by blackknight438 on 2008-09-09
It is fixed. Thank you so much. I also got Wine installed successfully. Thanks for everything.

---

