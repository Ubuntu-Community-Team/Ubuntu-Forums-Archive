---
title: "NVIDIA.com drivers installed OK, but just no screen (Ubuntu is there though)"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by Breepee on 2005-06-30
I've downloaded the latest drivers for my Geforce FX 5900XT from nvidia.com, installed them from console (as it requires) and everything went OK. I edited the xorg.conf as stated and rebooted. Guess what, no screen! I can see th console and the whole bootup procus until the point where X is executed. The screen goes black. Ubuntu is there though, I can login (without seeing what I'm doing) and I hear all the right sounds. I can shutdown by pressing the shutdown button. So obviously there something wrong, but I dont know what.

My specs:

Home-compiled 2.6.12 kernel (straight from kernel.org)
Geforce FX5900XT
IIyama Prolite E431S (17" TFT screen)

I've included xorg.conf, hope someone can get me back on track.

---

### Post by jobli on 2005-06-30
Hi!

There is a lot of people having problems with nvidia.
Search the forum for nvidia and maybe you will get a solution.
Right now I'm using the nv driver, it works.
Not so fun though..........

---

### Post by Tom^ on 2005-06-30
I had the same problem and I didn't figure out solution with ubuntu tools. Downloading & compiling drivers with nvidia-installer and installing proper kernel headers did the trick for me. I'm using GeForce 6200. 

This really needs to be issued. The screen isn't actually totally black, I can see little bit with high contrast screen.

---

### Post by njm106 on 2005-06-30
I have just had the same problem, I was about to give up but then I tried my TFT on the vga port and it works. Don't suppose anyone knows how to get the DVI port working?

---

### Post by Breepee on 2005-06-30
[QUOTE=Tom^]I had the same problem and I didn't figure out solution with ubuntu tools. Downloading & compiling drivers with nvidia-installer and installing proper kernel headers did the trick for me. I'm using GeForce 6200. 

This really needs to be issued. The screen isn't actually totally black, I can see little bit with high contrast screen.[/QUOTE]
 That's what I did. The stuff in apt-get doesn't work here.

I use DVI, maybe that's it? I'll try D-sub.

---

### Post by Breepee on 2005-07-01
[QUOTE=Breepee]That's what I did. The stuff in apt-get doesn't work here.

I use DVI, maybe that's it? I'll try D-sub.[/QUOTE]
 OK, I've connected my TFT with an analog cable and tada! It works! Only the mouse doesn't work on startup, I've to reconnect it.

Why won't DVI work? Anyone knows?

---

### Post by Breepee on 2005-07-01
OK, I read the readme.txt that comes with the drivers (should have done that first :)). Adding

Option		"ConnectedMonitor" "DFT"

to xorg.conf fixed my screen! Now only on bootup, my keyboard talks gibberish (for a short while) and the mouse is real slow (for a short while). Reconnecting them fixes it. Anyone know how to fix that?

---

### Post by Tom^ on 2005-07-01
[QUOTE=Breepee]OK, I've connected my TFT with an analog cable and tada! It works! Only the mouse doesn't work on startup, I've to reconnect it.

Why won't DVI work? Anyone knows?[/QUOTE]
 I actually used the d-sub and not the dvi and it didn't work.

---

### Post by Breepee on 2005-07-01
[QUOTE=Tom^]I actually used the d-sub and not the dvi and it didn't work.[/QUOTE]
 Did you remove the DVI cable from your videocard?

And try DVI again with that line I added, that works fine here.

---

### Post by ebonflame on 2005-07-03
I too am experencing the same thing with my DSUB connector.  I only use one monitor but once the text is done, I get a black screen.  I see the HD activity light go on and on, but eventually it stops any my screen becomes a display of blinking solid ASCI blocks.  I had to go back to the nv drivers to get X to work.

---

