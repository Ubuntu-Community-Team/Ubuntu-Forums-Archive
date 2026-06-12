---
title: "Always having to reinstall nvidia drivers"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by jdmpike on 2005-07-20
All,

I recently installed the NVIDIA drivers for my GeForce2 MX card on my Dell Inspiron 8200 and I am constantly having to reinstall the drivers for it. Everytime I shut down and boot back up, I get the NVIDIA splash screen flash on and off about twice and then the screen goes black. From there, I hit alt+f1 to get to the prompt, clear the screen of the Xserver error, and run **sudo sh NVIDIA-Linux-x86-1.0-7667-pkg1.run** which reinstalls the proprietary NVIDIA driver.

When I do the reinstall, it says that something has modified the driver since the last install, I really want to find out what is doing this and shake it until blood comes out of its ears.

Any help would be great - also at this point I think I would be oh-so happy to have my simple, open, but awful at 3D nv driver... it at least worked every time...

Much love for all of you Ubuntu-ers out there! Take care, God bless!!!

Peace, love, ubuntu!

---

### Post by wellery on 2005-07-20
follow this to install the drivers:

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by Khannie on 2005-07-21
This only tells how to install the default repository driver. I've had the same problem and am on the verge of ditching ubuntu and going back to windows.  :mad:

---

### Post by Gojyo on 2005-08-01
Hi,
I've the same problem, and I figured out where the changed files are.
After installind Nvidia drivers, two files (one is just a symlink) are copied into /usr/lib/tib/ or something like that (if you need the precise path just ask).
After starting X, those files are deleted.
The next time I try to start X, the screen becames sometimes black or sometimes white with strange lines. In both cases X doen't start, and I have to rebook the pc.

I'm wondering why those files are deleted and where exactly is the problem.
Someone has an idea?

---

