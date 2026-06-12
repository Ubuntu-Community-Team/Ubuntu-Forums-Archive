---
title: "Problem changing video card from NVidia to Radion"
date: 2016-12-08
forum: Hardware
---

### Post by twgray on 2016-12-08
I am currently running XUbuntu 14.04 and changed my video card from an NVidia to an MSI R7240 so that I can use my LG 4K TV at true 4K resolution...the NVidia would only run it at 1080P.

Upon changing the card the system boots up but gives me a desktop of 8-bit pixelated checkerboard.  The only way I can get to my normal desktop is to boot into recovery mode and select Resume Boot. This gives me a 1080P desktop.  In looking at Additional Drivers, I am showing to be running AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested), and if I change it to either of the 'proprietary' drivers it ignores the change and returns to the open source one.

I know the video card works with XUbuntu 16.04 since I booted a live-USB and it came up in 4096x2160 resolution.

Any ideas how to fix this?

---

### Post by Bucky Ball on 2016-12-08
You have the NVidia driver removed? Try this and see if it makes any difference.

When you get to the list of OSs at boot, highlight your kernel and hit 'e' to edit it. Find the line that ends in 'quiet splash' and add 'nomodeset' after a space. Follow instructions to save and continue to boot.

If there is an NVidia driver messing with things that might bypass it. Could you also provide the output of this command:

```
sudo lshw -C video
```

Put the output between code tags (see link in my signature below) please.

---

### Post by oldfred on 2016-12-08
You also may need a newer kernel, unless you have it thru the Enablement stack.
 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr) 


[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4K-4.3-Fix)
       List installed kernels:
uname -a

---

### Post by twgray on 2016-12-09
The 'nomodeset' suggestion was a wash...it booted correctly but gave me only a screen resolution of 1440xXXXX.

Here is the result of 'sudo lshw -C video:

```

twgray@Rampage:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Cape Verde LE [Radeon HD 7730/8730]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fbd00000-fbd3ffff ioport:e000(size=256) memory:fbd40000-fbd5ffff

```

Thanks for the help.

---

### Post by Bashing-om on 2016-12-09
twgray; Hello;

this :
> 
 configuration: latency=0

says you have no graphic's driver loaded.
Let us prepare to clean up from the old driver installed and proceed then to properly install a driver for the ATI card.

As it is ATI, we need to know what kernels are installed.
Post back :
```

uname -r
dpkg -l | grep linux- 

```

Let's clean up and
[INDENT][INDENT][INDENT]give the proper direction
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2016-12-09
Look to see if you have a leftover xorg.conf file in /etc/X11 from the nvidia setup.
If so, that might be causing conflicts, since the xorg file will be telling the system to load a driver for a card that does not exist.
Or that is my thinking on it.

---

