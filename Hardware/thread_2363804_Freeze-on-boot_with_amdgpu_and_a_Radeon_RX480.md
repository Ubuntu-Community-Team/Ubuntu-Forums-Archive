---
title: "Freeze-on-boot with amdgpu and a Radeon RX480"
date: 2017-06-14
forum: Hardware
---

### Post by omniomnibus on 2017-06-14
Hey everybody!

I just upgraded my computer with a radeon RX 480, since I read everywhere that after some work it runs very well with the stock drivers on Linux. I am personally a Xubuntu user, but I tried Ubutnu as well ,since I just cannot get this card to work. I have te following issue:

After just installing the card in my computer, Xubuntu/Ubuntu will not boot anymore. To specify "will not boot":

- After grub (grub works fine), booting into Xubuntu 16.04:
- black screen (curiously it stays on, though!)
  - Note: the screen stays black even if I remove "quiet splash" from the kernel boot options
- The numlock LED goes on, then off, and stays off
- My mouse has LEDs that fancily turn on when (I think) it gets initialized. Those also turn on, then off, and stay off.
- After the LED stay off, the computer does not react to inputs anymore. No Ctrl+Alt+Delete to trigger a reboot, no nothing.

I have seen this happen on the distros: Xubuntu 16.04, Xubuntu 17.04, Ubuntu 17.04.

I read the articles regarding the RX480 and I know that one needs to perform extra trickery to get it to work with 16.04, which is why I also played around with 17.04. No luck.

Since it is clearly some hardware-software interaction, I dipped my feet already into kernel debugging and tried to:
 - create crash dumps with kdump: [https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html](https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html)
 - write logs to another console using netconsole: nothing

- I would buy a usb-to-serial adapter to do serial logging, but do not have the necessary hardware yet.

It is not hardware issues, since the graphics card works fine using Windows 7. I can also boot into all my linux systems when using "nomodeset" in the kernel boot options, which leads to amdgpu failing to initialize, therefore, falling back to VGA-drivers which work fine. I need OpenGL support though.

I am now trying to install Arch Linux to see if any optional Linux component causes this issue.

-------------------

My question is: does someone have an idea how to further debug this issue, or does someone experience the same issue?

---

### Post by gsahli on 2017-06-15
I had trouble using the amdgpu driver too.
I used ideas from this:
[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)
I ended up adding the simple xorg.conf to force use of amdgpu driver. Also blacklisted the (older) radeon driver (/etc/modprobe.d/blacklist.conf)
HTH

---

