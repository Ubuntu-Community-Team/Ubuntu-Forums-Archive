---
title: "Mouse speed affects pointing stick, not touchpad"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by matt_b on 2008-04-07
Hi all,

I've got a Dell Latitude D430 laptop that has both a pointing stick and a touchpad. The mouse cursor moves too slowly when I use the touchpad, but if I speed it up using the "Mouse Properties" dialog it affects only the pointing stick.

Can someone tell me how I can make this "speed" setting affect the touchpad too?

Thanks
Matt

---

### Post by chewearn on 2008-04-08
This will adjust the speed of your trackpad only (you can adjust the mouse via GUI).

Add the addional lines below into the appropriate section of your xorg.conf:
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"

    Option        "HorizEdgeScroll"    "0"
    Option        "HorizScrollDelta" "0"
    Option        "SHMConfig" "true"
    Option        "MinSpeed" "0.60"
    Option        "MaxSpeed" "1.00"
    Option        "AccelFactor" "0.20"
EndSection

```I have adjusted the parameters to suit my Dell D620; you might need to tweak them for your hardware.

EDIT:
You need to reboot after making this change.

---

### Post by matt_b on 2008-04-08
Excellent, that's sorted it!

Thanks
Matt

---

### Post by jorwex on 2008-04-09
Is there any way to do this in a gui? My Xorg-illiterate/frightened friend has these symptoms and GSynaptics doesn't change his touchpad sensitivity. 

Thanks

---

### Post by chewearn on 2008-04-09
> **jorwex said:**
> Is there any way to do this in a gui?

Not that I know of.  Sorry.

---

### Post by seamustry on 2008-04-10
does that work for alps touchpad too? i don't know if synaptics is the same lol...

---

### Post by chewearn on 2008-04-10
> **seamustry said:**
> does that work for alps touchpad too? i don't know if synaptics is the same lol...

My understanding is: for synaptic touchpad you don't need the additional settings in xorg.conf, because the default is already working fine.  However, the alps variant, while being compatible to the synaptic (i.e. the same driver can be used), requires these additional settings.

So, if your Dell touchpad works without any adjustment, you have synaptic touchpad; but if you need adjustment, you have alps touchpad.

---

### Post by mmm2010 on 2008-04-17
Just to let you know ahead of time, I am a noob, so be patient.

I searched for the xorg.conf file, and there were two.  One was in etc/X11, and the other was in usr/share/xresprobe. First of all, I didn't know which to edit.  I made backup copies of both on my desktop just in case, then went into them.

In the file in etc/X11, there was no synaptic device, whatever it was called, so I assumed it wasn't in that one.

I went into the other file, and although it had the correct section, I wasn't able to save it because I didn't have the permissions.  I went to the folders it is located in and went to properties>permissions.  It said that I wasn't the owner so I couldn't change them. 

First of all, what does it mean that I am not the "owner?"  I installed the operating system, there is only one user account on it, and I had just typed my password in somewhere else.  Secondly, am I correct in thinking that the file to edit is the one in usr/share/xresprobe?

Thanks a lot!  If I am able to make my touchpad respond quicker, I think that I will be using Ubuntu a lot more!

---

### Post by chewearn on 2008-04-17
> **mmm2010 said:**
> Just to let you know ahead of time, I am a noob, so be patient.

I searched for the xorg.conf file, and there were two.  One was in etc/X11, and the other was in usr/share/xresprobe. First of all, I didn't know which to edit.  I made backup copies of both on my desktop just in case, then went into them.

The correct one is /etc/X11/xorg.conf.  The one in /usr/share/xresprobe is probably a back-up or work copy of the xresprobe (I'm not familiar with this tool).


> In the file in etc/X11, there was no synaptic device, whatever it was called, so I assumed it wasn't in that one.

Can you post the file?  Also, what is your laptop brand and model number?


> I went into the other file, and although it had the correct section, I wasn't able to save it because I didn't have the permissions.  I went to the folders it is located in and went to properties>permissions.  It said that I wasn't the owner so I couldn't change them. 

First of all, what does it mean that I am not the "owner?"  I installed the operating system, there is only one user account on it, and I had just typed my password in somewhere else.  Secondly, am I correct in thinking that the file to edit is the one in usr/share/xresprobe?

To edit a file outside your home directory, you need to escalate to root privilege.  You do this by adding "gksu" in front of the commands you want to run.  Example:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by mmm2010 on 2008-04-17
Thank you very much for the reply.  I looked again at the etc>X11 file, and it turns out it was there; I must have overlooked it the first time.  I oped the file with the gksu line, added the lines, restarted my computer, and now it works great.

Thanks for the help!  :)

---

### Post by evadwolrab on 2008-04-23
> **AstalaVista said:**
> This will adjust the speed of your trackpad only (you can adjust the mouse via GUI).

Add the addional lines below into the appropriate section of your xorg.conf:
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"

    Option        "HorizEdgeScroll"    "0"
    Option        "HorizScrollDelta" "0"
    Option        "SHMConfig" "true"
    Option        "MinSpeed" "0.60"
    Option        "MaxSpeed" "1.00"
    Option        "AccelFactor" "0.20"
EndSection

```I have adjusted the parameters to suit my Dell D620; you might need to tweak them for your hardware.
Hmm... I have a Dell Latitude D400, adding these lines of options doesn't seem to make any difference. I've put the numbers up ridiculously high just to make sure, and the speed is the same.

---

### Post by evadwolrab on 2008-04-23
Needed a reboot! Mouse is going mental now. :p

---

### Post by chewearn on 2008-04-23
So I assumed it's working now?  I add in the instruction to reboot into my previous post.

---

### Post by evadwolrab on 2008-04-24
Yeah, the instructions work. Cheers. :)

Does anyone know of a way to just "restart" your mouse/touchpad? It's a bit of a chore to try and get the right settings perfected when you have to restart every time.

---

### Post by chewearn on 2008-04-24
You can restart only Xorg, by CTRL+ALT+Backspace.  That should be faster than full reboot.

---

### Post by tiwag on 2008-06-12
> **AstalaVista said:**
> This will adjust the speed of your trackpad only (you can adjust the mouse via GUI).

Add the addional lines below into the appropriate section of your xorg.conf:
```
Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"

    Option        "HorizEdgeScroll"    "0"
    Option        "HorizScrollDelta" "0"
    Option        "SHMConfig" "true"
    Option        "MinSpeed" "0.60"
    Option        "MaxSpeed" "1.00"
    Option        "AccelFactor" "0.20"
EndSection

```I have adjusted the parameters to suit my Dell D620; you might need to tweak them for your hardware.

EDIT:
You need to reboot after making this change.

thanks a lot for this info !
it works fine with my Dell Latitude D820 now,
the touchpad was incredibly slow before.

brgds, tiwag

---

### Post by paulderol on 2008-06-12
there IS a gui tool for this, in the repos, search "touchpad" in synaptic, as i'm not with my laptop to let you know, but i do have the gui tool for that set up, so there is one. somewhere. i personally like this answer better, but i'm a terminal hound of late.

---

