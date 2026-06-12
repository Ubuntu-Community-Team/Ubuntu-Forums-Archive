---
title: "Help installing Creative 3D Blaster Banshee"
date: 2008-11-10
forum: Hardware
---

### Post by badbrad70 on 2008-11-10
Hi, I'm hoping someone can help me out with this. I found a driver for my card on the us.creative.com site: [http://ccftp.creative.com/manualdn/Drivers/Others/219/XF86_Banshee-1.01.tar.gz](http://ccftp.creative.com/manualdn/Drivers/Others/219/XF86_Banshee-1.01.tar.gz) which is "The latest 3D Blaster Banshee standalone driver update for Linux Operating System".

The install complained about and invalid file XF86Config and taking a look at the script I figured out that it was missing from /etc/X11 so I cp it over. Running the install again seemed to work as it gave no errors. So I did a restart.

Now when the PC starts up I get the ubuntu splash screen with the progress bar... and then I am bumped out to the command line.

I have tried finding a solution to this and keep coming up empty handed. :-\ 

if I try running xterm or gedit (or anything like that) it gives an error like: can't open display or DISPLAY is not set
gdm is running
lscli lists my VGA compatible controller as: 3DFX Interactive, Inc. Voodoo Banshee (rev 03)

I am running Ubuntu 8.0.4 with a current dist-upgrade.

----

Thanks for your time and consideration,
Brad.

---

### Post by pbelaustegui on 2009-08-12
to recover the symbolic link like it was before you run the installation script

sudo ln -sf /usr/bin/Xorg /etc/X11/X

now you can strat xserver.

greetings.

---

