---
title: "GeForce G210M (Sony Vaio PCG61112L - NVIDIA GLX"
date: 2009-11-24
forum: Hardware
---

### Post by wentzr on 2009-11-24
Hi, I just purchased a 64 bit core 2 duo sony vaio 14" laptop.. It has an Nvidia Geforce G210M GPU video card, and I'm having no luck after installing either the 185 or the 190 video driver... upon installing either and restarting, I get a black screen... as in the screen goes off... it's not displaying black pixels, it's not displaying *anything*. 

help please!

I haven't tried 32 bit karmic on this laptop but 64 bit is the point. i do 3d graphics and intend on using the laptop for 3D.

---

### Post by wentzr on 2009-11-26
ok.. so user "egghead" over on the nvnews forums has a work around for this for now supposedly it's worked for most everyone:
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)
Kudos, egghead!! 

You need to extract the EDID (hardware identifier for your laptop's LCD screen) from windows, then reference the bin file from within your xorg.conf. 

unfortunately this doesn't help me. as I have no windows on this laptop.

What was the first thing i did when i got my vaio 61112L? install suse, fedora and ubuntu after completely wiping the harddrive of win7 and all restore partitions that were on there... and of course the only windows i ever bought and used (win xp sp2) gives a BSOD while installing. . . so yeah. this work around requires you have windows running on the same laptop so you can extract the EDID. i guess my bad for throwing windows out the window.... or out of the picture.. whatever. 

If anybody happens be able to help me out by shooting me the EDID file for my specific laptop, I'd appreciate it *greatly*. The model in question here is a Sony Vaio.. The box says its the VPCCW13FX/B, and the underside of the laptop says its model PCG-61112L. The video card is the GeForce G210M and the laptop has a 14" display (1366x768. Thank you greatly to anyone who might be willing to pass on this specific EDID, you should be able to send me a message off the forums

Otherwise I might just return this laptop ... I thought I was doing GOOD by picking out one with an NVIDIA chipset over ATI. It's a shame cause i love everything else about this portable. again  I got it at Frys Electronics, sales guy actually pulled this from the back as they are a special build I suppose. shoulda been a red flag in my mind for running Linux, but i for whatever was under the impression that NVIDIA>ATI for linux support (I do high end graphics) and literally every floor model was stocked with an ATI card.

---

### Post by Daban on 2009-12-24
hi all

i have the same problem 
I just buy a Vaio laptop just like(GeForce G210M (Sony Vaio PCG61112L - NVIDIA GLX)

after installing nvidia driver i got a black screen , and i am really new in using ubuntu , so plz help me  for fixing that big problem 

note / i read this [http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

but really i couldn't undrastand most of it 
if there is a better way or other solve for this big problem plz tell me 

Best Regards.

---

### Post by RedSingularity on 2009-12-24
What does you xorg file look like?  Its located in /etc/X11/xorg.conf

---

### Post by Daban on 2009-12-24
i could'nt find it in /etc/X11/

what should i do?

i use ubuntu 9.10

---

### Post by cajual on 2009-12-24
Open a terminal.
Type `gksudo gedit`
Enter your password.
Click `Open`.
If no address bar is present, press CTRL+L.
In the address bar, type `/etc/X11`.
Double-click `xorg.conf`, and open it.

Now you can follow Egghead's advice.

CTRL+S to save, CTRL+ALT+BACKSPACE, or `sudo /etc/init.d/gdm restart` to restart your X Server.

---

### Post by Daban on 2009-12-25
Thanks cajual and RedSingularity

i didi'nt sleep last night Oops, but I'am really happy cause i solved my probliem by createing a new xorg.conf and puting the Section in to it

```
Section "Device"
   Identifier         "Device0"
   Driver              "nvidia"
   VendorName    "NVIDIA Corporation"
   Option            "ConnectedMonitor"   "DFP-0"
   Option            "CustomEDID"          "DFP-0:/etc/X11/daban.bin"
EndSection
```

and i got the EDID from my windows 7 and i create a file daban.bin in etc/X11/ , now nvidia working perfectly , and i just add a Compiz-Fusion

Thanks all for replay
and thanks for
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

.
Best Regards.

---

### Post by wentzr on 2010-01-02
> **Daban said:**
> Thanks cajual and RedSingularity

i didi'nt sleep last night Oops, but I'am really happy cause i solved my probliem by createing a new xorg.conf and puting the Section in to it

Best Regards.


it's great to fake X into thinking it knows about your screen, but I've run the same trick here and it is by no means a solution, unless compiz and youtube is as far as you happen to push the nvidia drivers, or eventually have to hit ctrl+alt+f1 again (like for say an NVIDIA update) and realize you're flying blind again...

My suggestion?? You, and anyone who hits this thread with this problem -** send a bug report to NVIDIA. this is a bug. They should know about it. **The "IgnoreEDID" option does nothing to remedy the problem either. settling for a "successful" workaround that requires installing windows is not a solution by any stretch.

---

