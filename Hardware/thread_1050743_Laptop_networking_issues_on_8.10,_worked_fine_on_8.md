---
title: "Laptop networking issues on 8.10, worked fine on 8.04"
date: 2009-01-26
forum: Hardware
---

### Post by HyperHacker on 2009-01-26
OK, so. I have a Gateway MX7515. Installed Xubuntu 8.04 on it, worked great. Supported everything right out of the box. I eventually broke it by deleting some files I didn't think were important, and then a few weeks later it started crashing at random.

So I formatted and installed 8.10. It took a lot of messing about to get it to a working, usable state (which is funny, because with 8.04 everything worked right from the start), and there's still a couple issues.

Whereas 8.04 connected to the wireless network automatically, 8.10 couldn't operate the network hardware at all. dmesg told me to go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and follow the instructions there. The Ubuntu instructions don't work (the script doesn't exist), so I did the manual method. That got wireless working (only if I turn the radio on, disable networking, and enable it again), but it won't connect to a wired network. It shows "the network has been disconnected" as soon as I enable networking. I'm told eth0 doesn't even exist.

At startup I see a message "Aperture beyond 4GB, ignoring." It only has 1GB of RAM, so what would that mean?

I can't install zsnes from the Add/Remove Applications window. The checkbox is greyed out. O_o

---

