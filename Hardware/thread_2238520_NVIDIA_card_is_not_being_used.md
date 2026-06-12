---
title: "NVIDIA card is not being used"
date: 2014-08-08
forum: Hardware
---

### Post by harsha_vardhan on 2014-08-08
I have an NVIDIA GeForce GT750M card on my  HP Envy 15 j133tx. I want to run some programs using the NVIDIA card instead of the integrated graphics card.

So, I have installed Bumblebee and tried to run the 'glxgears' using optirun, but I get the following error:

```

[ 1238.061055] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ 1238.061087] [ERROR]Aborting because fallback start is disabled.

```

lspci | egrep 'VGA|3D' command gives the following output:
```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)

```

This is the content of the file /etc/bumblebee/xorg.conf.nvidia : [http://pastebin.com/NdrX531x](http://pastebin.com/NdrX531x)

Any help would be greatly appreciated

---

### Post by harsha_vardhan on 2014-08-08
Hey guys!

I was able to fix this issue by issuing the following commands:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331

```

maybe some of the steps above were gratuitous, but it solved my problem

---

### Post by coffeecat on 2014-08-08
*Thread moved to **Hardware**.*

---

