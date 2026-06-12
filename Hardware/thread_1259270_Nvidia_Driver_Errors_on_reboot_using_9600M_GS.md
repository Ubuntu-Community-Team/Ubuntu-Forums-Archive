---
title: "Nvidia Driver Errors on reboot using 9600M GS"
date: 2009-09-06
forum: Hardware
---

### Post by Turbo2007ad on 2009-09-06
Hi Everyone,

I decided to try Ubuntu 9.04 (Jaunty) on my Asus M70VM-C1 laptop since I got rather sick of Windows Vista.  The initial installation was easy and everything seemed to work.  However, after installing the proprietary nvidia driver for my 9600M GS vidoe card I get this error every time I reboot the system:

"Ubuntu is running in low graphics mode"

It goes on to tell me that it was unable to detect my hardware settings and that I need to configure them myself.  For some reason, I am able to bypass this by simply going to a terminal and restarting the system a couple times.  I am not sure what the problem is, but I have been unable to find a workaround.

I gave both the 173 and 180 drivers a shot, and even tried those same drivers through EnvyNG in the hope that it would fix my settings, but I had the same issue each time.  I did see a thread somewhere that mentioned I may need to add the horizontal sync and vertical refresh for my display to the xorg.conf manually, but I have not been able to figure out what those ranges are.

Can anyone help me?  I have been searching for hours and have not found a solution.  Once I make it to the desktop everything works perfectly, nvidia-settings see's the driver I have installed (currently the 180 driver recommended by ubuntu but installed through EnvyNG).  I have the full 1900x1200 resolution with graphics acceleration and have not had any problems.  It is only on a restart that I run into errors.

I have attached my xorg.conf so that you can see for yourself what it has right now.

---

### Post by Turbo2007ad on 2009-09-08
Hi Again,

I have still not been able to resolve this issue.  It has reached the point that I have sometimes had to modify my xorg.config file in order to get back to my desktop.  I have now tried adding display modes to the xorg.conf that I know work with my laptop screen, and I have also tried adding / removing the following line from my xorg.conf in the device section:

Option     "UseEdid" "False"

The line above lets me boot up to the desktop every time, however I have a blank screen when it is turned on.  By playing with the xorg.conf and/or rebooting enough times I am always able to return to the desktop, however this is very annoying. Is there a way to tweak the xorg.conf file so that the above option is enabled and yet I can see the screen?  Can anyone shed some light as to what the problem might be?  Any help would be very appreciated.

---

### Post by Turbo2007ad on 2009-09-08
Hello Again,

After doing some more digging I tried a BIOS update for the laptop to see what kind of effect it would have. I updated from version 207 to version 210.  I now only run into the low graphics error from Ubuntu when I restart the laptop.  If I simply shutdown instead, I can immediately reboot the system once it has powered off and there are no problems.  I have also confirmed that the suspend and hibernate features are working.

It would be wonderful if someone could provide a fix that allows my laptop to use the restart option without any errors, but I can live with the system as it is now that I can get it to boot properly on a consistent basis using shutdown.

If no one replies to my situation within a week I will close this thread and come back to the topic at a later date.  If anyone else has run into a similair problem with the same hardware, feel free to post here and I can try to help you.

---

