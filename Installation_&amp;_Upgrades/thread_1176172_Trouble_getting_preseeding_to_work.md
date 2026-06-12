---
title: "Trouble getting preseeding to work"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by mmilliss on 2009-06-02
I've finally seen the light and am switching from fedora to Ubuntu 9.04. The only stumbling block is trying to automate the installation using preseeding (I used kiskstart in Fedora land). I have about 30 PCs to upgrade so an automated method is preferable.

I've tried many different variations to get preseeding to work and I still end up getting asked questions that I though would be removed when I used preseeding.

Here's the different ways I've tried.
1. remastered the CD by modifying the /isolinux/text.cfg file, changing this line 
append file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
to this line
append url=http://192.168.0.29/preseed.cfg boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --

2. remastered the CD by modifying the /isolinux/isolinux.cfg file, adding this line to the end of the file
preseed/url==http://192.168.0.29/preseed.cfg

3. manually added the line below to the boot parameters at install time
url=http://192.168.0.29/preseed.cfg

None of these seem to work, I still get the questions asked at install time. I've tried with a minimal preseed file as per below but nothing seems to work.

#start preseed.cfg
### Localization
# Locale sets language and country.
d-i debian-installer/locale string en_US

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# # /usr/share/zoneinfo/ for valid values.
d-i time/zone string Australia/Sydney
#end preseed.cfg

Any help would be appreciated
Cheers
Matt

---

