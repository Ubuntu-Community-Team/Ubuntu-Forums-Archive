---
title: "[SOLVED] ATI Multi monitor high res mode solved howto and explanation"
date: 2008-10-04
forum: General Help
---

### Post by f1r31c3r on 2008-10-04
Hey all good ppl welcome to my thread.

in this thread i am aiming to give you insight into my work around for the 2048x2048 limit on ATI graphics card.

I have dual monitors one is 1440x900 and the other is 1440x900 so identical resolutions with identical refresh rates connected via DVI. I am running stock Ubuntu hardy 8.4.1 with proprietary FGLRX drivers and compiz fusion on both monitors very smoothly and my card is FireGL X1 R300 chip so as long as you have a R300 +++(later) then this info and tutorial should work for you as it did for me note my graphics R300 is AGP It should work much better for you if you are running a PCIE card.

The Myth on texture size limit 2048x2048, urm well it's not a myth its a fact and its true lol. the R300 Firegl X1 card i have actually has a 2560x2560 texture limit but for compatibility reasons the limit of the older 2048x2048 is used this means that like with my resolution 1440x900 x2 is 2880x900 which exceeds not only the physical size of my card but the limited size of the value within Xorg.

This means no matter what you do how you do it OpenGL AIGLX will not span this high res full stop so it wont work but how did i get it to work you ask Am i fooling you? Am i tricking you? NO it does work and here is how.


when you add the resolutions of your monitors together they of course like in my case become 2880x900 instead of 2880x1800 this is because you are adding only the width of the screen together as your monitors are side by side making only the width the longer party.

Yup if you guessed it the secret is to have your monitors above and bellow. NOT Physically of course this in fact gives you a resolution of 1440x1800.

hope that all made sense if not lets look at the practical how to you should figure it out.

First install your Ubuntu desktop system i used the latest hardy 8.4.1 once installed enable the ATI restricted drivers etc etc and use synoptics manager to install fusion-icon and the advanced settings manager.


After all that is installed run the aticonfig utility in a terminal like this 


> sudo aticonfig --initial --input=/etc/X11/xorg.conf --dtop=vertical --overlay-on=1


Make sure it don't error if it says fglrx section found open xorg.conf in your editor and change the "fglrx" section to "radeon" then run the above command again it should say uninitialized file found etc etc backed up to etc etc

Once you've done this restart reboot or log out and back in again whichever and you will notice that the desktop has stretched vertically if it has not then go to:
> 
System -> Preferences -> Screen Resolution and you should be able to select a high res that elongates the display vertically rather than horizontally.

your mouse moves to the next monitor at the bottom of the first screen and the top of the second screen to get back to the monitor, windows will also drag the same way.

Now run Fusion-icon and select compiz as the window manager and emerald as the theme manager etc and you have 2 cubes and all slideable between monitors perfectly. all be it up and down rather than left or right

Hope this helps someone and makes your Ubuntu experience easier and much more fun thanks to every other developer and Linux users helpers etc on here for all your assistance and work in making this compiz and Ubuntu release a stable and fun OS.:D:popcorn::D

---

