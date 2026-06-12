---
title: "Nvidia Geforce 9600 GT...Need help!!!!!"
date: 2008-06-17
forum: Hardware
---

### Post by ryclegman on 2008-06-17
Ok.... sorry to have to come back but i got a problem a again.... I was working on ubuntu for a while then a window popped up and said updates r avlaible..... so i did them and the restarted the computer... when i came back the desktop effects were gone... but i noticed after or before idk remember .. the nvidia symbol still showed up... i got pissed after a while and descided to screw this... so i reinstalled ubuntu... I know not the best idea.... I got my themes back to the way i like them. i then did the nvidia installer that i did before that did work. But this time i had no such luck. I got the blackj screen and i couldnt get into it execpt through crtl alt f1........ i tryed it a second time and i got the error that my kernel may of been messed up or configuring issues? Then i reinstalled ubuntu again and did the installer and now i got the message headers werent installed and i already updated everything so i had to of had the linux headers.... then i got that fixed and then i got it installed.. but during installation i got could not get kernel from Nvidia.com so i had to later re install ubuntu.... I am hesitent to even try it again... but on the other hand i want the desktop effects and cude...... IDK whats wrong with my computer....SOMEONE HELP!! PLEASE....

---

### Post by psyopper on 2008-06-18
Here's the thing with the Nvidia drivers - they need to compile against the kernel when you install them. When you updated the kernel it broke your Nvidia driver installation.

This is covered in a number of threads in this forum. Here's what you need to do:

Get the kernel you want installed.

Get the headers for the kernel installed.

Install the Nvidia drivers.

DO NOT UPDATE YOUR KERNEL unless you are prepared to go through this exercise again.

---

### Post by Sef on 2008-06-18
> DO NOT UPDATE YOUR KERNEL unless you are prepared to go through this exercise again.

Not necessarily.  I have an NVidia 8600 and have updated the twice so far in Hardy Heron and have had no problems.  Using Compiz-Fusion too.

---

### Post by Sef on 2008-06-18
Moved to Hardware and Laptops.

---

### Post by ryclegman on 2008-06-18
Thank you i will try this tonight!!

---

### Post by stchman on 2008-06-18
> **Sef said:**
> Not necessarily.  I have an NVidia 8600 and have updated the twice so far in Hardy Heron and have had no problems.  Using Compiz-Fusion too.

True, but when Ubuntu updates to a new kernel they update your nvidia-glx new package as well.  So your new kernel gets the new nvidia stuff as well.

---

### Post by ryclegman on 2008-06-18
yha so my nvidia shouldn't of done that then... Like _i said above i still had that Nvidia symbol that pops up before the login_... It just wouldn't work..

---

### Post by stchman on 2008-06-18
> **ryclegman said:**
> yha so my nvidia shouldn't of done that then... Like _i said above i still had that Nvidia symbol that pops up before the login_... It just wouldn't work..

The nvidia-glx-new in Ubuntu uses the 169.12 driver and that will not support the 9xxx series of nvidia cards.  You will need to get the 173.14 drivers for those cards and install them manually.

---

### Post by ryclegman on 2008-06-18
ok, i see. Before i used this method:

You might want to print this out.


Download the latest driver from NVidia:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Step 1
in terminal window

Code:

sudo apt-get install build-essential

Then :

Code:

sudo apt-get remove nvidia*


[this should get rid of all unwanted NVidia drivers. please check /lib/linux-restricted-modules/2.6.24.xx-generic/video and make sure there's no nvidia directory in there. There shouldn't be.] [xx = kernel version]


Step 2
on your keyboard

ctrl+alt+backspace <==== this is for KDE4 [Use the correct shortcut for your X11]

Wait for the drop out of X11.

Step 3

Login into terminal as yourself. Go to the directory where you downloaded the newest NVidia driver.

type :

Code:

chmod a+x NVIDIA-Linux-x86-173.14.05-pkg1.run

