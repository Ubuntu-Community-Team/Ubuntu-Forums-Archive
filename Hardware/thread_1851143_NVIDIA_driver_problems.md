---
title: "NVIDIA driver problems"
date: 2011-09-27
forum: Hardware
---

### Post by lonestar101x on 2011-09-27
Hello,
  
   I am running ubutnu 10.04 on my dektop now and I recently purchased a ZOTAC NVIDIA GT520 for it and I went to install the driver onto the computer and every time I try  I get some sort of error:

[LIST]
[*]error in sums xxxxxxxxxxxx xxxxxxxxxxxxxx (can't remember what the numbers are)
[*]error: md5
[*]extraction failed
[/LIST]
Then sometimes, about 5% of the time the acutal driver program starts, then after 2 seconds an error rises and I got two messages

"distribution scirpt failed"
"unable to build kernal module"

The actual program only ran once, all the other times it would say I'm running in the x server and make me to quit

the code i run is:
sudo -s
cd Desktop
sudo sh NVIDIA-Linux-x86-230.13.run
*uually get the sum or md5 error

or I'd try:
ALT+CTRL+F1
```
sudo -s
cd Desktop
sudo sh NVIDIA-Linux-x86-230.13.run
*uually get the sum or md5 error
(doin i this way actually ran the driver software but then ran into an error quickly before the program ended)

```
Oh and one last thing, each time I open System -> Administration -> NVIDIA X Server Settings, the program tells me that I am not running the NVIDIA X driver and I'm like not duh it won't let me do it.
Tells me to run 'nvidia x-config' as root (which I have) and it did nothing

Please I don't want to give up I miss dual monitors and I don't want to waste $60

Last note:
when I type in 
sudo lshw -C video:
```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:d0000000-d7ffffff(prefetchable) memory:d8000000-d9ffffff(prefetchable) ioport:dc80(size=128) memory:dfe00000-dfe7ffff(prefetchable)

```

---

### Post by ajgreeny on 2011-09-27
> error in sums xxxxxxxxxxxx xxxxxxxxxxxxxx (can't remember what the numbers are)
error: md5
extraction failed
All of those error messages mean that the driver you downloaded (how did you do that?) is corrupt and therefore explains why you can not install it successfully and why the nvidia card is not currently in operation.

Tell us how you got the driver.  Did you try the **Additional Drivers** utility in the System ->Administration menu?

---

### Post by lonestar101x on 2011-09-28
I went to NVIDIA.com and downloaded the driver from there.
 
I also went to the ZOTAC website and tried a driver download from them.
 
Could it be my computer not downloading properly? Should I try a diffenet IP at like the library or something and transfer via usb?
 
when I'm at 'Additional Drivers" in the System -> Administration, I get an enabled driver that is called 'NVIDIA Accelerated Graphics driver (version current)'.  So I assume that the driver I am trying to install is in...
 
But why is my computer half working?  During the boot process th screen flashes and shows flashes of the screen when you are out of the x server and then flashes back and forth to that and god knows what, until a black screen with a small window in the center that says:
 
 'Couldn't run/find the NVIDIA Driver.  Have to run in low graphics mode.  Couldn't find the nvidia kernel module.' (not exact but that's the jist of it.)
 
I'm willing to install an older driver (you know one that will actually allow me to use my GPU, if someone could email it or something or tell me a proper download link.
 
Thank you for all your help.

---

### Post by lonestar101x on 2011-09-29
UDATE: I have just installed Ubuntu 11 and almost gave up on the card when I was messing with arduino and rand the dmsg command in the terminal and got this back (i assume) for information about my PCI slot:

```
[    0.777257] PCI: max bus depth: 1 pci_try_num: 2
[    0.777300] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.777312] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.777318] pci 0000:00:01.0: PCI bridge to [bus 01-01]
**[    0.777323] pci 0000:00:01.0:   bridge window [io  disabled]**
[    0.777331] pci 0000:00:01.0:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.777338] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    0.777348] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.777355] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.777364] pci 0000:00:1c.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.777373] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.777386] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.777393] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.777404] pci 0000:00:1e.0:   bridge window [mem 0xdfa00000-0xdfbfffff]
[    0.777411] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.777448] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.777456] pci 0000:00:01.0: setting latency timer to 64
[    0.777468] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.777476] pci 0000:00:1c.0: setting latency timer to 64
[    0.777488] pci 0000:00:1e.0: setting latency timer to 64
[    0.777496] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.777501] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.777507] pci_bus 0000:01: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.777513] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.777518] pci_bus 0000:02: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.777524] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.777530] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.777535] pci_bus 0000:03: resource 1 [mem 0xdfa00000-0xdfbfffff]
[    0.777541] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.777546] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
```

Cold the line: 

[    0.777323] pci 0000:00:01.0:   bridge window [io  disabled]   have anything to do with why my computer isn't working with my card?

---

### Post by dino99 on 2011-09-29
sudo rm /etc/X11/xorg.conf

sudo apt-get install synaptic
sudo synaptic
         search all the "nvidia" installed packages (left pane: status -> installed) and remove/purge them
         then go to synaptic menu: settings -> repo -> other software -> add
there, add this ppa (copy/paste): ppa:xorg-edgers/ppa 
(from: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)) 
and update, then install: nvidia-current & nvidia-settings

reboot then check driver activation (sudo jockey-gtk)

---

### Post by searchfgold6789 on 2011-09-29
What everyone is trying to tell you to do is to just get the Nvidia from the repositories. Ubuntu provides you with the ability to automatically download Nvidia drivers and installs them automatically if you need them, which is what their instruction is centered around. If you want to do that then OK, it'll probably save you alot of trouble.
However, if there is any particular reason why you downloaded them from the website instead, then I can tell you that the Md5 error results from a file that did not download correctly. So, all you need to do is download the driver again.
 - search

---

