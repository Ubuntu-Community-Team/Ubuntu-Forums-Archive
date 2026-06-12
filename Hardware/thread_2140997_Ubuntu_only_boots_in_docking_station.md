---
title: "Ubuntu only boots in docking station"
date: 2013-05-01
forum: Hardware
---

### Post by Christoph Bier on 2013-05-01
Hi all,

since I upgraded to 13.04 Ubuntu only boots when my ThinkPad X200s is placed in the docking station. Without docking station I can choose Ubuntu from GRUB'S menu but after entering the passphrase to decrypt the HDD I see the splash screen for about 30 minutes—the longest time I waited in case there was fsck checking the hdd. I checked /etc/fstab and /boot/grup/grub.cfg for correct HDD mapping. AFAICS everything is ok (hdd are identified by its UUID).

Any ideas what's going wrong here? What further information do you need to help me?

Best regards
Christoph

---

### Post by Christoph Bier on 2013-05-03
For those who care: Just remembered that previous versions of Ubuntu showed a message when some external drives mounted on /media were not found&#8212;one had to press &#8220;s&#8221; to skip mounting. I did that and it worked. Looks like a bug to me. The previous message &#8220;The disk drive for /media/XXX is not ready or not present. Continue to wait or press S to skip mounting or M to manual recovery.&#8220; should be shown again. I'll file a bug when I find the time to do it.

---

