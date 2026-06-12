---
title: "Gentoo Kernel"
date: 2009-01-20
forum: Gentoo and derivatives
---

### Post by Mr.Macdonald on 2009-01-20
I finally managed to get Gentoo to PARTIALLY boot!!

I am dual booting Ubuntu and Gentoo.

now I get dumped into a prompt to set the root directory, or to enter a shell. When I enter the shell I looked into the /dev and found only 1 drive, And that in my iPod. I don't know what kernel options to select to support my drive.

Here is lspci:
> 00:00.0 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge (rev 10)
00:00.1 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VX800 Serial ATA and EIDE Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. CX700/VX700 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. CX700/VX700 Internal Module Bus
00:13.0 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. CX700/VX700 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] (rev 03)
02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


---

### Post by Bachstelze on 2009-01-20
My method to find out the modules you need tor your ATA chipset: boot a Live CD and start unloading modules until your hard drive is not detected anymore. The last one you unloaded is the one you need. ;)

Useful commands:

[font="monospace"]lsmod[/font] lists the currently loaded modules
[font="monospace"]modprobe modulename[/font] loads a module
[font="monospace"]modprobe -r modulename[/font] unloads

---

### Post by Mr.Macdonald on 2009-01-20
Now If I find that (haven't yet, but will), how do select that option in the kernel. To me the options in the kernel seem very different that the ones from the menuconfig.

Also how do I make sure that I am not removing ones that are required for other things? could I make the system crash by pulling modules.

Or could I just get a list of modules that were loaded by the udev on the live cd.

What if I need more that one module. Should I reload and skip that one in the list

---

### Post by RedSquirrel on 2009-01-20
While you are in menuconfig, you'll have to read the documentation that accompanies each option. It will tell you what the option is for and the name of the module if you choose to build that option (driver) as a module.

Note that 'lspci' has useful options, for example:

```
# lspci -vv
```
```
# lspci -k
```

---

### Post by Mr.Macdonald on 2009-01-20
I would need to compile all those into the kernel, right? But how do those relate to the kernel options?

So I just search for each of those?

---

### Post by Bachstelze on 2009-01-21
There is a key in menuconfig you can press to get a search box (I think it's /). Then type the module name, and it should bring you to the corresponding option.

---

