---
title: "Acer Aspire One Hang on Reboot"
date: 2012-03-26
forum: Hardware
---

### Post by rsmereka on 2012-03-26
Hi All,

I have an Acer Aspire One D257-13434 with it's 250gb hdd split between Win 7 (starter) and Linux. I had xubuntu (11.04) running on it without any issues.

I decided to give lubuntu a try and installed from the 11.10 full (from a USB stick) and now when I get lubuntu to reboot, the netbook hangs at a black screen. The power is still applied but it's in limbo. I have to perform a hard stop (either press and hold the on/off button or pull the AC adapter and pull the battery).

Any ideas on why this happens with lubuntu but not with xubuntu? Any ideas on how I can fix this behavior?

TIA,
Rick

---

### Post by LoRd MuldeR on 2012-10-22
Hi.

I have the very same problem with my Acer Aspire One D257.

Everything works fine under Ubuntu, except that it will hang with black screen, when I try to reboot. So I have to do a "hard" power-off.

Shutdown works fine. So when a reboot is needed, I currently have to shutdown + power-on.

This happened with Ubuntu 12.04 until I upgraded to 12.10 recently, but 12.10 has the same problem :(

It's really sad, because except for the reboot issue, Ubuntu works absolutely flawless on the Acer Aspire One D257 netbook...

Any ideas?

Thanks in advance!

---

### Post by wnelson on 2012-10-22
Is your system UEFI. If so? Add noefi to your /etc/default/grub

GRUB_CMDLINE_LINUX="noefi"

Todo this on the fly just edit the grub/kernel menu option.

This disables UEFI runtime services the Some UEFI implementations have wonky runtime services. There are three services boot, runtime, protocol noefi only disables runtime. With this option enabled /sys/firmware/efi/efivars will be empty. 

If you have to update grub at any time you will have to remove the above change before upgrade.

Walt

---

### Post by LoRd MuldeR on 2012-10-22
Don't think it's using UEFI. It's just a very simple Atom Netbook, no fancy stuff. But how do I check?

---

### Post by vegtelenegy on 2013-04-16
Hi All,

Here is the solution: [http://www.expertcore.org/viewtopic.php?f=20&t=3009](http://www.expertcore.org/viewtopic.php?f=20&t=3009)

---

