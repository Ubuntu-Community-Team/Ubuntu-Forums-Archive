---
title: "Touchpad and PS/2 Mouse"
date: 2011-04-30
forum: Hardware
---

### Post by drgnrave on 2011-04-30
Hello,
   I have just upgraded to Ubuntu 11.04 (Gateway NV53u Laptop), with no problems except that I have lost the ability to scroll with my touchpad on my laptop.

Running xinput list shows that there is a PS/2 Mouse and AlpsPS/2 ALPS Glidepoint. Also, going through the Mouse and Pointer Device options, I see touchpad options, which I can fiddle with, but have no visible change. It seems as though the touchpad is recognized as a PS/2 Mouse, but a touchpad is recognized.

Any help would be appreciated.

---

### Post by cbennett926 on 2011-08-01
I have this same problem, I really hope someone notices this and knows how to fix it.

---

### Post by thiagopv on 2011-08-07
I am sharing exactly the same problem on Sony Vaio VPCSA.

---

### Post by dixoncx on 2011-08-14
Me too face same problem, in ubuntu 11.04
with sony vaio VPCEH

---

### Post by pepsi.farkas.peter on 2011-09-29
Same to me...
My model number Sony Vaio VPCEH1Z1E

I'm looking forward to a solution. ;-)

---

### Post by mrvoxel on 2011-10-05
I have the same issue with the Sony S VPCSA.

While searching numerous forum reports similar to this one, I came across the following (partial) workaround:

```

#!/bin/bash

sudo rmmod psmouse
sudo modprobe psmouse proto=exps

```

I have this script run on startup.

This enabled scrolling on my machine.  HOWEVER **(and this is important):**  The "trackpad" tab in the Mouse settings disappeared.  Not that they actually *did* anything before hand (I had the same issue where it caused no visible change) but now it just doesn't exist.

While scrolling works, I cannot disable click-by-touch on the trackpad, which I personally dislike, as I bump the trackpad often while typing.

EDIT: Edited to clarify language

---

### Post by Copper Bezel on 2011-10-18
Does [_modifying udev rules_]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html/") change anything? I know this is old stuff, but it should theoretically be possible to change or disable tap-to-click from there.

---

### Post by linuxfan34 on 2011-12-02
Problem solved!  Solution is found here, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051).  Have been unable to scroll with the touchpad on my hp dm4 2070us.  Installed the deb file found at comment #57, restarted the laptop, and the touchpad scrolling works!  Horiz scrolling and disabling the touchpad while typing all work.  Been waiting a long time for this fix.

---

