---
title: "Live CD with All proprietary Drivers"
date: 2012-02-02
forum: Hardware
---

### Post by bmeslabs on 2012-02-02
Good Day,

I am trying to build a customized Ubuntu Live CD with the major proprietary drivers avaialbe to the user so that they may run the CD with accelerated graphics on a large variety of machines; namely those with Intel, Nvidia, and ATI graphics cards.

I want the system to detect before starting X.org which one the user has and properly load the right modules and create the appropriate Xorg.conf.  I have looked at Ubuntu Customization Kit and Remastersys.  Remastersys says that explicitly blacklists all of the proprietary drivers.  

Xbmc-live project has done this and I've ready that sabayon does this also, so I know it is possible.  I'm OK with either a Live CD/DVD or a Casper install on a USB stick.

There were two approaches I came up with:
1.  Capture the different drivers in additional sqaushfs (supplemental to the casper-rw file, like home-rw I could have an nvidia-rw, ati-rw, and intel-rw) files and select the driver you want to load during the grub boot menu.
2. Install all driver packages and create startup scripts which call jockey-text to switch between them before X starts up.

Any help, suggestions, or ideas would be appreciated.

Thanks.

---

