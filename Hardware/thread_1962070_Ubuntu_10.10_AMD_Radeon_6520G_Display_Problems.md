---
title: "Ubuntu 10.10 AMD Radeon 6520G Display Problems"
date: 2012-04-20
forum: Hardware
---

### Post by Gazok on 2012-04-20
Hi,

I just purchased a new Thinkpad Edge 525, which comes with an AMD Radeon 6520G integrated graphics controller. I guess I should have checked before purchasing whether there were any problems with it. 

I tried installing Mint 12 and Ubuntu 11.10 before switching to 10.10. In both of these, the OS would boot until the xserver started, at which point the display would turn off. I then replaced the **'splash'** option in grub with **'nomodeset'**. After this, the screen didn't go blank, but GDM failed to initialize, and I was dumped in the console.

Now, 10.10: X and GDM worked fine, but my resolution is fixed at 1024*768. This is with the **xserver-xorg-video-amd** and **xserver-xorg-video-radeon** drivers. I tried manually installing the official AMD fglrx drivers, and created a new /etc/X11/xorg.conf file with the line ```
amdconfig --initial -f
```
After this, Ubuntu froze at the loading screen, so I used recovery to remove the xorg.conf file and uninstall the fglrx drivers.

I'm on windows at the moment and can't remember precisely, but:

lspci | grep VGA outputs Compatible AMD Radeon 97##.
xrandr -q says my minimum, maximum and current resolutions are 1024*768.

I tried ```
X :2 --configure
``` to generate a new xorg.conf file, but it only resulted in a segfault.

Does anyone have any ideas?

(I suppose just creating a new modeline for my actual resolution would be a Bad Idea?)

Thanks.

---

### Post by Claus7 on 2012-04-20
Hello,

10.10 has a nice support for proprietary fglrx drivers. I would recommend to follow the procedure:

wipe out everything as far as graphics drivers and configurations are concerned and start from scratch.

I think that it would be a nice idea to use proprietary drivers. 

I think also that your card is still supported.

Follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

DO NOT forget to start from scratch, otherwise, most of the symptoms about freezing have to do with messed up installations.

Regards!

---

### Post by LinuxFan999 on 2012-04-20
Ubuntu 10.10 is no longer supported. You can try Ubuntu 10.04, which is still supported.

---

### Post by mastablasta on 2012-04-21
> **LinuxFan999 said:**
> Ubuntu 10.10 is no longer supported. You can try Ubuntu 10.04, which is still supported.


it is supported but will go out of support soon.

11.10 shoudl work. what happens if you install the driver from additional drivers menu instead of manually?

---

### Post by Gazok on 2012-04-21
Hi,

My mistake - I first tried installing 10.10 from an old disc, but it was broken. I'm currently running 10.04.

I tried reinstalling from scratch, first manually, and then using X Team's PPA. The reason I'm not using the Hardware Drivers program is because it doesn't list any drivers available. X Team's version seems to be older than the version I installed myself, which is **"amd-driver-installer-8.961-x86.x86_64"**, but the outcome is the same as before. If xorg.conf is set to use the ATI/AMD drivers, it fails at start-up.

I ran the aticonfig program in a console, and it reported that no compatible adapter was detected, which explains why it's stalling.

After that, I reinstalled pretty much every xserver-xorg-video driver that had anything to do with AMD, but it's still not working properly.

---

### Post by MonkeyPaw on 2012-04-21
Can you hook up to an HDMI display for the install? If so, you might get a picture. Once installed, run the AMD proprietary display drivers before disconnecting from HDMI.

---

### Post by Gazok on 2012-04-23
The problem isn't that I can't get any video output, it's that neither driver is handling the graphics card properly. The open-source driver says the screen is "Unknown" and only allows a resolution of 1024*768, and the fglrx driver doesn't seem to like the card at all. Unless you're suggesting that one of the more recent Ubuntu releases might work with fglrx?

---

### Post by mastablasta on 2012-04-23
more recent releases have more recent fglrx.

---

### Post by MonkeyPaw on 2012-04-23
> **Gazok said:**
> The problem isn't that I can't get any video output, it's that neither driver is handling the graphics card properly. The open-source driver says the screen is "Unknown" and only allows a resolution of 1024*768, and the fglrx driver doesn't seem to like the card at all. Unless you're suggesting that one of the more recent Ubuntu releases might work with fglrx?

From my own experience dealing with Llano (your CPU), 11.04 will install with a picture no problem. However, the proprietary AMD drivers had noticeable lag. I went up to the beta 2 of 12.04 LTS, and could not get a picture on install. I ended up using an dedicated graphics card to get the install complete and the AMD drivers installed and everything worked with no lag. You don't have that option, but from what I've seen of others with Llano-based notebooks, they can get a picture while installing 11.10 or 12.04 through HDMI. Once install is complete, install the FGLRX driver and you should then get a picture on the panel. 

From what I have seen in the bug reporting, this issue has been fixed and merged in the later Gnome3 kernels. Hopefully the final release of 12.04LTS has this fix worked in so all those Llano users can catch a break. :)

---

### Post by Gazok on 2012-04-26
Okay, I managed to get my hands on an HDMI cable, an HDMI compatible screen, and an ethernet connection (wireless isn't working either, apparently) - a miracle, in my neck of the woods - and the Additional Drivers program found and installed everything correctly, and it works.

Woohoo!

I figure it would probably have worked for Ubuntu 10.04, but I forgot to uninstall the opensource drivers, which explains the errors. Ah well.

Thanks for everyone's help.

---

