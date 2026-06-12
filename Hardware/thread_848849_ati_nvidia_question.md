---
title: "ati nvidia question"
date: 2008-07-03
forum: Hardware
---

### Post by fazavon on 2008-07-03
I just need some clarity.

I am using an ATI something or other

For what ever reason the Nvidia-kernel-common is install and I have the nvidia-kernel in my startup scripts...

I am just wondering if I can remove the nvidia-kernel from boot-up with out causing issues?

Or if I can clear out all nvidia traces with out causing issues.

Thanks in advance

//j

---

### Post by fazavon on 2008-07-03
Sorry I forgot something..

Can I also remove all of the xserver-xorg-video that are not ATI?

Thanks again

//j

---

### Post by phidia on 2008-07-03
You can remove drivers the system doesn't need/use.
Just curious but how did you determine this > I am using an ATI something or other
?
You may want to look at [this guide]("https://help.ubuntu.com/community/Video") and check to make sure what card your computer has.
This command > lspci | grep VGA entered in a terminal should provide that.

---

### Post by fazavon on 2008-07-03
lspci

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)


I just did not remember which ATI it was.. (to lazy to run the command the first time.. might have helped to :) 

Thanks for the quick response.

//j

---

### Post by phidia on 2008-07-03
Glad to be of help. Do you need to enable the driver for that? If so take a look at [this]("http://ubuntuforums.org/showthread.php?t=515573").
I'm really not sure why you have that kernel package installed so I find it hard to confidently recommend removing it.

---

### Post by fazavon on 2008-07-03
Well I am going through the uninstall process and when I try to remove the nvidia-kernel-common it is trying to take my kernel

linux-generic
linux-restricted-modules2.6.24...
linux-restricted-modules-generic

for some reason I am thinking that might be a bad idea?

the others went off with out a hitch

---

