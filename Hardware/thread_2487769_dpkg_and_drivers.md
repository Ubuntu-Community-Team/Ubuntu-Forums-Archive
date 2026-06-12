---
title: "dpkg and drivers"
date: 2023-06-14
forum: Hardware
---

### Post by pioflor on 2023-06-14
I probably have some issue with the drivers.. When I update the packages, I get this error:
```

dpkg: error processing package oem-sdcard-o2micro-dkms (--configure):
 installed oem-sdcard-o2micro-dkms package post-installation script subprocess r
eturned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encoun
tered while processing:
 intel-i915-backport-3.8-dkms
 oem-audio-hda-daily-lts-quantal-dkms
 oem-bt-dw1550-dkms
 oem-wireless-bluetooth-intel-7260-dkms
 bbswitch-dkms
 oem-bt-ath3k-dkms
 oem-sdcard-o2micro-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
My laptop model is: dell latitude 5300 2-in-1

---

### Post by Bashing-om on 2023-06-14
Hello pioflor -- Welcome to the forums.

Looking about at " oem-sdcard-o2micro-dkms " and I do not find it in the current LTS software repository.
So >>
what release are you on ?
```

lsb_release -a

```
and how does " oem-sdcard-o2micro-dkms ' play into this ?
```

apt policy oem-sdcard-o2micro-dkms

```

where we see what we can find out
[INDENT]and where to go from here
[/INDENT]

---

### Post by pioflor on 2023-06-15
```

hubble@main01:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy
hubble@main01:~/Desktop$ apt policy oem-sdcard-o2micro-dkms
oem-sdcard-o2micro-dkms:
  Installed: 1.0
  Candidate: 1.0
  Version table:
 *** 1.0 100
        100 /var/lib/dpkg/status
hubble@main01:~/Desktop$ 

```

---

### Post by Bashing-om on 2023-06-15
pioflor - 

I am mot that much smarter but looking about -
This appears to be a Dell thing -
My reference:
[https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=74m75](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=74m75)

But, that has no bearing on ubuntu - >>
> 
100 /var/lib/dpkg/status
oem-audio-hda-daily-lts-[color=red]quantal[/color]-dkms


Maybe best now to take a look at your sources and see if we can see then where "oem-sdcard-o2micro-dkms" comes from.
Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT]gots to be a reason
[/INDENT]

---

### Post by pioflor on 2023-06-16
```

hubble@main01:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223)]/ jammy main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pl.archive.ubuntu.com/ubuntu/ jammy main restricted
     6    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pl.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    11    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pl.archive.ubuntu.com/ubuntu/ jammy universe
    17    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy universe
    18    deb http://pl.archive.ubuntu.com/ubuntu/ jammy-updates universe
    19    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pl.archive.ubuntu.com/ubuntu/ jammy multiverse
    27    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy multiverse
    28    deb http://pl.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    29    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pl.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    37    # deb-src http://pl.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu jammy-security main restricted
    40    # deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
    41    deb http://security.ubuntu.com/ubuntu jammy-security universe
    42    # deb-src http://security.ubuntu.com/ubuntu jammy-security universe
    43    deb http://security.ubuntu.com/ubuntu jammy-security multiverse
    44    # deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse
    45    
    46    # This system was installed using small removable media
    47    # (e.g. netinst, live or single CD). The matching "deb cdrom"
    48    # entries were disabled at the end of the installation process.
    49    # For information about how to configure apt package sources,
    50    # see the sources.list(5) manual.
hubble@main01:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/archive_uri-https_repositories_intel_com_graphics_ubuntu-jammy.list <==
deb [arch=amd64] https://repositories.intel.com/graphics/ubuntu focal main
# deb-src [arch=amd64] https://repositories.intel.com/graphics/ubuntu focal main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/notepadqq-team-ubuntu-notepadqq-jammy.list <==
deb https://ppa.launchpadcontent.net/notepadqq-team/notepadqq/ubuntu/ jammy main
# deb-src https://ppa.launchpadcontent.net/notepadqq-team/notepadqq/ubuntu/ jammy main

==> /etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-jammy.list <==
deb https://ppa.launchpadcontent.net/plushuang-tw/uget-stable/ubuntu/ jammy main
# deb-src https://ppa.launchpadcontent.net/plushuang-tw/uget-stable/ubuntu/ jammy main
hubble@main01:~$ 



```

---

### Post by deadflowr on 2023-06-16
Disable both the uget-stable and the notepadqq PPAs as they are unsupported in 22.04.

---

### Post by Bashing-om on 2023-06-16
pioflor - Hey hey

In addition to deadflowr's last there is the remnant:
> 
deb [arch=amd64] [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) [color=red]focal[/color] main

which, as you are on jammy, needs either removed or updated.

Before we spin wheels to update this repo - what is the reason that you require this outside source ?

-the more we know-

---

