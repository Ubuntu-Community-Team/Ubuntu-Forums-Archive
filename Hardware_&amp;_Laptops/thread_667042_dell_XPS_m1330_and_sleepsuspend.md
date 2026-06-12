---
title: "dell XPS m1330 and sleep/suspend"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by kswenson on 2008-01-14
I would like to get people's feedback on how well sleep (suspend to memory) works for everyone on their m1330.
Mine has the following configuration...

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
WLED scree with 0.3 Mpixel webcam

I find that sleep (i.e. close the lid and have it suspend to RAM and then open the lid and have it come back) works a little more than half the time...
   the times that it doesn't work are mostly problems when coming back up but sometimes it doesn't go down right.

I haven't found any patter.  It seems to have nothing to do with how long it is asleep or whether or not I have compiz running.
(I have fixed the "sound doesn't work after waking up bug")

Are other people having similar issues?
Has anyone managed to fix this?

---

### Post by kswenson on 2008-02-01
I FOUND A PATTERN!

If I leave my machine on a desktop with no windows then the thing always wakes up!
Strange.

EDIT:  OK, this doesn't always work either.

---

### Post by dev.urandom on 2008-02-01
From my experience from  testing hibernate:

Hibernate works only 2/3 of the time. Sometimes, the laptop won't turn off when hibernate is initialized. The biggest problem however, is that whenever the laptop returns from hibernation, the volume is always increased to it's maximum. Even if you try to lower the volume, it will still increase itself. That, and the fact that hibernation is almost as slow as regular booting. I can't figure out why vista can boot from hibernation in less than 5 seconds, skipping the post, boot loader and everything, but ubuntu has to go through both the vista bootloader and grub, and then start booting as if it was on runlevel 1.

---

