---
title: "GeForce 8400GS killed my system"
date: 2010-09-25
forum: Hardware
---

### Post by Quadari on 2010-09-25
Hi All,

I have an older system that I'm attempting to use as a mythbuntu box.  Just today I bought a Sparkle GeForce 8400GS PCI (_not_ PCIe) card to use as a graphics card.  That's when the trouble started.

The system boots and runs perfectly just before I plugged the card into one of the PCI slots.

Then I turned off the computer, plugged the card in, and tried to start it up.  i got a screen full of jibberish, with the last thing I could see on screen being:
```

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/prof failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found.  Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
enter 'help' for a list of built-in commands.

(initramfs)

```

So I unplugged the card and tried to start up again.  Now, even though the card isn't plugged in, I get exactly the same behavior.

So it seems that somehow the graphics card permanently broke the system even when I unplug it.

I read lots of pages and threads about getting Nvidia cards to work, but they all involve being able to boot up and get a command line, which I can't seem to do.  When I first booted up, before I plugged the card in, I tried running the NVIDIA-Linux-x86-256.53.run.sh driver install script, but got a warning that it couldn't find any installed NVIDIA cards, so I quit, figuring that I had to run that script after I plugged the card in.   Maybe I was wrong about that?  :confused:

Here is some of the output of lshw that I recorded before this incident happened:

```

description: Desktop Computer
    product: Product Name
    vendor: System Manufacturer
    version: SYS-xxxxxx
    serial: Serial number xxxxxx
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: SAMBA-1845GL
       vendor: First International Computer, Inc.
       physical id: 0
       version: PCB 1.x
       serial: Serial number xxxxxx
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (03/31/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0

     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:c0000000-cfffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-d7ffffff(prefetchable) memory:e0000000-e007ffff

```

Anyway - some help in restoring my system so that it will boot and then getting it to work with the graphics card would be greatly, greatly appreciated.

Thanks!

---

### Post by PRC09 on 2010-09-25
If you can get into recovery mode (if you cant see the recovery mode hold the shift key down while reboot) and see if you can get to dpkg and run that first.Then try failsafe X and see if you can at least get back to the desktop.I am not so good at terminal commands so you can try that.....

---

### Post by Quadari on 2010-09-25
The problem has been resolved.

I managed to get my system back to booting again using the livecd.  Then after that happened I followed a couple of other posts.

If other people are having similar problems, please see the following posts:

The one that really explained it all is trespuntos' post on this page:
[http://ubuntuforums.org/showthread.php?t=1467074&page=4](http://ubuntuforums.org/showthread.php?t=1467074&page=4)

I had to use some more blacklists in my /etc/modprobe.d/blacklist.conf to get it to work.  See this post:
[http://ubuntuforums.org/showpost.php?p=9885855&postcount=13](http://ubuntuforums.org/showpost.php?p=9885855&postcount=13)

Note that I had to ssh into my box in order to complete most of those steps since some of those early steps caused the screen to go black when using my built-in graphics card.  But the machine was still running so I could ssh into it and get things done.

But it appears to be working as of now....

---

