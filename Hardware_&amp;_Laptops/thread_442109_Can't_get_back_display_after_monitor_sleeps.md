---
title: "Can't get back display after monitor sleeps"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by alvinistic on 2007-05-13
Hi, everyone.

I've got a problem. I'm using a Toshiba M30 laptop 

I've set the power management "put computer to sleep when inactive for" to never. After inactivity for 10 mins, the (non-GL) screensaver works well and If i do something at this point of time I can bring the display back. But the problem is if we leave the laptop inactive for too long, the monitor starts to turn off and it will not be able to awake again, just leaving me with black screen.

Anyone can help? Thanks.
FYI, i'm using an Nvidia card (GeForce FX 5200Go)

---

### Post by botulismo on 2007-05-13
I really have no idea what's causing this. It has happened to me once or twice -  but I'm on a Gateway desktop computer with an integrated x200 ATI chipset... I turned power management off because I always by habit turn my monitor off when I get up for more than a few seconds, I just figure I'm more reliable power management than the PC anyway. Not that it helps you as you use a laptop. Anyone know?

---

### Post by alvinistic on 2007-05-13
Thx Botulismo for your reply :D

I tried "xset q" in terminal and found out that my monitor does not support DPMS.

> 
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfffef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  **prefer blanking:  yes**    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/alvin/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/,/home/alvin/.gnome2/share/fonts
Bug Mode: compatibility mode is disabled
[B]DPMS (Energy Star):
  Display is not capable of DPMS[/B]
So, I tried to comment out the Option "DPMS" in my xorg.conf, but it does not work.

Another thing I found interesting is the prefer blanking. Thought this is the cause of my problem, so I did a 
xset s noblank

I haven't tested it. I'll update u about the progress. Thanks.

---

### Post by botulismo on 2007-05-17
Ha! I was semi-out for a few days because I replaced Ubuntu Feisty with Ubuntu Studio Feisty... Slick interface and some nice programs included, other than that it's Ubuntu all the way.

After reading this, I solved the problem by changing my monitor out... I have a few sitting around the house because people give me theirs whenever they buy new ones, so I have quite a collection of hand-me-down monitors. I changed to a huge (clunker) 19" monitor that I know supports energy star and... No problem since! Thanks a lot for the heads up. Now I know which monitor does not go with Ubuntu.

I decided to try Ubuntu Studio because a backport of Ktorrent (I just like it better than Azureus and the gnome-btdownload) I had set to auto-start was destroying my computer whenever it started... Surely, I could have fixed it, but it was an excuse to try UbuStu.

---

### Post by n0deal on 2007-11-05
I am also having a similar problem on my Toshiba M30 notebook.  I am running Ubuntu 7.10 with the restricted nvidia drivers and after a period of inactivity my monitor will go black and the only way I can get the screen to come back on is to disconnect the ac power so it goes to battery power.  As soon as I do this I get my screen back.  I've already set the power saving settings to never turn off my display and that didn't have any effect on the problem.

alvinistic, did you ever resolve your problem?  If not can you also recover your video if you unplug and plug back in your ac power?

---

