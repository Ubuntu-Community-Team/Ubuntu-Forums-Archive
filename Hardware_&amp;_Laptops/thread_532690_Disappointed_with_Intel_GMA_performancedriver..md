---
title: "Disappointed with Intel GMA performance/driver."
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by bogoliubov on 2007-08-23
I recently bought a laptop with Intel GMA 945 graphics. For some reason though, 3d acceleration is very poor under Feisty. I tried Egoboo and it displays 0 fps. Secret Maryo is extremely slow. Sauerbraten just crashes (though I'm not sure if this is because of the graphics driver or something else).

When I switched from the i810 driver to the intel driver, Egoboo displays decent fps but textures are missing. I've also experienced problems with the wireless network when using this driver (no idea why).

At work I use an external monitor, but setting this up is not easy and I've only succeded with the i810 driver. I have to use Xinerama, which means lousy 3d. I need to run visualization stuff, which uses OpenGL; this is not working very good (I have to keep the window on the laptop screen). 

Glxgears gives some 800-900 fps (i810 gives higher than intel for some reason). But if I boot the Dapper LiveCD I get 1700! 


I thought that since Intel released open-source drivers and since this card is quite common, that it would be working OK in Ubuntu. But it turns out to be a real dissapointment.
I also thought that Ubuntu was getting better by each release, but not in all areas obviously.
Having to edit xorg.conf then reboot just to plug in an external monitor or projector is not exactly user friendly.
Also, for some reason TV out is black and white here in Europe. I can't understand why this shouldn't work either. 
I still think Ubuntu is the best OS around, but some things should really be working better!


Oh, of course, if anyone has any ideas on how I can improve the performance, please let me know!

---

### Post by tseliot on 2007-08-23
The "intel" driver available in Feisty's repositories is not stable, "i810" is.

Ubuntu's next release will feature a stable release of the "intel" driver

---

### Post by bogoliubov on 2007-08-24
> **tseliot said:**
> The "intel" driver available in Feisty's repositories is not stable, "i810" is.

Ubuntu's next release will feature a stable release of the "intel" driver

I wouldn't consider any of them "stable". I know that Gutsy will most likeliy improve things a bit. But my point was that this stuff should really be working today. And the "intel" driver still don't have TV-out for PAL.

---

### Post by EXCiD3 on 2007-08-24
> **bogoliubov said:**
> I wouldn't consider any of them "stable". I know that Gutsy will most likeliy improve things a bit. But my point was that this stuff should really be working today. And the "intel" driver still don't have TV-out for PAL.

Its not so much Ubuntu's fault as it is the card maker's. They fail to realize that Linux users exist and will probably purchase hardware from them again if they ahve good linux support. However the Windows demographic is so much larger the overlook it too often. In time they will realize how much Windows really does suck.

---

### Post by bogoliubov on 2007-08-24
> **EXCiD3 said:**
> Its not so much Ubuntu's fault as it is the card maker's. They fail to realize that Linux users exist and will probably purchase hardware from them again if they ahve good linux support. However the Windows demographic is so much larger the overlook it too often. In time they will realize how much Windows really does suck.

Yeah, you have a point. But I really had my hopes up for this card since I knew that Intel released their driver as free software. Of course this doesn't necessarily mean that they give it as much effort as the windows one. But still I thought the drivers should have been more mature than the Nvidia drivers for Linux. 

Another thing that I mention is that the speed of the i810 driver under Feisty is about half of that under Dapper. Isn't this a Ubuntu issue only?

---

### Post by fig_jam_uk on 2007-08-31
What I cant understand is that under frdora core 7 the intel drivers work perfectly but under Ubuntu the fps is soooooo poor, I hope there will be a more stable version soon because I love Ubuntu and want to continue using it. 

Ubuntu :guitar:

---

### Post by TheIdiotThatIsMe on 2007-11-08
I have a mobile Intel915GM (according to hardware info anyways), and Ubuntu 7.04 for me to provide a decent driver and performance, and Ubuntu 7.10 so far has done the same. So while it's definitely not perfect, it's gaining some traction and adding support for more Intel mobile hardware, so hang in there and keep an eye out for a fix.

---

### Post by bogoliubov on 2007-11-08
Now in 7.10 dual monitors work OK thanks to Xrandr. The Displayconfig thingy has only caused me problems so far, so I stick with a little script (with a GUI) that I wrote to set up dual monitors for the GMA card.

I also managed to get slightly better performance by switching to X86-64. But the performance is still really bad. I know it's not a fast card, but for some reason it was faster in Dapper. Really strange...

---

### Post by TubaTodd on 2007-11-08
> **bogoliubov said:**
> Now in 7.10 dual monitors work OK thanks to Xrandr. The Displayconfig thingy has only caused me problems so far, so I stick with a little script (with a GUI) that I wrote to set up dual monitors for the GMA card.

I also managed to get slightly better performance by switching to X86-64. But the performance is still really bad. I know it's not a fast card, but for some reason it was faster in Dapper. Really strange...

I would like to try a dual monitor setup with my laptop and 22" ext monitor. Could you please post the script? Thanks

---

### Post by bogoliubov on 2007-11-09
Absolutely. But please know that I cannot promise that it will work for your system. Also, setting up extended desktop with a TV crashed Ubuntu. So if you want to use a TV, have it in clone mode.

Oh, also. The way it's made, one can't set up more than two monitors at once, and one has to be the internal display.

Also, how you can set up dual monitors with the GMA cards depend on your "Virtual" setting in xorg.conf. The whole desktop must fit into this, but if you have it higher that 2048x2048, DRI is disabled (no 3d acc.).


Put this script in a convenient place, then you can create a button on your gnome-panel that will run it (nicer than having to open a terminal).

---

