---
title: "Graphic Card Driver Unknown"
date: 2011-11-26
forum: Hardware
---

### Post by sah000 on 2011-11-26
This is my First thread. Im also an epic noob at how everything works on ubuntu. So please explain how to do things in a easy to understand way. Im not used to this stuff.

UBUNTU 11.10 System Info: Graphics: Driver Unknown Experience Standard.

No idea whats going on with this :3.

Graphic Card: 82915G/GV/910GL Integrated Graphics Controller
I checked. I have NO IDEA if this is compatible with Ubuntu. I also checked google to see if i could download a driver for it.... In other words. I dont know what im doing :confused:. plz help

Extra question. What can the graphic driver help with?

---

### Post by Basher101 on 2011-11-26
as far as i know, there are two ways for graphics to be onboard, that is if it is either on the CPU chip or integrated on the motherboard. 
As for the driver, try ```
sudo lshw
``` that will output your ENTIRE hardware. Not sure if it also displays the driver tho..

---

### Post by BC59 on 2011-11-26
Well look here for a similar issue

[http://ubuntuforums.org/showthread.php?t=646064](http://ubuntuforums.org/showthread.php?t=646064)

---

### Post by grahammechanical on 2011-11-26
I see the same when I open System Info. This is a utility that is not fully functional. Do not worry about it. Linux/Ubuntu is an OS under development. We accept this. After all it did not cost us anything, did it?

If you have a working Ubuntu on your computer then your video adapter is compatible with Ubuntu.

Open the Dash and search for Additional Drivers and open that. It may offer you a proprietary driver. If you choose to do this the utility will download the driver and install it for you. When the driver is installed you will also get a configuration utility for your video card. You will also find it in the Dash.

You may find that you can only use the built in driver and that this driver is limited in what it can do with your video adapter because this driver is still under development.

This is why we have the ability do run Ubuntu from a CD to test it so that we know that our hardware is compatible with Ubuntu.

Have tried going to System Settings>Displays and seeing what that says about you video system.

Regards.

---

### Post by sah000 on 2011-11-27
So pretty much, i cant do anything about it. OK then.

---

### Post by Mark Phelps on 2011-11-29
You have an "old" Intel 915 chipset -- and Intel hasn't written any drivers for this since the days of Windows XP.  If you're having problem with the default drivers, the only solution is to upgrade the video card.  As far as I know, there are no newer drivers available.

---

### Post by MoreOrLess on 2011-11-30
So what is the problem (other than the system info incorrectly reporting no driver) ?

---

### Post by dasnk on 2011-12-02
I have the same problem.

It is a problem for me because i don't know what "experience standard" means, it could mean that i am not getting the "best" experience, and this could be because it has an "unknown" driver.

I installed the driver via the Ubuntu additional drivers utility, I don't understand how the OS cannot know the driver, when the OS is what presented with me the driver in the first place?

---

### Post by MoreOrLess on 2011-12-03
The issue in only with the sysinfo program. It's not hurting your system. Stop using sysinfo (it's for clueless Windows converts) or report a bug against it if it bothers you. Use glxinfo to verify your video driver is installed correctly if you're still worried about it.

---

### Post by edocastillo on 2011-12-20
Try with 
```
sudo apt-get install mesa-utils
```then
```
glxinfo | grep direct
```

---

