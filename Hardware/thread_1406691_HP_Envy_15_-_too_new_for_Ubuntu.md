---
title: "HP Envy 15 - too new for Ubuntu"
date: 2010-02-14
forum: Hardware
---

### Post by akos.maroy on 2010-02-14
I just got an HP Envy 15 notebook, and I went through the process of installing Ubuntu on it. In short, the conclusion is that this laptop is just too new for Ubuntu / Linux in general.

Ubuntu 10.04 alpha runs with limited results on the machine, details below.

**specs**

the laptop is configured as follows:

CPU: i7 1.6GHz
RAM: 8GB
video card: ATI Mobility Radeon HD 5830
display: 1900x1080
SSD: 2x160GB in hardware raid
external USB DVD-RW

details:

```

$ sudo dmidecode -s system-product-name
HP ENVY 15 Notebook PC
$ sudo dmidecode -s system-version
0491110000241910001430000
$ lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/'
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI
[8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express
Root Port 1 [8086:d138] (rev 11)
00:05.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express
Root Port 3 [8086:d13a] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor
System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor
Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor
System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor
Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI
Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI
Routing and Protocol Registers [8086:d151] (rev 11)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series
Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series
Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series
Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series
Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05) (prog-if 20)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge
[8086:2448] (rev a5) (prog-if 01)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC
Interface Controller [8086:3b03] (rev 05)
00:1f.2 RAID bus controller [0104]: Intel Corporation Mobile 82801 SATA
RAID Controller [8086:282a] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset
SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device
[1002:68a1]
01:00.1 Audio device [0403]: ATI Technologies Inc Juniper HDMI Audio
[Radeon HD 5700 Series] [1002:aa58]
02:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev
03) (prog-if 30)
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 6000
Series [8086:4239] (rev 35)
04:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device
[1969:1063] (rev c0)

```

**installation**

installation is tricky, as the installation image is not recognized from the external USB DVD drive, while the machine would not boot from the internal SD Card reader.

thus, the trick is to create a bootable CD / DVD with the installation image, and copy the same stuff over to the SD Card reader. but the CD into the DVD drive and the SD card into the reader. when turning on the laptop, select the DVD as the boot device (tap ESC while starting, select F9 and go for the DVD). as you reach the installation menu, select 'Install Ubuntu', which will find the install medium in the SD Card reader, and it will install.

if you try your luck with 9.10, you'll see that at the end, you'll get an error message that grub could not be installed. and yes, the grub in 9.10 just cannot deal with the hardware raid controller in the system. I could only boot using the super grub disk on a USB stick.

thus I recommend to going for 10.04, albeit it is still alpha, which solves other issues as well.

**status - what works and what doesn't**

**CPU** - works, although I'm not sure about the power states. in idle, the machine is 50 C hot, and the went is always on. Alex Chiang claims that a kernel patch of his has been accepted into 2.6.33-rc2, but I also saw the 50 C idle temp on 2.6.33-rc8 (see Alex's site here: [http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15/](http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15/) )

**RAM** RAM works fine :)

**SSD / HDD** - there's an intel raid controller in the system, thus the 2x160GB SSDs are recognized as a single 320GB drive. but, the raw disks are still present and appear in all sorts of disk-aware applications as /dev/sda and /dev/sdb - which brings in some confusion. the SSD is very fast.

**ethernet** - the built-in ethernet adapter works fine

**wifi** - the built-in wifi does not work on 9.10, but works on 10.04 fine

**video** - well, not good. the binary ATI driver does not support the 5830 card as yet. the open source radeon driver causes screen corruptions every once in a while (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/440544](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/440544) ). going for more recent packages solves this issue. X either starts with the radeon or the radeonhd open source driver. with the radeon driver, gdm crashes at startup (see [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/521436](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/521436) ), thus X has to be started with startx

**video/2d** - 2d seems to be OK, flash videos like youtube also play fine. have not checked mplayer or other players yet

**video/3d** - 3D is extremely sluggish, seems to be software-emulation

**keyboard** - the keyboard works fine, including the special keys

