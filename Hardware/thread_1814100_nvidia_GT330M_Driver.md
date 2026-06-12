---
title: "nvidia GT330M Driver"
date: 2011-07-28
forum: Hardware
---

### Post by DoneRightI.T. on 2011-07-28
I'm beating my brains out here and cannot for the life of me sort through this.

I have an acer TravelMate with a NVidia GT330M video card
I installed NVIDIA-Linux-x86-275.21.run from tty1 without having any other nvidia drivers running and used the command (as root)
```
 sh NVIDIA-Linux-x86-275.21.run -k $(uname -r)
```

upon completion it requested me to reconfig the xorg.conf file, ok fine
See Attached xorg.conf.nvidia.txt

I restarted the machine and it failed to boot to X. the message indicated it had failed on something but I knew it was not true... so I dropped to tty1 again and logged in and rooted up.
from there I stopped x
```
service gdm stop 
```
then figured I would tail all relevant files and try a few things so I could analyze further and sort through this.
```
tail -f syslog kern.log Xorg.0.log dmesg Xorg.log | tee ~/nvidiafail.txt &
```

I backgrounded the above so that I could both watch the code as well as log any output for investigating... possibly could be improved by doing a 2>1& | tee however...
see the attached file nvidiafail.txt

now I hunted through the file in search of some help

