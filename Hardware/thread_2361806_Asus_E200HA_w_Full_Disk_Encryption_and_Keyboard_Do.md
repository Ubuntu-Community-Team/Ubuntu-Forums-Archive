---
title: "Asus E200HA w/ Full Disk Encryption and Keyboard Doesn't Work on Boot -- FIX"
date: 2017-05-20
forum: Hardware
---

### Post by KenUBF on 2017-05-20
Hi all!! I just recently installed Ubuntu Gnome on my Asus E200HA laptop and I set up full disk encryption on install. Everything, with the exception of the sound, worked great...until I rebooted for the first time and was asked for my decryption password. To my surprise my keyboard was not being recognized at this point. I had to use a USB keyboard to enter my password and once the system booted my keyboard worked as normal. I found very little information on the forums about this issue. One thread mentioned that re-flashing of the bios fixed the issue, but this did not work for me. So I got some help and he figured it out. The issue is that the modules needed to recognize the keyboard were not loading at this stage, so he manually inserted them. I'm still new to learning Linux and a little fuzzy on the exact details but a brief  blog post was written about how this issue was solved: [http://www.azloco.org/node/257](http://www.azloco.org/node/257)  Here is copy of the text in the post:

> The critical information was found on this page: [https://forums.linuxmint.com/viewtopic.php?t=211313](https://forums.linuxmint.com/viewtopic.php?t=211313)
 
We theorized that a driver needed for the laptop keyboard is on the encrypted drive and therefore not yet available when the password was needed.
using lsmod showed more than 100 modules loaded. Which ones were needed for the keyboard wasn't clear (simply using those ones that mention "hid" was not successful). We simply added all modules shown by lsmod to the /etc/initramfs-tools/modules file and re-created the initramfs.

On next boot the keyboard was operational and usable for entering the disk password.




I hope this can help someone at some point in the future.

---

