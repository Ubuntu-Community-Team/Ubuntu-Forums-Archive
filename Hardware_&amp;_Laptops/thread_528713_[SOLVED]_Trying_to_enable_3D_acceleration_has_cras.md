---
title: "[SOLVED] Trying to enable 3D acceleration has crashed my pc"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by davehkent on 2007-08-18
I have just successfully loaded Ubuntu 7.04 onto an old pc running Windows 98, which consequently has an old Nvidia GeForce 4 video card inside. I have just tried to enable 3D acceleration for the card, but something is obviously not right because Ubuntu no longer loads.

I went into Synaptic and searched for, and installed,  'nvidia-glx' then typed 'sudo nvidia-glx-config enable' at the terminal, after which I was prompted to reboot. Which I did, but now it shows pages of text  on restart, then the message 'Failed to start the X server. It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem'. Pressing Yes or No shows more messages, and eventually returns me back to the screen with all the text on. The last line of text shown is '* Running load boot scripts (/etc/rc.local), under which is the cursor flashing.

And that's where I am now - stuck. How can I get back to the desktop or terminal command line, or anywhere to try and fix this?

Thanks in advance.

---

### Post by luisromangz on 2007-08-18
Your card is quite old, so you cant use nvidia-glx drivers. You need the nvidia-glx-legacy package.

---

### Post by davehkent on 2007-08-18
I was thinking along those lines, but how can I get back to Synaptic from the flashing cursor I've got on the screen? If I can boot into Recovery Mode can somebody help me from there?

---

### Post by tseliot on 2007-08-18
Boot in recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```

select the "nv" driver and press ENTER whenever you don't know the answer to a question.

and finally type:
```
reboot
```

and boot as usual.

If it still doesn't work, try "vesa" instead of "nv"

---

### Post by davehkent on 2007-08-19
Thanks tseliot, done as you suggested, now back up and running.

Presumably, 3D acceleration is still not enabled? Is it best to use nvidia-glx-legacy from Synaptic, or is there a better way?

Thanks for your help

---

### Post by tseliot on 2007-08-19
> **davehkent said:**
> Thanks tseliot, done as you suggested, now back up and running.

Presumably, 3D acceleration is still not enabled? Is it best to use nvidia-glx-legacy from Synaptic, or is there a better way?

Thanks for your help

there is no need to use the legacy driver.

If you want to help me diagnose the error you can follow these steps:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by davehkent on 2007-08-22
thanks for the reply. Since my last post I have been playing around and have enabled Desktop Effects, with the result that I now have Restricted Drivers installed. As ubuntu appears to be working ok, I'm going to stop playing around and do something I know, like get Firefox working like I have it on Windows! Thanks for your help

---

