---
title: "Touchscreen LG T1710B not working?"
date: 2011-03-15
forum: Hardware
---

### Post by Muhsin7 on 2011-03-15
Hi

I am fairly new to Ubuntu so I would appreciate any help. I am working  on a project that requires the use of a touchscreen. The touchscreen in  use is the LG T1710B and I need to get it working in Ubuntu 10.04. I  have tried it with the evtouch drivers but it cannot even load the  drivers , I know this from the Xorg.0.log file. 

The previos touchscreen that I got working was the LG 1730, but they  have stopped manufacturing it apparently. I managed to get it working by  doing the following: 
      sudo apt-get install xserver-xorg-input-evtouch    
      sudo gedit /usr/lib/X11/xorg.conf.d/10-evtouch.conf
I got the driver and then edited the .conf file wit the MaxX, MinX,  MaxY, and MinY values so the cursor is as close to your finger as  possible. 

I have used Google and came across a Patch but I am not sure what to do  with it. I am not sure if I can post the link but if I can please let me  know. I also saw on the Ubuntu forums a reply to a post on a similar  issue but I was unable to get it working, I tried it and synaptic  manager gave me an error that it had no signature.

Does anyone know which driver to use and how I should get the touchscreen going? I will appreciate your help.

Regards
Muhsin Hoosen

---

### Post by Muhsin7 on 2011-04-26
If you are running **ubuntu 10.04** and would like to get the touch screen working you have to update the kernel to that of **ubuntu 11.04** which is 2.6.38.

In terminal type in he following:
# sudo apt-add-repository ppa:kernel-ppa/ppa && sudo apt-get update
# sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

Then reboot your Pc and your touchscreen will work.

---

