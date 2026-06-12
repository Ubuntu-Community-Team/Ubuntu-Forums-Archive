---
title: "Mouse Quits Working After Login"
date: 2013-07-10
forum: Hardware
---

### Post by SBJ95 on 2013-07-10
I'm having an issue in Kubuntu (also tried in Mint with Cinnamon and Arch with kde/kdm) where, upon login, I can move my (USB) mouse for about 5 seconds.  After that, my mouse freezes and will not move; mouse buttons do not work either.  If I unplug it and plug it back in, it does not even light up.  I've tried other USB ports on the computer, which do not work either.  I've tried plugging it in to another machine and it works fine there.  It used to work fine on this same computer when it ran windows.  If I plug in another mouse, the new mouse works fine indefinitely, and sometimes causes my existing mouse to work while its plugged in.

Also interesting to note, the whole system locks up when I try to go to a tty (Ctrl+alt+F[1-5]).  Haven't had that issue before either.  Oh, and the mouse worked the last time I had 13.04 installed on this computer.

I've looked through dmesg, /var/log/*, lspci, and lsusb, and there's nothing that indicates any sort of failure.  It finds the mouse just fine and loads the kernel modules just fine.  After the failure, there's nothing at all to indicate it's stopped working.  If I unplug it and replug it, nothing.  I don't know where else to look for any information, or what to do.  I'd rather not use another mouse because this mouse *should* work fine and is rather nice (it's a Razer Tron).

I appreciate any insights!

---

### Post by dino99 on 2013-07-11
maybe try with the solaar ppa  [https://launchpad.net/~daniel.pavel/+archive/solaar](https://launchpad.net/~daniel.pavel/+archive/solaar)

---

