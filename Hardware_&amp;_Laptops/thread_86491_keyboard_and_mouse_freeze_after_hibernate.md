---
title: "keyboard and mouse freeze after hibernate"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by russelld on 2005-11-05
Hi
Using an Acer 3002WLC.

Restarting after hibernate works up to the login prompt.  Then the mouse and keyboard freeze, so a login is not possible.  

When it's powered off, the desktop briefly appears while the laptop switches itself off.  
So very frustrating!  ](*,) 

any clues?

TIA

---

### Post by simohell on 2005-11-08
This is not a problem with just your Acer. Some HP laptops have the same problem (like my nx9005). 

-So if you find a solution let me know, will you

---

### Post by russelld on 2005-11-08
I have found a possible solution in suspend2.
[http://ubuntuforums.org/showthread.php?t=75443]("http://ubuntuforums.org/showthread.php?t=75443")

and my experience with suspend2
[http://ubuntuforums.org/showthread.php?t=75443&page=5]("http://ubuntuforums.org/showthread.php?t=75443&page=5")

Suspend2 does require a bit of work and close reading of the instructions.  With suspend2, only the keyboard is unresponsive, and leaves the touchpad OK.  So I can get about and do things, like action a software suspend to ram.  After which restoring from this state, the keyboard is restored.
I have noticed in suspend2 that if I disconnect the laptop over night from the mains power, then suspend2 works like its supposed to. 

Leaving me a very happy chappy :D  

This hasn't been tested with battery as it really gets to run on mains power.  After all unecessary discharging and recharging only shortens the battery life.

---

### Post by pjbgravely on 2005-11-08
I have the same problem with an HP ze4805wm. The strange thing is that a ps2 keyboard and a usb mouse work fine after resume. The built in keyboard works now that I changed some things to get the touch pad working. I believe all I need is to add a modprobe in /etc/acpi/rusume.sh, but I am unable to determine what the touch pad driver is called.

By the way, everything else works great after hibernate, even wirless and it doesn't lock up 1/2 the time like it did in windows.

---

### Post by mythagel on 2005-11-09
I'm having the same issue with my laptop running Breezy.

After resume, the keyboard and mouse don't work at all.

I've managed to get the mouse to work after resume by adding 'psmouse' to the MODULES list in /etc/default/acpi-support like the following:

```

...
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES="psmouse"
...

``` 

But i'm still unable to get the keyboard to work after resume.

Any ideas?

-nick

---

### Post by deja-vix on 2005-12-19
[QUOTE=mythagel]I'm having the same issue with my laptop running Breezy.

After resume, the keyboard and mouse don't work at all.


I'm not having issue with the USB mouse, but both keyboard and touchpad are dead. Also, the resume process was really slow - but I don't know if this is supposed to be... Never used hibernate feature before.

I'm on Ubuntu 5.10, HP nx9005. Everything else seems to work OK.

vix

---

### Post by Tiede on 2006-01-07
I am confirming the same problem with an Acer 3009WLCi. No touchpad or keyboard access. Also, when I resume from hibernate, a lot of strange lines and squares of different colors appear on the screen for about 5 secs. Is anyone else noticing the same thing?
Praying for a workaround to fall from the skies...

---

### Post by ralph thomas on 2006-08-02
I was running into this issue on my desktop, where I have a USB keyboard and mouse. I was able to fix it by adding 'usbhid' to the MODULES list in /etc/default/acpi-support

Hibernate and resume used to work fine, I'm not sure how it got broken (but am glad that it works now).

---

### Post by yuv on 2006-08-05
I am confirming the same problem with my desktop.

Also, hibernate and resume used to work fine, and also I'm not sure how it got broken.

After resume, the keyboard and mouse don't work at all and I have to push the  power button :(

I have tried adding 'psmouse' and all modules from /etc/modules, to the MODULES list in /etc/default/acpi-support but these did not solve the problem.

I also have tried Suspend2 but it was almost the same.

---

