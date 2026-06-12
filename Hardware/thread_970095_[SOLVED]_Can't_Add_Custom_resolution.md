---
title: "[SOLVED] Can't Add Custom resolution"
date: 2008-11-03
forum: Hardware
---

### Post by AlfredoZ on 2008-11-03
Hi Everyone,
I've tried every tutorial in this forums and in others, and i can't get my 19" external monitor to its recomendeded resolution. Im using it with a 1280x800 and it should be at 1440x900. Every time i modify the famous xorg.conf file, i have to boot to recovery mode to repair x server, cause i never get it right. 
Please help me to add a new resolution!!!

I have an hp pavilion tx2500 series
ATI radeon HD 3200
Intrepid Ibex (64-bit)
¿any more relevant specs?

I attached my xorg.conf in a zip file. 
Hmm, maybe its not a xorg.conf issue, but of monitor.xml or other related file that modifies resolution after login(dont remember were it is, but it should be in the user folder).

Thanks for your help.

---

### Post by gali98 on 2008-11-04
This page may be of some help:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

also a couple of other things... Have you tried GNOME's built in resolution utility?
System->Preferences->Screen Resolution

and are you sure that the graphics can put out a resolution larger than 1280x800?

Kory

---

### Post by AlfredoZ on 2008-11-05
Nope, I've already tried it, and the same result. Had to repair x server from recovery mode, and yes my graphic card supports this resolution. I use it in vista and work perfectly.

Thanks for your help.

---

### Post by AlfredoZ on 2008-11-05
Ok, i was reading the page and im sure the answer is in doing some xrandr commands in terminal, as the last example of the xrandr manual ($ man xrandr). But im not sure how to write this commands due to my newness to ubuntu. Need some help.

---

### Post by gali98 on 2008-11-05
this is beyond my scope, but I am sure someone else can. If you had the tx2000 (what I have.. its an older model)
you could just use the nvdia configuration thingie. it works really well. there is probably some tutorial out there that could help you... sorry
Kory

---

### Post by AlfredoZ on 2008-11-05
Ok, let mi understand. Your graphic card is an ATI and your using the nvidia configuration tool???

---

### Post by gali98 on 2008-11-05
No.. that's the point.. I have the tx2000 series which has nvidia graphics in it. So I can use the nvidia graphics utility.
the tx2500 series has ati. as far as I know, there is no such utility for ati...
That's why I can't really help you. Sorry for the confusion.
Kory

---

### Post by harak on 2008-11-06
> **AlfredoZ said:**
> Hi Everyone,
I've tried every tutorial in this forums and in others, and i can't get my 19" external monitor to its recomendeded resolution. Im using it with a 1280x800 and it should be at 1440x900. Every time i modify the famous xorg.conf file, i have to boot to recovery mode to repair x server, cause i never get it right. 
Please help me to add a new resolution!!!

I have an hp pavilion tx2500 series
ATI radeon HD 3200
Intrepid Ibex (64-bit)
¿any more relevant specs?

I attached my xorg.conf in a zip file. 
Hmm, maybe its not a xorg.conf issue, but of monitor.xml or other related file that modifies resolution after login(dont remember were it is, but it should be in the user folder).

Thanks for your help.

fglrx does not work via xorg.conf anymore... see the following

[http://www.tuxmachines.org/node/28676](http://www.tuxmachines.org/node/28676)

you should use aticonfig command for adding new display sizes etc.. you may want to use grandr or as kory has said

---

### Post by AlfredoZ on 2008-11-10
I did it!!!
I changed my resolution!!!
The only bad thing is... i dunno what i did?... I just played with the aticonfig command, then Alt+ctrl+backspace, and i had it.... THANK YOU ALL FOR YOUR HELP!
one issue solved, and one to go.

---

### Post by Horshamite on 2008-11-10
I had an issue with my resolution. The screen when i first installed Ubuntu 8.10 was visible, but half the screen was missing. Reading about it, my screen was what I could see however the OS was setting a virtual screen size way bigger.

Fiddling with the resolution just totally assed up the display making it unreadable. 

However, I found one method which does work, I guarantee.

Run .... gksudo gedit /etc/X11/xorg.conf in Terminal.

Scroll around until you find the screen section. After the device label, insert a Display subsection, specifying the resolution needed. In my case I required "1280 X 800"

```

Section "Screen"
     Identifier "Default Screen"
     Monitor    "Configured Monitor"
     Device     "Configured Video Device"
     [COLOR="Red"]Subsection "Display"
         Modes      "1280x800"
     EndSubSection[/COLOR]
EndSection
```

The red part is what I added in. After a reboot, the screen setting is now perfectly set.

---

### Post by Biopyro on 2010-12-24
I had the same problem, only occurred after I moved house, no idea why but the monitor was no longer detected. I don't like that it's inflexible but the solution above definitely worked. 

Is there anything I can do that might encourage re-detection of my monitor?

---

