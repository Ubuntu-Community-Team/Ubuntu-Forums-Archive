---
title: "DWL-650 Not Working?"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by Linux_Houftie on 2005-11-25
So I recently tried to get my wirless card working again (was never attemped on a linux platform prior). I'm using Breezy on the laptop with the wireless card, which is a DWL-650. After 2 hours beating my head off Google, I don't seem to be making any progress at all. The System->Administration->Networking  doesn't show the wireless card at all. I've read posts about people using the "Add" button to add another connection, I don't even have the add button. I'm extremely new to Ubuntu, just started using it with the latest release. Any help would be stellar here since I'm not really able to benefit from having a portable system. :) Thanks for any help in advance!

---

### Post by Lambert on 2005-11-25
I don't think you have a working driver so let's start here.

run these commands

sudo lshw -businfo

find your device in the list and notice the class of the device. Then

sudo lshw -C <class>

Post the output here.

You can also try the link in my signature wirelesstroubleshootingguide to see if you can get your card to work.

---

### Post by shartrec on 2005-11-26
I have a DWL-650 and am using it now under Breezy to write this post.  It can be installed with one of 2 different drivers but I can only recommend the wlan-ng drivers.  The Orinoco driver that ships with Ubuntu can be used for this card but it was not designed for it and does not work very well.

Because the ubuntu developers disabled pcmcia functionality in their wlan-ng package you need to download the source and compile the package yourself  [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng).  You will need the kernel sources installed and configured to do this.  You also need to remove the current references to DWL-650 in the  /etc/pcmcia/config and /etc/pcmcia/hermes.conf so that the default driver does grab the card before the wlan-ng one.

I am a newby to ubuntu and debian systems so can't really give line by line instructions on setting up kernel sources but those instructions are available elsewhere on this site.  I used synaptic and just searched for kernel and selected kernel sources for my kernel.

The instructions in the README for the wlan-ng drivers are easy to follow and work well.  All the configuration is in the /etc/wlan directory

---

