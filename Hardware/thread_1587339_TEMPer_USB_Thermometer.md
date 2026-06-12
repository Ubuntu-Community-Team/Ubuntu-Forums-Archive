---
title: "TEMPer USB Thermometer"
date: 2010-10-03
forum: Hardware
---

### Post by stepstools on 2010-10-03
Has anyone had any luck with this - [http://pcsensor.com/index.php?_a=viewProd&productId=15]("http://pcsensor.com/index.php?_a=viewProd&productId=15")  I just want to see before I buy it for my other PC.

Thanks in advance
~ stepstools

---

### Post by FlameLicker on 2011-12-14
... ok, my answer comes a bit late. Just for the records:

I succeeded with [COLOR=Blue][https://wwwx.cs.unc.edu/~hays/archives/2010/03/entry_25.php]("https://wwwx.cs.unc.edu/%7Ehays/archives/2010/03/entry_25.php")[/COLOR].

As a shortcut I made this script:

[FONT="Courier New"][INDENT]#!/bin/bash
sudo apt-get install libusb-dev
sudo cpan -fi Bundle::CPAN
sudo cpan -fi ExtUtils::MakeMaker
sudo cpan -fi Inline::MakeMaker
sudo cpan -fi Device::USB
sudo cpan -fi Device::USB::PCSensor::HidTEMPer
cd $HOME/scripts
wget -O temper_mon.pl [http://www.cs.unc.edu/~hays/dev/bash/temper/temper_mon.pl]("http://www.cs.unc.edu/%7Ehays/dev/bash/temper/temper_mon.pl")
chmod a+x temper_mon.pl[/INDENT][/FONT]

It asks a lot of questions which I always respond with ENTER. Maybe there are some tweaks in.

Regards

PS.: I have a number of Ubuntu Server running 10.04 LTS 64bit - neither of them failed to show the temperature.

---

### Post by SorryGoFish on 2012-07-16
I know this is an old thread, but the command ```
sudo cpan -fi Device::USB
``` results in ```
ERROR: Can't find libusb library.
```

I do have [FONT="Courier New"]libusb[/FONT] and [FONT="Courier New"]libusb-dev[/FONT] installed.

---

### Post by FlameLicker on 2012-07-16
... alarmed by your post I took a fresh Ubuntu 10.04 LTS installation (all packages are from the repository) and tried the script again. Result: I can't confirm your error message - all run the way I'd expected. Maybe there is a version conflict on your box?
Regards

---

### Post by glymph on 2013-02-15
I encountered this problem on Debian Wheezy having come across this thread, it turned out I needed to install libusb-1.0-0-dev and set LIBUSB_LIBDIR and LIBUSB_INCDIR to point to the location of libusb.so; this was on a Raspberry Pi, but I hope it's useful.

---

