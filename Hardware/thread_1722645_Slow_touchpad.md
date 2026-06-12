---
title: "Slow touchpad"
date: 2011-04-06
forum: Hardware
---

### Post by MustangV10 on 2011-04-06
Hi,

I'm using Ubuntu Latest Ubuntu 11.04 with my Toshiba Satellite Pro L500-1XM, all updates installed with a touchpad. My touchpad acceleration speed is set to 'Fast' yet it's still pretty slow, at least compared to what I'm used to from Windows 7 which I recently just moved from.

My finger is now aching from this slow touchpad, if that's the fastest it will go, that's pretty pathetic.

Is there any reason for this?

Thanks.

---

### Post by MustangV10 on 2011-04-07
Bump

---

### Post by MustangV10 on 2011-04-08
Bump again..

---

### Post by rausuar on 2011-04-12
> **MustangV10 said:**
> Hi,

I'm using Ubuntu Latest Ubuntu 11.04 with my Toshiba Satellite Pro L500-1XM, all updates installed with a touchpad. My touchpad acceleration speed is set to 'Fast' yet it's still pretty slow, at least compared to what I'm used to from Windows 7 which I recently just moved from.

My finger is now aching from this slow touchpad, if that's the fastest it will go, that's pretty pathetic.

Is there any reason for this?

Thanks.

Hi, try downloading from ubuntu software center a package called "pointing devices", which you can find if you type in search box: touchpad, it will install a small program GUI where you can play with speeds and all that for the touchpad... I had the same problem!, now it is solved, but bee careful, it can get very very sensitive the touchpad!

---

### Post by Nuc72 on 2011-04-29
I've got the same problem. (Dell Inspiron, AMD, 11.04)
I've installed gsynaptics, set speed in UI - it works well, BUT when I've logged in again or restarted, it lost its settings, so I have to adjust it all the times.

Any idea or solution?

Thx in advance.

---

### Post by reborn7778 on 2011-04-29
> **MustangV10 said:**
> Hi,

I'm using Ubuntu Latest Ubuntu 11.04 with my Toshiba Satellite Pro L500-1XM, all updates installed with a touchpad. My touchpad acceleration speed is set to 'Fast' yet it's still pretty slow, at least compared to what I'm used to from Windows 7 which I recently just moved from.

My finger is now aching from this slow touchpad, if that's the fastest it will go, that's pretty pathetic.

Is there any reason for this?

Thanks.

Ubuntu should have a setting mouse, where you can click acceleration. you can check a setting, mouse device.

---

### Post by Nuc72 on 2011-04-30
> **reborn7778 said:**
> Ubuntu should have a setting mouse, where you can click acceleration. you can check a setting, mouse device.

Our problem is we set the mouse acceleration speed to the highest value, but it's not enough quick (on 10.10 it was perfect). I've installed gsynaptics, set speed in GUI - it works well, BUT when  I've logged in again or restarted, it lost its settings, so I have to  adjust it all the times.

My main problem is all sources talks about how can I modify my xorg.conf file. I've read about it on the net, and found a file in /usr/share/doc/xserver-xorg-input-synaptics folder called README.debian, which explains the details of modification. BUT XORG.CONF DOES NOT EXIST in my etc/X11 folder. Of course I could create a new one, but I don't know its content!

---

### Post by Nuc72 on 2011-04-30
Any idea?

---

### Post by ophysis on 2011-05-01
Same issue here...

Just did a clean install of 11.04.

The touchpad pointer is soooo slow...
I have changed the speed and acceleration to max on the mouse menu options, but it remains the same: slow...
The touchpad speed hasn't been an issue for me with ubuntu until 11.04.
Also installed "pointing devices" but after a reboot the speed reverts to defaults.

Any ideas?


Tks

---

### Post by ophysis on 2011-05-03
bump

---

### Post by Nuc72 on 2011-05-03
My solution: install Kubuntu. It works!

---

### Post by ophysis on 2011-05-05
bump
anyone please?

---

### Post by ophysis on 2011-05-13
bump

---

### Post by behindclosedeyelids on 2011-05-16
Are you running cpufreqd? I noticed that it really messed up the touchpad motion when I tried it earlier today on my Acer Aspire One D260 (11.04-x86).

---

### Post by yangexp on 2011-05-16
i'm using Hp Pavilion DV 2000, when upgrade Ubuntu 10. to 11. , touchpad was disable,i think that it need to install driver for it but i don't know where/how to find Driver, how to resolve this problem ?? :(

---

### Post by jura12 on 2011-05-24
This was succesfully tested on ubuntu 11.04 dell inspiron n5030.
You can speed up your ALPS touchpad by this way. Type this code in yourfile.sh, make executable and add it to user autoload.
```

xinput list-props "ImPS/2 ALPS GlidePoint" | grep Velocity
xinput set-prop "ImPS/2 ALPS GlidePoint" "Device Accel Velocity Scaling" 100
xinput list-props "ImPS/2 ALPS GlidePoint" | grep Velocity
```

Explore your hardware and compose xinput set-prop command for your device:
```

xinput list
xinput list-prop "touchpadname"
man xinput
```I am sorry for my english.

---

### Post by spreeker on 2011-05-27
I had the same problem with my Dell. In the mouse options, try increasing the speed but decreasing the sensitivity.

---

