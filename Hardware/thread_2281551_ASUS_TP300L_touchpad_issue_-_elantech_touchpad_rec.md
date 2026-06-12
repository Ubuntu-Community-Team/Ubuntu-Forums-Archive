---
title: "ASUS TP300L touchpad issue - elantech touchpad recognized as a logitech mouse."
date: 2015-06-07
forum: Hardware
---

### Post by Glen_Keane on 2015-06-07
Hey all,

Kinda new guy here, trying to troubleshoot an issue I'm having with my new laptop. I recently picked up the Asus tp300l transformer notebook and first thing I did was load up ubuntu on it. Its been great so far, except, my touchpad is being recognized as a logitech mouse :(

Here is the output of xinput:

```

glen@toormore-TP300LA:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel                                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

Not looking good, aye? I have tried fixes I came across from other searches, namely using the latest kernel, 4.0.4-wily, but its not working :(
This is the main link I used when troubleshooting: [http://ubuntuforums.org/showthread.php?t=2241520](http://ubuntuforums.org/showthread.php?t=2241520)

I also came across this, but Its for arch linux, or something like that, and I simply don't know how to use it: [https://aur.archlinux.org/packages/elantech-asustouchpad-dkms/](https://aur.archlinux.org/packages/elantech-asustouchpad-dkms/)
I have installed another dkms package to try fix this, but it didn't work, and I seem to have lost the link to it because I've scouring the internet for a fix! 

Any help you guys could give in fixing this issue would be much appreciated!

---

### Post by dino99 on 2015-06-08
the vanilla kernels are not supported by ubuntu, and may have some troubles due to the missing ubuntu patches.
that said your touchpad is working as expected, as you said, so why trying to fix something that is not broken ?

some doc: [http://community.linuxmint.com/tutorial/view/1361](http://community.linuxmint.com/tutorial/view/1361)

---

### Post by Glen_Keane on 2015-06-08
I may not have been clear with my issue, the touchpad works, but multitouch is disabled and therefore using the touchpad for navigation is annoying, I would simply like to resolve it so navigation is easier :)

I was using the latest kernel, to see if my issue is resolved in a newer build: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

I'm looking into that doc though, thanks.

---

### Post by craig-bauer on 2015-07-22
I had the same problem for many months on the same laptop.  Tonight I just upgraded from 4.0 kernel to 4.1.3 kernel and voila, multitouch scrolling!  Don't know when addition happened that made this work--must be in 4.1.something.  In any case, I am happy!

---

