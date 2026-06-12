---
title: "Acer 6935g Sound Problems"
date: 2009-05-09
forum: Hardware
---

### Post by medivh on 2009-05-09
I recently bought a laptop and there are some problems with the audio.

1- When I turn on the laptop with headphone pluged. Headphones work but when I remove them speaks does not start working and wise versa. There is no headphone switch in Volume Control.

2- Internal sub woofer doesn't seem to work.

I tried several things like installing a new alsa driver or editing some config files but nothing worked. I manage to get sound but far less comfortable than windows. 

PS: For 9.04 they spend a lot of time for boot up time. Please put such effort for driver issues in 9.10 at least for audio drivers.

---

### Post by Love&lt;3Duckie on 2009-07-13
Hi, can I just ask what method you went about using in order to get sound on this laptop?

I also recently got this laptop along with a WUBI installation of Ubuntu. However, I cannot seem to get sound no matter what to do. I have yet to do some tinkering with the drivers however, I don't know where to start.

---

### Post by applefreakpeeps on 2009-08-12
Get the latest alsa-driver snapshot from [http://www.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090812.tar.bz2](http://www.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-20090812.tar.bz2)

Untar this, change to the alsa-driver directory, compile and install it using

> ./configure
make && make-install

Ensure you have dependencies like linux kernel headers and kbuild installed, else this will fail.

Reboot to get audio chip working. Everything works (SPDIF/Jack sense and automuting/Woofers/Internal and External mic).

---

