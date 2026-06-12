---
title: "ATI FGLRX Install Successful but have slight problem"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by circuitjump on 2007-05-05
Hello everyone, I just started using Ubuntu Linux about two weeks ago. Everything's looking great so far and have been really pleased with what Ubuntu has allowed me to do. Though I'm having a small problem with my ATI RADEON 9600 driver install. 

I have an IBM Thinkpad T42.
Running Ubuntu Feisty 

I installed the ATI/AMD Radeon Linux drivers using the instructions listed [here]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") . 

After that I kept getting the output below with fglrxinfo
```

$ fglrxinfo 
Xlib: extension “XFree86-DRI” missing on display “:0.0&#8243;.
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: www.mesa3d.org 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

So I ran the following commands which I found on [here]("http://www.thinkwiki.org/wiki/Problems_with_fglrx").
```

# mkdir -p /usr/X11R6/lib/modules/dri 
# ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri

```

That got rid of the Xlib extension error but I was still getting the output shown below.
```

$ fglrxinfo 
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: www.mesa3d.org 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

So I found this [page]("http://ubuntuforums.org/showthread.php?p=2582869").

I followed the commands below 
```

sudo rmmod fglrx
sudo insmod /lib/modules/(your kernel version)/misc/fglrx.ko
sudo modprobe fglrx

```
and rebooted X and wallah, it worked!!!

But then I decided to reboot my system and see if it loaded the new drivers. This is where I have a problem. When I boot my computer up and boot into Ubuntu, I get the old FGLRX 8.34.8 drivers loaded so I get the MESA output and no rendering. So in order to get the new ATI FGLRX drivers working I have to run the rmmod, insmod and modprobe commands above and reboot X with ALT+CTL+BACKSPACE to load the new ATI drivers. Then everything work with no problem.

So with that long winded description I ask, how can I get rid of the old fglrx drivers and ensure that the new drivers run on boot?

I've tried doing this
```

File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

``` 

and I've tried looking for the 8.34.8 drivers in apt-get and aptitude and nothing. So I'm kind of stumped. I originally thought that rmmod command was specifically for that but I guess I'm wrong. Well any help given would be greatly appreciated. I also hope that the steps I've described can help someone else.

Thanks!

---

### Post by IcemanV9 on 2007-05-05
Try to blacklist it in /etc/modprobe.d/blacklist instead of "DISABLED_MODULES="fglrx" in /etc/default/linux-restricted-modules-common.

---

### Post by circuitjump on 2007-05-06
Cool thanks a lot I'll try this out and get back to post my results.

---

### Post by circuitjump on 2007-05-08
Okay so I tried looking into **/etc/modprobe.d/blacklist** and added fglrx in there and still no go. But I'll post back when I get a solution worked out. 

Either way, thank you for the response IcemanV9. It's given me a few more ideas.

---

### Post by penguins! on 2007-06-01
I'm having the *exact* same problem here so any update would be greatly appreciated

---

### Post by lsutiger on 2007-06-06
bump

---

### Post by scr4p3r on 2007-06-09
I have exactly the same problem, upgraded from Edgy to Feisty about a week ago, got everything working again except 3d accel, so I anyone knows a  more "permanent" solution to this I would love to know :)

---

### Post by Caligula on 2007-06-09
i had that problem

running
```
depmod -ae
```

solved it.

good luck!

---

### Post by scr4p3r on 2007-06-09
Didn't work either, is there maybe a way to completly remove fglrx (including older versions) and start fresh?

---

### Post by neptho on 2007-06-09
If you want to entirely remove your old fglrx.ko, and force reinstall your own, a very brutal way of doing this:

```
sudo find /lib/modules -name fglrx.ko -exec rm {} \;
```

This will kill *every* module for fglrx you may have.

Then, rebuild, mkdir /lib/modules/`uname -r`/misc; cp my_new_fglrx.ko /lib/modules/`uname -r`/misc; depmod -ae

---

### Post by scr4p3r on 2007-06-10
It worked awesome thanks man :)

---

