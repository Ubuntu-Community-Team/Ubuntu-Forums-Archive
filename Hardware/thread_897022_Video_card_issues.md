---
title: "Video card issues"
date: 2008-08-21
forum: Hardware
---

### Post by rwslippey on 2008-08-21
Hello all and before i post i'd like to thank anyone and everyone for their assistance... I have been scratching my head and searching the net for 3 days....

I am kind of new to linux although i have used it in the past and have used it on servers more then once...

I have a Compaq F572 US Laptop with a Nvidia GeForce GO 6500... 
I have installed the drivers from the hardware drivers tool under system administration...

What I am trying to do is enable 3D support to support desktop effects and a few games... in additional I think it would be interesting to try...

I have desktop effects running however it only runs in 2D ...

I currently have nvidia Xserver installed but I see no options or settings for 3D and I am useing a propritary driver from the hardware driver tool under system administration

again any help would be greatly appriciated...

running ubuntu 8.04

---

### Post by phidia on 2008-08-21
Do you have a nvidia-settings applet under System > Admin? If not you should be able to install it through synaptics. Once you have that you can try and adjust settings.
Make sure the "nvidia" driver is being listed in the device > driver section of /etc/X11/xorg.conf

---

### Post by rwslippey on 2008-08-21
I have Nvidia X server Settings under system admin 

and it is listing the Nvidia driver under the device section... 
Here is what the section says

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


none of the setting I see in the XServer have anything todo with 3D

---

### Post by rwslippey on 2008-08-21
I believe I have the 3D working or atleast this cammand to my understanding says it is working

glxinfo|grep rendering  

it comes back with yes...

however... I am still not able to run the program for witch i was trying to get 3D functioning... and I exspected the cube effect differently if 3D was functional... 

When rotateing the cube it is just a 2 sided screen that flipps... not what I'v seen in a few how-tos

---

### Post by tuxxy on 2008-08-21
That is because you have not enabled the desktop cube or your desktop size is set to 2 not 4.

Do you have compiz effects manager installed, if not then open a terminal and type

```

sudo apt-get install ccsm
```

Now open **system > prefs > advanced effects > general options > desktop size** , now switch the horizontal virtual size to 4

Make sure desktop cube and rotate cube plugins are also enabled, these are located on the desktop tab of ccsm

---

### Post by rwslippey on 2008-08-21
ok   feeling like a total NOOB now...

I got the 3D effect with the cube effect... now to tackle the game... witch maybe a different issue... Thanks for all the help



Ubuntu = lots and lots of learning!!! but it is acctually fun!
I love it!!

---

