---
title: "nVidia GeForce 6600 Go issues"
date: 2011-03-20
forum: Hardware
---

### Post by EvanJackPenn on 2011-03-20
Hello! I'm new here so go easy on me.

I have an issue with my graphic card drivers. I have installed Ubuntu 3 times now. On my first install, it all went smoothly and worked. I booted up for the first time, installed all updates, installed the recommended driver for my card and rebooted. I then got no graphical interface - just a command line.

I reinstalled, thinking it was something I did. I did all the same things, with the same result.

This time (third and current install), I did not update drivers. SHAZAM! It worked!

But now, I wanted to run Minecraft. And I got a black screen error (posted below). I did some googling, and found it was due to graphics card drivers. Games running on my windows partition also told me to update drivers.

```


      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 20/03/11 11:20

Minecraft: Minecraft Beta 1.3_01
OS: Linux (i386) version 2.6.35-28-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:260)
	at net.minecraft.client.Minecraft.run(SourceFile:632)
	at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT 97b47eb8 ----------



```

This is played in downloaded client. I get the login screen etc, but as soon as I've logged in - black screen. Five seconds pass: CRASH. Playing in browser gives a white screen.

Now then, I have a dilemma. Do I update drivers, and risk losing my interface? Or just not play? All of your help will be greatly appreciated.

Many thanks!

---

### Post by EvanJackPenn on 2011-03-20
I fixed the drivers on the windows side. I used a modified INF (i think that's what its called) to install a generic driver.

However, I'm still too worried to try on Ubuntu. Help appreciated :)

---

### Post by EvanJackPenn on 2011-03-26
Sorry people, but I still haven't sorted this. All help would be appreciated

---

