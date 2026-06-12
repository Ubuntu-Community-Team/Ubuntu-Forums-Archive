---
title: "HP HDX 9300 Media Remote"
date: 2010-08-14
forum: Hardware
---

### Post by ductoman16 on 2010-08-14
Hi, 
 This is my first thread here on ubuntu forums, so let's hope it goes well....

I have an HP HDX 9300 laptop with 64 bit Crunchbang linux lite (Based on ubuntu 9.04), and I've been trying to get my windows media center remote to work. It's a builtin remote that docks to the keyboard, and it's got a windows media center button and was originally designed for windows media center, so I'm assuming that's what it is. 

I've tried configuring it with gnome-lirc-properties and irrecord, both produced no result, except for the error message gap not found; can't continue by irrecord. Since then I've discovered that there is no entry for any sort of remote in /proc/bus/input/devices, and I'm assuming that's the problem. 

Also, the power button on the media remote does work to turn on the computer, so I know the remote physically works (I guess that functionality is in the hardware). 

I'm sure someone out there knows how to fix this, so thanks in advance.

---

