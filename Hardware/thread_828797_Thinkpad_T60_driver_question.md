---
title: "Thinkpad T60 driver question"
date: 2008-06-14
forum: Hardware
---

### Post by MaindotC on 2008-06-14
I screwed up my video configuration and I accidentally "moved" instead of "copied" configurations in /etc/X11/xorg* to xorg.conf so I'm trying desperately to set this up properly.  What happened is for some unthinkable reason I decided to install the ATI proprietary driver from the amd website and I didn't do it by the wiki and now I'm stuck w/ 800x600 resolution, booting into "low-graphics" mode, tiny letters at login - T60 users know what I mean.

So I disabled the restricted driver, rebooted <steps missing here>, enabled the restricted driver, rebooted <steps missing here> and I'm trying to go back to the usual resolution.  I have an external 21'' monitor that I set to 1600x1200.  Unfortunately, I'm not sure what to change in Screens & Graphics.

In the Screens & Graphics menu the driver keeps appearing as vesa.  I believe I select "fglrx", correct?  I did that but I'm still booting into low graphics mode.  If you can advise me of settings I should put, gui-style not command line, I would appreciate it.  Very frustrating.

---

### Post by MaindotC on 2008-06-14
How do I get my machine to use fglrx and stop reverting back to vesa?

---

### Post by Abu_Dayya on 2008-06-14
Try the following, it worked for me with my nvidia:

- sudo dpkg-reconfigure -phigh xserver-xorg
- reboot (if after rebooting the resolution went back to 600x800 do the previuos command again)
- install the driver
- reboot
- if the resolution is still bad, go to the restricted driver manager and  enable ATI driver

---

### Post by MaindotC on 2008-06-14
Thanks for the reply.  Once I enable the driver, do I choose "fglrx" in Screens & Graphics?

---

### Post by MaindotC on 2008-06-14
bump

---

### Post by MaindotC on 2008-06-16
Ok - how about this.  I re-installed and enabled the restricted drivers, ran all the updates and such.  Now, I would really like to download and install the latest driver per the instructions in the thinkwiki entry (Ubuntu Gutsy on a T60) but I'd like to be able to revert my machine to its original state before this driver I install crashes my system.  Can you help me with this?  Thanks!

---

### Post by MaindotC on 2008-06-16
bump x 10

---

### Post by Abu_Dayya on 2008-06-16
was the installation of the driver successful?

---

### Post by MaindotC on 2008-06-17
I can't really tell if the installation was successful because my question wasn't answered.  No matter how I configured that driver or dpkg reconfigure I still didn't know what to select from Screens & Graphics.  I chose fglrx but each time I rebooted it reverted back to vesa.

I tried re-installing gutsy then restoring my /home folder and that totally screwed up everything so I re-installed again, this time I didn't have sound, so now I'm trying Hardy.  It's been a while since it's been released so I'm testing it out.  Evolution contacts integrating with LDAP in Exchange still doesn't work.  Aside from that it's decent.

Can you tell me what you selected from the Screens & Graphics menu?

---

### Post by Abu_Dayya on 2008-06-17
Hardy didn't work for me, the screen kept freezing all the time. Gutsy worked perfectly on my T60 out of the box. %100 trouble free, even hibernate and suspend works fine......... But

I got screwed with my T60 purchase (technically i didn't purchase it. I got it as a gift) but the specs aren't like advertised.
processor is core due 1.8 Ghz - instead of 2.0 Ghz
hard disk is 80 GB - instead of 100 GB (what the h**l am I suppose to do with ONLY 80GB)
VGA card is integrated - instead of ATI x1400 

So my installation was perfect right from the start. The restricted driver manager shows only the wireless driver. I didn't choose anything from the graphics menu. 

On my PC though I had a lot of trouble getting my nVidia 8500GT to work. Choosing nvidia driver from the graphics menu did absolutely nothing, nor did manually editing xorg.conf file. envy didn't work either. I got it working using the guide I gave you earlier

Did you try Envy?

---

### Post by Abu_Dayya on 2008-06-17
try this link

[http://www.phoronix.com/forums/showthread.php?t=7193](http://www.phoronix.com/forums/showthread.php?t=7193)

---

