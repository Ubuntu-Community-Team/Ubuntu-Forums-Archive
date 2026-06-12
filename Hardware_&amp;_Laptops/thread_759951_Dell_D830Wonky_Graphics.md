---
title: "Dell D830:Wonky Graphics"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by dcreamer01 on 2008-04-19
Hey all. Long time reader/user, but I don't post here that often. My question of the day...I have a Dell D830 with the Nvidia NVS140M built-in card, and the WXGA (1280x800 res.) Out of the box with the standard Vesa driver, I get it to work at that resolution, with 60Hz refresh. Now comes the tricky part...if I install either the restricted driver, or the driver straight from Nvidia's site, I get the white screen of death (white screen with a black line in the middle). I can hear the boot sounds; I can CTRL+ALT+F2 into the terminal and login. In 7.10 I could edit the xorg.conf file and fix the xserv. With Hardy I have to init 2, and fix the xserv. When I do that, and restart X, it is back to Vesa, and the 1280x800 res. This happened in both Feisty and the Hardy beta, which I just put in again yesterday, the 18th or April. I have seen other users with this issue, and no solutions. So, my question....can it work? Whatever anyone needs from me to get me a little more along, I'll get it. This is a work machine, and cannot be down much longer. I have another laptop that I have no phased out yet, so, I'm not dead in the water. 

Sorry for the ramble, 
Thanks in advance,
Dave

---

### Post by wbellman on 2008-05-14
Hey dcreamer01,

  Were you able to get anywhere with your issue?  I am having the exact same problem. I have tried:

[LIST=1]
[*]Automatic Install of the Restricted Drivers
[*]Manually selecting the nvidia-glx-legacy, nvidia-glx, and nvidia-glx-new packages and configuring xorg by hand as well as with the nvidia-xconfig tool.
[*]Attempted to utilize the "Envy" package's automatically detection to configure my system.
[/LIST]

All end up with the "white-screen-of-death" you mentioned.  I'm going to keep trying things, and I'll post if I come up with anything but was curious if you (or anyone else browsing) had gotten anywhere.

---

### Post by dcreamer01 on 2008-06-09
> **wbellman said:**
> Hey dcreamer01,

  Were you able to get anywhere with your issue?  I am having the exact same problem. I have tried:

[LIST=1]
[*]Automatic Install of the Restricted Drivers
[*]Manually selecting the nvidia-glx-legacy, nvidia-glx, and nvidia-glx-new packages and configuring xorg by hand as well as with the nvidia-xconfig tool.
[*]Attempted to utilize the "Envy" package's automatically detection to configure my system.
[/LIST]

All end up with the "white-screen-of-death" you mentioned.  I'm going to keep trying things, and I'll post if I come up with anything but was curious if you (or anyone else browsing) had gotten anywhere.

Nothing yet. No answers here. Just waiting to see what happens. Had to go back to XP, as this is a work machine, it needed to be up and running. Still waiting to go back to Ubuntu

---

### Post by mindhaq on 2008-06-09
I'm sorry I don't have a solution, but I have a D830 as well (1680x1050 resolution), and never had this particular white screen error. I did a fresh install of Hardy.

Sometimes, if the screen was locked after standby, I have a different white screen, where I see the mouse pointer, and can unlock the screen by typing my password blindly.

---

### Post by jaranguren on 2008-06-10
I have the same exact problem with my Dell D830.

My workaround is to use pm-suspend.

After I verified that suspend and resume works with pm-suspend, I edited /usr/sbin/pmi to call pm-suspend instead of the original script.

It's been working fine so far.

---

