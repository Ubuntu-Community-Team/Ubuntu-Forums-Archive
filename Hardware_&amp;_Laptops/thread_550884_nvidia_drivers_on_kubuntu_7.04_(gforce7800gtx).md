---
title: "nvidia drivers on kubuntu 7.04 (gforce7800gtx)"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by gorgeous_george on 2007-09-14
Hi guys! 
I'm trying to install nvidia-binary drivers  I' ve downloaded from their webpage.
I downloaded the right version for my 7800gtx . I run kubuntu 7.04 with kernel 2.6.20-15, and after I log on in console-mode, and run

```
sh ./NVIDIA-Linux-x86-100.14.11-pkg1.run
```

they tell me  I have some kind of trouble with kernel headers, and the final diagnostic message is "you need to have libc headers installed".
I know these aren't the correct words they used, but i'm in a hurry so now I can't be more specific; I'll add further informations later, if in the meanwhile anybody solves the problem.

Thanks a lot!
    bye

---

### Post by logos34 on 2007-09-14
update to the -16 linux kernel.  Then try this howto (-->method 2):
[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by gorgeous_george on 2007-09-14
Back again :) Installed the drivers. (Even upgraded kernel to 2.6.20-16)
The procedure was not that described in the tutorial you kindly posted above, but everyway I installed them.
In the xorg.conf file, lines about VGA seem as follows:
```
 section  "device"
          identifier "Nvidia G70 (7800 gtx)"
          driver "nv" 
```

This should be right.But now, when i finally log on and type in my terminal
```
 glxinfo | grep -i render 
```
this is the answer :
```

george@george-desktop:~$ glxinfo | grep -i render
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Any idea?
Bye!

---

### Post by bilkan on 2007-09-14
Try this: [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html]("http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html")

---

### Post by JC Casiano on 2007-09-14
As long as "nv" is the driver you won't get GLX.  There are a number of ways to get your xorg.conf file changed, I find editing xorg.conf much more reliable.  But first, back up xorg.conf, then manually edit your driver to "nvidia".  Restart you X server, you should get an NVidia splash screen.

I'm leaving work, I'll check in when I get home.

---

### Post by gorgeous_george on 2007-09-15
@jc_casiano:

In fact, I tried that solution, but then, after rebooting, X couldn't load. Later I'll try that again so I could post here the error-in the meanwhile, thanks for the help!

bye

---

### Post by gorgeous_george on 2007-09-16
problem solved. just by using Envy (nice tool!).Thanks all for your attention!
bye

---

