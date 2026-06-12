---
title: "Serious (and puzzling) problem with Nvidia card..."
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by Naerymdan on 2006-04-26
Hi,

Let's get it out of the way now: I'm kinda new, but not completely stupid :???: 

I have a 'Chaintech VNF4 Zenith Value Edition' motherboard and a 'XFX GeForce 6800 XT PCIe' video card. 

Everything works fine with the 'nv' driver, as it should.

The problems start when I try using the 'nvidia' ones: All i get is a blank/black screen and absolutely no response from the system.

Here are some more info: 

1 - I use Dapper Drake up-to-date.

2 - I tried using the nvidia-glx package, installing the package directly from [www.nvidia.com](www.nvidia.com) and I also went up to recompile the whole kernel with the drivers (actually worked, all except the video card that is...) and I always get the same problem.

3 - No sound from gdm starting, can't ctrl-alt-F1 or ctrl-alt-backspace, nor log in without monitor (the monitor is correctly detected).

4 - I tried about every trick / walkthrough / tip / help on the subject, with no luck.

Here are the log files that were generated durint one attempt to boot normaly with nvidia-glx activated: Xorg.0.log, kern.log, dmesg and i also included in the file 'others.zip' the log debug, evms-engine.log, messages, udev and syslog.

I also attached xorg.conf for your viewing pleasures.

There are some lines, mainly in 'kern.log' that seems wrong:

> 
PCI: Cannot allocate resource region 3 of device 0000:05:00.0
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4800-0x487f has been reserved
pnp: 00:00: ioport range 0x4880-0x48ff has been reserved

and

nvidia: module license 'NVIDIA' taints kernel.
**** SET: Misaligned resource pointer: f7e79b02 Type 07 Len 0
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 74

and lastly,

PCI: Setting latency timer of device 0000:00:0b.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0c.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0d.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0e.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS



Here are the important parts of my Xorg.conf file:

> 
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
#   Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "Device"
    Identifier    "NVIDIA GPU GeForce 6800 XT"
    Driver        "nvidia"
    BusID        "PCI:5:0:0"
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA GPU GeForce 6800 XT"
    Monitor        "Samsung SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


and that's about it... 

Something that also baffles me is Xorg.0.log; it doesn't end in error or nothing, it just seems to... hang?

Thanks.
Vincent.

---

### Post by rjwood on 2006-04-26
go to synaptic and make sure you have "nvidia-glx" and 'nvidia-restricted-modules" and all the correct headers installed for your kernel. to find out which kernel you had just do "uname -r" from a terminal. (without the quotaion marks of course)---good luck..

---

### Post by Naerymdan on 2006-04-26
I have  the following packages installed regarding nvidia:

nvidia-glx
nvidia-kernel-common
nvidia-kernel-source
xserver-xorg-driver-nv

and also

linux-restricted-modules-2.6.15-21-386
linux-image-2.6.15-21-386
linux-headers-2.6.15-21-386
linux-headers-2.6.15-21
linux-source-2.6.15

Of course, i use kernel 2.6.15-21-386

I did not find any packages named 'nvidia-restricted-modules' and i have enabled all package repositories (main, restricted, universe and multiverse on all repositories).

---

### Post by whoisvince on 2006-04-26
I'm having the exact same problem with a Toshiba Satellite laptop with a GeForce4 440 Go chipset.  The thing worked beautifully under Breezy, but after installing Dapper last night, I can't get it to come up using the nvidia drivers--I'm stuck with the nv drivers.

The scenario is the same for me.  The X server hangs on startup with a frozen cursor in the upper left hand side of the screen, no gdm, no startup sounds, and I can't kill the server with ctrl-alt-backspace or bring up a terminal.  The Xorg log file shows no errors to speak of.  I've tried a few things and can't get it to work.

---

### Post by Naerymdan on 2006-04-27
I thought I'd add one thing:

I'm running Ubuntu Dapper 386 on an Athlon 64 CPU. Of course it can and does take 32 bit instructions, but still i didn<t have any problems with the 'nvidia' driver in Breezy x64 previously...

---

### Post by whoisvince on 2006-04-29
Well, this worked for me:  In /etc/modprobe.d/options, add this line, then reboot or reload the nvidia driver:

options nvidia NVreg_Mobile=1

This got my laptop up and working with the nvidia driver in the dapper repositories.  There is no need to make any changes to xorg.conf other than to specify the nvidia rather than the nv driver in the device section. 

I don't know how that will work for you Naerymdan, because this line looks like something specific for mobile nvidia GPUs (I'm on a laptop), but it's worth a shot.

Now if I could just get my resolution to display at the full 1400x1050 instead of having it default to 1372x1050, I'd be set!

---

### Post by Naerymdan on 2006-05-02
Since I'm not using a mobile GPU, this tweak doesn't work...

Actually, I tried about every modifications to the nvidia options in xorg.conf possible and even altered my /etc/modprobe/options file with other options. Nothing works...

---

### Post by whoisvince on 2006-05-04
You might want to try booting into recovery mode and starting X on your own using the command "startx -- -logverbose 6" which will give you more useful information than the normal log level, assuming that recovery mode will automatically load the nvidia driver.  You might have to do a "sudo modprobe nvidia" first.

You can also try running "cat /proc/driver/nvidia/registry" and seeing what that spits out.  All of those options are changable by adding an options line in your /etc/modprobe.d/options file.  For example, one of the lines my registry spits out is "FlatPanelMode: 1", so if I wanted to turn flat panel mode off, I would add a line that says "options nvidia NVreg_FlatPanelMode=0" and that would do it for me.  I belive there's some documentation about it in the driver README on Nvidia's website.

Looking at your log, it would probably be worth it to check your bios as well.  Try playing with the option that says assign IRQ to VGA if you have one, clearing your nvram, or going back to BIOS defaults.

Good luck!

---

