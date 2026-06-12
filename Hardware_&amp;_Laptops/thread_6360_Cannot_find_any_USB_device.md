---
title: "Cannot find any USB device"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by haocheng on 2004-11-27
Hi~~~

I have used Ubuntu for a few weeks and it works very well  :smile: 

Except that it cannot find any USB device I plugged in :???
So I have to switch to Windows when I need to use my flash...

I tried several ways but I just cannot find my usb device...

```

robin@ubuntu:/ $ lshw -short |grep scsi
/1                scsi0   storage
/2                scsi1   storage 

```

```

robin@ubuntu:/ $ df
Filesystem             1K-blocks      Used     Available    Use% Mounted on
/dev/sda1               993631       180635    759984     20% /
tmpfs                   517908            0           517908      0% /dev/shm
/dev/sda7             94157708       542916  88831844   1% /home
/dev/sda6             21172948      2246592  17850808  12% /usr
/dev/sda5              3130888       609484    2362364  21% /var
/dev/hda1              8281348      6992108   1289240   85% /mnt/win_c
/dev/hda5             21701200     15370864   6330336  71% /mnt/win_d
/dev/hdb1             14998048     13028528   1969520  87% /mnt/win_e
/dev/hdb5             14990016     12628472   2361544  85% /mnt/win_f
/dev/sda3             32756576        70528     32686048  1% /mnt/win_g 

```

```

robin@ubuntu:/ $ ll /media
lrwxrwxrwx  1 root root    6 2004-11-17 07:24 cdrom -> cdrom0
drwxr-xr-x  2 root root 1024 2004-11-17 07:24 cdrom0
drwxr-xr-x  2 root root 1024 2004-11-17 07:24 cdrom1
lrwxrwxrwx  1 root root    7 2004-11-17 07:24 floppy -> floppy0
drwxr-xr-x  2 root root 1024 2004-11-17 07:24 floppy0 

```

I use P4P800 SE and install Ubuntu on SATA HD (/dev/sda).
The kernel is 2.6.8.1-3-686-smp.

Any help is appreciated and many thanks in advance~~~

---

### Post by haocheng on 2004-11-28
This is the output of dmesg:

```

cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.0: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 16, io base 0000eec0
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0000ef00
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0000ef20
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0000ef40
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)
ehci_hcd 0000:00:1d.7: can't reset
ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95
ehci_hcd: probe of 0000:00:1d.7 failed with error -95
hw_random: RNG not detected
ICH5: IDE controller at PCI slot 0000:00:1f.1
PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH5: chipset revision 2
ICH5: not 100% native mode: will probe irqs later
ICH5: port 0x01f0 already claimed by ide0
ICH5: port 0x0170 already claimed by ide1
ICH5: neither IDE port enabled (BIOS)
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
AC'97 0 analog subsections not ready
intel8x0_measure_ac97_clock: measured 49569 usecs
intel8x0: clocking to 48000
ACPI: PCI interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 22 

```

Here's the error message that may cause the problem:
(Thanks to Jeremy Lynton :-D )
```

ehci_hcd 0000:00:1d.7: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI

Controller

ehci_hcd 0000:00:1d.7: BIOS handoff failed (104, 1010001)

ehci_hcd 0000:00:1d.7: can't reset

ehci_hcd 0000:00:1d.7: init 0000:00:1d.7 fail, -95

ehci_hcd: probe of 0000:00:1d.7 failed with error -95

```

Did anyone know how to solve this problem?
It's very annoying to boot in Windows just for using my USB device :-( 

Any help is appreciated and many thanks in advance~~~

---

