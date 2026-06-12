---
title: "[SOLVED] Going Back to 7.10"
date: 2008-07-23
forum: General Help
---

### Post by mikedemario17 on 2008-07-23
i first got into Linux when my two windows xp CPUs got the blue screen of death...i couldn't do any thing to them...and i don't have the disk to restore for them coz around my house i got like 4 CPUs and my parents have 2 vista laptops and 2 CPUs that r newer windows xp....anyways i took all my computers and put them into one good PC and got rid of the rest coz they were all 98 or old xp -----anyways---- i installed Ubuntu 7.10 to a CD then i installed it onto the windows xp dead PC... and it worked fine...i started to use my other PC that i shared with my family for a year and i just got back on here and to my surprise there was a new Ubuntu..woo i thought...but when i updated my PC is slow and freezes every 2 min. on Firefox... [SIZE="3"]so i am hear asking u guys...should i go back to 7.10?  [/SIZE]most people on this have said there have been many problems with this new version ... so i don't know what to do...

---

### Post by northern lights on 2008-07-23
Nope you shouldn't.

I don't know how you heard of "many problems" with "that new version", but it's certainly bogus.

In case you're system is truly screwed a clean install of Hardy (8.04) is required in the worst case scenario.

Can you describe the crashes in more detail?

Anyhoo, lemme fire a first guess: Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

---

