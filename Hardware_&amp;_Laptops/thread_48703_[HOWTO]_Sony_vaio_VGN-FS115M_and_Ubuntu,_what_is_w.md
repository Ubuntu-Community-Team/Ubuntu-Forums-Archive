---
title: "[HOWTO] Sony vaio VGN-FS115M and Ubuntu, what is working and what not."
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by hannes_ on 2005-07-13
Hi, well first of all, the combination of this vaio and Ubuntu works fine after a bit working.
I have to say that i am a real lin nub so please, if there are any hints post them.

Ok here is what is working, or better what i made it work .

Working:
well i think everything except the two things in the "not working" section.

> 
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0167 (rev a1)
0000:06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:06:03.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1068 (rev 04)

Not working:
[COLOR=Red][B]acpi stuff |--> u have to install / boot with the option  acpi=off
wlan 2200BG |--> i tried every tut, every driver and i still wasnt able to get it working!
Speedstep  !!! Need help on this !!![/B][/COLOR]

Here we go, this is what u have to do:

Sound Card:
This is not supported in Ubuntu after a fresh installation.
To fix this simple do the following.

> 
su
[enter root pw]
cd /tmp
mkdir vaio
cd vaio
mkdir sound
cd sound
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.9.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.9.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.9.tar.bz2](ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.9.tar.bz2)
tar jxvf alsa-driver-1.0.9.tar.bz2
tar jxvf alsa-lib-1.0.9.tar.bz2
tar jxvf alsa-utils-1.0.9.tar.bz2
tar jxvf alsa-oss-1.0.9.tar.bz2
cd alsa-driver-1.09
./configure --with-oss=yes --with-cards=hda-intel
make
make install
cd ../alsa-lib-1.0.9
./configure
make
make install
cd ../alsa-utils-1.0.9
./configure
make
make install
cd ../alsa-oss-1.0.9
./configure
make
make install
/usr/share/alsa-base/snddevices
alsaconf  |--> [just always press enter and choose your soundcard]

|--->  Reboot your box and sound should work now.

if everything is allright delete all the temp files for the sound

cd /tmp/vaio/
rm -r ./sound


**Next is the graphics device:**

> 
su
[enter root pw]
apt-get install linux-restricted-modules-2.6.[your kernel number(hint: uname -r)] nvidia-glx nvidia-settings
nano /etc/X11/xorg.conf

Replace in the device section of your graphic card

Driver    "nv"

with 

Driver "nvidia"

my section now looks like this:
+++++++++++++++++++++
Section "Device"
        Identifier      "NVIDIA Corporation NV40M? [GeForce Go 6200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
+++++++++++++++++++++

Now to get the right resolution we have to adjust the Modline in the Monitor section.
put in front of your existing Modline "#" (just uncomment it) and put directly under it
        Modeline        "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827

my section now looks like this:
+++++++++++++++++++++
Section "Monitor"
        Identifier      "Standardbildschirm"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     30-60
#       Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
        Modeline        "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
EndSection
+++++++++++++++++++++

strg+o [press enter]
strg+x

strg+alt+backspace (to restart the x server.)

Now the nvidia Logo should splash up.

[B]
Need help for the acpi module and sonypi, speedstep usw!!![/B]

Well i think the rest works fine for me, check out [http://ubuntuguide.org](http://ubuntuguide.org).

Greets Hannes

---

