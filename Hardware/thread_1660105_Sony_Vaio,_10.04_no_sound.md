---
title: "Sony Vaio, 10.04 no sound"
date: 2011-01-04
forum: Hardware
---

### Post by WASHAD on 2011-01-04
I had to give up on 10.10 with my new i7 sony vaio - just couldn't get it to work. Instead, I've reverted back to 10.04. 

Trouble now (among others) is that I have no sound. I've searched lots of posts and tutorials to no avail. 

I appear to have the latest version of alsa, and I've run the mixer and have set volumes on everything. 

Nothing seems to work, any help is appreciated. 

Thanks, 

Steve

---

### Post by lidex on 2011-01-05
I don't think the lucid kernel incorporates the latest alsa. Can you give some info please?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by WASHAD on 2011-01-05
Awesome, thanks for the reply. 

> [http://www.alsa-project.org/db/?f=1bb58b480b8dc03572f2e193d311dc2a430109b2](http://www.alsa-project.org/db/?f=1bb58b480b8dc03572f2e193d311dc2a430109b2)

---

### Post by lidex on 2011-01-05
Can you post this output for me:
```
dpkg -l | grep "alsa"
```

---

### Post by WASHAD on 2011-01-05
> **lidex said:**
> Can you post this output for me:
```
dpkg -l | grep "alsa"
```


Here it is:

```
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-27-generic    2.6.32-27.201101031600                          Ubuntu-supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-27-generic 2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.

```


Much thanks;

SteveJ

---

### Post by WASHAD on 2011-01-05
Wow! I've got audio now. Unfortunately, a couple of things happened simultaneously, no I'm not certain which fixed it. 

On today's update, their was an update to alsa. Also, I went into sound preferences and selected the radio buttons for internal audio on both the inputs and outputs. I'm not sure if they were there before. If they were, I just missed them. 

At any rate, I have audio now - Now on the rest of my problems. 

Thanks, 

SteveJ

---