**touchpad** - it's a 'clickpad' style thing, which is quite annoying. initially one can't even click properly, as click area is also an active touchpad, and your finger moves while pushing the button. Takashi Iwai submitted a kernel patch that makes things work a lot better (see [http://www.spinics.net/lists/linux-input/msg06333.html](http://www.spinics.net/lists/linux-input/msg06333.html) ), which will emulate the 3 mouse buttons on the bottom of the touchpad. nice. still, gestures like two-finger scrolling are missing

**audio** - the built-in audio works. the HDMI audio channel also appears as a separate audio device, but I haven't checked.

**webcam** - the built-in webcam works fine, as a video4linux device under /dev/video0

**SD Card reader** - the SD card reader works fine

**bluetooth** - haven't tested, though the bluetooth applet in the gnome bar crashes regularly

**poweroff / suspend / hibernate** - these don't work at all. actually, shutdown doesn't work either, the machine is just left hanging there, see here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072)


**things to do**

- make radeaonhd the xorg driver that is loaded, instead of the radeon driver

- make the gdm screen not crash with the ioctl error calls, see here [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/522215](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/522215) and here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/521436](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/521436)

- make the idle temperature of the system lower

- pray for 3D support, either from the ATI binary driver, or the open source radeonhd driver

- make susped / hibernate work, see here: [https://bugs.launchpad.net/ubuntu/+bug/522263](https://bugs.launchpad.net/ubuntu/+bug/522263)

if you have any inputs on the above, don't hesitate to drop a comment below...


**relevant pachtes**
to make the XHCI driver not freeze the system when a new device is plugged in: [http://markmail.org/message/vqcbzks4gnbrlir3](http://markmail.org/message/vqcbzks4gnbrlir3)

some other helpful XHCI patch: [http://patchwork.kernel.org/patch/81830/](http://patchwork.kernel.org/patch/81830/)

see Takashi Iwai's clickpad patch above


**summary**

in general, the hardware is very poorly supported by Linux at the moment. the CPU is overheating, the video is not handled properly, gets corrupted, and the gdm login screen doesn't even start. no suspend / resume, which is quite important for a laptop. the touchpad support has to be patched into the kernel manually.

these together with the fact that only an alpha-grade Ubuntu version, 10.04 is suitable to boot on the system at all, creates a very unstable laptop for the time being. hopefully 10.04 matures into production grade in a few months, and meanwhile some of the open issues get solved as well.

the obstacle that seems to be the most difficult one is the video: ATI just doesn't support this card yet, and there's no telling when they will. the open source radeonhd driver is brand new, and there's no telling when it will have 3D support in it.

---

### Post by c0un7d0wn on 2010-03-10
I have the the second generation envy 15 too. I had to roll my own kernel from linus git + airlied's drm-radeon-testing for kms and the clickpad patch and use the xorg-edgers PPA for the radeon driver.

Temperature wise the laptop cpu actually runs cooler than win7. But you will get no power management for gpu.

i7z [http://code.google.com/p/i7z/]("http://code.google.com/p/i7z/") tells me that the C states and the turbo boost is working.

My current problems are:
1) No video accel
2) no suspend/resume

---

### Post by akos.maroy on 2010-03-10
I'm sorry I haven't updated the main post for a while

I managed to get the ATI binary driver 10.2 working: first, install the 'official' fglrx packages coming from the ubuntu apt repo. then, download the 10.2 binary driver tarball from ATI, unpack, and install manually (building the deb package won't work). this will _not_ manage to install the fglrx module though - so you have to:

```

cd /usr/src/fglrx-8.702/
./make.sh
mkdir -p /lib/modules/`uname -r`/kernel/drivers/char/drm
cp fglrx.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/fglrx.ko

```

then you have to manually get an xorg.conf that uses the fglrx driver from somehwere, and put it in /etc/X11 .

then it works, is really fast..

---

### Post by babyhuey on 2010-03-11
I have the same problems as already mentioned with my 2nd gen Envy 15. I have no suspend/resume and the laptop will not shutdown. 
I've tried the OSS ATI driver with/without KMS, fglrx, and vesa along with  kernels 2.6.31 - 2.6.34. All exhibit the same suspend/shutdown behavior.

---

### Post by akos.maroy on 2010-03-11
I'm experimenting with unloading as many modules as possible, testing
the suspend feature using various levels of /sys/power/pm_test

I managed to get the number of modules as low as these:

```

Module                  Size  Used by
binfmt_misc             7454  1
bnep                   11287  2
btusb                  12729  2

```

then I was going through these steps;

```

echo freezer > /sys/power/pm_test
echo mem > /sys/power/state
echo devices > /sys/power/pm_test
echo mem > /sys/power/state
echo platform > /sys/power/pm_test
echo mem > /sys/power/state
echo processors > /sys/power/pm_test
echo mem > /sys/power/state
echo core > /sys/power/pm_test
echo mem > /sys/power/state

```

and all these worked fine - meaning that I got back to the console
screen. I also ran dmesg, and didn't see anything suspicious.

but, when I do:

```

echo none > /sys/power/pm_test
echo mem > /sys/power/state

```


the machine will still hang :(

---

### Post by suprem1ty on 2010-03-13
sorry if you've tried this or w/e but when my laptop had trouble suspending by default in 10.04 i used s2ram manually and it worked fine (although i had to force it - s2ram -f)
i dont have that particular laptop but linux was having trouble identifying hardware etc in my laptop also so perhaps the solutions may be similar?
good luck getting it workin regardless

---

### Post by akos.maroy on 2010-03-13
> **suprem1ty said:**
> sorry if you've tried this or w/e but when my laptop had trouble suspending by default in 10.04 i used s2ram manually and it worked fine (although i had to force it - s2ram -f)
i dont have that particular laptop but linux was having trouble identifying hardware etc in my laptop also so perhaps the solutions may be similar?
good luck getting it workin regardless

yes, I tried s2ram as well, but it didn't work either. I also posted the issue on the related mailing list, but to no avail :(

---

### Post by babyhuey on 2010-03-15
I'm not really sure where to report the bug since there are no errors. On tip of that, the only difference between the 1st gen, which has working suspend/shutdown, is Arrandale and the ATI 5830. 
As far as I can tell other laptops with arrandale aren't having the same problems. So that leaves the video card which as I mentioned has the same behavior across 3 different drivers. In the end I haven't a clue which component is at fault.

---

### Post by akos.maroy on 2010-03-15
> **babyhuey said:**
> I'm not really sure where to report the bug since there are no errors. On tip of that, the only difference between the 1st gen, which has working suspend/shutdown, is Arrandale and the ATI 5830. 
As far as I can tell other laptops with arrandale aren't having the same problems. So that leaves the video card which as I mentioned has the same behavior across 3 different drivers. In the end I haven't a clue which component is at fault.

yes, the most annoying thing is the lack of ability to dig down deeper. I posted the issue on the linux-pm mailing list, but there was no response :(

---

### Post by akos.maroy on 2010-03-15
I did some additional debugging, after receiving tips from the linux-pm list. that is, I booted the kernel with the no_console_suspend and initcall_debug options and then:

```

echo 8 > /proc/sys/kernel/printk
rmmod xhci
echo mem > /sys/power/state

```

and then I got to the console, the last screen had messages like:

```

ACPI: Preparing to enter sleep state S3
Broke affinit for irq 25 (same for 26, 27 and 28)
CPU 1 is now offline (same for CPUs 1...8)
SMP alternatives: switching to UP mode
Extended CMOS year: 2000

```

and then the machine hangs - nothing happens anymore...

---

### Post by babyhuey on 2010-04-14
akos.maroy posted a bug on launchpad for the 2nd Gen Envy 15 users who can't shutdown or suspend their system:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072)

If you suffer from this bug, please say so on the launchpad bug report.

@akos.maroy
Do you mind editing your first post to put a link to your bug report?

---

### Post by akos.maroy on 2010-04-14
> **babyhuey said:**
> akos.maroy posted a bug on launchpad for the 2nd Gen Envy 15 users who can't shutdown or suspend their system:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557072)

If you suffer from this bug, please say so on the launchpad bug report.

@akos.maroy
Do you mind editing your first post to put a link to your bug report?

good point, updated the post with it..

---

