---
title: "[HowTo] Toshiba A200-1OR (PSAE6) and Gutsy"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by Blogan on 2008-01-23
I bought the Toshiba A200-1OR notebook not so long ago, and installed Ubuntu Gutsy on it. It worked very well, I must say. There are some minor issues which I will describe below, and their solutions. Just a small detail: I flashed the BIOS to the XP version via the Toshiba site, it might make a difference...

**Splash screen**
As many other notebooks, the splash screen doesn't work when using Gutsy. You will get a black screen instead. If you don't fix this issue at the beginning, you will get in trouble later on, when you install the latest ATI drivers. The only way you can get the Login Manager to work then is adding "nosplash" to the kernel line.

Anyhow, follow these simple instructions:
1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) Run this in a terminal:
```
sudo update-initramfs -u -k `uname -r`
```

**ATI Display Driver**
The HD2400 graphics card is not auto-detected by Gutsy. Install it by using [Envy](http://albertomilone.com/nvidia_scripts1.html). Just use the auto-detection. After installing this driver you can also use Compiz / Desktop Effects. After installing this driver and restarting the notebook, you will notice Gutsy selects the 1280x800 resolution and 3D acceleration is working.

**Sound Driver**
The soundcard works, but unfortunately not with the mini-jack. The sound quality is also better under Windows XP. The notebook has a Intel ICH8 HD Audio Controller, which is not so good supported atm. I tried [this topic](http://ubuntuforums.org/showthread.php?t=616845), but no success. If you have a solution for this, then please post a reply to this topic =).

All the other devices work as far as I could test it (webcam, function keys, etc.). :)

---

