---
title: "Intel N3150 graphics not recognised in 16.04"
date: 2016-06-27
forum: Hardware
---

### Post by joelittlejohn on 2016-06-27
I've just installed Ubuntu 16.04 LTS onto a [Zotac ZBOX CI323]("https://www.zotac.com/us/product/mini_pcs/zbox-ci323-nano#spec"). This ZBOX has an [Intel Celeron N3150]("http://ark.intel.com/products/87258/Intel-Celeron-Processor-N3150-2M-Cache-up-to-2_08-GHz"), with integrated graphics.

When I install Ubuntu 16.04 I see the 'Low graphics' warning. I had to add the **nouveau.modeset=0** boot parameter to get past this. When I get to the Ubuntu Desktop I can see that the GPU hasn't been recognised correctly because the resolution is very low. lshw shows the following:

```

        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64)

```

([full lshw output is here]("https://www.refheap.com/120870"))

16.04 is supposed to include the latest Intel drivers for Linux v1.4.0 ([as described here]("https://01.org/linuxgraphics/downloads/intel-graphics-installer-linux-1.4.0")). My kernel version is 4.4.0-21.

I'm out of ideas on what the problem could be here. Is the integrated GPU in the N3150 not yet supported under Linux?

---

### Post by mastablasta on 2016-06-28
so this one has Intel HD Graphics 400  which is supposedly supported under Linux and it looks like it has been supported for osme time by the kernel (since 3.19): [SIZE=2]http://www.phoronix.com/scan.php?page=article&item=intel-braswell-upgrade&num=1

and since these cips are found in some chromebook they definitelly have good Linux support.

so i do not know why you are having issues.

one thing though - i do not know what nouveau has to do with Intel graphics as they are nVidia opensource drivers.

edit: [SIZE=2]https://wiki.archlinux.org/index.php/intel_graphics
[/SIZE]

> [h=2]Loading[/h]The Intel kernel module should load fine automatically on system boot. 
If it does not happen, then: 

[LIST]
[*] Make sure you do **not** have nomodeset or vga= as a [[COLOR=#0077bb]kernel parameter[/COLOR]]("https://wiki.archlinux.org/index.php/Kernel_parameter"), since Intel requires kernel mode-setting.
[*] Also, check that you have not disabled Intel by using any modprobe blacklisting within /etc/modprobe.d/ or /usr/lib/modprobe.d/.
[/LIST]




[/SIZE]

---

### Post by sudodus on 2016-06-28
Try to install a small package, that helps with some Intel graphics chips.

```
sudo apt-get install xserver-xorg-video-intel
```

It might help you too. If it is already installed we have to look somewhere else.

You should also get a current kernel, I think 4.4.0-25 or newer. It may work better with your graphics. Run the commands

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and reboot with the current kernel.

---

### Post by joelittlejohn on 2016-06-30
Thanks for your comments guys. Turns out this was my own stupidity (kinda).

In order to get the installer to display at all, I had to activate the nomodeset option. Turns out if you activate this for the installer, it is permanently active on your installed system. So I had nomodeset set in grub options and this is what cause 'Low graphics' mode.

I still don't know why setting nouveau.modeset=0 onto the end of the grub options then allowed me to get past 'Low graphics mode' and into a (poor quality) desktop.

Anyway, the GPU driver _was_ available and it's now all sorted by removing nomodeset and nouveau.modeset=0 from the grub options entirely.

---

### Post by sudodus on 2016-07-01
Congratulations :KS

In order to help other users find your solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

