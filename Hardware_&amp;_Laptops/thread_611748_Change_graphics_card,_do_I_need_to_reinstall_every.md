---
title: "Change graphics card, do I need to reinstall everything?"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Melhisedek on 2007-11-13
I'm fed up with ATi performance in Linux (gaming mainly) so I'm thinking of switching with my brother who has 6800GT (I have 1900XT :( ) until I get myself 8800GT or GTS down the road. 
Question is, can I do it without reinstalling Ubuntu, something like, remove ATi drivers, switch cards and than Ubuntu finds Nvidia and "installs" nv drivers? Or at least gets me to X so I can try and install them myself?

Any tips?

---

### Post by taurus on 2007-11-13
Edit /etc/X11/xorg.conf 

```
gksudo gedit /etc/X11/xorg.conf
```
and change whatever driver you are using right now to **vesa**.  Save it and shutdown the machine.

Now, replace the ATI with the new nVidia and boot the machine.  Once you get into X, install a driver for your nVidia in System -> Administration -> Restricted Drivers Manager.

Otherwise, you can reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```

No need to reinstall just because you switch video cards.

---

### Post by Melhisedek on 2007-11-13
Do I have to somehow remove ATi drivers I have now?

---

### Post by rsambuca on 2007-11-13
There is a line in the xorg which tells the system which driver to use.

---

### Post by ricanelite on 2007-11-13
now what happens if the graphics card is intergrated? How will you go about getting Linux to see the new graphics card?

---

### Post by Daelyn on 2007-11-13
> **ricanelite said:**
> now what happens if the graphics card is intergrated? How will you go about getting Linux to see the new graphics card?

Basically, the easiest way to identify H/W changes is to do the change and boot up with a LiveCD and run ```
lspci
```

It will tell you which PCI bus ID your "new" GFX (or whatever) has. If you need to edit the /etc/X11/xorg.conf manually that is.

Mount your Linux partition and backup the installed sessions **/etc/X11/xorg.conf** 

If Linux has it's own driver for the GFX card, just copy the Xorg.conf from the live session over to the one on your HDD,

If Linux on the other hand needs a driver not existing in linux itself, start ubuntu live in safe graphics mode and copy over that xorg.conf (dont forget to back up the pre existing one), then reboot into your installed session and install the correct driver as per instructions.

That is the easiest and most failsafe way according to me, but you can also try booting into safe graphics mode in your installed session and do a reconfig of xorg.conf with the driver install, the X config utility or manually.

Well, what do I know. Still a n00b. 

I would go the LiveCD way to see if all is working out of the box and just use that xorg.conf.

---

### Post by Daelyn on 2007-11-13
> **Melhisedek said:**
> Do I have to somehow remove ATi drivers I have now?

Get your new GFX card to boot up and run in VESA mode.
If you are already using the built in ATI driver, just reconfigure for your new GFX card and all should work just fine.

If you are using a installed ATI driver, I recomend you to uninstall it (I have a vague memory that there was some ati uninstall script in a ATI folder somewhere) when using vesa mode. Reboot into vesa again, install and do the config of the nividia glx driver. Then reboot again.

If you don't uninstall the separate ATI driver (not the built-in one now), you could be unlucky and get some issues with the links to OpenGL libraries, and as a result of that, bad performance in OpenGL or none at all.

I'm switching frequently between two GFX cards on my laptop (hybrid), and I had issues when I forgot to redirect OpenGL libraries depending on used GFX card. But, some tears and screams, and sleepless nights sorted that, eventually :)

---

### Post by ricanelite on 2007-11-14
well currently right now I have a Intel 950 Intergrated Video Card. I will be picking up a Geforce this weekend. Because Ubuntu Linux with Compiz/XGL is running really bad on my Desktop Gateway PC. Which is crazy because It is a Dual Core 1.6GHZ/2 RAM/and the computer is about 3 months old. I was looking at the bios and reading specs the Intel 950 Intergrated card has zero memory. So hopefully when upgrading the graphics card it will run this a lot more smoother.

---

### Post by rsambuca on 2007-11-14
> **ricanelite said:**
> well currently right now I have a Intel 950 Intergrated Video Card. I will be picking up a Geforce this weekend. Because Ubuntu Linux with Compiz/XGL is running really bad on my Desktop Gateway PC. Which is crazy because It is a Dual Core 1.6GHZ/2 RAM/and the computer is about 3 months old. I was looking at the bios and reading specs the Intel 950 Intergrated card has zero memory. So hopefully when upgrading the graphics card it will run this a lot more smoother.

It is an integrated card, so it gets allocated memory from your RAM.  Are you sure you need a new card?  You may just be wasting your money.

---

### Post by Daelyn on 2007-11-14
> **ricanelite said:**
> well currently right now I have a Intel 950 Intergrated Video Card. I will be picking up a Geforce this weekend. Because Ubuntu Linux with Compiz/XGL is running really bad on my Desktop Gateway PC. Which is crazy because It is a Dual Core 1.6GHZ/2 RAM/and the computer is about 3 months old. I was looking at the bios and reading specs the Intel 950 Intergrated card has zero memory. So hopefully when upgrading the graphics card it will run this a lot more smoother.

If you look at your specs of the machine it should say something about shared memory.
Doesn't really matter what it says, because you can override it in Linux.

You can use a "VideoRAM xxxxxx" (kbytes) switch in the /etc/init.d/xorg.conf to dedicate some RAM to your GFX card.

My intel GMA950 works splendid, even without use of any dedicated RAM. Haven't been bothered yet. When I need some power I just flip the switch, and reboot with the nvidia card activated instead.

---

### Post by itchy88 on 2007-11-14
does anyone know how to read the xorg.conf file from ubuntu live, the one it's using and copy it to the xorg.conf file that the installed version uses.  when i go in through the file system and the etc folder and the x11 folder, i'm not sure which one i'm looking at and where then the other one would be.

thanks!

---

### Post by Daelyn on 2007-11-15
You got that in your priv message, but for everyone else that don't know:

Ubuntu Live will create it's own file system in memory. All storage media hooked up to computer (being external hdd, sd reader etc) will as standard be mounted in "/media" folder. 

My USB HDD automounts when I load up Live, but the internal HDD is identified and I just need to click on the partitions in "Explorer" and they automount to /media/disk (and a number in case of need)

To view the UbuntuLive CD's own configfiles etc, just do the same as you do when you are on your installed session. 

Example, to edit Xorg.conf on Ubuntu Live
Open terminal
```
 sudo gedit /etc/X11/xorg.conf
```
enjoy!

---

### Post by Melhisedek on 2007-11-16
Maaaan what a dissapointment :( I opened everything up, mine and brothers PC pulled cards out and first when I was about to insert the nvidia one I noticed it is AGP while my mobo is PCI-E
I was sooo close to crying :)

---

