---
title: "Video tearing problem in ubuntu(DELL XPS 15)"
date: 2011-11-06
forum: Hardware
---

### Post by 14quartz on 2011-11-06
[FONT="Georgia"]Hi ALL,

I got this big problem video tearing :(. I'm using DELL XPS 15.(Intel i3 processor & NVIDIA GE force GT 525) which uses optimus technology.So I'm unable to use the drivers, if installed results in black screen.Did a lot of googling but of no use like setting COMPIZ refresh rate, Mediubuntu pack etc. I tried LINUXMINT where this is not happening(Video tearing). In both the case I never installed NVIDIA drivers. Am I missing any video codec?.

Please help me.

Thanks,
14Quartz[/FONT]

---

### Post by 14quartz on 2011-11-20
[SIZE=3][COLOR=darkslategray]_**[FONT=Comic Sans MS]Got the Solution for Screen Tearing Problem[/FONT]**_[/COLOR][/SIZE]
[FONT=Comic Sans MS][COLOR=darkslategray][SIZE=2]Install Compiz[/SIZE][/COLOR][/FONT]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Start Compiz[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Go for OpenGPL in General and select Sync To VBlank[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Go to Workarounds in utility[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]set Legacy Fullscreen support[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Set Fix screen updates in XGL with fglrx[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Set Force synchronization between X and GLX[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Set Don't wait for video sync[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Comic Sans MS][COLOR=darkslategray]Set Force full screen redraws(buffer swaps) on repaint[/COLOR][/FONT][/SIZE]
 
[SIZE=2][COLOR=darkslategray]I tried many options finally this alone worked for me[/COLOR][/SIZE]
 
[SIZE=2][COLOR=darkslategray]in [/COLOR][/SIZE][COLOR=darkslategray]**[FONT=Book Antiqua][SIZE=2]Ubuntu 11.10 Dell XPS 15 :)[/SIZE][/FONT]**[/COLOR]
 
**[SIZE=2][FONT=Book Antiqua][COLOR=darkslategray]I don't know how it worked but worked for me.:guitar:[/COLOR][/FONT][/SIZE]**

---