1. in checking the file I found reference to: [http://wiki.x.org]("http://wiki.x.org")
and in hunting around there managed to find
[http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28No%29|%28devices%29|%28detected%29#Message.3A.22Nodevicesdetected.22]("http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28No%29|%28devices%29|%28detected%29#Message.3A.22Nodevicesdetected.22")
hurray...

2. so from here I did a less on /var/log/Xorg.0.log and found a few lines that had some pretty confusing output, for me anyways as they in no way reference my video card manufacturer...
```

[   870.137] (II) Loader magic: 0x81ffde0
[   870.137] (II) Module ABI versions:
[   870.137]    X.Org ANSI C Emulation: 0.4
[   870.137]    X.Org Video Driver: 10.0
[   870.137]    X.Org XInput driver : 12.3
[   870.137]    X.Org Server Extension : 5.0
[   870.138] (--) PCI:*(0:0:2:0) 8086:0046:1025:040b rev 24, Mem @ 0xf0000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[   870.138] (--) PCI: (0:1:0:0) 10de:0a29:1025:040b rev 162, Mem @ 0xac000000/16777216, 0xb0000000/268435456, 0xae000000/33554432, I/O @ 0x00002000/128, BIOS @

```
the one in use above is the one with the *
so from here realizing that this information is loaded(or should be) from the lspci I did 
```
lspci -v | tee /tmp/lspci.txt ; less /tmp/lspci.txt
```
I managed to find my card within all of this fun fun stuff
```

01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 040b
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ac000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at ae000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        [virtual] Expansion ROM at ad000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidia, nouveau, nvidiafb

```

however have attached the entirety of this file in hopes that it helps.

I have supplementary to this tried a raft of other methods and am quite committed to getting the nvidia driver working! however, this said need any help I can get. 

Please let me know what other logs are required or would be of help and thank-you for your help!

---

### Post by movieman on 2011-07-29
My laptop has a GT330M and it works fine; I think I started with 10.10 and upgraded to 11.04. However, I installed it the official way with the 'Additional Drivers' panel in Ubuntu, you might want to try that instead of using the Nvidia installer in case something conflicts.

---

### Post by DoneRightI.T. on 2011-07-29
> **movieman said:**
> My laptop has a GT330M and it works fine; I think I started with 10.10 and upgraded to 11.04. However, I installed it the official way with the 'Additional Drivers' panel in Ubuntu, you might want to try that instead of using the Nvidia installer in case something conflicts.

I have attempted that way as well. If its not to much can I get a copy of your xorg.conf for reference. Nice to know someone has it working :)

---

### Post by DoneRightI.T. on 2011-07-29
I'm trying to dig up more information regarding this, I have come across the fact that this laptop has 2 graphic cards; one from intel and a nvdia geforce gt330M

"it features Intel HD graphics in addition to NVIDIA GeForce GT 330M graphics." -- [http://www.pcworld.idg.com.au/review/notebooks/acer/travelmate_timelinex_8572g/369295]("http://www.pcworld.idg.com.au/review/notebooks/acer/travelmate_timelinex_8572g/369295")

I am positive that is where the reference comes from ( PCI: ) from within the Xorg.0.log

checking the bios now.

---EDIT----
the bios has 2 settings only for Graphics, Discrete Mode, and Switchable. upon changing it from the default "Switchable" to "Discrete Mode" and restarting, x comes up with a nasty resolution and fails to boot, with or without xorg.conf in place...

so restored back to "Switchable" and bounced
renamed the xorg.conf 
restarted X
back to the start.

---

### Post by Ophidion on 2011-07-29
See these 3 posts then I hope you figure it out:

[LIST=1]
[*]Proprietary driver bugs: [http://ubuntuforums.org/showthread.php?p=10774752#post10774752](http://ubuntuforums.org/showthread.php?p=10774752#post10774752)
[*]X-server too: [http://ubuntuforums.org/showthread.php?p=10828892#post10828892](http://ubuntuforums.org/showthread.php?p=10828892#post10828892)
[*]Alternate driver: [http://ubuntuforums.org/showthread.php?p=11089181#post11089181](http://ubuntuforums.org/showthread.php?p=11089181#post11089181)
[/LIST]
You better stick to installing the mesa driver instead. I didn't test it with Compiz, but It is working fine with Metacity.

---

### Post by movieman on 2011-07-29
That's intriguing: my /etc/X11/xorg.conf only contains the following:

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

I guess the driver must be figuring out the rest itself? I'm sure the file on my Nvidia CentOS machine at work is a lot more complex.

---

### Post by DoneRightI.T. on 2011-07-29
ok, thank you all so far for your help.

after having to fight through this, I think I have figured out where the problem lies

the pci access tools are missing which is making the below extremely painful

however; the driver is attempting to use itself on the first detected device; which just so happens to be the intel video card; and as such it is failing to load up.

the xorg.conf file allows you to specify the BusID however, according to an older post or possibly even older versions the command 'Xorg :0 -scanpci'
does not exist, I am not able to find any reference to this command anywhere useful; though it is referenced in the xorg.conf man page as per below.
```
       BusID  "bus-id"
              This specifies the bus  location  of  the  graphics  card.   For
              PCI/AGP    cards,    the    bus-id    string    has   the   form
              PCI:bus:device:function (e.g., “PCI:1:0:0” might be  appropriate
              for an AGP card).  This field is usually optional in single-head
              configurations when using the primary graphics card.  In  multi-
              head  configurations, or when using a secondary graphics card in
              a single-head configuration, this entry is mandatory.  Its  main
              purpose  is to make an unambiguous connection between the device
              section and the hardware it is representing.   This  information
              can usually be found by running the pciaccess tool scanpci.
```

I can however pull the pci device out by doing 
```
lspci -v | less
```
which shows me the device I'm looking for:
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 040b
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at ac000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at ae000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        [virtual] Expansion ROM at ad000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidia, nouveau, nvidiafb

now subsequently according to other peoples xorg.conf files that I have seen thus far the formatting for the value BusID is to be PCI:0:0:0
or such... but that is not standarized formatting... its somewhere else... no now I'm stuck at the point of trying to translate this 01:00.0 to something usable by xorg.conf

I will hopefully figure it out and keep you posted.

---

### Post by godhika on 2011-07-29
You might wanna look at this one here. [http://ubuntuforums.org/showthread.php?t=1763742]("http://ubuntuforums.org/showthread.php?t=1763742")The problem is that currently Nvida Optimus is quite a pita. Maybe this solution also works for you

---

### Post by DoneRightI.T. on 2011-07-29
I guess the question I have first and foremost is simply this.

how do I change xorg to load the 2nd PCI and at least attempt to use it?

```
[   184.448] (--) PCI:*(0:0:2:0) 8086:0046:1025:040b rev 24, Mem @ 0xf0000000/41
94304, 0xd0000000/268435456, I/O @ 0x00001800/8
[   184.448] (--) PCI: (0:1:0:0) 10de:0a29:1025:040b rev 162, Mem @ 0xac000000/1
6777216, 0xb0000000/268435456, 0xae000000/33554432, I/O @ 0x00002000/128, BIOS @
 0x????????/524288
```

Can this not be done manually?

---

### Post by DoneRightI.T. on 2011-07-30
I just won with the help of the irc channel.

here's ultimately what was done.

remove ALL nvidia packages
```
 sudo dpkg -l | grep -i nvidia | xargs apt-get remove 
```

Restart
Go into the computers bios and switch it to "Discrete Mode"

add the Bumblebee ppa to your sources list, as per:
[https://launchpad.net/~mj-casalogic/+archive/bumblebee/]("https://launchpad.net/~mj-casalogic/+archive/bumblebee/")

don't forget to apt-get upgrade, and do an apt-get install of bumblebee and the nvidia drivers

** This may have just been me, but I had to mv the xorg.conf file as it failed when I booted **

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.$(date +%d-%m-%Y)
```

restart and your done like dinner.


for anyone interested, my current installation; looks like this

```

cthompson@cthompson:~$ dpkg -l | grep nvidia
rc  nvidia-common                         0.2.30                                          Find obsolete NVIDIA drivers
ii  nvidia-current                        280.04-0~nattyubuntu3                           NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       275.19-0ubuntu1~natty~xup1                      Tool of configuring the NVIDIA graphics driver

```

and for more details:
```

root@cthompson:~# dpkg -l | grep nvidia | awk '{ print $2 }' | xargs apt-cache policy
nvidia-common:
  Installed: (none)
  Candidate: 0.2.30
  Version table:
     0.2.30 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/main i386 Packages
        100 /var/lib/dpkg/status
nvidia-current:
  Installed: 280.04-0~nattyubuntu3
  Candidate: 280.04-0~nattyubuntu3
  Version table:
 *** 280.04-0~nattyubuntu3 0
        500 http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/ natty/main i386 Packages
        100 /var/lib/dpkg/status
     275.19-0ubuntu1~natty~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ natty/main i386 Packages
     270.41.06-0ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/restricted i386 Packages
nvidia-settings:
  Installed: 275.19-0ubuntu1~natty~xup1
  Candidate: 275.19-0ubuntu1~natty~xup1
  Version table:
 *** 275.19-0ubuntu1~natty~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ natty/main i386 Packages
        100 /var/lib/dpkg/status
     275.19-0~nattyubuntu0 0
        500 http://ppa.launchpad.net/mj-casalogic/bumblebee/ubuntu/ natty/main i386 Packages
     270.29-0ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/main i386 Packages

```

and the real key is noted within the /var/log/Xorg.0.conf on boot up; goes from a failed PCI location:
```

[    18.111]    X.Org ANSI C Emulation: 0.4
[    18.111]    X.Org Video Driver: 10.0
[    18.111]    X.Org XInput driver : 12.3
[    18.111]    X.Org Server Extension : 5.0
[    18.112] (--) PCI:*(0:0:2:0) 8086:0046:1025:040b rev 24, Mem @ 0xf0000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[    18.112] (--) PCI: (0:1:0:0) 10de:0a29:1025:040b rev 162, Mem @ 0xac000000/16777216, 0xb0000000/268435456, 0xae000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288

```

to after this hopefully to a successful one
```

[    16.759] (II) Module ABI versions:
[    16.759]    X.Org ANSI C Emulation: 0.4
[    16.759]    X.Org Video Driver: 10.0
[    16.759]    X.Org XInput driver : 12.3
[    16.759]    X.Org Server Extension : 5.0
[    16.762] (--) PCI:*(0:1:0:0) 10de:0a29:1025:040a rev 162, Mem @ 0xcc000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
[    16.762] (II) Open ACPI successful (/var/run/acpid.socket)

```


If I ever do figure out how to manually reference the PCI's from within the xorg I might re-visit this, in the meantime huge thanks goes to everyone that helped figure this out :)

---

