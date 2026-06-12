---
title: "Acronis True Image &amp; GRUB"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-12-28
I just received the following help from Acronis after a failed restore. I had to FIXMBR before I could restore an Acronis Image the restore GRUB; a real pain.
Here's Acronis's answer; sound ok? I'm reluctant to try anything in case I bugger it up again:

If you want to have Acronis Startup Recovery Manager and GRUB at the same time, please do the following:

Set the Linux boot (/root) partition Primary and Active (you can use any disk management software to do this)

Boot in Linux and install GRUB on this partition:
  #/sbin/grub-install /dev/boot_partition

Boot in Windows and activate Acronis Startup Recovery Manager

The above refers to LILO boot manager as well. To install LILO on a certain partition use the following command:
  #/sbin/lilo /dev/boot_partition

Please feel free to contact us at any time if you have further questions.

Thank you.:???:

---

### Post by xinloiemnham on 2008-05-10
> **AllanP said:**
> I just received the following help from Acronis after a failed restore. I had to FIXMBR before I could restore an Acronis Image the restore GRUB; a real pain.
Here's Acronis's answer; sound ok? I'm reluctant to try anything in case I bugger it up again:

If you want to have Acronis Startup Recovery Manager and GRUB at the same time, please do the following:

Set the Linux boot (/root) partition Primary and Active (you can use any disk management software to do this)

Boot in Linux and install GRUB on this partition:
  #/sbin/grub-install /dev/boot_partition

Boot in Windows and activate Acronis Startup Recovery Manager

The above refers to LILO boot manager as well. To install LILO on a certain partition use the following command:
  #/sbin/lilo /dev/boot_partition

Please feel free to contact us at any time if you have further questions.

Thank you.:???:

Are all the command typed in Terminal ?? Why all of them are begun with "#", or that 's only the link ??
I'm not English or American so my English is not good, sorry if what I typed was impolite.

---

