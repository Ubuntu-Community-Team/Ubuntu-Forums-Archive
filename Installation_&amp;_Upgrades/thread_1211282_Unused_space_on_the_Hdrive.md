---
title: "Unused space on the Hdrive"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Bert_421 on 2009-07-12
I installed Fedora on the same drive as Ubuntu. I see Linux does not play nice with other Linux Distro's, Fedora does not see Ubuntu or add it to the boot loader. This is true about Ubuntu as well after farting around with both distro's I was unsuccessful to get either   distro to see each other  so I deleted the Fedora distro and now I have been trying to get Ubuntu to use up the free space left from Fedora.
 

 1. How is this done?  ( I fooled around gparted but it will not allow or have the option available to expand the current Ubuntu portion)

---

### Post by oldos2er on 2009-07-12
Some distros add other OSes to grub when they install, some don't. I've always found Ubuntu "played nice" by adding any other OSes it finds to its grub menu.

 If you're trying to alter a partition that's mounted (in use), you'll need to unmount it first. If it's your boot partition, you'll need to boot from the gparted CD, or an Ubuntu LiveCD.

---

