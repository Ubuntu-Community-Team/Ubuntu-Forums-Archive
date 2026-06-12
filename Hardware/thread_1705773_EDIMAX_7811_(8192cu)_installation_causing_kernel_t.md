---
title: "EDIMAX 7811 (8192cu) installation causing kernel to lock up in 10.10 server (64-bit)"
date: 2011-03-12
forum: Hardware
---

### Post by dreyas on 2011-03-12
Hey folks,

I'm setting up a new server rack and I'm trying to use the EDIMAX nano for wireless access.

I've tried a number of ways to install the modules, but everything I do results in a kernel lockup.

Here's what I've tried (and failed at):



fresh OS install

#sudo apt-get install build-essential linux-headers-generic

download drivers from EDIMAX

# make clean
# make

(at this point I get a bunch of warnings about pointers being address improperly)

# sudo make install
# sudo modprobe 8192cu

kernel returns a slew of errors
(kernel freeze)

(also tried insmod instead of modprobe and also done the whole thing as root, always results in kernel freeze once the USB device is plugged in)

Any thoughts? I have a feeling it's the 64-bit part that's the problem, but does that really mean I need to choose between wireless and 64-bit operations?

Thanks so much for your time!

Peace,
Drew

---

### Post by dreyas on 2011-03-12
Nevermind... I fixed it...

For those of you who are having this exact problem... you need to download the RTL8192CU drivers from RealTek's website and install those instead. No more compile errors and it's up and running fine now.

---

