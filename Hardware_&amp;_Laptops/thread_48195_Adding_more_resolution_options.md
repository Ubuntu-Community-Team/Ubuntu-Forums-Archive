---
title: "Adding more resolution options"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by punkcoder on 2005-07-11
During the install of Ubuntu I didn't choose to add any additional resolution modes above 1024 x 768.  While this does work good since I am running Ubuntu under VMWare 5.0; I was wanting to know how I could maybe bump the resolution choices up with a couple more options.  When I go to full screen mode in VMWare, 1150 or 1280 would probably work pretty nicely.  Is it as simple as adding some lines to a config file or is there a utility I can run?  Any help would be greatly appreciated.

---

### Post by varunus on 2005-07-11
You can add lines to /etc/X11/xorg.conf to add more resolutions.  Go to the screen section, and for each bit-depth, add resolutions to the Modes lines.  You could change:

```
Modes "1024x768"
``` 

to 
```
Modes "1024x768" "1280x1024" "800x600"
``` 

for example.  The mode that is present first is the default resolution.  You can change the resolution from GNOME using System->Preferences->Screen Resolution after you have added modes to the xorg.conf file.

Enjoy.

---

### Post by punkcoder on 2005-07-11
Thank you very much for the prompt reply.  Worked like a charm.

---

### Post by Massive Brain on 2005-07-12
[QUOTE=varunus]
```
Modes "1024x768" "1280x1024" "800x600"
``` 
[/QUOTE]
&#9835; One of these things is not like the others &#9835;

Everytime you use a 5:4 resolution on a 4:3 screen, I kill a kitten.

---

### Post by pixelnate on 2005-07-12
I have an nvidia 6800 and a Hitachi CM751 monitor that are capable of 1280x1024 @ 85Hz, but all that Ubuntu says is available is 60Hz. Is there any way to force Ubuntu to refresh the screen at 85Hz?

I have installed the nVidia driver using Synaptic. It shows as installed, but I cannot find any nVidia configurations options. Is there some place I should be looking besides the screen resolution window?

Thanks in advance.
 ](*,) 
-pixelnate

---

### Post by varunus on 2005-07-12
You also need to install the nvidia-settings package from synaptic.  Also, you need to set up your xorg.conf to use the Nvidia driver (I'm not sure if nvidia-settings can do that, but I know there's a howto on this forum).

---

