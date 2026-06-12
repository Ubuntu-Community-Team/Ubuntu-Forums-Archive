---
title: "Lenovo T61 with Intel GMA X3100 GM965 DRI/Dual Head"
date: 2008-06-29
forum: Hardware
---

### Post by canoe529 on 2008-06-29
Hi folks,
I just bought a Lenovo T61 laptop with the Intel GMA X3100 GM965 video card. By and large, everything works on the laptop and I love it. The only thing I'm having trouble with is getting the VGA output to work in a dual-head configuration and getting 3D acceleration to work. I've searched the forums for any information, and come up with some useful posts, such as [this]("http://ubuntuforums.org/showthread.php?t=506744"), but they solutions they talk about don't seem to solve the problem for me. I've uninstalled the VESA and i810 drivers and installed the xorg-xserver-video-intel driver, to no avail. Does anyone out there have experience getting 3D acceleration and dual-head mode working with this video card? Or has anyone downloaded the source from Intel ([Intel Linux Graphics]("http://intellinuxgraphics.org/download.html")) and compiled from scratch? How did that go? 

Thanks!

---

### Post by Dimitar Uzunov on 2008-06-29
I also cannot get hardware acceleration to work! But I have a R60e with a 945GM. It seems to be a 7.10/8.04 problem as I did have hardware acceleration before that. I know - I haven't had much use for hardware acceleration for some time :-) I was having a lot of work. I have the same drivers installed but it still doesn't work. Games are choppy and the GPU has a temperature of -128° C. I worry that my CPU is getting hotter because of this. Its currently around 46° C.

Thanks in advance.

PS. I forgot to mention that I use Ubuntu, not Kubuntu, but its the same in this matter, isn't it?

---

### Post by canoe529 on 2008-06-30
I downloaded the Intel drivers and tried to compile them. That went well enough, but I ran afoul of the Mesa drivers. Specifically, in a dependency of the Mesa drivers. In order to compile Mesa, I need several other packages, including libXext. I downloaded that from the repository but it errored out during the autoconf script with:
Requested 'xproto >= 7.0.13' but version of Xproto is 7.0.11
Requested 'x11 >= 1.1.99.1' but version of X11 is 1.1.3
Requested 'xextproto >= 7.0.3' but version of XExtProto is 7.0.2

The second one really threw me. Does 8.04 really use a version of X that is that far out of date? 

On second thought, I don't know that it matters. I already have all the Mesa stuff installed, unless they changed the API, all I should have to do is use the intel DRI drivers. I'll give that a shot and we'll see how it comes out.

---