NVIDIA-Linux-x86-173.14.05-pkg1.run = name of the file you downloaded. If it's different, then make corrections.


Step 4

type in :

Code:

sudo sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run


Follow directions on the screen.

Step 5

Reboot, and you should be good as new. I don't use Envyng, or Compiz. I like a nice clean install of my devices.

Good Luck



---------------------------------------------------------------------
This worked for about a week. I had some updates, so i did. Then i came back and for some reason the cube and desktop effects were gone. :(

---

### Post by ryclegman on 2008-06-18
And the above installation didn't work for me the last time i tried it.. I got no error message or anything.... Just a black screen after the Ubuntu bar loads.........................:confused:. I havent tried it yet tonight.

---

### Post by hotweiss on 2008-06-19
> **ryclegman said:**
> And the above installation didn't work for me the last time i tried it.. I got no error message or anything.... Just a black screen after the Ubuntu bar loads.........................:confused:. I havent tried it yet tonight.

You are in luck, Envy has the new Nvidia drivers as of June 11th.

1. sudo apt-get remove nvidia*
2. sudo apt-get install envyng-gtk
2. enable the proposed repositories
3. sudo apt-get update
4. sudo envyng -g
5. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
6. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by ryclegman on 2008-06-19
> **hotweiss said:**
> You are in luck, Envy has the new Nvidia drivers as of June 11th.

1. sudo apt-get remove nvidia*
2. sudo apt-get install envyng-gtk
2. enable the proposed repositories
3. sudo apt-get update
4. sudo envyng -g
5. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
6. Once the installation is completed, reboot and you will once again have a crisp screen.


Yha i only see 169.12, 96.43.05, and 71.86.04..... I dont see a 173

---

### Post by hotweiss on 2008-06-19
> **ryclegman said:**
> Yha i only see 169.12, 96.43.05, and 71.86.04..... I dont see a 173

You have to enable the proposed repositories:

[http://albertomilone.com/wordpress/?p=210](http://albertomilone.com/wordpress/?p=210)

---

### Post by ryclegman on 2008-06-19
yHA THANK YOU VERY MUCH IT WORKS GREAT!!!!:guitar::):KS

---

### Post by cyber_brain_mfkg on 2008-06-20
One note:

I installed ubuntu 8.04 on my new desktop machine at work with Nvidia 9600GT GPU! i was trying to install it as usual

1.download driver from nvidia.com
2.sudo apt-get install build-essential gcc g++ linux-headers-generic
3.Alt+Ctrl+F2
4.sudo /etc/init.d/gdm stop
5.sudo sh NVIDIA...blablabla
6.sudo shutdown -r now

Instalation went fine but after reboot X fails and it enters LowGraphicMode...I've tried same procedure couple of times but same problem occur.

Solution (maybe not the best one but it works)..any other suggestion is welcome :

Before you run NVIDIA driver instalation you should remove all old drivers...it seams that new NVIDIA installer has an bug that can't remove old driver as well as apt-get can .... so:

step no 5 would be: sudo apt-get remove nvidia*
6.sudo sh NVIDIA...blablabla
7.sudo shutdown -r now

and afer reboot EUREKA!!!

Peace 2 all ... hope this helps someone :D ;)

---

### Post by dannemil on 2008-07-16
> **psyopper said:**
> Here's the thing with the Nvidia drivers - they need to compile against the kernel when you install them. When you updated the kernel it broke your Nvidia driver installation.

This is covered in a number of threads in this forum. Here's what you need to do:

Get the kernel you want installed.

Get the headers for the kernel installed.

Install the Nvidia drivers.

DO NOT UPDATE YOUR KERNEL unless you are prepared to go through this exercise again.

I can second that. The upgrade to 8.04 broke my display. I had to drop back to the prior kernel in grub to be able, and only after a long arduous process was I able to get Ubuntu to work with my Nvidia G-Force card.

---

