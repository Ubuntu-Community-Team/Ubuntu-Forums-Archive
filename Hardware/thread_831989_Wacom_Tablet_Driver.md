---
title: "Wacom Tablet Driver"
date: 2008-06-17
forum: Hardware
---

### Post by samirar on 2008-06-17
I have installed the Ubuntu 8.04 Wubi on my desktop as a separate program and am very happy with it except for one thing.

I have a Wacom USB tablet on my computer model number CTE-430 (Graphite) which is not working properly. The cursor does not reach the far ends of the screen although I move the pen or mouse all the way. This is quite frustrating

Can you guide me to find and install the right driver for this tablet without too much complications as I am not very familiar with commands in the Terminal

---

### Post by argail1980 on 2008-06-17
hi, I have a bamboo fun running, and it's working good.

tell me what you did to get it working

---

### Post by samirar on 2008-06-18
> **argail1980 said:**
> hi, I have a bamboo fun running, and it's working good.

tell me what you did to get it working
Honestly I have done nothing. I was looking for a driver but I find it very confusing and difficult to do so in the linux system

---

### Post by jazzybob on 2008-06-18
Hi.  Use synaptic and type wacom or tablet.  The "drivers" are in Ubuntu 8.10.  There is also a wacom-tools package available from the synaptic package manager also.

---

### Post by argail1980 on 2008-06-19
well, this is kind of a beginner's question too, but, there's a source package for wacom tablets. Where does aptitude install them and where do I have to compile them?

I downloaded the driver source from [http://linuxwacom.sourceforge.net/]("http://linuxwacom.sourceforge.net/")

unpacked the tarball: 

(hit Alt+F2 and enter 'gnome-terminal') without quotes of course
then in the terminal cd to the place where I downloaded the source package
```
tar xvjf linuxwacom-0.7.9-4.tar.bz2
```
and followed the readme inside.

There's also a detailed HOWTO on that webpage.

---

### Post by samirar on 2008-06-20
Thank you for the advice. I used this method and the stylus is working except that the pointer does not cover the whole screen. It gets stuck at the top and I cannot reach the top menu. In other words the movement on the tablet does not correspond to the movement on the screen

---

### Post by argail1980 on 2008-06-20
there is a config tool called ```
wacomcpl
``` this might change the settings you want (can't say for sure, 'cause I have no tablet right here at the moment)

---

### Post by shnurui on 2009-09-27
> **argail1980 said:**
> there is a config tool called ```
wacomcpl
``` this might change the settings you want (can't say for sure, 'cause I have no tablet right here at the moment)

I can get the 'stylus' on my bamboo fun to traverse the whole screen, 640/480 at a time, if I "stroke" the pen.

I can't get the cpl util to work though, it doesn't see my devices.

---

### Post by Favux on 2009-09-27
Hi shnurui,

Are you in Jaunty 9.04?  If so the problem is that the 10-wacom.fdi is not parsing the names HAL/dBus is retrurning into linuxwacom names.  If not in Synaptics Package Manager check to ensure that wacom-tools is installed.

To see this enter in a terminal:
```
xsetwacom list
```
You should see stylus, eraser, cursor (if you have a wacom mouse), and pad.  If it's blank to see what HAL is calling your wacom devices enter:
```
xinput list
```
To get a wacom.fdi that parses the names correctly see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Hope this helps.

---

### Post by jtappin on 2009-09-27
> **jazzybob said:**
> Hi.  Use synaptic and type wacom or tablet.  The "drivers" are in Ubuntu 8.10.  There is also a wacom-tools package available from the synaptic package manager also.

8.10 is probably the worst choice for Wacom tablets.

In 8.04 and earlier, there are some extra lines you need to add to your xorg.conf in order to get the tablet to work properly, and you need to restart X after plugging it in.

In 9.04 (and later, I expect, though I've not tried) once you've installed everything called *wacom* it just works without any further ado.

But in 8.10, you need the extra lines to get the tablet to work properly BUT if you try to start X without the tablet it will come up in safe mode.

---

### Post by xecutech on 2009-09-27
I have had so many issues trying to get my to work as well. I don't use my tablet much with my laptop, but it's driving me nuts that it doesn't work.

---

### Post by Favux on 2009-09-27
Hi xecutech,

Is it a Wacom tablet?  If so then it will work.  What version of Ubuntu are you using?  Which tablet do  have?

---

