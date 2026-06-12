---
title: "How to configure GMA500 with the Ubuntu 9.10 repositories own Karmic."
date: 2010-01-11
forum: Hardware
---

### Post by jlimasa on 2010-01-11
After much suffering, I got an excellent performance at run videos in my AO751h with Ubuntu Remix 9.10, using almost exclusively packages Karmic own, ie, without the use of repositories Jaunty (9.04). The biggest problem, "jumps" or "freeze" was almost 100% resolved. That is to say that my bios was updated to version 3210.

Do not go into any details, but I hope the following reason make life easier for some who have suffered with this netbook. I made a compendium of I got so far and brought me a good result as stated previously, it was almost perfect. Follow the steps below to obtain best possible result.

1. Add the following repositories (/etc/apt/source.list) and install the their keys:
    deb [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/) karmic main
    deb-src [http://ppa.launchpad.net/lucazade/gma500/ubuntu/](http://ppa.launchpad.net/lucazade/gma500/ubuntu/) karmic main
    deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) karmic main
    deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) karmic main
    deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main #X-Updates PPA
    deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) karmic main #X-Updates PPA

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6699F3D9
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30
    sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
    sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220

2. Update system:
    sudo apt-get -y update
    sudo apt-get -y dist-upgrade

3. Install the following packages:
    sudo aptitude -y install psb-kernel-headers psb-kernel-source psb-modules xpsb-glx libdrm-poulsbo1 poulsbo-config psb-firmware

4. Download and install the following package:
    wget [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu/pool/main/x/xserver-xorg-video-psb/xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb]("http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu/pool/main/x/xserver-xorg-video-psb/xserver-xorg-video-psb_0.31.0-0ubuntu1%7E904um1_i386.deb")
    sudo dpkg -i xserver-xorg-video-psb_0.31.0-0ubuntu1~904um1_i386.deb

5. Add packages 2D and 3D:
    sudo aptitude -y install poulsbo-driver-2d poulsbo-driver-3d

6. Create or edit the file /etc/X11/xorg.conf leaving you with the following configuration:
    Section "ServerFlags"
        Option "DontZap" "False"
    EndSection

    Section "Device"
        Identifier "Configured Video Device"
        Option "IgnoreACPI"
        Option "AccelMethod" "uxa"
        Option "MigrationHeuristic" "greedy"
        Option "NoDDC"
        Option "DRI" "on"
        Option "Tiling" "true" # i8xx users: see note in guide
        Driver "psb"
    EndSection

    Section "DRI"
        Mode 0666
    EndSection

    Section "Monitor"
        Identifier "Configured Monitor"
    EndSection

    Section "Screen" Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
    EndSection

    #Added for mouse pad
        Section "InputDevice"
        Identifier "Mouse0"
        Driver "synaptics"
        Option "Protocol" "auto" 
        Option "Device" "/dev/input/mouse0"
        Option "ZAxisMapping" "4 5 6 7"
        Option "CorePointer"
        Option "HorizEdgeScroll" "1"
    EndSection

7. Add "psb" to the file /usr/bin/compiz in the following line:
    WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx", leaving it as follows: WHITELIST="psb nvidia intel ati radeon radeonhd i810 fglrx"

8. Install additional packages of compiz if you want to use the extra features:
    sudo aptitude -y install compizconfig-settings-manager compiz-fusion-plugins-extra

9. When the player alternated between video modes "window", "full screen" and again "window", the videos began to give "jumps". So I decided to remove the compiz, significantly reducing this problem. Who wants to choose to do the same to run:
    sudo apt-get remove compiz-core compiz-wrapper libdecoration0
    I have not found this problem when I switched only mode "window" to "full screen".

10. Add "enable_mtrr_cleanup mtrr_spare_reg_nr=1 mem=1984mb" to call your kernel in the grub2,  leaving the parameter GRUB_CMDLINE_LINUX_DEFAULT of file /etc/default/grub as follows:
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mem=1984mb"

    For earlier version of grub edit file /boot/grub/menu.lst leaving the parameter defoptions as follows:
    #defoptions=quiet splash enable_mtrr_cleanup mtrr_spare_reg_nr=1 mem=1984mb
    Do not remove # the previous line (not a comment).

11. Validate the previous amendment:
    sudo update-grub
    Restart the system.

12. References:

    [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552)
    [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) (To Fix Choppy Video Playback With Intel Video)
    [http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/](http://gadgetmix.com/index/new-gma-500-poulsbo-drivers-for-the-ubuntu-9-10-karmic-koala/)
    [https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)
    [http://ubuntuforum-br.org/index.php?topic=58947.0](http://ubuntuforum-br.org/index.php?topic=58947.0) (Grub2)

P.S.(1): I tested this tutorial on Kubuntu Netbook, except of course the steps that refer to compiz because it does not come by default in this version, and did not find any problems.
P.S.(2): This tutorial was originally submitted for publication on the site [www.vivaolinux.com.br]("http://www.vivaolinux.com.br") should be published in Portuguese soon.
P.S.(3): Sorry an error of language, I am not very fluent in English.

By Jessé Lima Sá.

---

### Post by brujoand on 2010-01-12
Hey, thanx a lot for posting this. I've been trying to get this to work with 9.10 for two days. I'll by trying your solution now, but Ive previously tried to get the bios upgraded byt putting openDOS on a usb pen with the unzip 3210 for windows on it. Boot it fails while booting. I've tried 4 different usb pens that all manage to boot fine with ubuntu. Any clues on this? or could you tell me how you did it?

Anders

---

### Post by jlimasa on 2010-01-13
> **GrimmVarg said:**
> Hey, thanx a lot for posting this. I've been trying to get this to work with 9.10 for two days. I'll by trying your solution now, but Ive previously tried to get the bios upgraded byt putting openDOS on a usb pen with the unzip 3210 for windows on it. Boot it fails while booting. I've tried 4 different usb pens that all manage to boot fine with ubuntu. Any clues on this? or could you tell me how you did it?

Anders


I have a test partition with WinXP, I did the update for it by downloading the application from the site of Acer. You can install UNetbootin apt-get or by downloading from here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), if not tried it yet, might help.

---

### Post by shaoxuan on 2010-02-20
Hello,

Thanks for your great job!

But I'm afraid there is probably one mistake you have typed:

```
Option "AccelMethod" "uxa"
```

I think it's:

```
Option "AccelMethod" "exa"
```

After I correct this, I can use psb driver with my AO751h following your instruction.

---

### Post by Kaweh on 2010-02-22
Thank you very much for this guide! Btw, did you make an update to the version ...19 kernel? I read somewhere else there might be problems with the GMA500 and this kernel.

---

### Post by shaoxuan on 2010-02-23
> **Kaweh said:**
> Thank you very much for this guide! Btw, did you make an update to the version ...19 kernel? I read somewhere else there might be problems with the GMA500 and this kernel.

Yes, I have upgraded the kernel to 19 version. And the instruction jlimasa provided is still feasible. I have not encountered any problems.

Thanks for the great job jlimasa!:)

---

### Post by adrjork on 2010-04-19
I didn't understand a thing: does opengl work in karmic-gma500?

---

### Post by sarang on 2010-06-08
At some point, I got an error that effectively meant 'starting in low-graphics mode, psb needs DRM to operate'. That was solved by dropping starting a console and running

```

sudo apt-get remove psb-kernel-source
sudo apt-get install psb-kernel-source

```

Note that I had to uninstall and then install again. The reinstall options of apt or aptitude did NOT work.

---

