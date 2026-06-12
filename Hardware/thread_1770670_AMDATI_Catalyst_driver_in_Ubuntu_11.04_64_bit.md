---
title: "AMD/ATI Catalyst driver in Ubuntu 11.04 64 bit"
date: 2011-05-29
forum: Hardware
---

### Post by ragtag on 2011-05-29
I just got a new/used computer with an AMD/ATI Radeon HD 5870 graphics card.

I've installed the default driver, and rebooted, but the end result is worse than with no driver. I get around 60fps in glxgears, both with or without the driver, but with the driver the gears move a bit jerky.

The Catalyst control center is there, but doesn't seem to have any features that could help.

I've only used Nvidia cards in the past, but got a good deal on this machine and thought ATI driver support had improved.

Is there any solution to this? Going back to 10.04 LTS? Selling the card and getting an Nvidia? Or some nice config trick I'm missing

---

### Post by Yellow Pasque on 2011-05-29
Install latest driver, especially if you're still using Ubuntu 10.10: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
60fps = vsync is on (IIRC, there's an option to disable it somewhere in CCC).

---

### Post by ragtag on 2011-05-30
I'm having no luck with this one.

On [this page]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html") I found instructions that said you should disable vsync in Compiz Config, but that made no difference. When I run it now I'm getting framerates like this:

20705 frames in 5.0 seconds = 4140.877 FPS

...BUT the animation on screen only updates when I click a menu, scroll the terminal or do some other change on the screen, and then it only steps one frame forward for each action. It also feels like everything becomes a bit laggy.

I read somewhere that with 11.04 you had to use the proprietary driver supplied by Ubuntu, because the ones from AMD/ATI were not compatible with this recent a version of X.

I've attached the output of glxinfo. Has anyone got a working Radeon HD card in 11.04 64 bit? And does anyone have any ideas how to solve this?

---

### Post by mastablasta on 2011-05-30
it's a bit hard to tell you without knowing what you already did and which drivers you installed and also how...
 
ATI 5870 - should be compatible well with Ubutnu Linux the problem was with 6xxx series. i owuld say if you enabled proprietary drivers in Ubuntu to try to disable them uninstall them and purge them then try to install the ones from AMD. 
 
if the linux driver is there for this card/chip then it should work.
 
there is also a chance that a setting is wrong somewhere in the system. but i can't help much here... using opensoruce drivers myself.
 
in case you didn't know AMD is now actually working with Cannonical to release their driver version in time of Ubuntu releases.

---

### Post by Fabled One on 2011-05-30
> **ragtag said:**
> I'm having no luck with this one.

On [this page]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html") I found instructions that said you should disable vsync in Compiz Config, but that made no difference. When I run it now I'm getting framerates like this:

20705 frames in 5.0 seconds = 4140.877 FPS


What did you do to get that high framerate? Did you change the xorg.conf or anything?

I have a 5830 and I only get around 800fps. I have uninstalled and reinstalled the OS and drivers several times/

---

### Post by Fabled One on 2011-05-30
> **mastablasta said:**
>  
... using opensoruce drivers myself.

How do you install the opensource drivers? I have looked at guides, but they never actually tell you how to install.

> **mastablasta said:**
>  
in case you didn't know AMD is now actually working with Cannonical to release their driver version in time of Ubuntu releases.

Do you know when they will release these?

---

### Post by ragtag on 2011-05-30
The only thing I've installed is the proprietary driver from the Ubuntu repos, using the Additional Drivers tool. I tried removing them, rebooting, and reinstalling them, and rebooting, but it didn't help.

I think I got a more correct framerate (as shown in the terminal) by messing with the vsync. In the Catalyst Control Center, under 3D>More settings>Wait for vertical refresh, I set it to off. And in ComizConfig Settings Manager (you may need to install this from the repos), under OpenGL, uncheck Sync To VBlank.

That's really all I have done. None of this has really solved the problem. glxgears still isn't updating, and I seem to be getting the same framerate in blender and blender-softwaregl. 

I haven't tried manually installing any drivers, or changed anything in xorg.conf so far.

---

### Post by ragtag on 2011-05-30
This isn't making sense to me, but everything is working, except glxgears. If I set vsync on in the driver, it will do 60fps and play back smoothly, but without it it feels like everything lags and it updates only when I move something on screen, yet it will print a much higher framerate in the terminal

I decided to test other programs, so I downloaded the demo to Amnesia: Dark Descent, and that ran smooth, both with and without vsync, with everything on highest.

So I installed phoronix-test-suite and ran the lightsmark test with the following results.

```

$ phoronix-test-suite benchmark lightsmark

Lightsmark:
    pts/lightsmark-1.2.0 [Resolution: 1280 x 1024]
    Test 1 of 1
    Expected Trial Run Count: 3
        Started Run 1 @ 20:49:35
        Started Run 2 @ 20:51:37
        Started Run 3 @ 20:53:38  [Std. Dev: 1.14%]

    Test Results:
        365.9
        374.34
        370.8

    Average: 370.35 Frames Per Second

```

I found some test results that showed an older ATI Radeon HD 3870 doing 122.7fps on the same test. Which is about right, as the card I have is aprox 3 times faster in Cinebench results I've seen on the net.

Even though everything seems to be working, I would kind of like to know why glxgears is misbehaving.

---

### Post by ragtag on 2011-05-31
A co-worker just had the same problem when installing Ubuntu 11.04 on his laptop, with an Nvidia graphics card. So this seems to be wholly unrelated to the graphics driver.

He found out that if you disable Compiz (and loose Unity) it goes away and gears plays smoothly. So it seems to be some kind of incompatibility between desktop effects (maybe composite) and glxgears.

It's not really a problem, so I'm marking this thread as solved. :)

---

