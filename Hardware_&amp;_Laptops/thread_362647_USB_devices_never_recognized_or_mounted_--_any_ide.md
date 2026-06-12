---
title: "USB devices never recognized or mounted -- any ideas why, or how I could fix this?"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by monocongo on 2007-02-15
I have installed Ubuntu onto my system and everything appears to be working fine except that it never recognizes USB devices (I've tried with 3 external drives and a flash drive).  My system is a dual boot Windows/Linux configuration using the latest Ubuntu distribution (6.10).  I have run the update utility and installed a few additional packages (Eclipse, Banshee, ntfs-3g, a driver for my ATI video card, etc.), but I don't think I've done anything which would hose USB support.

When I plug external devices into my USB ports I never see the devices appear in the File Browser, so I'm assuming that they're not being recognized and mounted as filesystems.  I have little understanding as to how this works, but I was assuming that I could just plug these in and they would be mounted automatically as separate filesystems visible in the File Browser application.

Below is the result of lshw showing three USB controllers.

```
$ sudo lshw -C bus
  *-usb:0
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13
       bus info: pci@00:13.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02d000-fe02dfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@1
          logical name: usb1
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:1
       description: USB Controller
       product: IXP SB400 USB Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.1
       bus info: pci@00:13.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ohci bus_master cap_list
       configuration: driver=ohci_hcd
       resources: iomemory:fe02c000-fe02cfff irq:201
     *-usbhost
          product: OHCI Host Controller
          vendor: Linux 2.6.17-11-generic ohci_hcd
          physical id: 1
          bus info: usb@2
          logical name: usb2
          version: 2.06
          capabilities: usb-1.10
          configuration: driver=hub maxpower=0mA slots=4 speed=12.0MB/s
  *-usb:2
       description: USB Controller
       product: IXP SB400 USB2 Host Controller
       vendor: ATI Technologies Inc
       physical id: 13.2
       bus info: pci@00:13.2
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: ehci bus_master cap_list
       configuration: driver=ehci_hcd
       resources: iomemory:fe02b000-fe02bfff irq:201
     *-usbhost
          product: EHCI Host Controller
          vendor: Linux 2.6.17-11-generic ehci_hcd
          physical id: 1
          bus info: usb@3
          logical name: usb3
          version: 2.06
          capabilities: usb-2.00
          configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
```

When I plug in a USB device I get four messages from /var/log/messages:
```
$ tail -f /var/log/messages
Feb 14 17:39:33 monocongo kernel: [17179794.496000] usb 3-5: new high speed USB device using ehci_hcd and address 13
Feb 14 17:39:44 monocongo kernel: [17179806.152000] usb 3-5: new high speed USB device using ehci_hcd and address 14
Feb 14 17:39:56 monocongo kernel: [17179817.808000] usb 3-5: new high speed USB device using ehci_hcd and address 15
Feb 14 17:40:06 monocongo kernel: [17179828.344000] usb 3-5: new high speed USB device using ehci_hcd and address 16
```

If anyone can give me a clue as to where else I might look for the trouble, or what I might try to fix this then I'll certainly appreciate it. Thanks in advance!


--James

---

### Post by dcstar on 2007-02-15
> **monocongo said:**
> 
.......
If anyone can give me a clue as to where else I might look for the trouble, or what I might try to fix this then I'll certainly appreciate it. Thanks in advance!

--James

Look at the output of **dmesg** when you plug things in.

---

### Post by monocongo on 2007-02-16
Thanks for the idea.

Here's what I get after turning on an external hard drive plugged into a USB port:
```
[17180176.660000] usb 3-4: new high speed USB device using ehci_hcd and address 3
[17180177.660000] ehci_hcd 0000:00:13.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17180188.204000] usb 3-4: device not accepting address 3, error -110
[17180188.316000] usb 3-4: new high speed USB device using ehci_hcd and address 4
[17180199.860000] usb 3-4: device not accepting address 4, error -110
[17180199.972000] usb 3-4: new high speed USB device using ehci_hcd and address 5
[17180210.396000] usb 3-4: device not accepting address 5, error -110
[17180210.508000] usb 3-4: new high speed USB device using ehci_hcd and address 6
[17180220.932000] usb 3-4: device not accepting address 6, error -110
``` 

I have tried running "modprobe usb-storage" but this has had no effect.

I have found a forum thread which appears to address the issue that I think I'm dealing with: [http://www.ubuntuforums.org/showthread.php?t=81153]("http://www.ubuntuforums.org/showthread.php?t=81153").  However the thread is about a year old, and I would like to confirm that the advice offered therein is still valid before I start trying voodoo like that myself.  If someone can confirm that this is something that is still advisable to try and safe to do with my configuration (uname output listed below) then please let me know and I will go for it.

```
$ uname -a
Linux monocongo 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```


--James

---

### Post by monocongo on 2007-02-16
Well I tried the workaround suggested in the other thread and as I feared bad voodoo ensued.  To wit I added "irqpoll" to the end of the kernel line in /boot/grub/menu.lst, and after rebooting I ended up getting a black screen which looked something like this:```
BusyBox Built in shell (ash)
/bin/sh: can't access tty; job control turned off
(initramfs)
```

After rebooting into a previous kernel version and backing out the changes to menu.lst I am now back to where I was before.

Does the above error tell us anything, i.e. should the irqpoll option not have this effect?  Does the bad result of adding the irqpoll option to the kernel line in /boot/grub/menu.lst indicate a possible source of the USB error (or maybe something worse like a system misconfiguration)?


--James

---

### Post by monocongo on 2007-02-18
It turns out that using the kernel boot option 'irqpoll' was the answer to my USB problems after all.  See **[this]("http://www.ubuntuforums.org/showthread.php?t=81153")** thread for the details.

--James

---

### Post by upro on 2007-02-23
It's a permission problem. 

With all the same messages form /var/log/syslog and dmesg I figured out that I could mount a camera and import images by doing

sudo gnome-volume-manager-gthumb

It wouldn't work as user.

So, just check persmissions...

Hope that helps,

upro

---

