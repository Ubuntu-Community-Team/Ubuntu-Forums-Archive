---
title: "Ubuntu 12.04 Nvidia issue"
date: 2012-05-04
forum: Hardware
---

### Post by vegarend on 2012-05-04
Ok, so I've upgraded to Ubuntu 12.04 recently and my graphics card is not working. Same old story if you ask me, but I'm not able to fix this one.

Here's my NVIDIA info:

```

:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev a2)

```

No available drivers in the 'Additional drivers' app. 

I've got the impression that glxinfo should say something different than this, given that opengl is working:

```

:~$ glxinfo 
name of display: :1.0
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't find RGB GLX visual or fbconfig

```

Tried manually installing drivers from nVidia, but no luck. If i update the xorg.conf i get a desktop with 640x480 max resolution,  above diagnostics stays the same :/

Any thoughts, comments or ideas are appreceated :)

---

### Post by kc1di on 2012-05-04
There is a bug with compiz and Nvidia. see here:[http://ubuntuforums.org/showthread.php?t=1971463]("http://ubuntuforums.org/showthread.php?t=1971463")

solution for now is use the open source driver for your nvidia card.

---

### Post by vegarend on 2012-05-04
Thx for the quick reply.

The post you refer to says that there are problems with proprietary drivers. I've seen this before, and have stuck with an open source alternative as it has had better performance in my case. My problem now is that I seem to have no hw acceleration either way :(

Since I am not up to speed in this topic: 
- Are there alternative open source drivers for graphics? 
- If so, is it worth testing our should I stick with what I've been dealt from 12.04?

---

### Post by vegarend on 2012-05-04
Activate quick reply?

---

### Post by Axxon95 on 2012-05-04
Vegarend, I PMed you something that might help.

---

### Post by vegarend on 2012-05-04
Tried booting with nomodeset for disabling KMS, but it just resulted in lower screen resolution.

---

### Post by mörgæs on 2012-05-04
> **Axxon95 said:**
> Vegarend, I PMed you something that might help.

Please post suggestions in the open as this will help other Nvidia users.

---

### Post by vegarend on 2012-05-04
> **mörgæs said:**
> Please post suggestions in the open as this will help other Nvidia users.

Suggestions were:

1) Install NVIDIA driver via repository: [http://www.youtube.com/watch?v=OMi3-2MyBtQ](http://www.youtube.com/watch?v=OMi3-2MyBtQ)

2) Install driver from NVIDIA webpage

Two good suggestions that has worked for me in the past, but not this time. 

I've had both proprietary and open source drivers working in previous Ubuntu's on this machine.

---

### Post by vegarend on 2012-05-05
Ok, looking into the glxinfo issue I found this debian thread:

[http://forums.debian.net/viewtopic.php?f=6&t=73028](http://forums.debian.net/viewtopic.php?f=6&t=73028)

Installed bubmlebee using this guide:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Problem solved :)

Summary:

```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

```

Don't know if it had any impact, but before installing bumblebee I removed NVIDIA stuff as well:

```

sudo apt-get purge nvidia*
sudo nvidia-uninstall

```

---

### Post by Sepero on 2012-06-25
> **vegarend said:**
> Ok, looking into the glxinfo issue I found this debian thread:

[http://forums.debian.net/viewtopic.php?f=6&t=73028](http://forums.debian.net/viewtopic.php?f=6&t=73028)

Installed bubmlebee using this guide:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Problem solved :)

Summary:

```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

```

Don't know if it had any impact, but before installing bumblebee I removed NVIDIA stuff as well:

```

sudo apt-get purge nvidia*
sudo nvidia-uninstall

```

I have an Nvidia Geforce GT 630M, on an Asus laptop. Thanks, This worked great for me.

---

### Post by robtygart on 2012-06-25
I have been having trouble with my Nvida drivers as well 

The Nvidia "version current" would refuse to load only in fail safe. So I went to "Post release Updates" 

My computer will not detect my second monitor, I can get some action form it if I enable it in the Nvidia settings but nothing looks right, I never had to enable it before, all I had to do was plug in my monitor and restart and it would take over as the defult monitor.

---

### Post by Fpetrick on 2012-06-25
> **vegarend said:**
> Ok, looking into the glxinfo issue I found this debian thread:

[http://forums.debian.net/viewtopic.php?f=6&t=73028](http://forums.debian.net/viewtopic.php?f=6&t=73028)

Installed bubmlebee using this guide:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Problem solved :)

Summary:

```

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

```

Don't know if it had any impact, but before installing bumblebee I removed NVIDIA stuff as well:

```

sudo apt-get purge nvidia*
sudo nvidia-uninstall

```

How do you suppose I do this when I'm not able to boot Ubuntu at all?](*,)

---

### Post by javicente on 2012-07-26
I have an Nvidia Geforce GT 630M, on an new Dell vostro 3460 laptop. I executed this instructions without exit, my resolution continues at 640x480.

I'm desperate, I have two days fighting with the problem.  The fact is that worked fine until you apply an update of ubuntu. I tried this procedure in different ways but I can not I recognize the graphics card I have.

 I tried loading the drivers have supposedly nvidia certificates, without exit.

 Any ideas?

I would like to install or recovery the default driver which was workin right until the ubuntu updates?

---

### Post by Sepero on 2012-07-26
> **javicente said:**
> I have an Nvidia Geforce GT 630M, on an new Dell vostro 3460 laptop. I executed this instructions without exit, my resolution continues at 640x480.
Your problem is the Intel driver, not Nvidia. The Nvidia driver does not run your desktop view. Try this and reboot:
```
sudo apt-get install mesa-utils
```

If that still doesn't work, try xrandr (replace 1366x768 with your resolution)
```
xrandr -s 1366x768
```

---

### Post by javicente on 2012-07-30
Thanks Sepero,  mesa-utils are installed but  when i execute xrandr   with different possible resolutions 800x600, 1366x768 it sais "size  xxxxxx not found in available modes." :(

At the end we got success  :) removing the /etc/X11/xorg.conf where it was saying to use the nvidia driver, which doesn't work.   Removing this file seems that it used the Intel device instead.

Now seems i'm using the Intel device with the default driver or nouveau  driver and mesa-utils (I don't know exactly),  and wasting my new nvidia  GT 630M 1G   :(

Thanks, and I hope this small contribution helps someone else.

---

### Post by Sepero on 2012-08-03
These instructions allowed me to use my Nvidia Geforce GT 630M Optimus graphics card
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Do Not install the linux driver from nvidia, and if you did, try to undo everything it did.

---

