---
title: "My xorg.conf gets overwritten on reboot."
date: 2014-04-28
forum: Hardware
---

### Post by ibbles on 2014-04-28
Since I updated to 14.04 (from 13.10) something have started to overwrites my xorg.conf on every boot. I use aticonfig to configure my monitors the way I want them


```
sudo aticonfig --initial --adapter=1 --heads=2
```


and inspecting xorg.conf shows something that looks like what I want. Don't know enough xorg.conf-ish to understand the details, but it's a pretty big file. I'll paste the content at the end of the post. However, I have to reboot for the changes to apply, but once I've rebooted the config file suddenly contains the following instead.


```
Section "Device"    Identifier "Default Card 0"
    BusID "PCI:0@0:1:0"
EndSection


Section "Device"
    Identifier "Default Card 1"
    BusID "PCI:1@0:0:0"
EndSection
```


The effect of this is that I can only get my desktop on the built-in Trinity GPU, while my main GPU, a 7950, displays the BIOS/POST stuff and then just the kubuntu logo. 

How can I get the desktop on my 7950?




```
~$ sudo aticonfig --list-adapters
* 0. 00:01.0 AMD Radeon HD 7660D                                                                                                                                                   
  1. 01:00.0 AMD Radeon HD 7900 Series                                                                                                                                             
                                                                                                                                                                                   
* - Default adapter  

```

xorg.conf produced by aticonfig:


```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[1]-0" 0 0
        Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
EndSection


Section "Module"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection


Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection


Section "Device"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection


Section "Device"
        Identifier  "aticonfig-Device[1]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[1]-0"
        Device     "aticonfig-Device[1]-0"
        Monitor    "aticonfig-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


Section "Screen"
        Identifier "aticonfig-Screen[1]-1"
        Device     "aticonfig-Device[1]-1"
        Monitor    "aticonfig-Monitor[1]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by ibjsb4 on 2014-04-28
gpu-manager.conf?

A bug with a work-a-round.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1310489)

---

### Post by ibbles on 2014-04-29
Seems related. So gpu-manager takes precedence over aticonfig? I tried to figure out how to use gpu-manager to get everything configured the way I want, but it wasn't very helpful:

```

~$man gpu-manager
No manual entry for gpu-manager
~$gpu-manager --help
gpu-manager: unrecognized option '--help'
~$gpu-manager -h
gpu-manager: invalid option -- 'h'

```

Will comment out some lines from gpu-manager.conf, as suggested in the bug report, but the mention of system freezes worries me a bit...


edit: It works. Got my desktop the way I want it. But i wonder for how long. I can already see the system updates icon tempting me to let it prod about violently among my packages and configuration files. What if the dreaded gpu-manger gets an update, and along with it a new gpu-manager.conf? I'd be stumped. My xorg.conf would be defiled and aticonfig violated yet again.

---

### Post by MarisO on 2014-05-01
I have the same problem.  

gpu-manager resets xorg.conf file which causes X11 to fail to start !

have you tried removing [COLOR=#545454][FONT=arial]ubuntu-drivers-common package ?[/FONT][/COLOR]

---

### Post by MarisO on 2014-05-01
why did someone write a code that breaks linux config ?   :lolflag:

---

### Post by ibbles on 2014-05-01
> **MarisO said:**
> have you tried removing [COLOR=#545454][FONT=arial]ubuntu-drivers-common package ?[/FONT][/COLOR]

No. That sounds like a bad idea. I added a bunch of '#'s to /etc/init/gpu-manager.conf so that it now contains

```

#start on (starting lightdm
#          or starting kdm
#          or starting xdm
#          or starting lxdm)
task
exec gpu-manager --log /var/log/gpu-manager.log

```

Everything works the way I expect it to now.

---

### Post by ibjsb4 on 2014-05-01
Good deal :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

