---
title: "Desktop effects not working... why?"
date: 2008-09-11
forum: General Help
---

### Post by styles234 on 2008-09-11
Ok, so my parents computer is already running Linux Fedora Sulphur and that works fine, but I live booted Ubuntu today and found that the desktop effects worked, but the system was really slow, so I never got a good representations of them.
So I tried the same thing on my computer with a bit more power, but it said they desktop effects could not be enabled.

For reference, I'm am running a 1.8 GHz Sempron (lame I know) 768 MB of RAM, and an Nvidia GeForce 6600 OC PCE-E with 512 MB.
There is enough graphical power to run them, but why is it they don't work?

Any help would be greatly appreciated.

---

### Post by Another Monkey on 2008-09-11
Is your card supported or is it blacklisted?  Check the two stickies at the top of this forum.

Also, [this post]("ubuntuforums.org/showpost.php?p=5770449&postcount=3") may help (or it may totally confuse you, I'm a newb too)

---

### Post by Whiffle on 2008-09-11
I'm thinking its because you're using a LiveCD and you have NVIDIA hardware, which needs "restricted drivers" to enable effects, and AFAIK, that isn't possible/enabled on a LiveCD.

---

### Post by styles234 on 2008-09-11
is there anyone who can provide step by step instructions as to what to do? What to download if there is anything, where I can find it... all that good stuff.

---

### Post by semitone36 on 2008-09-11
I dont know if i heard you right. Did you say that you are only running in Live? If so im not sure I can help you, I only know how to work an installed version of Ubuntu.

What I would recommend if you installed Ubuntu is making sure you NVIDIA driver is running.  On my rig my NVIDIA card uses an unsupported driver but it still runs perfectly.  There should be an icon on the top panel of your desktop that says something like "unsupported drivers". If you click on it (and i assume youre using Hardy here) it will bring you to a page that will allow you to enable your NVIDIA driver.  This is how i got mine working.

The next step is to install Compiz Fusion.  Youll find it easily in the Synaptic Package manager.  Once installed youll find it in System-Preferances-Advanced Desktop Settings.

The last thing that you have to do before you can enable your desktop effects is you must go Settings-Preferences-Apperance.  Click on the last tab desktop effects and enable either Normal or Extra to enable the effects in Compiz.

Hopefully this will get you through. If not, im sure someone else around here will be able to help you better than i can :guitar:

---

### Post by styles234 on 2008-09-11
But see why does the effects work on my parents old piece of crap computer while running it in live? like this thing has no power.... no graphics card worth mentioning (old Intel integrated thing) Plus, when I ran it live on my system, there was nothing there for an un-supported video driver... it was installed fine, I just could not enable desktop effects. It doesn't make sense to me, like it has me baffled.

---

### Post by ellalan on 2008-09-11
Hi
can you go to System-> Admin-> Hardware Drivers and see whether you have the device driver enabled, if not you can enable it and try.HTH,

---

### Post by Whiffle on 2008-09-11
> **styles234 said:**
> But see why does the effects work on my parents old piece of crap computer while running it in live? like this thing has no power.... no graphics card worth mentioning (old Intel integrated thing) Plus, when I ran it live on my system, there was nothing there for an un-supported video driver... it was installed fine, I just could not enable desktop effects. It doesn't make sense to me, like it has me baffled.

Your parents computer has a graphics chipset that has open source drivers (like Intel), and those drivers are the ones that are shipped with Ubuntu, on the LiveCD.  Your computer, on the other hand, has an NVIDIA chip, which "works" with open source drivers, but requires the closed source drivers from NVDIA itself to do anything fancy (like desktop effects or 3d games), which are not included on the LiveCD, and can't be installed in a LiveCD session. 

In order to get it working, you'd have to install Ubuntu to your hard drive, and then install the NVIDIA drivers.

---

