---
title: "Upgrade to UbuntuStudio9.04 now screen resolution is stuck at 800x600"
date: 2009-06-12
forum: Hardware
---

### Post by grand_tale on 2009-06-12
hey guys.

i searched the forum and the related posts ive seen doesnt answer my question since im new to ubuntu and the linux world.

my problem is that i had ubuntu 9.04 succesfully installed and up and running. had resolution problems but somehow i did something to fix it. 

now...

i have installed the ubuntustudio 9.04 packages, graphics, audio and video, and when i try to log in with the rt-kernel, i get an message that says low graphics mode and ubuntu cant load my screen. when i fiddle through the menus i can log in but the resolution is stuck at 800x600. here is what i already did:

1. i tried to install the latest driver of nvidia-glx-180 again and to activate it but it just brings up the popup for downloading and does nothing.

2. under synaptics nvidia-glx-180 shows its already installed (it works on the generic kernel.)

3. the nvidia x server settings doesnt load. gives a message saying something about x server is not running or something. 

4. the output of the command "xrandr" doesnt recognize my screen i think. it doesnt show the available resolutions above 800x600 like when i load the generic kernel. it looks like it either doesnt see the drivers or doesnt recognize my screen.


did some of you have this problem too? i dont know why the resolution in the generic kernel is working now and not in the rt-kernel.

hope you guys can help me please.

regards.

---

