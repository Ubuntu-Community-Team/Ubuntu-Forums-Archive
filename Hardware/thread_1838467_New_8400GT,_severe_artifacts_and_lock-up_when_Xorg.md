---
title: "New 8400GT, severe artifacts and lock-up when Xorg starts."
date: 2011-09-03
forum: Hardware
---

### Post by infested999 on 2011-09-03
I'm upgrading from a ATI Rage 3D, which worked ok but doesn't support resolutions higher than 800x600. First time I booted up with a new Geforce 8400 GT the screen was just divided in the center, black on the left half, white on the right half. I have never seen a problem like this before so I tried a different LiveCD.

I tried the card with boot the DVI and VGA connectors on another computer and the card was running just find under stock Ubuntu in the other computer. Then I plugged in a Windows XP hard drive on the "broken" computer and it worked just fine.

I booted TinyCoreLinux and ti booted fine, I was able to add 'text' to the boot line in grub.cfg so I can work on it. Next time it booted into tty1 and I removed all packages that started with nvidia-*, hoping that it will boot into either nouveau or vesa. Still the same error every time. Here is the log file I was able to save over scp:

[http://paste.ubuntu.com/681409/](http://paste.ubuntu.com/681409/)

What do I try next? I know that it works under Xvesa because TinyCoreLinux was running just fine, and XP was running just find, and stock Ubuntu on my other computer was running just fine.

---

### Post by infested999 on 2011-09-03
I've removed all nvidia* related files and nouveau* related files and it's running using the vesa drivers just fine now. It's somewhat of a waste that I bought a fast graphics card and I can't play 720p with it because the official drivers don't work though :(

---

