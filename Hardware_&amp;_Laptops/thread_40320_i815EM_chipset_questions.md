---
title: "i815EM chipset questions"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-06-08
Question (short form):  Could someone who has or at one time ran ubuntu on a laptop with a i815 chipset please post their glxgears fps?  How about people with similar laptops?

Questions(long form)  Been running ubunutu for a few weeks on my Dell Inspiron 2500.  Been doing my best to tweak what I can.  Now, i'm looking over the video performace. Once I edited xorg.conf to use 1024x768 at 16 bit color i managed to squeeze 350-400 FPS from glxgears (up from 80-150).  I can tell from /var/log/messages that abpgart (which must be included in the 2.6 kernal...cause i didn't add it) finds the i815 chipset and the 4 MB of system RAM allocated to it.  Is there a way I can get to agpgart to take MORE ram?  I have 512 in the laptop and swap is never used...if a few more MB would help FPS it wouldn't hurt.  Is this possible?

I saw the thread on 855resolution.  It seems that those people were having resolution problems...I am not.  Regardless, 855resolution does not find my chipset or VBIOS.  So, no go there.

DRI is specified and loading in my xorg.conf file.  I am using the i810 driver.  I looked over the i815 framebuffer driver.  Do i need to call the module at some point or is it already in my kernal?  The file was already there (i815fb.o).  Do i need to add it to my kernal boot options?  Is there someway to specify options?

Basically, I want to run some games.  I know this thing is not exactly a gaming machine but I feel that the video oughtt to be a bit better.  So, has anyone tweaked out their i815EM laptop to run 3d games well?  

PS -- don;t know if its related, but openGL stuff at 640x480 is awful looking (tuxracer or ET).  there are blank lines all over the screen at random intervals.  800x600 on ET looks good...just slow (framerate).

Please Help!!!

Thanks in advance,

Mak.

---

### Post by Sav on 2005-06-09
Hi, on my laptop I got an average value of 500 fps.
I recompiled the latest 2.6.11 source downloaded by synaptic.
In the xorg.conf file I disabled the "dri" module and left only the "glx" (I'm talking only about video modules, of course).
This gave me a spin from 300 to 500 fps.
By the way, I think that the I810 driver, provided with X.org, doesn't push the chip to its max, but it's Intel fault.
Bye

---

### Post by ruben_b on 2005-06-09
i have an intel 915gm graphic card with 128mb in my toshiba notebook and the card works fine but i only have about 800fps.
but i haven´t found a way to get more. i opened a topic too, but haven´t get any hints yet.
i think this card should do much more then 1000fps cause my old geforce 420 go allready did 1500fps.

---

### Post by makisupa123 on 2005-06-09
Thanks for the replies.

mak,

---

### Post by shof2k on 2005-06-09
I have an intel i810 driver running an i845 graphics chip.  Glxgears gives me 630fps.

---

### Post by Sav on 2005-06-10
Can you post your configuration, please?
1) kernel
2) window manager
3) xorg
4) etc....

Thanks in advance

---

### Post by makisupa123 on 2005-06-10
I was looking around on the x.org site and found some interesting information on the i810 driver being used.  Check out:

[http://www.x.org/X11R6.8.2/doc/i810.html](http://www.x.org/X11R6.8.2/doc/i810.html) 

Especially number 8 -- "known limitations."  It appears that the acceleration is only for 2d.  Am i reading this right?

Also, is it true that in older versions of ubuntu that used xfree86 full 3d support worked?  I'd be interested to know if anyone has any anecdotal evidence of better glxgears scores or games running better under xfree86.  Maybe we're just gonna have to wait....

My config:
Hoary 5.04 on a 
Dell Inspiron 2500 (celery 800 w/512 MB RAM) with the latest 
2.6.10 686 kernel
running Gnome

---

