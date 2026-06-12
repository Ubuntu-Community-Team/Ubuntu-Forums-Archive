---
title: "CPIA Error"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Tuxgrrrl on 2007-01-19
Fellow Humans all, greetings from the edge of the world.
Me Pengies coffed oop a Cleese ball....

I have this Intel® QX3T microscope to set up for a young scientist and I am lookin more stupid than usual here........
The ONLY working model we have found is using the CPIA package.
I have the latest CPIA deb but when I give it to the installer it gives me "Error: dependency not satisfiable: python".
Of course we are using python! The latest, and Idle.
The problem is that the installer takes the direction from the package to look for Python PRE 2.4 and I dont know how to tell it to accept a later version.
So far the same problem exists in Edubuntu and Knoppix as well. I am going to try more distros this weekend.

We posted on the Knoppix and Kubuntu forums and got lots of reads but no replies.
I washed up and brushed my teeth this time.

We need more detail but the installer, CPIA page and package contain zippy. ](*,) 
We tried searching and got nothing for the last couple years and none of it addresses this error.

Maybe its from the Ministry of silly error messages.

Is there a way to go around this error?


Thanks ALL.

---

### Post by x64Jimbo on 2007-01-19
Compile from source?

---

### Post by Tuxgrrrl on 2007-01-23
Those who have gone before tried to compile it and failed with the versions beyond 2.4xx.
We have the added burden that machine is being used for the students daily school so I cant go crashing about for more than a few hours at a time when I am tired myself.
The current tactic is to try to fool the CPIA package with some kind of "version ignore" or even somehow segregate the 2.4 ???? I dont know enough to guess what will happen if I try to install <<2.4.
Any help would be greatly enjoyed.

Thanks for your time.

---

### Post by linux_author on 2007-03-19
> **Tuxgrrrl said:**
> Those who have gone before tried to compile it and failed with the versions beyond 2.4xx.
We have the added burden that machine is being used for the students daily school so I cant go crashing about for more than a few hours at a time when I am tired myself.
The current tactic is to try to fool the CPIA package with some kind of "version ignore" or even somehow segregate the 2.4 ???? I dont know enough to guess what will happen if I try to install <<2.4.
Any help would be greatly enjoyed.

Thanks for your time.

- i am running my QX3 microscope under Ubuntu 6.10 as i write this... the scope works great (as it always has under older versions of Linux and Mac OS X)... the problem is the use of the upper/lower lighting - controls previously taken care of by a small Python script... i get around this by using external lighting - a small USB LED lamp...

- i'm testing a few video devices with Ubuntu at the moment, but first followed directions on updating the v4l driverset for the WinTV HVR 950, found here:

[http://lunapark6.com/?p=2682](http://lunapark6.com/?p=2682)

- after rebooting, i plugged in my QX3, then ran the xawtv client... the default video0 device worked fine... however, i had to put my notebook (an HP L2000 'Lance Armstrong' model) into a 16bpp X session - editing /etc/X11/xorg.conf to change the default session to:

 DefaultDepth    16 

- under xawtv, i used Video Source: Camera, TV Norm: PAL, and  Capture: grabdisplay...

my QX3 works under 6.10!

---

### Post by linux_author on 2007-03-19
- here's a screenshot (60x of a US$0.10 coin - a dime), but the screenshot and image, instead of being acquired via xawtv is acquired via The GIMP's Acquire menu! W00t!:

---

### Post by Tuxgrrrl on 2007-03-24
KewEL Author!

Off to try it. We have a bunch of light sources to try out. Did you take the frost plate off?
Now I just have to straighten out my Python mess I created trying to get 2.4 to play nice......
Will check back with light tests.

Happi Dukkies!

---

