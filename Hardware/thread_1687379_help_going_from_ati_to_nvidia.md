---
title: "help going from ati to nvidia"
date: 2011-02-13
forum: Hardware
---

### Post by shaunsoul55 on 2011-02-13
Ok, so my current desktop is running Ubuntu 10.04.1 and is currently using it's onboard ATI Radeon HD4200 with the proprietary ATI drivers. I'll soon be changing to an Nvidia GeForce GTS 450, and I was wondering if there were any particular steps I should take before installing the card. Will simply uninstalling fglrx be enough? And what drivers are best to use for Nvidia, the open source ones or proprietary?

---

### Post by sam1948 on 2011-02-13
basically just install (physically) the nvidia card.
when starting ubuntu it will be recognized and should offer u to install propriety drivers.

if it won't offer automatically do as describe in the attached picture

---

### Post by shaunsoul55 on 2011-02-13
Thanks! Should I disable the onboard 4200 before installing the new card?

---

### Post by cascade9 on 2011-02-14
> **shaunsoul55 said:**
> Thanks! Should I disable the onboard 4200 before installing the new card?

Yes, you should. 

BTW, jockey (system-> administration-> drivers) wont work with the GTS450. The nVidia driver version in 10.10 and earlier is not a late enough version to work with the GTS450. So you would need to add a PPA or manually install the drivers. Or get a GTX460, they arent much more, have a fair bit more power and work with jockey withotu sodding around.

*edit- the open soruce drivers work, but they are pointless in some ways. 3D performance is bad, and no VDPAU. If the 3D isnt a problem, just get a cheap GT220/GT240/GT430.

---

### Post by shaunsoul55 on 2011-02-14
Is this the correct PPA for stable proprietary drivers?
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

There are 3 packages listed for Lucid:
```

nvidia-graphics-drivers           270.18-0ubuntu1~lucid~xup1
nvidia-graphics-drivers-173    173.14.27-0ubuntu1
nvidia-graphics-drivers-96      96.43.18-0ubuntu1
```Since the latest package synaptic lists is "195.35.24-0ubuntu1~10.04" i'm guessing i should be installing the "270.18-0ubuntu1~lucid~xup1" package correct? Also, this package from the PPA adds, according to the changes file, an update for "nvidia-current-modaliases". If I install the the updated modaliases, will jockey correctly install the right driver?

EDIT:
I saw that the PPA lists 270.18 as the newest driver, while Nvidia's website only shows 260.19.36. [Link to Nvidia page]("http://www.nvidia.com/object/linux-display-ia32-260.19.36-driver.html")

EDIT2:
I noticed the 270.18 drivers on Nvidia's BETA drivers section([Link]("http://www.nvidia.com/object/linux-display-ia32-270.18-driver.html")). The description for the PPA says they are the latest STABLE drivers, why are they using packages that Nvidia considers BETA?

---

### Post by cascade9 on 2011-02-15
I think that is the right PPA, but I cant be sure....I virtually never use PPAs. 

As for the 270.xx drivers *shruggs*. IMO they shouldnt be using beta drivers.

---

### Post by shaunsoul55 on 2011-02-15
Would I be better off attempting to use the one from nvidia's site? I'll have to go about finding out how to install it in such a case. :?

---

### Post by sam1948 on 2011-02-16
i use nvidia. it works fine.
i just installed the Ubuntu automatically recommended.

---

### Post by shaunsoul55 on 2011-02-16
The problem is that the earliest driver Nvidia shows to support the GTS 450 is 260.19.12, while the latest package in Lucid predates this, being 195.35.24 which according to nvidia's site only supports the GTX 470/480.

EDIT:
Perhaps I should follow this guide here on the ubuntu forums for installing drivers from nvidia's site. [Link]("http://ubuntuforums.org/showthread.php?t=1467074")
The only question would be do I do the blacklist stuff BEFORE or AFTER I install the card.
Will leaving fglrx installed be a problem(or is it even possible)? If anything ever goes wrong with the nvidia card, I'd like to be able to have my onboard 4200 to fall back on with the proprietary drivers.

---

