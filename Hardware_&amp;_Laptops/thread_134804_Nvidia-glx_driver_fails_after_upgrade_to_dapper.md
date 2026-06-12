---
title: "Nvidia-glx driver fails after upgrade to dapper"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by gnu2tux on 2006-02-22
Hi,

 I have an Nvidia 5200 AGP card which worked with the nvidia kernel modules when I was using breezy. After flight 4 was announced i bumped up to dapper.

The nvidia modules are all downloaded and installed from the universe as best as I can see but the x server dies when I start up with the module 'nvidia'. I'm using 'nv' at the moment which is sloooooooooow but it works.

I went to the extreme of deleting my xorg.conf and doing a dpkg-reconfigure xserver-xorg but to no avail.

This is the nasty bit :

---
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
---
shee-it.

Any ideas? I'm stuck. I hate being stuck.

Cheers,

Al.

---

### Post by bluebyt on 2006-02-22
I am sorry cannot help you, because I have the same problem as you!
I am using dapper with the same card 5200 and the output error are the same.

If I find something, I let you know. I tried to correct the problem since yesterday, that drive me crazy! :(

edit: the only thing different is that I did a fresh install of dapper.

---

### Post by gnu2tux on 2006-02-22
Thanks!

---

### Post by gnu2tux on 2006-02-22
uh-oh I think I forgot to install the linux-restricted-modules- for the new kernel:

$sudo apt-get install linux-restricted-modules-`uname -r`

i'm rebooting now, after making the necessary change to /etc/X11/xorg.conf

i hope that I'm not *that* dumb...

lol!

---

### Post by gnu2tux on 2006-02-22
i was that dumb...

\\:D/

---

### Post by puelocesar on 2006-03-24
I installed linux-image-2.6.15-19-k7 and linux-retricted-modules-2.6.15-19-k7 and I still get this error:

--
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

It was working perfectly with 2.6.15-14-k7

---

