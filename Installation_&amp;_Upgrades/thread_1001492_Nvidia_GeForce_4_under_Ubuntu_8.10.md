---
title: "Nvidia GeForce 4 under Ubuntu 8.10"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by NerdZilla on 2008-12-04
I realize there have been dozens of threads on this subject but I wasn't able to find one that nailed down my exact problem. I recently upgraded to 8.10 (studio) from 8.04, and as expected my nvidia driver stopped working. I was previously using driver version 96 with a GeForce 440 MX, which of course no longer operates under 8.10. I've read about the opensource "nv" driver but am unsure exactly how to get it working. I realize one possible solution would be to upgrade my graphics card to one that uses a driver which works under 8.10, which would be nice but I'd like to avoid that for now. Anyone want to point me in the right direction?

---

### Post by seagullplayer77 on 2008-12-04
Might just have to wait and see if nVidia releases a driver for your card. Could always check their Website and see if they have any support...probably not, but you never know.

---

### Post by jerrykenny on 2008-12-04
I have this card working in 8.10 . . . but i'm not at that particular desktop right now.

I did initially install the recommended driver via the gui, which didnt really give me 3d, i then installed a lower number nvidia ( i forget now the numbers) and restarted x . . . but x wouldnt start !

I then installed an intermediate number . . . and rebooted . . .and this time it worked.

Sorry to be vague about the numbers, but i.m not even on 8.10 on this laptop so i cant search.

Are you confident enuff if you cant get x to start ? ubuntu actually seems to be quite robust inasmuch as it can start a low resolution x-server for you.

You might want to edit /boot/grub/menu.lst and remove the "splash" option, i find the splashscreen most irritating when i'm trying to troubleshoot.

---

### Post by jerrykenny on 2008-12-04
PS, my screen refresh rate was still low, so i simply copied my old xorg.conf file from 8.04 . . . . (which i had tinkered with and knew was just peachy)

---

### Post by NerdZilla on 2008-12-05
well if you get any of the version numbers that would help but I'll try to figure it out, and if I have to work in a command line or in twm I will.

---

### Post by kolibri on 2008-12-05
NVIDIA has new drivers on their website as of Nov 12 or so.  They aren't fixing my problem,  when I turn on the computer it says:

Failed to initialize the NVIDIA graphics device
...
Run Ubuntu in low graphics mode

Once I'm logged in the hardware drivers says that NVIDIA driver 177 is activated and currently in use.

When I try to start NVIDIA X server settings it says
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again.

This happened on one of my last upgrades, and I don't remember how I fixed it. I think just running envy worked then. I see others having the same problem, but none of those threads seem to solve the issue.

---

### Post by NerdZilla on 2008-12-06
maybe I'm wrong but doesn't 177 not work with the GeForce 4? cause every time I install it I can't get it to show up in hardware drivers.

EDIT: I was using 96 prior to the upgrade

---

