---
title: "Display issue in Ubuntu 22.04 DTS"
date: 2023-07-19
forum: Hardware
---

### Post by wlathan on 2023-07-19
Over the past several days, I have had to reinstall several times for various reasons. However, there's one problem I cannot solve. This morning I turned off my computer. Then after an errand, I turned it on again and the display came up in 800x600 mode. When I look at display settings, there are no up/down arrows for me to select any other resolution. Is there another way to do this? I am using an old Viewsonic TD2420 which is capable of much better resolution, as seen after the installation. I can't afford to lose any more hair with this problem. Any ideas?

TIA,

Bill

---

### Post by Bashing-om on 2023-07-19
wlathan; Hello -

More info please:
what release are you running
```

lsb_release -a

```

what is the hardware:
```

lspci -k | grep -iEA5 'vga|3d'

```

Is a display driver loaded:
```

sudo lshw -C display

```

From these, we see where we go.

-all in the process-

---

### Post by wlathan on 2023-07-20
Thanks for the message. Info requested:
_______
bill@bill:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:        Ubuntu 22.04.2 LTS
Release:                22.04
Codename:         jammy
bill@bill:~$ lspci -k | grep -iEA5 'vga|3d'
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 630 OEM] (rev a1)
                Subsystem: Micro-Star International Co., Ltd. [MSI] GK107 [GeForce GT 630 OEM]
                Kernel modules: nvidiafb, nouveau
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)
                Subsystem: Micro-Star International Co., Ltd. [MSI] GK107 HDMI Audio Controller
                Kernel driver in use: snd_hda_intel
bill@bill:~$ sudo lshw -C display
[sudo] password for bill:
  *-display UNCLAIMED      
       description: VGA compatible controller
       product: GK107 [GeForce GT 630 OEM]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 2
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=800,600
bill@bill:~$
_________

To be explicit, here's what I did:

1. Installed 22.04 from disk image for Ubuntu 22.04 DTS ... without internet 
2. Hooked machine to internet
  did ... sudo apt update and sudo apt upgrade to get updates to software needing such on disk image
3. rebooted system

At this point the display is in 800x600 resolution with no options for other resolutions shown. The resolution after installation was 1920x1080. So all I can assume is that by updating the software, things have gone haywire. Did I do the updates correctly?

Many thanks for your help,

Bill

---

### Post by wlathan on 2023-07-20
Well, I believe my problem is resolved. Not by me doing anything other than reinstalling Ubuntu 22.04 DTS, but this time I let the install download the updates to the boot image and install them. I have no idea why this worked, but so far with several reboots, the resolution stays at1920x1080 as I wanted.

I did find a question and answer on Ask Ubuntu from a couple of months ago. It is titled "[How to solve recurrent resolution issue on Ubuntu 22.04.]("https://askubuntu.com/questions/1465329/how-to-solve-recurrent-resolution-issue-on-ubuntu-22-04")" It suggests a couple of things I was prepared to do, but as I said, I think I am okay for now.

Thanks for the help you provided. I really appreciate it.

Bill

---

### Post by Bashing-om on 2023-07-20
wlathan'; Great

Any solution is better than no solution - even if that nuclear one :D

reason:
> 
shw -C display >> *-display UNCLAIMED


As to why there was no driver loaded; will forever now remain as an open question as to why !

As this matter is now resolved
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]sometimes that red button
[INDENT][INDENT]is the thing to do
 [/INDENT][/INDENT][/INDENT]

---

