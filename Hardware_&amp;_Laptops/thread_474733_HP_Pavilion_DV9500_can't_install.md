---
title: "HP Pavilion DV9500 can't install"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by rrranch on 2007-06-15
I am unable to install ubuntu 7.04 on this new laptop. I get message, can't access tty job control turned off. If anyone has suggestions I would lappreciate the help.

---

### Post by shrimants on 2007-07-04
Hi there. i actually have the exact same model laptop as you so i know hwat you are talking about. heres the deal: your graphics card, among other things, is not supported. so heres what i did to at least install it.

download the alternate install CD

use that to install.

viola, now your laptop can fail WITHOUT the cd as opposed to WITH the CD. i also managed to get my ethernet (not wireless) working, so i could at least run an update/upgrade. and then i did some sort of messy install of the graphics card. it was a horrible work around. also, the CD drive probably wont work, because i know mine doesnt, and furthermore, thers probably a whole bunch of other stuff that wont work either. i dont know what exactly, i just know that mine now has like 3 kernels isntalled on it for no apparent reason, and none of them work. i hope someone can shed some light on this because its driving me insane trying to look for a different distro. there just isnt anything as familiar to me, especially because despite all of this, the problems im having are too advanced for me to learn from.

my advice to you for now: find a different temporary distro or use vista till the september release of gutsy.

---

### Post by expostfacto on 2007-07-10
It's mostly working for me -- I had to use the alternative CD to install, then get the Nvidia driver installer from Nvidia's site and run that before X would work.  (Boot the recovery option, whatever it's called, until then.)  You can do this from the "links" browser; it is somewhat unpleasant, but there is no alternative; X won't work _at all_ with the default drivers.

Don't have sound or wireless working yet.  (Just got the machine today.)  I'm optimistic about wireless; less so about sound.  Both are "nice to have but optional" for me.  (You can also get cheap usb devices for either usb or wifi that will definitely work with it, so that's another option.)

I definitely don't have 3 kernels installed.  I'm not sure how you would have that happen without realizing it. :)

---

### Post by the.unclean.cpp on 2007-09-05
The 3 kernel problem is easy to solve. You have 3-4 kernels because you updated the system and if you look closer you'll see that the kernel versions are different. You shouldn't worry about that. Your kernels are definitely working, I bet the problem is with the graphics card, so here's the workaround:
1. Boot a (recovery mode) kernel

2. Change the dir to /etc/X11
                ```
cd /etc/X11
``` 

3. Open the xorg.conf file
                ```
vim xorg.conf
```

4. Search for ```
Driver          "nv"
``` or ```
Driver      "nvidia"
``` and replace it with ```
Driver        "vesa"
```

5. Save the file and reboot

This should give you a crappy, but working X server(that's the graphical interface). After you entered successfully in Ubuntu, update to the latest version. Then download Envy and install it. It may not work from the first install. In this case, don't worry. Just boot your computer with the first kernel and then type ```
envy -t
```
This will install envy in the text mode. You will the get the nvidia driver installed all right and you will be able to change the resolution to whatever you want.

---

### Post by skinnie on 2007-09-28
I had the same problem,with the alternate version it fails the X..
decided to try the 7.10 "beta" 5, first issue,it doesn't recognize vista on the grub,2nd issue can't use envy to configure the 8600M GS,3rd problem no sound..
I'll try pclinuxos or stay with vista until the 7.10 comes out...

---

### Post by Princegiri on 2007-11-29
[http://ubuntuforums.org/showthread.php?p=3324442](http://ubuntuforums.org/showthread.php?p=3324442)
read the starting that tells you how to boot into live cd bypassing the TTY thing....

the link above was the MAIN thing that helped me make a stable install on my HP dv9505t

---

