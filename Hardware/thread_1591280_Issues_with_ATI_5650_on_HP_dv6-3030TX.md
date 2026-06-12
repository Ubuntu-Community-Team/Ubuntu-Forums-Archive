---
title: "Issues with ATI 5650 on HP dv6-3030TX"
date: 2010-10-09
forum: Hardware
---

### Post by maciek256 on 2010-10-09
Hi everyone,

I have just bought new HP Pavilion dv6-3030TX:
[http://apcmag.com/notebookhunter/hp-pavilion-dv6-3030tx.htm](http://apcmag.com/notebookhunter/hp-pavilion-dv6-3030tx.htm)

It's got ATI Mobility Radeon HD 5650, so I chose to install ATI drivers... and that's pretty much the end of my story. After rebooting the ubuntu loading screen shows up for a fraction of a second and then the screen goes black.

I have tried reinstalling ubuntu again and installing ATI drivers again and same thing happened. I just wanted to confirm it's ATI drivers causing trouble, not some other packages I've installed in the meantime. I've tried installing ATI drivers via both ubuntu's "hardware drivers pop-up" as well as manually downloading appropriate package for my card (seems ATI supports it) from ATI website.

Also, when installed ATI drivers, the "recovery" option from boot menu freezes forever, so my only option (I'm linux newbie) was to reinstall OS.

Has anyone else experienced similar thing?

Thanks!

ps. It's probably not useful info, but my ATI card works fine under Win7

---

### Post by P4man on 2010-10-09
Strange that recovery mode didnt work.

When its stuck in the black screen, can you try pressing control+alt+F1 and see if you get a login prompt for a full screen terminal? If so, log in (typing password doesnt show on screen, type it blind) and try running this command:

```
sudo aticonfig --initial
```

then reboot

```
sudo reboot
```

No guarantees, but its worth trying. 

Another thing to try is adding nomodeset to your boot options. In grub menu, edit the default boot line by pressing E, then go to the line that begins with "kernel", press E again, press END to go to the end of that long line. SHould end with something like "quiet splash". Just add nomodeset and so it looks like "quiet splash nomodeset" (no quotes). TO boot press (I think) control+X.

This will only apply for a single boot, but if it works, we can make it permanent.

---

### Post by ketafix on 2010-10-13
Hey I have the same laptop and recently did the same thing installing Ubuntu and then activated the ati drivers... after which I had the same issue... screen black out after the Ubuntu load screen and eventually I also had to do a clean installation, now that you are saying you have the same problem on the very same laptop, it seams it is a hardware bug, most probably with the ati card, im on the look out for a work around and have emailed ati regarding this... will post if I find anything

on a different not the card works perfectly under win 7 64 bit

Cheers

---

### Post by chrisjbell on 2010-11-13
I've got the same laptop and the same problem. It looks like the cause is that there isn't good support for the switchable graphics that are in our systems and since HP doesn't have a BIOS switch to choose between them that we are stuck using the basic Intel graphics. I've gone through all kinds of iterations and I can get the ATI drivers to load (fglrx) and get the same black screen. 

I'm pretty sure that what is happening is that the driver is trying to load but isn't able to switch over to the ATI hardware and when it loads the ATI driver on top of the Intel hardware it craps out. BTW, you can safely shut down your computer from that state by holding down <alt> and <prt scr> and then typing r s e i n b. If you had any luck logging on then you did better than I.

To get the system to run again, the easiest thing to do is delete the xorg.conf file out of /etc/X11. You aren't loading the ATI driver any more, though, even though the hardware driver app (System->Administration->Hardware Drivers) thinks it is. The ATI Catalyst utility knows better.

The really crappy thing is that the ATI hardware is still drawing power, so your laptop battery will drain at the high level graphics rate. There's a kernel patch available to turn it off, which I've installed but am not sure if it is really working. 

I could have the story wrong - but this is what I think the deal is. I've got my machine set up to dual boot Ubuntu and Windows 7. The graphics switching works great in Windows. Its a really nice graphics card, too. I can't wait to see it work under Linux. :(

---

### Post by webdevbrian on 2010-11-13
Yep same problem here.  I'm on a DV7-4070US, and learned the hard way my first time around with the "hardware drivers" pop up message that appeared when I first booted in.  Same symptoms as described above, and I registered just to reply I have the same issue.

Really needing my 5650 working, I'm a windows refugee, and just recently discovered the 3D rotating desktop ... my life has changed forever.

I hope someone finds a solution!

It's running quite nice on the integrated graphics by default, but like I said the 3D rotating desktop running, it gets a little slow :(

Best,
WDB

---

### Post by estima on 2010-11-27
Any news on this issue? Just bought a DV6 3030 SP and installed 10.10 X64. Same problem. After enabling the proprietary driver the X server will not start.

Removing the Driver line from the /etc/X11/xorg.conf will revert the X to the previous state. Booting corrrectly without the driver.

With the driver set in the xorg.conf I get this error in the X server log file.
 (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
 (EE) No devices detected.

Someone got this working?

---

### Post by sn3rd on 2010-11-27
> **estima said:**
> Any news on this issue? Just bought a DV6 3030 SP and installed 10.10 X64. Same problem. After enabling the proprietary driver the X server will not start.

Removing the Driver line from the /etc/X11/xorg.conf will revert the X to the previous state. Booting corrrectly without the driver.

With the driver set in the xorg.conf I get this error in the X server log file.
 (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found
 (EE) No devices detected.

Someone got this working?

Also waiting for a solution to this on a dv6 3063

In my case, I can get the system to boot by commenting out the driver option in xorg.conf

However, I'm unable to get the Intel graphics to work. I can do without massive 3D acceleration (games are on Windows), but I'd like it if I can at least use the Intel 3D acceleration (compiz and all that).

---

### Post by estima on 2010-11-28
Anyone tried de 32 bits version of 10.10? Mayb the driver works correctly with that version.

There are threads reporting success with the ATI driver and the 5650... I don't know why it won't work in this specific model.

---

### Post by Axalix on 2010-11-28
I use HP 3030er and I have absolutely the same problem :( I found that some useful info can be read here
[http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/](http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/)
though people claim, that there is no any reasonable solution yet.

> The proprietary ATI *fglrx* driver refuses to work because it  cannot deal with switchable graphics. It also does not yet support  kernel 2.6.34, but this can be fixed by patching the install scripts.  The big problem remains the changed memory address where the firmware  resides. You cannot do much about it because this is closed source. Yet  some kernel developers meanwhile try to modify *vga_switcheroo*  that it also copies the firmware when switching graphic adapters. We  just need to sit back and wait whether the kernel developers are  successful or will fail due to the closed source.
 Whether and when ATI addresses this problem with an updated driver remains unknown.
 The free *radeon* driver works but does not yet support 3D  acceleration, resulting in crappy desktop effects that are rendered with  software method. This may be an option if you require the DisplayPort  or HDMI output. But for everyday use, the Intel adapter is the better  choice at the moment.
I am also aware of some attempts people to ask HP whether they can add ability in BIOS to disable 1 video card. The response was "we do not plan to work on it". Thank you HP, thank you ATI and AMD.

[http://h30434.www3.hp.com/t5/Display-and-video/Envy-14-Turn-switchable-graphics-off-in-BIOS/td-p/289172](http://h30434.www3.hp.com/t5/Display-and-video/Envy-14-Turn-switchable-graphics-off-in-BIOS/td-p/289172)


also
[http://www.phoronix.com/forums/showthread.php?p=145549](http://www.phoronix.com/forums/showthread.php?p=145549)

---

### Post by aximab on 2010-11-28
Hi all,
  same problem here with an pavilon dv6-3162sf
As far as i know the 32 bits version does'nt help at all ( i tried it a few hours )
Does someone know if the last bios from HP allows to go back to a not so locked bios ? like to put discrete mode on one cards ?

---

### Post by Axalix on 2010-11-28
Hope, somebody will try and share experience in making custom BIOS with  [Phoenixtool]("http://forums.mydigitallife.info/threads/13194-Tool-to-Insert-Replace-SLIC-in-Phoenix-Insyde-Dell-EFI-BIOSes") so user could switch (or block) 1 card.
People already do that (sorry it's in Russian): [http://habrahabr.ru/blogs/DIY/108820/](http://habrahabr.ru/blogs/DIY/108820/)

Would be good to have this
[http://www.wfu.edu/~yipcw/is/t400/issues/images/bios-gfx-switchable.gif](http://www.wfu.edu/~yipcw/is/t400/issues/images/bios-gfx-switchable.gif)

---

### Post by aximab on 2010-11-28
As stated in a previous link, I blacklisted the radeon driver so i didn't get any more problem ( black console , recovery mode...) except that if i switch to a tty in graphic mode i can not go back to the graphics mode with alt +7 ..
When you rebuilt your initrd after blacklist the radeon there is no switch mode anymore so :
Does someone tried to blacklist the intel driver and see what's going on with the radeon or fglrx ?
i didn't dare to do it ( not so power user ...)

Sorry for the english ...French writer.

---

### Post by lmgarcess on 2010-12-07
Hi all I have and HP dv6-3031ss with the same problem. I have been tried everithing including the things from
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
and
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)
I thing that I will give up soon and Windows have won't this battle becuase unfortunately Who have the mone have the power. If some body know how to deal with gratefull to help...
In a world with out Walls and fences who needs Windows and Gates???
Luis

---

### Post by Marc128000 on 2011-01-18
I have an HP Envy 14, which also uses the ATI HD 5650/Intel setup. In my blog I have the step by step instructions to get the switchable graphics running correctly and also make it easy to switch between the integrated chipset and the GPU. 
[http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/)
Its titled Tackling switchable graphics. Hope you find it helpful.

---

### Post by aximab on 2011-07-13
The switch works now  fine for every one I guess. But this is with open source driver. 
Any news from catalysist driver?
 A few months ago i tried it and it resulted in a kind of disaster. Did someone succeed to get hardware acceleration with the amd's card ?

---

