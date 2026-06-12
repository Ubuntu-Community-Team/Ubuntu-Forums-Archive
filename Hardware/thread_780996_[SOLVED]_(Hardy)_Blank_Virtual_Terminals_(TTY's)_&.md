---
title: "[SOLVED] (Hardy) Blank Virtual Terminals (TTY's) &amp;amp; nvidia-glx-new"
date: 2008-05-03
forum: Hardware
---

### Post by llama320 on 2008-05-03
I've got a problem that's been somewhat documented about switching to the virtual terminals via Ctrl-Alt-F(1-6). When I try this, I see only a blank screen.

I've searched through the forums and found a few how-to's that seem to solve the problem, but none of these fixes have worked for me.

Most notably, I tried the thorough fix on 
[http://georgia.ubuntuforums.org/showthread.php?t=585454](http://georgia.ubuntuforums.org/showthread.php?t=585454) 
which had me editing /etc/modules & /etc/initramfs-tools/modules along with /boot/grub/menu.lst...but to no avail.

I know that if I boot into rescue mode, I can see the tty's. In addition, I'm currently running the nvidia-glx-new driver, but when I tried installing nvidia-glx I could see the tty's but couldn't enable compiz.

I'm running on an HP Pavillion dv6000 with an nVidia Geforce 6150 Go card.

Hopefully there's another fix other than the above, because I so dearly miss my virtual terminals

I've attached my xorg.conf, if it's of any use.

---

### Post by llama320 on 2008-05-07
*shameless bump*

---

### Post by mbradlcu on 2008-05-07
I had this problem when using Option "NvAGP" "1" in the xorg.conf under card,, may have been "0" but switching from one to the other resolved the issue for me. hope it helps

---

### Post by llama320 on 2008-05-07
Thanks for the suggestion
I tried adding the option but it didn't help

Though I'm a little new at this, I don't think my laptop's using an AGP..when i run lspci I can find my graphics card, so I think it's a pci device

On a side note, since the original post I've also tried taking out the "splash" line from /boot/grub/menu.lst, but to no avail

---

### Post by llama320 on 2008-05-12
*another bump*

---

### Post by mykrob on 2008-05-12
I had the same problem, found a bug reported at nvnews. Fixed it by manually installing the nvidia driver 100.14.23

---

### Post by llama320 on 2008-05-12
it worked!!
I finally had some time to work on it
Thanks muchly, it was really bugging me :)

---

### Post by dmsynck on 2008-05-22
Here are the steps I took to resolve the problem. (Nvidia 6200 card)

1. Turned off "desktop effects"
2. Removed Nvidia-glx-new through "Administration - Hardware Drivers"
3. Installed EnvyNG
4. Installed Nvidia 96.43.05 drivers
5. Re-enabled "desktop effects" and tested

Now I have all six tty's and the graphical desktop intact with Compiz effects(cube)

---

### Post by llama320 on 2008-06-05
Just a quick little addition: if anyone is having trouble with low resolution on reboot after manually installing an nvidia driver, check this thread out

[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

enjoy

---

