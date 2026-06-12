---
title: "Computer crashes when using Firefox"
date: 2008-11-08
forum: General Help
---

### Post by Bödvar on 2008-11-08
There has already been [a post about this]("http://ubuntuforums.org/showthread.php?t=216841"), and I have already posted my problem as a reply to [this thread](http://ubuntuforums.org/showthread.php?t=974764), without any solution. Please, I need help.

Basically my problem is this:

> **Bödvar said:**
> I have the exact same problem no. 2! Every EVERY single time! Today alone my computer has probably freezed ten times - and I have to turn off my computer without shutdown (I don't have a restart button). Why is this?

My only addons are:
1. NoScript
2. Adblock Plus
3. Greasemonkey (with very few scripts, just for [www.last.fm](www.last.fm), and I don't even visit that site when the computer freezes)
4. Flashblock

Can it be any of those? I'm guessing thousands of other users have these plugins, as they are so functional, why can they break an entire computer, time after time? It's really getting annoying. How to fix this? Please help!

I'm running Ubuntu Intrepid 8.10 (the new one, you know, Ibex).

Thanks!

I have now disabled all addons, restarted Firefox, and for the past 5 minutes haven't experienced a freeze yet. I will see if this works, but obviously, it would be very convenient if there was a way where I could use my computer without it crashing.

---

### Post by glotz on 2008-11-08
Using the Adobe flash plugin? That's lately been causing a LOT of people crashes. No fix in sight. Since it's proprietary closed source, only Adobe can fix it... suckers.

---

### Post by Bödvar on 2008-11-08
> **glotz said:**
> Using the Adobe flash plugin? That's lately been causing a LOT of people crashes. No fix in sight. Since it's proprietary closed source, only Adobe can fix it... suckers.

Hi, thanks for your reply. I have not yet installed Flash as I don't need it (yet). But thanks for your reply anyway.

---

### Post by Tamlynmac on 2008-11-08
Why not enable one addon at a time and identify which addon(s) may be causing the problem. Enable one addon and see if it reboots - if not turn it off and enable the next until you can identify which addon(s) are causing this issue. I had some problems with "No Script" and had to uninstall and reinstall.

---

### Post by Bödvar on 2008-11-08
> **Tamlynmac said:**
> Why not enable one addon at a time and identify which addon(s) may be causing the problem. Enable one addon and see if it reboots - if not turn it off and enable the next until you can identify which addon(s) are causing this issue. I had some problems with "No Script" and had to uninstall and reinstall.

Thanks, I shall try that.

---

### Post by glotz on 2008-11-08
Here are some other causes [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes)

---

### Post by Bödvar on 2008-11-09
I have isolated that Firefox causes a lot of the freezes, however, even when Firefox is not running, while I'm editing track information in Banshee, or when I just click on a random button, like an X to exit an application, or a "yes" to confirm a popup message, then my computer will just hang...

Thanks for your ideas, but Firefox is not the problem. I am considering converting to Windows as I cannot just turn off my PC and wait for it to boot 20 times a day.

---

### Post by Ryadt on 2008-11-09
Can you post the specs.
Also post the output of ```
top
```

---

### Post by glotz on 2008-11-09
What version do you use? I'm on Hardy (8.04) and it never crashes. Also, did you check the install media for defects before installing? Also, scanning your memory for errors might be a good idea if you haven't.

---

### Post by Bödvar on 2008-11-09
> **Ryadt said:**
> Can you post the specs.
Also post the output of ```
top
```

Hi. These are my specs:

```
adriaan@adriaan-desktop:~$ sudo lshw
[sudo] password for adriaan:
adriaan-desktop           
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 8I915MD-G
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F1 (08/12/2005)
          size: 128KiB
          capacity: 320KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: Socket 775
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV380 0x3e50 [Radeon X600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV380 [Radeon X600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:14:85:26:8c:8f
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD080HJ
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ZH10
                serial: S08EJ30YA34351
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d972d972
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: a4b6975f-14bd-4eda-af19-795e1065813e
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-06 16:52:48 filesystem=ext3 modified=2008-11-09 11:39:32 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-09 11:39:32 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1466MiB
                   capacity: 1466MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r
                configuration: status=nodisc
           *-disk:1
                description: ATA Disk
                product: ST3160815A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 9RA4DLF3
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a70932af
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/160
                   version: 3.1
                   serial: 6e5fb330-6703-de41-a4cd-f56f29b03ca5
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-04-25 21:20:59 filesystem=ntfs label=160 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:72:8a:53:0e:3b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

The output for ```
top
``` is:

```
top - 12:58:59 up  1:19,  2 users,  load average: 0.46, 0.40, 0.37
Tasks: 120 total,   2 running, 118 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.2%us,  2.6%sy,  0.0%ni, 89.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:    514236k total,   507096k used,     7140k free,    16848k buffers
Swap:  1502036k total,    73540k used,  1428496k free,   109608k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5507 adriaan   20   0  197m  79m  19m S    7 15.9  11:10.72 banshee-1          
 5296 adriaan   20   0 31600 4560 3040 R    6  0.9   3:13.64 pulseaudio         
 4971 root      20   0  402m  69m  19m S    6 13.9   5:37.56 Xorg               
 5640 adriaan   20   0  238m  86m  26m S    2 17.2   2:40.23 epiphany-browse    
 5395 adriaan   20   0 22020 8132 5672 S    1  1.6   0:22.56 compiz.real        
 5417 adriaan   20   0 27036  13m 9712 S    1  2.8   0:02.18 update-notifier    
 6092 root      20   0  3932 1780 1516 S    1  0.3   0:01.72 http               
 6119 adriaan   20   0 99912  23m  12m S    1  4.7   0:00.82 gnome-terminal     
 6140 adriaan   20   0  2416 1152  884 R    1  0.2   0:00.10 top                
    1 root      20   0  3056 1324  524 S    0  0.3   0:01.32 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         

```

But the content changes the whole time, so I hope I copied and pasted everything.

---

### Post by Bödvar on 2008-11-09
> **glotz said:**
> What version do you use? I'm on Hardy (8.04) and it never crashes. Also, did you check the install media for defects before installing? Also, scanning your memory for errors might be a good idea if you haven't.

I am using Ubuntu Intrepid Ibex 8.10. I checked the CD for errors before installing, as my previous installation crashed on the first day saying "cannot load cman" or something similar. This installation has been running smoothly for about two days now.

Thanks for your ideas. How do I scan the memory for errors?

---

### Post by Ryadt on 2008-11-09
Try using metacity instead of compiz and see if it helps.
```
metacity --replace
```

---

### Post by Bödvar on 2008-11-09
> **Ryadt said:**
> Try using metacity instead of compiz and see if it helps.
```
metacity --replace
```

What does that do? Will it be safe? Can I revert to "compiz" again if that didn't work?

---

### Post by Ryadt on 2008-11-09
It's safe.
```
compiz
``` should revert it back

---

### Post by Bödvar on 2008-11-09
> **Ryadt said:**
> It's safe.
```
compiz
``` should revert it back
Thanks, I've entered the metacity thing now. My screen flashed and is back to normal now. I will open Firefox and see how long I can go before everything freezes up again.

By the way, is there any way to escape a freezed system? Everytime everything freezes, the current song playing through one of my players (Amarok/Banshee/Rhythmbox) keeps on playing until it finishes, but the next song never loads. I can also move the pointer around. But the system is non-interactible. Is there a button I can press to stop the process that is causing the trouble? Or is the only solution to pull the plug everytime?

---

### Post by Ryadt on 2008-11-09
Ctrl+Alt+Backspace will log you out.

---

### Post by Bödvar on 2008-11-09
About a minute after I posted my last post, I couldn't open any windows. I tried clicking on "terminal" that was in the bottom bar, but nothing happened. I tried clicking on the other Epiphany windows on the bottom bar - nothing happened. But the system was still interactible. So I just logged off and on again. Is this normal?

---

### Post by Ryadt on 2008-11-09
> **Bödvar said:**
> About a minute after I posted my last post, I couldn't open any windows. I tried clicking on "terminal" that was in the bottom bar, but nothing happened. I tried clicking on the other Epiphany windows on the bottom bar - nothing happened. But the system was still interactible. So I just logged off and on again. Is this normal?
Not really. 
When you log back in re-enter the metacity command and see if you still have the issue.

---

### Post by Bödvar on 2008-11-09
> **Ryadt said:**
> Ctrl+Alt+Backspace will log you out.

Thanks.

---

### Post by Bödvar on 2008-11-09
> **Ryadt said:**
> Not really. 
When you log back in re-enter the metacity command and see if you still have the issue.
Thanks, I did that. It just flashed like in the first place, but everything's working now, so I guess this is solved. Thanks!

---

### Post by Bödvar on 2008-11-09
> **Bödvar said:**
> Thanks, I did that. It just flashed like in the first place, but everything's working now, so I guess this is solved. Thanks!
Okay so directly after I posted that message, the same happened. All the minuses, boxes and X's disappeared from the currently open Epiphany window, so I couldn't escape it. I could also not access that windows that was on the bottom bar. So I had to log off and on again.

Now I am typing this using Firefox. I am now going to see whether I can use Firefox without trouble. The only active addons now are Greasemonkey and Adblock Plus.

---

### Post by glotz on 2008-11-09
[QUOTE=Bödvar]I am using Ubuntu Intrepid Ibex 8.10. I checked the CD for errors before installing, as my previous installation crashed on the first day saying "cannot load cman" or something similar. This installation has been running smoothly for about two days now.

Thanks for your ideas. How do I scan the memory for errors?[/QUOTE]

8.04 is the latest LTS (long term support) version. Those versions probably are more stable than the intermittent versions which push the envelope and bring in new stuff. LTSes are released every 2 years.

You can check the memory at boot time. Select the mem86 boot option in the grub menu. Let the thing go through your memory a few times. It will take some time, depending on the amount you have, even up to hours.

I hope you get it sorted out.

---

### Post by Bödvar on 2008-11-09
> **glotz said:**
> 8.04 is the latest LTS (long term support) version. Those versions probably are more stable than the intermittent versions which push the envelope and bring in new stuff. LTSes are released every 2 years.

You can check the memory at boot time. Select the mem86 boot option in the grub menu. Let the thing go through your memory a few times. It will take some time, depending on the amount you have, even up to hours.

I hope you get it sorted out.
I didn't know that 8.10 was an intermittent version at all. Do you recommend downgrading to 8.04? I will do that then.

---

### Post by glotz on 2008-11-09
They're all official and stable versions. It might be worth a try still. Suggest you do the memory testing first.

---

