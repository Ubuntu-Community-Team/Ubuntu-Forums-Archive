---
title: "Stuck on boot screen when using proprietary nVidia drivers for 840M on 64bit machine"
date: 2015-01-01
forum: Hardware
---

### Post by cyb3r_sn4k3 on 2015-01-01
Hello everyone, recently I bought a new Lenovo laptop (Z50-70) which comes with an Optimus configuration. Though originally the additional drivers came up empty, after following the directions at [http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop](http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop) and adding the edgers PPA, the nvidia 340.65 shows up. But after I select it and reboot. The system gets stuck on the loadsreen (the one with the ubuntu logo and 3 dots). I then have to purge nvidia off my system and reboot so that nouveau takes over, after which the system seems to run.


Thanks in advance :)

---

### Post by Bashing-om on 2015-01-02
cyb3r_sn4k3; Hello ;

Does "optimus" equal hybrid grahics equal "Nvidia-prime" ?

Does 'lspci' output show 2 graphics sets ?
```

lspci -nnk | grep -iA3 vga

``` such that without direction, the system does not know what to do .

IF 2 sets then consider the "Nvidia-Prime" alternative:
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html) <- quickly switch between Intel and Nvidia graphics cards.

[INDENT][INDENT]sometimes even 'buntu
[INDENT][INDENT][INDENT]needs a bit of help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by buzzingrobot on 2015-01-02
Some Lenovo's have three video options available in BIOS settings:  1.  Internal Intel only; 2. Discrete Nvidia/AMD only; 3.  Hybrid combination of both.  Worth a look.

---

### Post by cyb3r_sn4k3 on 2015-01-03
It seems though, its only detecting the Intel GPU. 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
```

Running ```
lspci | grep -i nvidia
``` Gives
```
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
```

Right now, I'm running completely on Noveau.

---

### Post by cyb3r_sn4k3 on 2015-01-03
Mine has only the first two, and its in discrete mode.

---

### Post by Bashing-om on 2015-01-03
cyb3r_sn4k3; Well ....

I think still the better option to try is with Nvidia-prime.
To that end, let us remove all the present driver components, and install Nvidia-prime from scratch.

Show what we have that might be required to remove:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l  | grep nvidia
sudo find / -name "NVIDIA-Linux-*"

```
Roll our sleeves up

[INDENT][INDENT]go to work
[/INDENT][/INDENT]

---

### Post by cyb3r_sn4k3 on 2015-01-04
> **Bashing-om said:**
> cyb3r_sn4k3; Well ....

I think still the better option to try is with Nvidia-prime.
To that end, let us remove all the present driver components, and install Nvidia-prime from scratch.

Show what we have that might be required to remove:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l  | grep nvidia
sudo find / -name "NVIDIA-Linux-*"

```
Roll our sleeves up[INDENT][INDENT]go to work
[/INDENT]
[/INDENT]

Alright. lets do it :D
```
 $ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu-GNOME 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://in.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://in.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://in.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://in.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://in.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main

```

```

$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main

```

```
 $ dpkg -l  | grep nvidia
``` Gives nothing.

```
 $ sudo find / -name "NVIDIA-Linux-*"
``` Also, gives nothing.

---

### Post by Bashing-om on 2015-01-04
cyb3r_sn4k3; Ho Kay;

Looks as if the Nvidia drivers did not get installed, but let's play it safe.
Remove any of the current Nvidia driver files:
```

sudo ppa-purge xorg-edgers
sudo apt-get remove --purge nvidia*

```
Now make sure x-swat is not able to (re-)install;
Fire up the text editor with the required elevated privileges :
```

gksudo gedit /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list

```
 ##( Be aware, possible on your system 'gksudo' has been superseded )
and comment out the entry by placing a '#' character at the start of the line.
Save the file and exit back to terminal.

Now let's see what happens:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install nvidia-prime

```

It is my hope that installing 'nvidia-prime' from the software repository will also install the needed drivers for the Intel integrated driver as well as the driver for the Nvidia card.

Reboot and let's see you come up on the GUI, and all is hunky dory.

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by cyb3r_sn4k3 on 2015-01-05
I tried it, but installing nvidia-prime only well, installs nvidia-prime and nothing else, trying to do ```
prime-select query
``` gives Unknown as the result. :/

---

### Post by Bashing-om on 2015-01-05
cyb3r_sn4k3; Well then !

Give it something to bite on:
```

sudo apt-get install nvidia-current

```
let the installer figure out the correct version.

Reboot and 
[INDENT][INDENT][INDENT]maybe Yes
[/INDENT][/INDENT][/INDENT]

---

### Post by cyb3r_sn4k3 on 2015-01-09
> **Bashing-om said:**
> cyb3r_sn4k3; Well then !

Give it something to bite on:
```

sudo apt-get install nvidia-current

```
let the installer figure out the correct version.

Reboot and [INDENT][INDENT][INDENT]maybe Yes
[/INDENT]
[/INDENT]
[/INDENT]


No luck, same issue as when I installed from additional-drivers, gets stuck on boot.:sad:

---

### Post by Raman Narasimhan on 2015-01-26
> **cyb3r_sn4k3 said:**
> No luck, same issue as when I installed from additional-drivers, gets stuck on boot.:sad:

Hi cyb3r_sn4k3,

I also purchased the same laptop earlier this month and I also have this same issue. I cannot get hybrid graphics working,

Please let me know if you were able to solve this issue?

---

