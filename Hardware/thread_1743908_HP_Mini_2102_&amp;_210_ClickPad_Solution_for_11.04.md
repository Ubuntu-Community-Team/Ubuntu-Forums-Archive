---
title: "HP Mini 2102 &amp; 210 ClickPad Solution for 11.04!!!"
date: 2011-04-29
forum: Hardware
---

### Post by VideoRoy on 2011-04-29
Sorry for a double post but the other thread has been marked solved for quite some time even though it is not.

I know many people have been waiting for a fix and some of us had it working in 10.10 but it broke in 11.04.

Well due to some hard work by a few folks in the link below I seem to have a working solution!!!!

I followed the build instructions in post #144 in the link below and created a new .DEB package.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809")

Note: I had to uninstall Synaptics Xorg driver in Synaptic manager before installing my new .deb or else it just reinstalls the original.

Here are the features I use that are fixed:
1. Left Click Button Drag
2. Right Click Button
3. Right side of pad scroll

I can also confirm 2 finger tap emulates a Right Click but I think that worked in 11.04 already.
 
I do not use any of the other multi-finger or advanced features due to a slight disability in my fingers so I cannot confirm if anything else works.

This probably works for other computers that use the Synaptics ClickPad.

Good luck!

---

### Post by Gaby_A on 2011-05-12
I tried to follow the instructions in post #144 but i get stuck at the beginning. When I type "apt-get source xserver-xorg-input-synaptics" i get a reply in the terminal saying that the xserver-xorg-input-synaptics package couldn't be found, i tried copy-paste to avoid typos several times but i always get the same answer. 

Maybe the solution is simple, but I'm a total newbie and i'm completely  lost about what to do next. Please help :(

---

### Post by LaHyenne on 2011-05-24
Hi, this solution kind of worked for my computer. I am still in trouble when I want to click with my mouse sometimes moving around randomly, but essentially it is now usable. Which is great compared to what I went through!

@Gaby_A > apt-get is secure and needs you to add "sudo" at the beginning of the line.
"sudo apt-get  source xserver-xorg-input-synaptics"

---