### Post by phill on 2005-01-13
I know it doesn't really solve your problem but I have a very similar issue with USB (can' reset) and it seems to be connected to the ACPI system (by virtue of USB working under the Live CD but not with the Install CD).  You may want to follow this thread too in case a answer gets posted there:
[http://www.ubuntuforums.org/showthread.php?t=11001](http://www.ubuntuforums.org/showthread.php?t=11001)

In the meantime you could just add acpi=off to the end of the kernel line in /boot/grub/menu.lst and that will solve your problems (but disable acpi  :( )

---

### Post by zAo on 2005-01-13
Try this and post  and post your output

```
sudo apt-get install usb-view
```

---

### Post by CAPTAIN RON FL on 2005-01-14
I am having the same problems. I did what you said and I got an error. Couldn't find package usb-view. :-( 

 I really need to get this up and running as this is what I use to upload pictures to my computer.  HELP [-o< 

Thanks, Captain Ron

---

### Post by phill on 2005-01-14
I believe zAo meant to type
sudo apt-get install usbview

---

### Post by wulf on 2005-01-14
[QUOTE=CAPTAIN RON FL]I am having the same problems. I did what you said and I got an error. Couldn't find package usb-view. :-( 

 I really need to get this up and running as this is what I use to upload pictures to my computer.  HELP [-o< 

Thanks, Captain Ron[/QUOTE]
 Also, keep an eye on this thread:

[http://www.ubuntuforums.org/showthread.php?t=10455](http://www.ubuntuforums.org/showthread.php?t=10455)

In reply to it, I mentioned my observation that USB mass storage devices would work the first time I connected to them but not thereafter, unless I stopped and restarted gnome-volume-manager. I haven't had time to pursue that any further yet, but the more eyes looking in that direction, the more chance someone will have a solution! :D

I'd certainly like to see USB devices come under the category of "it just works"!

Wulf

---

### Post by CAPTAIN RON FL on 2005-01-14
OK It's working somewhat now. I can plug it in and unplug it. I can change different CF cards. It opens a folder on my desk top .  It then pops open a window saying that  there are pictures and do I want to put them in an album.  I have tried that and it shows there is an image but it can not open it. I have tried opening it with gimp and no joy too. 

I do not know for sure what I did to get it to work this far. 
This is what I did.  


$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

Then I enabled the Universe APT repository by following these instructions.
[http://www.ubuntuforums.org/showthread.php?t=179](http://www.ubuntuforums.org/showthread.php?t=179)

I then turned off the box went to bed got up this morning and turned it back on... there it was. 

Now if I can just figure out  how to get the picture I will be almost there.

Any ideas???
 Thanks, Ron

---

### Post by CAPTAIN RON FL on 2005-01-14
I know this probably has nothing to do with it, but I did two other things .  I hooked up xchat and talked awhile on it and I hooked up gaim.  I think that is all I did. I stayed up to 3 this morning so pretty grogie. 

I hope that helps. 

Ron

---

### Post by CAPTAIN RON FL on 2005-01-14
I just remembered. I wanted to use Imagemagic so I used synaptic to get it after I did an upgrade. 

Still not sure why it's working. Just throwing things out there.  :shock: 

Ron

---

### Post by CAPTAIN RON FL on 2005-01-14
I can't believe it . Everything is working. After everything started to work except for getting picture. That part was operator error. I checked the image in windose and same thing... no image. Then I remembered I had down loaded Imagemagic on to my XP to try it out before I loaded it to ubuntu.  I tried to resize it and save. It won"t save it just leaves a empty shell.  I do not know if it acts this way in linux. But happy days.  Almost there. 

Just have to find a program that will let me resize the image in linux. 
 Thanks. Ron

---

### Post by coulter on 2005-05-01
Thanks to all for the previous posts.

Here is what worked for me.  As root, just to see the "before" output, execute:
    /sbin/fdisk -l

If you don't have usbview, install it:
    apt-get install usbview

If you are running VMWare, plug in the usb device while the guest OS running
ubuntu has the screen.  You also need the default option of a usb device 
plugged in gets owned by the guest OS if it has focus at the time.

run /usr/bin/usbview.  It may take a couple of minutes for the flash disk to show
up in the display.  Click on the flash disk to examine it.  This will force the system
to create a device file for it.

Now when you run fdisk -l, it will show a new device, /dev/sdb, in my case, and
will be somewhat confused about it.  Create your mount point and mount the
device:

   mkdir /mnt/sda
   chmod 777 /mnt/sda
   mount -t vfat /dev/sdb /mnt/sda

I found that I could only access the USB drive as root.  I made the mount point
/mnt/sda to match the mount point on a prior system.

-- Michael Coulter

---

