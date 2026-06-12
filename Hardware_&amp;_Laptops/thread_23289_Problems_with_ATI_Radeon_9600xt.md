---
title: "Problems with ATI Radeon 9600xt"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by Michael_Grosberg on 2005-04-01
I have a newly installed Ubuntu 5.04 on a PC with a Radeon 9600xt.
Up until now I used the default "ATI" driver, but yesterday I decided to try and connect my TV and see if I can see movies on it from my computer (works fine on windows).

So, I plugged the S-video, and booted. I saw the boot text cloned on my TV, but when the graphical UI was supposed to come up, all I got was a brown background, a mouse pointer (which I could move) and nothing else - the system just stopped there, right before the Ubunto logo was supposed to be displayed.

I disconnected the cable, re-booted. Worked fine. I went looking for a working radeon driver, and found this page:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto/view?searchterm=ati](http://www.ubuntulinux.org/wiki/BinaryDriverHowto/view?searchterm=ati) 

Now I got to installing the FGLRX driver, which I did through synaptic. I installed xorg-fglrx and also fglrx-control. I wasn't sure about what I should do now according to the instructions. What I did was: first, did step 2 of the instructions on the page - opened a terminal and wrote:
```
echo fglrx | sudo tee -a /etc/modules
```
I then removed nvidia.ko from its directory as per the instructions on the page.
Lastly I edited xorg.conf to use "fglrx" instead of "ati", and then rebooted.

Here's what I got:
First, the system still hangs when the S-video is connected at boot.
Second, the resolution has jumped back to 1600X1200 (too much for my 17" monitor) from its previous 1152X864 setting.
Trying to change the resolution back caused this error message:
```
The X Server does not support the XRandR extension.  
Runtime resolution changes to the display size are not available. 
```
Trying to open Totem caused this error message:
```
Totem could not startup.
Resources are busy or not available. 
```

I cannot find the promised control panel that was supposed to be installed.

Ideas, anyone? Where did I go wrong?
I'd appreciate any help on this!

---

### Post by Burgundavia on 2005-04-01
The problem with the Xrandr is a known issue with ATI and nvidia drivers. The only way you can change the resolution is by editing /etc/xorg.conf.

Corey

---

