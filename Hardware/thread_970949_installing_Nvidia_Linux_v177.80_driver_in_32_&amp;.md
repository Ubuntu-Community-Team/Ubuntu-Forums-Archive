---
title: "installing Nvidia Linux v177.80 driver in 32 &amp; 64 bit Ubuntu 8.10"
date: 2008-11-04
forum: Hardware
---

### Post by drugon on 2008-11-04
I am having problem installing Nvidia Linux v177.80 drivers in 32 and 64 bit Ubuntu 8.10. i have following cards:

Geforce 6200 series in 32 bit Ubuntu 8.10
GeForce 8600 M series in 64 bit Ubuntu 8.10

the first problem i am having is that i am not able to de-activate Ubuntu 8.04 V173 driver (system hangs up)
and the second problem is when i install new version out of the nvidia website, it is asking me to exit out of X-Server which i do not have in my system menu and do not know what is it?

when i am changing my Appearance Preferences to extra my system cannot locate the driver and that window is not responding and i have to force quit it. this installation was very easy and fast in Ubuntu 8.04 but after upgrading to 8.10, i started having trouble.

Thanks in advance for your help!

Dru

---

### Post by jhetfield17 on 2008-11-04
As far as the first prob i cant help you but the second is easy.
it's just telling you that you need to "shutdown" your graphics before being able to install a new driver and do the installation in a terminal without any form of graphics.After the installation you have to restart your graphics(x-server) to load the new driver(might need a reboot).

Try this:
1)take the driver to a location you know how to go to with cd from the terminal.
2)from a terminal do : 
sudo /etc/init.d/gdm stop
3)cd to the directory of the driver
4)from a terminal do : 
sh <driver file>
5)follow the instructions and install the driver and when you are finished you can either reboot(recommended) or
6)from a terminal again:
sudo /etc/init.d/gdm start


I think that'll do it but don't get too much hope.I've been battling with my nvidia 8600gs and the low graphics problem for over two months and even now I havent dealt with it.

---

### Post by drugon on 2008-11-04
I tried to stop Xsession but i am getting this reply 

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
stop: missing job name
Try `stop --help' for more information.

---

### Post by drugon on 2008-11-04
no luck...I tried the changes but it shut down my display and i had to restart my computer ...

---

### Post by drugon on 2008-11-04
Finally my brother and I figured it out how to work this. this may work for all video cards as well...

[FONT="Courier New"]press Ctrl + Alt + F2
[/FONT]
this will bring you into black screen command line mode and ask for your username and password. 

once authenticated go in the directory where your NVIDIA-Linux-x86_64-177.80-pkg2.run file is located. then type:

[FONT="Courier New"]$ sudo /etc/init.d/gdm stop[/FONT]

this will stop the X server
then run the driver as sudo

[FONT="Courier New"]$ sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run[/FONT]

and follow the steps.
make sure NVIDIA-Linux-x86_64-177.80-pkg2.run has the executable permissions.

after you install and come to the command line then re-start the X-server by typing

[FONT="Courier New"]$ sudo /etc/init.d/gdm start[/FONT]

this will bring you back to GUI version and then restart the system. and you are good to go..

have a great day

---

### Post by jhetfield17 on 2008-11-05
so it worked for you!!!nice
but unfortunately those of us battling the low graphics thingy aren't able to slip so easily through the enemy lines................

---

### Post by drugon on 2008-11-05
Yes, but thanks for the tip on how to shut down the X-server!!

---

### Post by jimv on 2008-11-05
Seems like you could have just run this command:

sudo apt-get install nvidia-glx-177

---

