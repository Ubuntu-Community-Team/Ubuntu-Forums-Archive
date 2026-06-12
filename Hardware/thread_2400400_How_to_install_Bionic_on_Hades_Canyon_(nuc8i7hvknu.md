---
title: "How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support"
date: 2018-09-05
forum: Hardware
---

### Post by dankegel on 2018-09-05
Here's how I installed Ubuntu 18.04 on Hades Canyon, either on the
the nuc8i7hvk (with cpu i7-8809G) and the nuc8i7hnb (with cpu i7-8705G),
and enabled the spiffy Vega M graphics support.  Thanks to everyone who
collectively came up with this recipe.

Beware, installing mesa or a kernel from a ppa is somewhat risky.  You
can safely downgrade back to stock mesa ... usually ... by installing
ppa-purge and running 'sudo ppa-purge ppa:ubuntu-x-swat/updates'.
But it's safer to assume that you'll have to wipe the system and install
afresh to get back to a supported configuration at some point.

1. (optional) Download latest BIOS from
[https://downloadcenter.intel.com/product/126141/Intel-NUC-Kit-NUC8i7HNK](https://downloadcenter.intel.com/product/126141/Intel-NUC-Kit-NUC8i7HNK) or
[https://downloadcenter.intel.com/product/126141/Intel-NUC-Kit-NUC8i7HNB](https://downloadcenter.intel.com/product/126141/Intel-NUC-Kit-NUC8i7HNB) as appropriate
(they probably point to same update)
by downloading the .bio file onto a dos-formatted USB stick,
then pressing F7 during boot and navigating the confusing
GUI to point it at the file on the usb stick
( [https://www.intel.com/content/www/us/en/support/articles/000005636/mini-pcs.html](https://www.intel.com/content/www/us/en/support/articles/000005636/mini-pcs.html) ).

2. Make sure BIOS is set to disable classic intel graphics (Performance / Graphics / disable);
setting it to 'auto' may be ok too.

3. Make sure BIOS is set to secure boot; for some reason it won't install ubuntu without it.
This is a problem for some users, see [https://ubuntuforums.org/showthread.php?t=2399033](https://ubuntuforums.org/showthread.php?t=2399033) 

4. Load the new kernel and graphics stack by running this script (adjust after the next
kernel RC comes out, or after 4.19 is released):

```
#!/bin/sh
# Update Ubuntu 18.04 to add Vega M (Hades Canyon) graphics support
# Caution: this is a bit risky.  It hasn't bricked anything for me, but then, I play an expert on tv.
# Ideally you'd read this, understand it, and run each step by hand, carefully.
# But it worked first try for me as is.
set -ex
mkdir tmp
cd tmp
# New mesa (ca. 18.1.5) and friends
sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt dist-upgrade        # pulls new mesa from above ppa
# New linux kernel (preview of 4.19)
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc2/linux-headers-4.19.0-041900rc2_4.19.0-041900rc2.201809022230_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc2/linux-headers-4.19.0-041900rc2-generic_4.19.0-041900rc2.201809022230_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc2/linux-image-unsigned-4.19.0-041900rc2-generic_4.19.0-041900rc2.201809022230_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc2/linux-modules-4.19.0-041900rc2-generic_4.19.0-041900rc2.201809022230_amd64.deb
sudo dpkg -i linux-*.deb
# New linux-firmware (will be released as 1.175 or something like that)
wget -m -np https://people.freedesktop.org/~agd5f/radeon_ucode/vegam/
sudo cp people.freedesktop.org/~agd5f/radeon_ucode/vegam/*.bin /lib/firmware/amdgpu
sudo /usr/sbin/update-initramfs -u -k all
cd ..
rm -rf tmp
```

Then reboot.  
Do 'apt-get install mesa-utils chromum-browser' if you haven't already.
Verify that 'glxinfo | grep str' outputs an OpenGL renderer string that says AMD VEGAM,
and that 'chromum-browser [http://fishgl.com](http://fishgl.com)' can display 400 fish at 60fps.
(Not Firefox, alas; see [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1732766](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1732766) )

Enjoy!

---

### Post by dankegel on 2018-09-06
Annoyingly, as mentioned in [https://www.intel.com/content/www/us/en/support/articles/000005545/mini-pcs.html](https://www.intel.com/content/www/us/en/support/articles/000005545/mini-pcs.html),
BIOS displays a different name for the product:

NUC8i7HNK is identified in BIOS as NUC8i7HNB
NUC8i7HVK is identified in BIOS as NUC8i7HVB

So when you see a Hades Canyon with a product number ending in B, just think K, evidently.

---

### Post by dankegel on 2018-09-07
Incidentally, because the Hades Canyon is capable of driving so many displays, it's tempting to try it with three 4k displays.

If you do, and one display just won't show up, you may have run into a limitation of X.org;
see [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1714178](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1714178)
and [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1776260](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1776260)
for a description and two workarounds.

---

### Post by osedit on 2018-09-08
[SIZE=4][FONT=arial]Just got a [COLOR=#111111]NUC8i7HVK. Ran your script rebooted and both my monitors work. Sleep/suspend also works under Kubuntu 18.04.1[/COLOR][/FONT][/SIZE]

---

### Post by dankegel on 2018-09-11
happy news: with the above 4.19rc2 setup, it's better than it was a month or two ago, in that it now supports three 4k displays side by side horizontally; the limit is now 16k x 16k rather than 8k x 8k (at least, it is on my machine, which has 32GB RAM).

---

### Post by dankegel on 2018-11-09
Update for the 4.19.1 kernel, with a happy little note encouraging you
to turn off secure boot in bios to avoid scary apt postinstall warnings.

Seems to work here; passes the fishgl test, anyway.

```
#!/bin/sh
# Update Ubuntu 18.04 to add Vega M (Hades Canyon) graphics support
# Note: may need to disable secure boot in BIOS to avoid scary warnings from new grub

set -ex
mkdir tmp
cd tmp

# New mesa (ca. 18.2.2 as of this writing) and friends
sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt update
sudo apt dist-upgrade        # pulls new mesa from above ppa

# Fresh linux kernel
# See http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901_4.19.1-041901.201811041431_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-image-unsigned-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-modules-4.19.1-041901-generic_4.19.1-041901.201811041431_amd64.deb
sudo dpkg -i linux-*4.19.1*.deb

# New linux-firmware (will be released as 1.175 or something like that)
wget -m -np https://people.freedesktop.org/~agd5f/radeon_ucode/vegam/
sudo cp people.freedesktop.org/~agd5f/radeon_ucode/vegam/*.bin /lib/firmware/amdgpu
sudo /usr/sbin/update-initramfs -u -k all

cd ..
rm -rf tmp

```

---

### Post by Jared Norris on 2018-11-30
Thanks for the guide, has my new NUC up and running.

One question, is there a reason you chose to use the unsigned kernel? It forces turning off secureboot (which isn't ideal). Is there a way to use a signed kernel and enable secureboot again?

---

### Post by anthirv on 2018-12-17
Device;NUC8iHVK
with 18.04 LTS and using current guide (updated kernel newer version) above I can see issue with my installation. Please see the snapshot log from installation

[B]ERROR (dkms apport): kernel package linux-headers-4.19.0-041900rc2-generic is not supported
Error! Bad return status for module build on kernel: 4.19.0-041900rc2-generic (x86_64)
[/B]Consult /var/lib/dkms/amdgpu/17.40-492261/build/make.log for more information.
Setting up linux-image-unsigned-4.19.0-041900rc2-generic (4.19.0-041900rc2.201809121232) ...
Processing triggers for linux-image-unsigned-4.19.0-041900rc2-generic (4.19.0-041900rc2.201809121232) ...
/etc/kernel/postinst.d/dkms:
[B]ERROR (dkms apport): kernel package linux-headers-4.19.0-041900rc2-generic is not supported
Error! Bad return status for module build on kernel: 4.19.0-041900rc2-generic (x86_64)[/B]

---

### Post by Sidrabs on 2018-12-20
I have followed the instructions very closely, but I can't get the OpenGL renderer changed to AMD VEGAM. No matter what I do, it stays llvmpipe, what is a software renderer.

```
$ inxi -G
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Vega [Radeon RX Vega M]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 3840x2160@88.00hz
           OpenGL: renderer: llvmpipe (LLVM 7.0, 256 bits)
           version: 3.3 Mesa 18.2.2
```

The reason there is only the AMD card is that I have disabled the Intel card in BIOS, in hopes that it would force Ubuntu to load the radeon drivers. I have tried the most recent kernel (4.19.11), and then downgraded to 4.18. Each time after adding new kernel, I activated the drivers with update-initramfs. But no luck.

What am I missing? How to force the system to load the Vega drivers?

---

### Post by ironstorm-gmail on 2018-12-30
Hey dankegel, thanks for this guide it was very helpful in getting my nuc8i7hvk up and running with accelerated X. :D

One amendment I would suggest to your instructions would be to grab the latest kernel via ukuu... 

> **dankegel said:**
> 
```
#!/bin/sh
# Update Ubuntu 18.04 to add Vega M (Hades Canyon) graphics support
# Caution: this is a bit risky.  It hasn't bricked anything for me, but then, I play an expert on tv.
# Ideally you'd read this, understand it, and run each step by hand, carefully.
# But it worked first try for me as is.
set -ex
mkdir tmp
cd tmp
# New mesa (ca. 18.1.5) and friends
sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt dist-upgrade        # pulls new mesa from above ppa

# New linux kernel
sudo add-apt-repository ppa:teejee2008/ppa
sudo apt-get update
sudo apt install ukuu
sudo ukuu --install-latest # Answer yes to get the latest

# New linux-firmware (will be released as 1.175 or something like that)
wget -m -np https://people.freedesktop.org/~agd5f/radeon_ucode/vegam/
sudo cp people.freedesktop.org/~agd5f/radeon_ucode/vegam/*.bin /lib/firmware/amdgpu
sudo /usr/sbin/update-initramfs -u -k all
cd ..
rm -rf tmp
```

Then reboot.  
Do 'apt-get install glx-utils chromum-browser' if you haven't already.
Verify that 'inxi -G' outputs an OpenGL renderer string that says AMD VEGAM,
and that 'chromum-browser [http://fishgl.com](http://fishgl.com)' can display 400 fish at 60fps.


Also recommend using "inxi -G" from a terminal inside X as I couldn't find a package for glxinfo

@[[COLOR=#000000]Sidrabs[/COLOR]]("https://ubuntuforums.org/member.php?u=1179152")[COLOR=#000000], [/COLOR]try ukuu to install the latest kernel and double check you have the firmware downloaded and put in the right spot.

---

### Post by dankegel on 2019-01-14
I used the unsigned kernel because I didn't know any better.

---

### Post by dankegel on 2019-01-14
ironstorm, thanks for the tips!  I'll try that approach sometime.

Now that 18.10 is out, people should just use that if they can, I think.  I'm still using 18.04 because my company needs LTS.

Here's my current recipe:

```

#!/bin/sh
# Update Ubuntu 18.04 to add Vega M (Hades Canyon) graphics support
# Note: may need to disable secure boot in BIOS to avoid scary warnings from new grub

set -ex
mkdir tmp
cd tmp

# New mesa (ca. 18.2.2 as of this writing) and friends
sudo add-apt-repository ppa:ubuntu-x-swat/updates
sudo apt update
sudo apt dist-upgrade        # pulls new mesa from above ppa

# Fresh linux kernel
# See http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901_4.19.1-041901.201812031343_all.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-headers-4.19.1-041901-generic_4.19.1-041901.201812031343_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-image-unsigned-4.19.1-041901-generic_4.19.1-041901.201812031343_amd64.deb
wget https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.1/linux-modules-4.19.1-041901-generic_4.19.1-041901.201812031343_amd64.deb
sudo dpkg -i linux-*4.19.1*.deb

# New linux-firmware (will be released as 1.175 or something like that)
wget -m -np https://people.freedesktop.org/~agd5f/radeon_ucode/vegam/
sudo cp people.freedesktop.org/~agd5f/radeon_ucode/vegam/*.bin /lib/firmware/amdgpu
sudo /usr/sbin/update-initramfs -u -k all

```

---

### Post by dankegel on 2019-03-06
Ubuntu 18.04.2 (which has the HWE kernel and graphics) happily supports Hades Canyon, yay!

Fun fact:  I hear that the
2nd network interface on the hades is named differently depending on if the SD card slot, Wifi, and Bluetooth on the Hades are enabled in BIOS.
If (they?) are disabled, the 2nd ethernet will be enp4s0, and if they are enabled the port will be enp5s0.  Or so I hear.

(See also [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) )

---

### Post by jareilly on 2019-08-10
Great guide!!! I finally got Ubuntu to boot in my nuc8i7hvk with it's help. Thanks!

I got an error at this step: 'sudo dpkg -i linux-*4.19.1*.deb' :
    linux-headers-4.19.1-041901-generic depends on libssl1.1 (>= 1.1.0); however:
    Package libssl1.1 is not installed.
I tried install libssl1.1 by hand, but that also fails so far. I am still investigating...

---

### Post by jareilly on 2019-08-10
I was pointed at this excellent article about NUC8i7vhk and Ubuntu 18.10: [Intel's Hades Canyon and Ubuntu 18.10 are Perfect Together]("https://www.forbes.com/sites/jasonevangelho/2018/10/22/intels-hades-canyon-nuc-and-ubuntu-linux-18-10-now-perfect-together/#62a272f15f72").
If someone is reading this thread, I can recommend reading that and going for Ubuntu 18.10.

(Note: I am following up further here: [https://forums.intel.com/s/question/0D50P00004PnSaISAV/nuc8i7hvk-booting-mmc0-unknown-controller-version3](https://forums.intel.com/s/question/0D50P00004PnSaISAV/nuc8i7hvk-booting-mmc0-unknown-controller-version3))

---

### Post by zhchunyo on 2019-09-08
On Sep 09 2019, tested with Ubuntu 18.04.3, Hades NUC is natively supported, no need to install patches anymore.

Same for Ubuntu 19.04.

But for LG 5K display, I can't figure out a way to configure 5K resolution as there are 2 DP displays in system settings.

Tips:
intel graphics must be disabled in BIOS, otherwise you can't boot into Ubuntu with only LG 5K display which has only ThunderBolt 3 interface.

---

### Post by oldfred on 2021-03-10
This is mostly older info. Nuc seem to always have issues.
But some may give a hint with your newer version.


[https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3](https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3)
NUC10i7FNH
this Network adapter Intel Corporation Device [8086:0d4f] is new and supported by mainline Linux kernel since the 5.5 Linux kernel.

How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)
Updated drivers for Hades Canyon
[https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay](https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay)
Intel NUC
[https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified](https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified)

---

