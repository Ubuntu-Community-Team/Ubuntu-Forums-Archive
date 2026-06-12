---
title: "Ubuntu Server won't install opencl compliant driver for ATI Radeon HD 4870"
date: 2013-05-06
forum: Hardware
---

### Post by some.hacker on 2013-05-06
I had an NVIDIA card in this computer and I installed the nvidia-opencl-dev package with no issues. After installing the ATI card, I tried to install the boinc-amd-opencl package and it tells me:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boinc-amd-opencl : Depends: amd-libopencl1 but it is not installable
E: Unable to correct problems, you have held broken packages.

lspci finds:
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4870

How do I install an opencl supported driver for this card?

---

### Post by matt_symes on 2013-05-06
Hi

amd-libopencl1 does not seem to be available for precise.

[http://packages.ubuntu.com/precise/boinc-amd-opencl](http://packages.ubuntu.com/precise/boinc-amd-opencl)

> amd-libopencl1 	         Package not available

An apt-cache search does not show it in Saucy either.

It also say's it's unavailable.

It may not be good for an AMD card.

[https://answers.launchpad.net/ubuntu/+source/boinc/+question/203438](https://answers.launchpad.net/ubuntu/+source/boinc/+question/203438)

Looks like debian may have it.

[http://pkgs.org/debian-wheezy/debian-nonfree-i386/amd-libopencl1_12-6+point-3_i386.deb.html](http://pkgs.org/debian-wheezy/debian-nonfree-i386/amd-libopencl1_12-6+point-3_i386.deb.html)

Kind regards

---

