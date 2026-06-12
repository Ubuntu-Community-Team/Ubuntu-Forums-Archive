---
title: "Graphics Options"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by jabb0 on 2005-09-06
hey guys,
 
I have just installed linux on a test machine, just to make sure i can get the necessary apps up and running before i ditch windows.
 
Everything has went real smooth.
 
The only thing is that when the screensaver appears it runs at a REALLY low framerate.  There is a nVidia Gforce4 in it so the thing should be having a lot of trouble 0 like it managed to run some pretty hefty games under windows.
 
Methinks that its just not configured right.  But the only options i can find from the desktop menus are resolutions / screensaver / desktop backgound etc...
 
has anyone got any ideas?

---

### Post by Leif on 2005-09-06
have you installed the nvidia drivers ? (see ubuntuguide.org if not)

---

### Post by jabb0 on 2005-09-06
Heya,
 
I just installed the nvidia drivers.
 
They seemed to install ok, and i can change several settings, however, the low FPS still occurs on the 3D screensavers.
 
I might actually try the installation again, cos i have done alot of messing around.
And on the install of the nvidia drivers, i got a few messages when i restarted the computer saying that i had not got the right privileges to run the selected program - perhaps something to do with the fact i logged in as a normal user not the super / root user.
 
Ill report back, however all ideas welcome in the meantime???

---

### Post by jabb0 on 2005-09-06
Ok
 
So i have reinstalled, installed the nvidia drivers, and not so much as one error. Great eh?
 
Yeah well the problem of the screensaver is still exactly the same as it was before i started - i got an FPS reading onscreen from one of the screensavers, "0.53FPS"
 
Surely this is not right, with a reasonable graphics card, i should be getting x10 times faster than the quoted framerate (remember its only a screensaver - not Doom3)
 
Any ideas?

---

### Post by Leif on 2005-09-07
you also have to enable 3d acceleration. in /etc/X11/xorg.conf, my section for the nvidia driver looks like this :

Section "Device"
        Identifier      "Nvidia GeForce 2 MX-200"
        Driver          "nvidia"
#       Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
#rendeaccel turned off because it crashes firefox atm
#       Option          "RenderAccel"   "true"
#       Option          "AllowGLXWithComposite" "true"
        Option          "NvAGP"         "2"
EndSection

# means the line following it is not processed. this line is what will enable 3d acceleration, but I have it turned off because my card gives problems while running firefox, but I'm sure this bug will get sorted soon. if you want to  know what "AllowGLXWithComposite" is for, please search the forums.

---

