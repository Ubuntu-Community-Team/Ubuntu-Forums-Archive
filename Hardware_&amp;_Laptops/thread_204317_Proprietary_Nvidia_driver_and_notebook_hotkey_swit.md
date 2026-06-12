---
title: "Proprietary Nvidia driver and notebook hotkey switching to external display"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by shazza on 2006-06-26
Hello,

in the last few days, I've been browsing through a number of related threads trying to find a solution to my problem. I'm completely new to Ubuntu and using Linux on a laptop, so please bare with me:

I'm using a Dell Inspiron 9400 notebook which has a built-in Nvidia Geforce Go 7800. When at home, I want to use an external flat screen monitor connected with a DVI cable. Using Windows, this setup works fine: The driver always detects the external monitor and then automatically switches output to it.

This doesn't work with Ubuntu though: The standard driver "nv" is somewhat slow but allows me to use the Fn key (+ F8 ) to switch between internal and external monitor. After each switch the X screen is garbled and I have to switch between console and back to X to get it working again.

I'd like to use the proprietary driver to get 3D acceleration working. I could get it working by doing a "apt-get install nvidia-glx" and changing my xorg.conf file. However, the hotkey switching doesn't work at ALL then. The driver automatically picks the internal monitor and then I can go whacking the Fn+F8 keys all day long - nothing happens. (The nvidia documentation says that TwinView needs to be turned off - which is the default case).

Does anyone know what to do here?

I'm using linux-image-2.6.15-25.42-686, linux-restricted-modules-2.6.15.11-2 and nvidia-glx-1.0.8762+2.6.15.11 (which are the latest versions of each of the packets as of right now)

Thanks for any help!!

---

### Post by m94mni on 2006-06-30
It's a bug in recent releases of the nvidia driver. Does not work for me either.

[http://www.nvnews.net/vbulletin/showthread.php?t=68382&highlight=hotkey](http://www.nvnews.net/vbulletin/showthread.php?t=68382&highlight=hotkey)

---

