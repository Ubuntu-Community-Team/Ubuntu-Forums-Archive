---
title: "Minimal CD install - what next?"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by theRick on 2008-12-19
I installed the Ubuntu 8.04 Minimal CD on a laptop with an unreliable CD Rom.

The install is finished and I'm at the command line prompt.

I would like to have the full desktop install like you would get with the normal CD, but I don't know how to get to that point.

If someone could give me the steps or point me to a link that will help me get back up to speed I would greatly appreciate it.

Thank you in advance.

---

### Post by snowpine on 2008-12-19
Hi theRick,

Plug in your ethernet, and type:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Then go have lunch. :)

That will install everything you would get in a full install of ubuntu. Good luck!

---

### Post by theRick on 2008-12-19
Thank you for the quick reply and the speed warning! I genuinely appreciate it.

---

### Post by snowpine on 2008-12-19
No problem. You picked a smart way to install since your computer has an unreliable CD drive. Good luck!

---

### Post by theRick on 2008-12-19
I may be asking this question to late, but I can always start over.

I forgot to mention that the minimal CD install was for an iBook PowerPC so I used the minimal CD port.  Does that change any parameter I need to add to the code?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by markbuntu on 2008-12-19
All the tricky stuff for the iBook should have been taken care of in the initial installation kernel build and the applications you are getting do not care about that, they leave that to the kernel and apt-get. Apt-get will not get anything that does not belong in your system, that is its job.

---

### Post by michelino on 2009-02-13
hi,

after installing the base system, through the mini-iso. I want only what I need, with no other unnecessary stuff.

My system::
Pentium 4, video nvidia,  SATA2, chipset intel.

These are the additional services/packages that I installed for a clean system:

    > sudo apt-get install xserver-xorg-video-nv xfonts-base
    sudo apt-get install gnome-core gdm
    sudo apt-get install jockey-common jockey-gtk update-manager
    sudo apt-get install linux-backports-modules-intrepid
    sudo apt-get install gtk2-engines-murrine human-theme ubuntu-artwork
    sudo apt-get install build-essential linux-headers-$(uname -r)
    sudo apt-get install network-manager
    sudo apt-get fast-user-switch-applet
    sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases
    sudo apt-get install epiphany-browser epiphany-extensions epiphany-webkit

i'm not a guru, so there is some other usefull services/packages that I haven't installed?:lolflag:

tnx

---

### Post by darksideforge on 2009-11-10
> **theRick said:**
> I may be asking this question to late, but I can always start over.

I forgot to mention that the minimal CD install was for an iBook PowerPC so I used the minimal CD port.  Does that change any parameter I need to add to the code?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

aHA!  Is THAT how I get my iBook to boot from the mini-iso??? I have to download and burn the PowerPC 32 bit variety? I tried the regular mini last night and the iBook somebody gave me explores the CD but won't boot from it.

I don't know one end of a Mac from the other so I'm going to try this now! I know when I tried to initialize the CD the iBook told me the CD didn't have the right parameters to boot.

Any other additional words of wisdom for me?

---

