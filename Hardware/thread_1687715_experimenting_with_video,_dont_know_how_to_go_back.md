---
title: "experimenting with video, dont know how to go back to previous conf"
date: 2011-02-14
forum: Hardware
---

### Post by Josunik on 2011-02-14
Hello there friends,

I will was "playing" a bit with playmouth, I was trying to make my loading screen to look different, but all I did is to screw-up my video resolution; 
I am using an Nvidia card and my current Ubuntu is a 10,10 maverick.

I entered terminal and was trying different configurations for the splash screen with this command:

sudo update-alternatives --config default.plymouth

But I wasn't getting my new screen. then I did something really silly,

I downloaded a playmouth manager and tried the automatic configuration function for restricted drivers, and now my res is 1024-700 when it should be 1440-900, I get scrub to boot only in failsafe mode, it wont give me normal boot option, and then I will enter only in fail safe for my video.

is there a way to reset everything to how it was, like a fresh install of my drivers and config files, I don't know where to start?

when I go to system preferences I don't have to screen resolution option since I am using Nvidia x server settings, but  I get an error when i go there.

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

thanks

---

### Post by Josunik on 2011-02-14
ok, so far this is the error that i get when trying Nvidia x server

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