### Post by mikedemario17 on 2008-07-23
well this is my pc....it could be coz its really old...
pc-windows xp home edition
Hewlett Packard Pavilion 7955 (P5269A#ABA) PC Desktop

whats a code tht shows the info of my pc ...? that i can post in forms so people know what im useing?

---

### Post by WRDN on 2008-07-23
What are the machine specifications?
The problems are often caused by lack of RAM so you could add more RAM (if possible), or try a lighter distribution such as Xubuntu or Puppy Linux.

---

### Post by northern lights on 2008-07-23
> **mikedemario17 said:**
> whats a code tht shows the info of my pc ...? that i can post in forms so people know what im useing?
Your looking for the output of ```
sudo lshw
```

That's a long list though, in order to retrieve specific hardware classes only, run ```
sudo lshw -C CLASS
```where CLASS should be replaced by the name of the class you want. For instance ```
sudo lshw -C network
``` would show you network devices...

For your own keeping, you can save the list as an .html file using```
sudo lshw -html > HardwareInfo.html

```

---

### Post by mikedemario17 on 2008-07-23
i have two xp 7955s and i took the ram out of the one and put two in the one im useing to go faster...... like i said...isnt there a terminal code tht i can post on this to let u guys know what i have...?... i got 40GB...if that helps...?

---

### Post by mikedemario17 on 2008-07-23
**well heres the long list one......>>>>>>**
mike@mike-desktop:~$ sudo lshw
[sudo] password for mike: 
PCI (sysfs)  
```
mike-desktop              
    description: Computer
    product: P5269A-ABA 7955
    vendor: HP Pavilion 04
    version: 70000TG101DUBLI
    serial: MX142B0751 NA040
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=8020B611-06F7-D411-A206-B452E0724AAE
  *-core
       description: Motherboard
       product: Dublin
       vendor: Hewlett Packard
       physical id: 0
       version: 3.05
       serial: xxxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 6.00 (09/21/2001)
          size: 98KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.0.10
          slot: WMT478/NWD
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 8KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-cache
          description: L3 cache
          physical id: 7
          slot: L3 Cache
          size: 256KiB
          capacity: 512KiB
          capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 512MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous [empty]
             physical id: 0
             slot: J6J1
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: J6J2
             size: 256MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             physical id: 2
             slot: J7J1
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 15
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: NC100 Network Everywhere Fast Ethernet 10/100
                vendor: ADMtek
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 11
                serial: 00:40:2b:19:c4:05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.2.3 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST340810A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.35
                serial: 6FB0M4BV
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=55054103
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: b41a1a61-7728-4e9e-860b-e0cda40add61
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-07-22 11:25:54 filesystem=ext3 modified=2008-07-23 10:48:27 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-23 10:48:27 state=mounted
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
           *-cdrom:0
                description: DVD writer
                product: DVD RW DRU-530A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0d
                serial: 3SONY    DVD RW DRU-530A 1.0d
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GD-8000
                vendor: HITACHI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0010
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
mike@mike-desktop:~$
```

---

### Post by northern lights on 2008-07-23
> **mikedemario17 said:**
> like i said...isnt there a terminal code tht i can post on this to let u guys know what i have...?.
Well...
How about the above post?

---

### Post by mikedemario17 on 2008-07-23
haha sorry i didnt reload my page ...i just say the post under mine

---

### Post by northern lights on 2008-07-23
> **mikedemario17 said:**
> i have two xp 7955s and i took the ram out of the one and put two in the one im useing to go faster

Shouldn't be the core of the problem. Most likely only a few things need tweaking, as it seems somethings didn't go too smooth with your distribution upgrade.

The "long list" doesn't help much either - your hardware is plenty to run Ubuntu for another few years.

Once again, can you describe the nature of the crashes in more detail?

Is firefox the only unstable candidate?

If so, what version of firefox are you running?

---

### Post by mikedemario17 on 2008-07-23
im useing firefox 3 beta 5.....

and in a differnt ?...is this pc a good one ? ..coz i want to run compiz and do the fancy desktop stuff....

> can you describe the nature of the crashes in more detail?
well when im in firefox and im on yahoo or youtube or this site ill be doing something and the browser freezes i can move the mouse and i can do a fource quit... and i can minamize the browser...but  if i wait 2 min. it starts to work again...so i tink it is the browser...i have installed 7.10 like 3 time from the live disk on this then i updated ...im makeing a 8.04 disk downstairs as we speak...so re-installing it not a problem the only thing i have on here is my bookmarks 

----

---

### Post by phidia on 2008-07-23
> **northern lights said:**
> Nope you shouldn't.

I don't know how you heard of "many problems" with "that new version", but it's certainly bogus.

In case you're system is truly screwed a clean install of Hardy (8.04) is required in the worst case scenario.

Can you describe the crashes in more detail?

Anyhoo, lemme fire a first guess: Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

It might be going too far to say that reports of problems with hardy are bogus since there are large threads like [URL="http://ubuntuforums.org/showthread.php?t=768200&highlight=hardy+worst+release"]this one here
[/URL] claiming otherwise. Experiences do differ though. 
BTW the dpkg-reconfigure commands seems to be changed in hardy. See the new [hardy xorg]("https://help.ubuntu.com/community/XORGHardy") methods.

---

### Post by Brandel Valico on 2008-07-23
If it's just Firefox freezing and not the network itself you can always just remove Version 3 and install Version 2 of Firefox.

I know Hardy had a habit of locking up my network access and would just stop working after a few minutes and I had to downgrade back to Gutsy to solve the issue a month or so ago. But that was a specific issue with my card not a common problem.

You can also try hitting escape when the computer is booting and try dropping back down to a Gutsy kernel. I believe the .24 was the latest. To check if it's a kernel issue. (Actually I just noticed that you had done a fresh install which means this option is out.)

---

### Post by northern lights on 2008-07-23
> **mikedemario17 said:**
> im useing firefox 3 beta 5.....
Here we go.

Since you're running a beta, you can obviously not expect it to be 100% stable.

I wonder why that is the case though, as the final release ("Firefox 3.0") is in the Ubuntu repositories. There actually is 3.0.1 already, but that's not in the repos yet.

Did you not run an update after the distribution upgrade?

Run ```
sudo apt-get update
sudo apt get upgrade
sudo apt-get autoremove
```

and check your version of firefox again...

[EDIT]
Reverting back to ff2 is obviously also an option, as above post reads
[/EDIT]

---

### Post by jimv on 2008-07-23
Bah, if Gutsy (7.10) worked well for you, go back to it.

Perhaps some of these guys haven't been paying attention, but Hardy has been having speed and hard-lockup issues on quite a few machines.  That's not EVERY machine, or MOST machines, but still a lot of machines.  Them denying the problem doesn't make it go away.

So like I said, if Gutsy worked, go back to it.  You can either spend your time troubleshooting Hardy, or you can actually be using your machine in Gutsy.

NOTE:  I'm not trying to say that Hardy is a bad release, but it has had it's share of problems.  It works ok for me and others, but there's nothing wrong with going back to Gutsy if it works better for some people.

If you want to save your bookmarks, you can copy them from ~/.mozilla/firefox/yourprofile/bookmarks.html

---

### Post by mikedemario17 on 2008-07-23
whats this mean.....>>>>
mike@mike-desktop:~$ sudo apt-get update
[sudo] password for mike: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@mike-desktop:~$

---

### Post by northern lights on 2008-07-23
Did you have Synaptic running while executing the update in the terminal?

That does not work...

---

### Post by mikedemario17 on 2008-07-23
no it shouldnt be...when i try to install  frostwire-4.17.0.i586.deb  it says error: failed to satisfy all dependencies (broken cache)..... how do i install it?

---

### Post by mikedemario17 on 2008-07-23
when i try to install anything it always says "only one software managemet tool is allowed to run at the same time....??? i dont have any thing else running on the pc so y this happoning? and i turned off my pc and i tryed to install limewire (not frostwire) right when i started the pc and it said the same error...same for aim or ant thing else

---

### Post by mikedemario17 on 2008-07-24
yeah so i went back to 7.10 and now everything is working as it should and there are no errors anywere so its alll good with 7.10..and thats wher ill stay untill 8.10

---

### Post by bsmith1051 on 2008-07-30
> **mikedemario17 said:**
> i went back to 7.10 and now everything is working as it should
You probably did the right thing...

---

### Post by mikedemario17 on 2008-07-30
yeah ill probly stay

---