### Post by Yellow Pasque on 2016-12-09
> The only way I can get to my normal desktop is to boot into recovery mode and select Resume Boot. This gives me a 1080P desktop.
Please do that (making sure you're not booting with nomodeset) and get the /var/log/Xorg.0.log and share it here. I think it will tell us what's wrong and answer everyone else's questions like what kernel you're running and whether there's a custom xorg.conf left over.

> **Bashing-om said:**
> this says you have no graphic's driver loaded.
Let us prepare to clean up from the old driver installed and proceed then to properly install a driver for the ATI card.

The open source radeon driver is already installed and should work. I'm fairly sure the output you're looking at is from when the OP booted with 'nomodeset' and thus, the radeon module did not load and gave 'UNCLAIMED' warning.

---

### Post by twgray on 2016-12-09
Results of uame and dpkg:

```

twgray@Rampage:~$ uname -r
3.13.0-58-generic
twgray@Rampage:~$ dpkg -l | grep linux-
ii  binutils-arm-linux-gnueabi                                  2.24-5ubuntu13cross1.97.1                  amd64        GNU binary utilities, for arm-linux-gnueabi target
ii  binutils-arm-linux-gnueabihf                                2.24-5ubuntu13cross1.98.1                  amd64        GNU binary utilities, for arm-linux-gnueabihf target
ii  cpp-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                   amd64        GNU C preprocessor
ii  cpp-4.7-arm-linux-gnueabihf                                 4.7.3-11ubuntu1cross1.85                   amd64        GNU C preprocessor
ii  cpp-4.8-arm-linux-gnueabihf                                 4.8.2-16ubuntu4cross0.11                   amd64        GNU C preprocessor
ii  cpp-arm-linux-gnueabi                                       4:4.7.2-1                                  amd64        The GNU C preprocessor (cpp) for armel architecture
ii  cpp-arm-linux-gnueabihf                                     4:4.8.2-1                                  amd64        The GNU C preprocessor (cpp) for armhf architecture
ii  g++-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                   amd64        GNU C++ compiler
ii  g++-4.7-arm-linux-gnueabihf                                 4.7.3-11ubuntu1cross1.85                   amd64        GNU C++ compiler
ii  g++-4.7-multilib-arm-linux-gnueabihf                        4.7.3-11ubuntu1cross1.85                   amd64        GNU C++ compiler (multilib files)
ii  gcc-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                   amd64        GNU C compiler
ii  gcc-4.7-arm-linux-gnueabi-base                              4.7.3-12ubuntu1cross1.85                   amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.7-arm-linux-gnueabihf                                 4.7.3-11ubuntu1cross1.85                   amd64        GNU C compiler
ii  gcc-4.7-arm-linux-gnueabihf-base                            4.7.3-11ubuntu1cross1.85                   amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.7-multilib-arm-linux-gnueabihf                        4.7.3-11ubuntu1cross1.85                   amd64        GNU C compiler (multilib files)
ii  gcc-4.8-arm-linux-gnueabihf                                 4.8.2-16ubuntu4cross0.11                   amd64        GNU C compiler
ii  gcc-4.8-arm-linux-gnueabihf-base                            4.8.2-16ubuntu4cross0.11                   amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-multilib-arm-linux-gnueabihf                        4.8.2-16ubuntu4cross0.11                   amd64        GNU C compiler (multilib files)
ii  gcc-arm-linux-gnueabi                                       4:4.7.2-1                                  amd64        The GNU C compiler for armel architecture
ii  gcc-arm-linux-gnueabihf                                     4:4.8.2-1                                  amd64        The GNU C compiler for armhf architecture
ii  linux-firmware                                              1.127.14                                   all          Firmware for Linux kernel drivers
ii  linux-headers-3.11.0-12                                     3.11.0-12.19                               all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-12-generic                             3.11.0-12.19                               amd64        Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                                     3.13.0-58.97                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                             3.13.0-58.97                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-21                                      3.8.0-21.32                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-23                                      3.8.0-23.34                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-27                                      3.8.0-27.40                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30                                      3.8.0-30.44                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31                                      3.8.0-31.46                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-35                                      3.8.0-35.50                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-generic                                       3.13.0.58.65                               amd64        Generic Linux kernel headers
rc  linux-image-3.0.0-12-generic                                3.0.0-12.20                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic                                3.0.0-16.29                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic                                3.0.0-17.30                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic                                3.0.0-19.33                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic                                3.0.0-20.34                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic                                3.0.0-23.39                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-24-generic                                3.0.0-24.40                                amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.11.0-12-generic                               3.11.0-12.19                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-24-generic                               3.13.0-24.47                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                               3.13.0-32.57                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                               3.13.0-58.97                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-29-generic                                3.2.0-29.46                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-32-generic                                3.2.0-32.51                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-33-generic                                3.2.0-33.52                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-37-generic                                3.2.0-37.58                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-38-generic                                3.2.0-38.61                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-25-generic                                3.5.0-25.39                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-26-generic                                3.5.0-26.42                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-27-generic                                3.5.0-27.46                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                                3.5.0-28.48                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-19-generic                                3.8.0-19.30                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-21-generic                                3.8.0-21.32                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-23-generic                                3.8.0-23.34                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-27-generic                                3.8.0-27.40                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-30-generic                                3.8.0-30.44                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-31-generic                                3.8.0-31.46                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-35-generic                                3.8.0-35.50                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                         3.11.0-12.19                               amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-25-generic                          3.5.0-25.39                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-26-generic                          3.5.0-26.42                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-27-generic                          3.5.0-27.46                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic                          3.5.0-28.48                                amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic                          3.8.0-19.30                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-21-generic                          3.8.0-21.32                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-23-generic                          3.8.0-23.34                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-27-generic                          3.8.0-27.40                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-30-generic                          3.8.0-30.44                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-31-generic                          3.8.0-31.46                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-34-generic                          3.8.0-34.49                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-35-generic                          3.8.0-35.50                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.58.65                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-58.97                               amd64        Linux Kernel Headers for development
ii  linux-libc-dev:i386                                         3.13.0-58.97                               i386         Linux Kernel Headers for development
ii  linux-libc-dev-armel-cross                                  3.13.0-12.32cross1.104                     all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-armhf-cross                                  3.13.0-12.32cross1.104                     all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems
ii  pkg-config-arm-linux-gnueabihf                              4:4.8.2-1                                  amd64        manage compile and link flags for libraries for armhf architecture
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                       all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                                      12-3ubuntu0.14.04.1                        all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy                               12-3ubuntu0.14.04.1                        all          collection of boot loaders (debian-wheezy theme)

```

---

### Post by twgray on 2016-12-09
Don't have an xorg.conf file at all...there are 3 .backup files from previous upgrades, etc.

---

### Post by Bashing-om on 2016-12-09
twgray; Well;

How about we purge whatever nVidia components are in residence, and install the radeon (open source) driver ?

If ya want run:
```

sudo apt purge nvidia*
sudo apt install dkms
sudo apt install xserver-xorg-video-radeon
sudo apt install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

```Here we use "apt" And I am assuming that your wheezy install supports "apt" ; else replace the apt with " apt-get" .
This should set up the system on the radeon driver .
Reboot the system to see the effect .

Now what is there to it ?
Maybe also here we are out of operating head room what with all those old kernels still on the system . ( df -h ; df -i )

[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-12-09
twgray; Well;

How about we purge whatever nVidia components are in residence, and install the radeon (open source) driver ?

If ya want run:
```

sudo apt purge nvidia*
sudo apt install dkms
sudo apt install xserver-xorg-video-radeon
sudo apt install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

```Here we use "apt" And I am assuming that your wheezy install supports "apt" ; else replace the apt with " apt-get" .
This should set up the system on the radeon driver .
Reboot the system to see the effect .

Now what is there to it ?
Maybe also here we are out of operating head room what with all those old kernels still on the system . ( df -h ; df -i )

[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

### Post by twgray on 2016-12-09
Temüjin:

The output is NOT with the 'nomodeset'.  Adding 'nomodeset' to grub boots into a low resolution desktop of 1440 pixels wide as the highest resolution selectable.

For some reason the forum rejects my /var/log/Xorg.0.log when I paste it into my reply.

---

### Post by twgray on 2016-12-09
Bashing-om,

Purging and re-installing xserver-xorg-video-radeon, libgl1-mesa-glx, libgl1-mesa-dri, and xserver-xorg-core did the trick.  Thanks for all the help, everyone!

---

### Post by Bashing-om on 2016-12-09
twgrayl Good deal;

Keep it in mind that " xserver-xorg-video-radeon " is the open source driver . With the collaboration of our developers and AMD the open source drivers just get better alla the time . After the 14.04 release there are no proprietary drivers offered.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

