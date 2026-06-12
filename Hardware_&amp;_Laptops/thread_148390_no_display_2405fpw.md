---
title: "no display 2405fpw"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by sorrow777 on 2006-03-22
](*,) Guys sorry to ask but i've tried everything i can find in the posts on this site.

Below is my rig, maybe someone could let me know how my xorg.conf file should look.

I used apt-get to install the latest nvidia drivers, and followed guides and posts here to setup my xorg.conf so it has the right modelines in it and still no luck.

I followed method one from tseliots post and now when i boot or when i startx it hangs.

I know many others have asked similar questions but i'm at a loss here.  i'm willing to reinstall 5.10, its no biggy.

a64 3800+ venice
evga 7900gtx
a8n32-sli delux (just one vid card)
WD 150gb raptor drive
audigyt 2zs sound card
2405fpw Dell lcd

Any help is much appreciated.  I would post an error if i was getting one, but seeing as the screen goes black and it doesn't respond to ctrl+alt+f2 f3 or anything.  I will take a look in the log file tomorrow when i get home.

thanks for any input!

---

### Post by tseliot on 2006-03-22
I guess geforce 7900 is too new to be supported by the driver in method 1.

a Quick fix (as as to use the Graphical interface again)

sudo nano /etc/X11/xorg.conf

and set the driver from "nvidia" to "vesa".

CTRL+O to save
CTRL+X to exit

then "startx" or reboot.

After you get everything to work you will have to uninstall the driver from Method 2:
Press CTRL-ALT-F1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)

Login with your username and password (if required)

Stop the xserver:

sudo /etc/init.d/gdm stop (OR "kdm stop" if you use KDE)

NOTE: if the backup of your xorg.conf doesn't work or you lost it try this command (so as to regenerate a clean xorg.conf): sudo dpkg -reconfigure -phigh xserver-xorg


cd path_to_the_nvidia_installer

sudo sh name_of_the_nvidia_installer --uninstall

Restart the xserver

sudo /etc/init.d/gdm start (or "kdm start" if you use KDE).

After that, follow Method 2 again (make sure you follow all the steps)

---

### Post by sorrow777 on 2006-03-22
Thanks man, ya the vesa trick worked for me atleast for now.  But the latest nvidia drivers don't support my card ):  I'm gonna have to wait until they release a new driver.

I'll keep an eye open for that new driver for sure hehe.

thanks again

---

### Post by sorrow777 on 2006-04-08
Got the new drivesr working.  It looks so much better. 

thanks for your help chief.

---