### Post by kswenson on 2008-02-11
Try this and see if it works:
[http://ubuntuforums.org/showthread.php?p=3608627#post3608627](http://ubuntuforums.org/showthread.php?p=3608627#post3608627)

---

### Post by atlas95 on 2008-02-11
try mon howto here : [http://www.atlas95.com/blog/2007/10/02/installation-tweaking-dell-xps-1330-avec-ubuntu-gusty/](http://www.atlas95.com/blog/2007/10/02/installation-tweaking-dell-xps-1330-avec-ubuntu-gusty/) 

in french sorry but maybe you will understand the command, and my xorg.conf is here: 
[http://www.atlas95.com/fichiers/xorg.conf.m1330](http://www.atlas95.com/fichiers/xorg.conf.m1330)

use it and I think you will have no problem, all is working for me ;)

best regards.

---

### Post by reidbold on 2008-02-11
Sort of related, the new 2.6.24 handles suspend much better on my T61, so it might be worth trying.  I haven't tried to hibernate with it.
install thread: [http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

---

### Post by chadeldridge on 2008-02-11
Wasn't there a reported bug with Dell laptops suspend function (cant find the link atm) and needing to add a line to the grub loader to fix the weird power management issues?

---

### Post by RichTJ99 on 2008-02-11
Has anyone tried this fix from Dell?

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

Ubuntu 7.10/Issues/8400M Suspend Hibernate-Failure
From DellLinuxWiki
< Ubuntu 7.10
Jump to: navigation, search


Description: Suspend and Hibernate do not always work with nVidia 8400M video controller and the 'nvidia-glx-new' driver
Systems Affected: Inspiron 1420n, XPS M1330n
Impact: Unable to suspend and hibernate properly
Fix/Workaround: Run the following script:

#!/bin/bash
# Workaround for Suspend and Hibernate with nVidia video cards
perl -p -i -e "s|MODULES=\"\"|MODULES=\"uvcvideo\"|g;" /etc/default/acpi-support
perl -p -i -e "s|SAVE_VBE_STATE=true|SAVE_VBE_STATE=false|g;" /etc/default/acpi-support
perl -p -i -e "s|POST_VIDEO=true|POST_VIDEO=false|g;" /etc/default/acpi-support
perl -p -i -e "s|# DISABLE_DMA=true|DISABLE_DMA=true|g;" /etc/default/acpi-support

The latest 3-D driver from nVidia (released Dec 20, 2007) at [http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html) has improved S3/S4 support. Until the driver is added to the Ubuntu 7.10 repository, it can be easily downloaded and installed with envy.

Note: This workaround is only applicable to the 'nvidia-glx-new' driver. There is currently no workaround or fix for the same problem with the native open-source 2D 'nv' driver. 


Im not exactly sure how the fix works (does this disable 3d)?

Thanks,
Rich

---

### Post by Havoc911 on 2008-02-15
Rich,

I can confirm that this script does indeed work. I was having the same problem with hibernation/suspension, and after applying this script I am now able to suspend/hibernate the laptop. It doesn''t appear that the script disables 3D or anything, it simply changes a couple of settings that the driver uses  so that hibernation works again. Let's hope that the latest drivers are added to the Ubuntu repository ASAP.


Regards,
Matt

---

### Post by thorcik on 2008-03-02
I checked this script and the effect is strange - suspend works just fine but is still crashes on hibernation - the screen goes black and laptop doesn't do anything, I can only turn it off by pressing and holding the power key.
Suspend used to do the same but is now OK.

---

### Post by gp2x on 2008-03-08
Same here - suspend now works but hibernate crashes.

Anyone with further ideas?

---

### Post by daxdog on 2008-03-20
This fixed my suspend issue.  I am still working on the hibernate.

Thanks.

> **RichTJ99 said:**
> Has anyone tried this fix from Dell?

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/8400M_Suspend_Hibernate-Failure)

Ubuntu 7.10/Issues/8400M Suspend Hibernate-Failure
From DellLinuxWiki
< Ubuntu 7.10
Jump to: navigation, search


Description: Suspend and Hibernate do not always work with nVidia 8400M video controller and the 'nvidia-glx-new' driver
Systems Affected: Inspiron 1420n, XPS M1330n
Impact: Unable to suspend and hibernate properly
Fix/Workaround: Run the following script:

#!/bin/bash
# Workaround for Suspend and Hibernate with nVidia video cards
perl -p -i -e "s|MODULES=\"\"|MODULES=\"uvcvideo\"|g;" /etc/default/acpi-support
perl -p -i -e "s|SAVE_VBE_STATE=true|SAVE_VBE_STATE=false|g;" /etc/default/acpi-support
perl -p -i -e "s|POST_VIDEO=true|POST_VIDEO=false|g;" /etc/default/acpi-support
perl -p -i -e "s|# DISABLE_DMA=true|DISABLE_DMA=true|g;" /etc/default/acpi-support

The latest 3-D driver from nVidia (released Dec 20, 2007) at [http://www.nvidia.com/object/linux_display_ia32_169.07.html](http://www.nvidia.com/object/linux_display_ia32_169.07.html) has improved S3/S4 support. Until the driver is added to the Ubuntu 7.10 repository, it can be easily downloaded and installed with envy.

Note: This workaround is only applicable to the 'nvidia-glx-new' driver. There is currently no workaround or fix for the same problem with the native open-source 2D 'nv' driver. 


Im not exactly sure how the fix works (does this disable 3d)?

Thanks,
Rich

---

### Post by sdennie on 2008-03-20
The script mentioned above makes suspend/resume work just fine for me (though, I had to do some things to explicitly restart Network Manager).  I've actually never tried hibernate and don't really see why it's even relevant.  With a 9 cell battery, an XPS m1330 can sit in suspend mode for something like 200 hours without losing battery power (assuming a fully charged battery).  I haven't actually attempted to keep it suspended for 200 hours because I use the machine constantly but, while suspended, the trend seems to be 1% battery life per 2 hours.

---

