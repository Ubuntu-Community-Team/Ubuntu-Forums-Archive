---
title: "Flaky Ubuntu 10.04 wireless on AcerAspireOne 110L"
date: 2010-04-20
forum: Hardware
---

### Post by arscariosus on 2010-04-20
I'm just curious, are there people here who still uses their AAO-110L netbook? If so, have you been experiencing the flaky wifi as well?

I hope this would be fixed tomorrow with the RC updates. If there's a work around with this, let me know. The wifi card is atheros.

---

### Post by Subban on 2010-04-23
The wife and I each use our AAO 110's a lot.

I just installed 10.04 on mine last night and did all updates. Had to use wired connection because wifi was incredibly slow and constantly dropped connection to the AP in the same room.

Edit:
Wireless seems to now be working ok with the manual installation of the following files:
[B]	linux-backports-modules-wireless
	linux-backports-modules-wireless-lucid-generic[/B] - Select this one first and it will select the other, for your kernel version.

You may need to open your Software Sources in Administration menu and enable the **"unsupported updates (lucid-backports)"**

I think you also need (Edit, this was already installed on a clean reinstall, but I will leave it to check)
**        bcmwl-modaliases** 



I think the media card slots are also still broken. Unless the card is in the slot at boot time it won't be seen when you insert it.
Edit: Fixed the media cards by the Following:

You need to edit **/etc/default/grub** (as root ofc) and find the line that starts:
**GRUB_CMDLINE_LINUX_DEFAULT=**

Change it to read in its entirety:
**GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 elevator=noop quiet splash"**

The pciehp fixes the card readers to be hot swappable and the elevator=noop improves SSD performance.

I have rebooted a few times, installed twice these fixes seem to work fine. 
Hope this helps you too.

---

### Post by arscariosus on 2010-05-11
Thanks for the card reader fix! :P

---

### Post by Subban on 2010-05-11
You are welcome, that and a couple other things to fix/correct for the AAO in Lucid 10.04 are up on my blog, My sig has link.

---

