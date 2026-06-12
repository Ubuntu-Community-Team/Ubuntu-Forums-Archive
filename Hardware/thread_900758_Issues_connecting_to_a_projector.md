---
title: "Issues connecting to a projector"
date: 2008-08-25
forum: Hardware
---

### Post by InfernalNeutrino on 2008-08-25
Hi all,

The situation is as follows. My wife and I have a pair of sony vaio laptops, which we use a fair amount for our research. One of the things we often have to do is give powerpoint (or actually, beamer for us) presentations and such at conferences or meetings or whatever, and in general it's good if we could use our own laptops to connect to the projectors used for these things. Now, I've been using xrandr to connect just fine, but my wife's laptop won't register the proper resolutions for a projector. Here is what I see on my computer:

> ~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected (normal left inverted right x axis y axis)
   1280x768       59.9  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.9*+   60.0  
   1280x768       60.0  
   1152x768       54.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)


My laptop is a sony SZ430N with the 64-bit Xubuntu 8.04 installed. I haven't messed at all with xorg.conf or any drivers. Here is what I see on the other laptop:

> ~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA connected 640x480+0+0 (normal left inverted right x axis y axis) 708mm x 398mm
   640x480        60.0*
   720x400        70.1
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.9*+   60.0
   1280x768       60.0
   1152x768       54.8
   1024x768       85.0     75.0     70.1     60.0
   832x624        74.6
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
TV disconnected (normal left inverted right x axis y axis)


That computer is a sony SZ491N with the 32-bit Kubuntu 8.04 installed. Again, I haven't messed with xorg.conf or any drivers. I connected both computers to the same thing for these tests (in this instance an LCD tv). Both computers are running the same version of xrandr. As a side-note, my advisor's vaio, which runs 32-bit Ubuntu 8.04 also gets the resolutions correct.

My question then is: what could there be different between the installations that would cause xrandr to get the resolutions correct for one but not the other? Thanks!

---

### Post by IntuitiveNipple on 2008-08-25
I've seen something similar before in a slightly different context, and then it was the differences between 32-bit and 64-bit that was the crucial part. Basically, 32-bit libraries can query video devices for their EDID information whereas 64-bit can't (a library/BIOS issue).

I'm wondering if that is what is affecting the results here?

If your wife's laptop is 64-bit capable, would it be worth starting it from the amd64 LiveCD and see what it makes of the projector?

Alternatively, start your laptop from an x86 (32-bit) LiveCD and compare results that way.

At least that way you'd get a clue as to whether it is a subtle hardware difference, or the CPU architecture.

---

### Post by InfernalNeutrino on 2008-08-26
All righty, so I managed to test with a couple live CDs I had lying around. Xrandr was able to read the proper screen resolutions for a projector with both 8.04 Xubuntu 64-bit and 7.10 Ubuntu 32-bit live cds on her computer.

I then tried a 7.10 Kubuntu 32-bit live cd on my computer, but that test was inconclusive because I had to start it in safe graphics mode so it didn't register any external displays at all. I currently am downloading an 8.04 Kubuntu live cd to try out on both computers. I'm now wondering if there is something different about Kubuntu vs. X/Ubuntu that is making the difference independently of the architecture? As I understand it, xubuntu and ubuntu have more in common than ubuntu and kubuntu. I suppose another interesting test would be to install ubuntu, see that it works, and then swap out gnome for kde to see if that works.

It just seems odd that the symptoms would appear to be delineating along desktop environment lines rather than architecture or something else. The xrandr package being used by both the working and not working installations appears to be the same (version number checks out). Weird. Anyways, I guess I have a few things to check out on my own, but if anyone had any additional insight I would of course appreciate it :)

Cheers!

---

### Post by IntuitiveNipple on 2008-08-27
I think I'll let you do the digging on this one! I'm sure you'll find out that there's some obscure and hard-to-find difference in the flavours that makes it all seem obvious... after you've spent many hours banging your head against the wall :D

---

### Post by InfernalNeutrino on 2008-08-28
I figured I would post the final chapter on this little story :)

So I booted from a new 8.04 live cd, and magically it recognized things properly (magically since the computer was running 8.04 kubuntu so in principle it's the same thing). So, due to the wonders of resizing partitions, I made the computer dual boot kubuntu and kubuntu lol. The new install seems to work just fine and the old one still has its problems. I'll just spend some time migrating files over and then just remove the old install. Cheers!

---

### Post by IntuitiveNipple on 2008-08-28
Is it worth doing a diff of the /etc/ files to try and discover any setting that might be causing it?

The other thing would be, if those settings are stored per-user, to try a new clean user account on the *dodgy* installation. I've seen that several times as a solution for various weird problems.

Just don't go copying things over and recreate the issue on the *good* installation! :D

---

### Post by InfernalNeutrino on 2008-08-29
That is a good point. When I actually start looking at migrating things, I'll check out what differences there are and see if I can narrow down what's causing the issue. If I can isolate something, I'll be sure to post it so the next guy doesn't end up confused like me :)

---

