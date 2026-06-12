---
title: "ubuntu 16.04 - black screen during boot"
date: 2017-06-09
forum: Hardware
---

### Post by panross on 2017-06-09
[SIZE=2][COLOR=#111111][FONT=Ubuntu]I am new here, so please bear with me. I have tried different resources available for the problem already, but with no effect.Long story short, Ubuntu 16.04.2 (Dual Boot: Ubuntu + Windows 8, UEFI installation) was working fine for a long time but since recently, It is booting to a blank screen.By blank screen, I mean:-

[/FONT][/COLOR][/SIZE]
[LIST=1]
[*][SIZE=2]after purple ubuntu screen (which always shows up during normal boot), there is just a 100% dark screen, no login screen shown.[/SIZE]
[*][SIZE=2]There is no mouse pointer.[/SIZE]
[*][SIZE=2]I am able to switch to the command-line screen or tty1.[/SIZE]
[*][SIZE=2]using _dmesg_ in command-line shows up error `[COLOR=#ff0000]_radeon_[/COLOR][COLOR=#ff0000]_ 0000:01:00.0: VCE init error (-22)_[/COLOR].[/SIZE]
[/LIST]
[SIZE=2]
[/SIZE]
[SIZE=2][COLOR=#111111][FONT=Ubuntu]But, when used with nomodeset command as mentioned in the [X/Troubleshooting/Blankscreen]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen") as a workaround. It is able to load the GUI and presents with a login screen.[/FONT][/COLOR]
[/SIZE][COLOR=#111111][FONT=Ubuntu][SIZE=2]I need the Ubuntu to work without using nomodeset. Thank you for hearing me out.[/SIZE]

**Update 1:**after running [SIZE=3]**lspci -nnk | grep Display, **it returns AMD Radeon HD 8550M / R5 M230. I guess the problem is with display-controller here.[/SIZE][/FONT][/COLOR]

---

### Post by LastDino on 2017-06-09
Installing 3rd party/proprietor drivers didn't help?

[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

Locate and download your drivers for the card displayed in your last command output.

Then install..

---

### Post by panross on 2017-06-09
Hi @LastDino , Yes I did try it, but then boot failed. I am still looking for a native solution.

---

### Post by Bashing-om on 2017-06-09
panrossl Hi ! My Welcome to the forum .

That card takes the radeon driver:
per: [https://wiki.gentoo.org/wiki/Amdgpu](https://wiki.gentoo.org/wiki/Amdgpu)

What do you have now installed ?
```

lsmod | grep radeon
lsmod | grep amdgpu
sudo lshw -C display

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by panross on 2017-06-10
Hi Bashing-Om,  lsmod commands did not give any output.  But sharing the output of sudo lshw -C display. It is to note that currently I am running in nomodeset mode.

**-display UNCLAIMED     *
*       description: VGA compatible controller*
*       product: Haswell-ULT Integrated Graphics Controller*
*       vendor: Intel Corporation*
*       physical id: 2*
*       bus info: pci@0000:00:02.0*
*       version: 09*
*       width: 64 bits*
*       clock: 33MHz*
*       capabilities: msi pm vga_controller bus_master cap_list*
*       configuration: latency=0*
*       resources: memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5000(size=64) memory:c0000-dffff*
*  *-display UNCLAIMED*
*       description: Display controller*
*       product: Sun LE [Radeon HD 8550M / R5 M230]*
*       vendor: Advanced Micro Devices, Inc. [AMD/ATI]*
*       physical id: 0*
*       bus info: pci@0000:03:00.0*
*       version: 00*
*       width: 64 bits*
*       clock: 33MHz*
*       capabilities: pm pciexpress msi cap_list*
*       configuration: latency=0*
[I]       resources: memory:b0000000-bfffffff memory:d0400000-d043ffff ioport:3000(size=256) memory:d0440000-d045ffff

[/I]
Apart from that, I have shared all the updates regarding the problem [here]("https://askubuntu.com/questions/922770/ubuntu-16-04-amd-radeon-hd-8550m-r5-m230-black-screen-after-boot").

---

### Post by gsahli on 2017-06-10
The dmesg error shows the wrong pci address is being used. You're going to have to get it to use the right address, probably in the grub "kernel" options command line. Or, maybe in an /etc/X11/xorg.conf.d file.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto)
[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

What I would try first: create /etc/X11/xorg.conf.d and add this as a file named: 20-amdgpu.conf
> Section "Device"
    Identifier "AMD"
    Driver "amdgpu"
EndSection

While this doesn't force the pci address, it does force the amdgpu driver to look for it.

---

