---
title: "why is compiling hostap driver so impossibly hard?"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by stanwebber on 2005-04-08
i've been working on this for the last week solid under 3 different linux distos (slack,debian) all with the same goddamn result.  at this point i am utterly desperate for help.  i am new to linux & have been trying to teach myself, but failing miserably

at present i have ubuntu 5.04 release candidate newly installed plus the following additional packages:
linux-source-2.6.10
build-essential

i extracted the kernel source to /usr/src & copied/renamed the .config file from /boot

i installed the latest stable hostap source (0.3.7) to /usr/src & defined the path to the kernel source in the makefile as well as on the command line

whenever i try to compile to driver i get upwards of 10000 warnings/errors before make fails.  this is the exact same result in all 3 distros i have tried including ubuntu 4 stable.  all kernel sources have been 2.6.8 or higher.  i've tried running make oldconfig on the kernel source plus a myriad of other hopeless ideas

for the love of god someone please tell me what i'm doing wrong

---

### Post by az on 2005-04-08
A pristine source is not what youneed.

1- try just using the kernel headers.  The packages is named linux-headers-(whateverversion) instead of the kernel source.

2-  If that does not work, your driver is peing picky.  It really does not need _all_ the source, but it asking you for it.  Install the source and kernel-package and unpack it
tar xvjf linux-source*
cd linux-source*
cp /boot/config-2.6.10-5 (Or whatever version of the kernel you use)
sudo make-kpkg --revision=1 --appen-to-version=-386 (You need to be specific to what your kernel version is named.) kernel_headers

This will compile the essential bits of your kernel so that you should be able to make the driver.  Be sure you have all your version information correct.  Now you should be able to use your source directory to build the module.

If that still does not work, rebuild your whole kernel (Really should not be neccessary!)

make-kpkg --revision=1 --appen-to-version=-386 (You need to be specific to what your kernel version is named.) kernel_headers kernel_image
cd ..
sudo dpkg -i kernel-image*.deb

---

### Post by stanwebber on 2005-04-08
questions

if i install the kernel headers via synaptic where will they be unpacked?  i assume i will need the 386 module for a debian/ubuntu default install.  do i still define KERNEL_PATH to the kernel source or to where the headers are located?

i am totally unfamiliar with debian make-kpkg.  i assume i will find my exact kernel ver name using uname.  could you please retype the make-kpkg command syntax to use a specific (to your system) example.  i can modify to apply to my system--your notations asis are confusing me.

let me stress i am completely new to this--as in the last 7days.  i am able to readily grasp linux concepts, it's the specifics that continue to elude me

---

