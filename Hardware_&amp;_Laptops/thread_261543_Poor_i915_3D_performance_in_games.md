---
title: "Poor i915 3D performance in games"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by zgornel on 2006-09-20
I'm using the 2.6.15-7 kernel (compiled it myself) and the i915 (march 2006 snapshot) drivers. Glxgears gives me ~ 1100fps but gaming performance (with wine 0.9.21) is very low (e.g. Quake3 - max quality Windows 92ps, Linux - 35fps, Warcrat III - unplayable). Acceleration is enabled, glxinfo states:

direct rendering: Yes
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1

I'm wondering if there is any chance of performance improvement.

---

### Post by rdlf0512 on 2008-01-28
have you tried upgrading you mesa to improve graphics performance?
[http://www.mesa3d.org/](http://www.mesa3d.org/)

---

### Post by KisGellert on 2008-02-04
I have the same problem. Xubuntu. XFCE, lightweight environment. 1.6Ghz celeron M . i915GM integrated graphics, laptop.
I play Counter Strike 1.6, 
30fps normal , but when more complex environment appear the fps is : 15 ! :(
even when i set 640x480 res!
direct rendering is enabled. I use opengl driver. I kill memory ,cpu required applications.
What can i do to increase performance?
i do not understand, because i can play half life with my veryvery old 650Mhz AMD Duron desktop computer, with ease , with Windows! 
My  acer laptop 1.6Ghz celeron is so-So better in CPU frequency and have more memory.
I hate windows, i want use linux. :KS
Helpme

---

### Post by zgornel on 2008-02-05
I do not know about how games would behave now, that was quite an old post. I haven't tried any game since then but anyway, with an intel integrated graphics card not much can be played.

---

### Post by roderick on 2008-02-05
> **zgornel said:**
> I do not know about how games would behave now, that was quite an old post. I haven't tried any game since then but anyway, with an intel integrated graphics card not much can be played.


Actually, Half-Life plays perfect on my Intel i945. Even Half-Life 2 works well.

I installed latest Wine from winehq, made sure my system was up to date (latest updates under Gutsy) and used Steam versions of Half-Life and Half-Life 2.

You may want to tweak DRI settings using a utility called driconf. It allows you to adjust things like texture compression, etc. 

There is also an Intel web page indicating games supported (yes, Intel can do gaming - despite peoples misconceptions). Inf fact, Intel's next gen card (X3100 - i965) is geared specifically towards this gaming market. Even Dungeon Seige II lists Intel 945 as a supported video card. Check out Intel's web site: [http://www.intel.com/support/graphics/intel945gm/sb/CS-021400.htm](http://www.intel.com/support/graphics/intel945gm/sb/CS-021400.htm)

Let's bust the "you can't play games on Intel myth" (ok, so not all games work, due to some hefty requirements on some games). World of Warcraft runs fine with wine and an Intel 945, which is a lot for some people. Besides, Intel is Open Source friendly, and we all like that a LOT.

Cheers,

Rod.

---

### Post by KisGellert on 2008-02-06
Hello.
The problem was solved.
I cannot tweak X. I try to configure 
/etc/X11/xorg.conf 
if someone intrested in see: 
# man intel 
; and 
# man xorg.conf
next i try 
# driconf
or 
# sudo driconf
but noone  help me.

Cedega is the transgaming application , works. 
It is the wine base game runnig "engine". But it is better than Wine.
Im amazing when Cedega run the self test, and i see the veryveryFAST glxgears running. ! I dont know what is the FPS, but it must be over 2500 !

I buy a counter-strike over Steam (in Cedega). 
The problem is no sound in game. I get an error "resource is busy" or somewhat. 
#lsof -n |grep snd
list me an opened files for sound card.
The Fck'in Clue is that the Steam bstard Steal the sound. :guitar:
Solution: 
I run amarok, or XMMS or .... (i get sound) !!
I run Steam. (hehe steam cannot steal sound)
I stop amarok, or XMMS
I launch Counter-Strike. (CS get sound)
Counter-Strike have sound !   ----------------   WOW =D>

---

### Post by KisGellert on 2008-02-14
The FPS is sometime slown down 20-15, 
when shooting / many player appear.

:( :( :( :( :( :(

---

### Post by mikekchar on 2008-02-25
> **roderick said:**
> 
Let's bust the "you can't play games on Intel myth" (ok, so not all games work, due to some hefty requirements on some games). World of Warcraft runs fine with wine and an Intel 945, which is a lot for some people. Besides, Intel is Open Source friendly, and we all like that a LOT.


I'd love to bust this myth.  But I still can't play WoW with wine and my Intel 945.  With INTEL_BATCH=1 I can get ~1700 FPS on glxgears, but I can only get ~10-15 fps in WoW with *everything* turned off.  It's unplayable.   Under Windows I generally have 30-50 fps walking around with most things turned on.  If I turn on absolutely everything I still get 20-30 fps.

So I'm getting much less than 1/3 the frame rate.  I haven't seen *anybody* who has done better.  Please, please, please give me your secret if you can get this game to work at greater than 25 fps.  

I also have trouble running Linux games like vega strike.  I can only get about 15-20 fps there if there is *anything* on the screen.  If I actually have to fight something it crawls down to sub 10s.  Basically, there are *no* 3d games that are playable.  Like I said, I would love to kill this myth -- I know the hardware is fast enough.  But there is something wrong with either my setup or with the drivers...

Edit:

I've managed to sqeak another 5 fps by using the intel driver and using opengl rather than d3d.  So now I can get 15-20 fps in Darnassus at 800x600 with everything turned off.  I've played with Legacy3D options and TripleBuffer, but these slow me down a bit.  But the drawback of opengl is some of the texturemaps look wrong.  My guess is this can be fixed with the proper settings in the X conf file, but it seems pointless unless I can find a factor of 3 or 4 improvement along with it.

---

### Post by sofamensch on 2008-03-04
Yes i know what you are talking about. In my case its a CrossPlatform game that i try, Sauerbraten. It is compiled for both Win and Linux. 
While under Win i hit the VSYNC Rate ;-) Linux is suffering around 30-40 fps. Well still "ok" but there is a major leak.

I wonder even more since the Intel drivers are open source, unlike Nvidia and Ati.

---

