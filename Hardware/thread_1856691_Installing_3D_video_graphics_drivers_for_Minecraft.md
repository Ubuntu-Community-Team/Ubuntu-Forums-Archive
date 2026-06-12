---
title: "Installing 3D video graphics drivers for Minecraft"
date: 2011-10-08
forum: Hardware
---

### Post by anotherstiffler on 2011-10-08
Hello,

I have a Samsung QX410 Laptop. I've installed Ubuntu 11.10 recently, upgraded from Ubuntu 11.04. I'm trying to get the correct drivers installed and activated so that I can enjoy Minecraft, a game. Because the drivers I have installed currently are not suited for 3D games or advanced graphics handling, the game crashes when I load it and I can't get passed the login screen.

I have never had proper drivers activated, even while using 11.04. 

When I try to launch Minecraft, this is the error that I get (immediately after logging in):

> Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 10/8/11 6:49 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (amd64) version 3.0.0-12-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:233)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT ae43d6f1 ----------

I believe this just has to do with the video drivers not working. The laptop is fully capable of playing Minecraft, as I've played it extensively while using Windows 7, and was even able to get it to work one random Ubuntu install a while back.

Thanks for the help.

---

### Post by Redblade20XX on 2011-10-08
Can you please post your graphics card? So we can find the proprietary drivers which give better 3d results. :)

-Red

---

### Post by anotherstiffler on 2011-10-08
> **Redblade20XX said:**
> Can you please post your graphics card? So we can find the proprietary drivers which give better 3d results. :)

-Red

I'd be glad to! Thanks for replying. 

NVIDIA GT218 GeForce 310M (rev a2)

---

### Post by Redblade20XX on 2011-10-08
If you want to test out the proprietary drivers to see if this rectifies the problem. Can you look under System ==> Admistration ==> Hardware Drivers and click it. You'll be able to see the proprietary drivers available to your system.:p

- Red

---

### Post by anotherstiffler on 2011-10-09
> **Redblade20XX said:**
> If you want to test out the proprietary drivers to see if this rectifies the problem. Can you look under System ==> Admistration ==> Hardware Drivers and click it. You'll be able to see the proprietary drivers available to your system.:p

- Red

Have already done that. There are two drivers available that I have selected and tried working with (both say they work with 3D). Neither works with Minecraft.

---

### Post by Bucky Ball on 2011-10-10
11.10? You are looking for a world of issues there and if you want a simple life and just getting a game to run I would advise maybe a release that is stable. I have asked the mods to put this in the Oneric forums. ;)

---

