---
title: "Ubuntu GNOME 580m nvidia optimus?"
date: 2015-04-27
forum: Hardware
---

### Post by niai on 2015-04-27
I just got a new graphics car for my M17Xr3 replaced the my AMD 6870m with the Nvidia 580m, this is my 1st time trying to run an Nvidia card in Ubuntu.

Ok so the problem is if I have my Intel HD3000 graphic activated in BIOS and install the drivers I am able to switch between then but if I run Heaven benchmark I am getting 10FPS with the Intel card and 6FPS with the Nvidia card, i have been at this all weekend and i cant seem to get it to work right.

If i disable the Intel card in BIOS and install the drivers I get 52FPS in Heaven benchmark this is what I am getting in windows to but TF2 is very choppy and the card seems to be running hotter then it should be.

I would like to be running with the Intel graphic and optimus as form the sounds of things its less taxing on the Nvidia card and has better power management but what am I doing wrong?

Ubuntu GNOME 15.04

---

### Post by dino99 on 2015-04-27
Configuring with nvidia-prime:  [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
Testing  [http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)

that card needs the 340 or better 346 driver

---

### Post by niai on 2015-04-27
Thats the way I have been installing it using the 346 driver, tried it muxed and muxless. In the Nvidia setting it says the Nvidia card is active but still getting less frames then with the Intel.

edit
just looked at nvidia-setting a bit more and noticed that the [COLOR=#008C00]****[/COLOR] powermizer dosent seem to move off of 1 even if i put in it performance mode, dont know if this has anything to do with it as it seems to underclock my Nvidia card a lot.

---

