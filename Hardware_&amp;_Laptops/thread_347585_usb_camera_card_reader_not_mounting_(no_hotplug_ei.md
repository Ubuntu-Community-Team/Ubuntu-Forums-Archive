---
title: "usb camera card reader not mounting (no hotplug either)"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by ender42 on 2007-01-27
So, I can't mount my usb card reader.  I tried fixing it, but since installing Dapper, I don't have 

```
/etc/init.d/hotplug restart
```

And upgrades are failing.
[http://ubuntuforums.org/showthread.php?t=344759](http://ubuntuforums.org/showthread.php?t=344759)

```
fdisk
```

Shows nothing as well...

Any ideas?

---

### Post by taurus on 2007-01-27
```
dmesg | tail
sudo fdisk -l
```

---

### Post by ender42 on 2007-01-27
```

root@machine:/proc # sudo fdisk -l | grep sda
root@machine:/proc # dmesg | tail
protections[]: 0 0 0
Normal free:2712kB min:2756kB low:3444kB high:4132kB active:108936kB inactive:347520kB present:491456kB pages_scanned:5079 all_unreclaimable? no
protections[]: 0 0 0
HighMem free:0kB min:128kB low:160kB high:192kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
protections[]: 0 0 0
DMA: 0*4kB 1*8kB 1*16kB 0*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 88kB
Normal: 0*4kB 3*8kB 8*16kB 0*32kB 0*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 2712kB
HighMem: empty
Swap cache: add 511472, delete 511472, find 287703/333640, race 0+10
Out of Memory: Killed process 31119 (gthumb).

```

---

### Post by taurus on 2007-01-27
```
sudo fdisk -l
```

---

### Post by ender42 on 2007-01-27
And you can see hda and hdb, so?

---

### Post by Speedy on 2007-01-27
Hi

I have had similar problems with my usb, this solved it 
Add irqpoll to grub 

sudo gedit /boot/grub/menu.lst
# defoptions=quiet splash noapic **irqpoll**
sudo update-grub.

Steve

---

### Post by ender42 on 2007-01-28
Did that grub modification: no luck on fidsk, nor on automounting.

Haven't rebooted it, however.

---

### Post by ender42 on 2007-01-29
Rebooted, no luck with this solution.

---

### Post by ender42 on 2007-02-04
I looked at some other people having issues with USB stuff, and learnt that I should be checking the differences of ```
dmesg
``` before and after plugging the USB card reader in.  I find no difference between the two on my machine.

I also tried ```
lsusb -v
``` and got nothing.

Seems like other people with problems just found work-arounds.

---

### Post by ender42 on 2007-02-10
So, I've been looking around for whatever replaced hotplug
```
man -k hotplug
```
Shows only two commands: pmount & pumount.

Had a buddy try to figure it out, they tried:

```

root@machine:~ # cat /proc/scsi/scsi 
Attached devices:
root@machine:~ #

```

Shows nothing.  But tested out two different working USB devices, which worked on another machine (ubuntu install)...

```

root@machine:~ # locate usb_storage
root@machine:~ # modprobe usb-storage
root@machine:~ # lsmod | grep -i usb
usb_storage            64064  0
usbcore               107384  1 usb_storage
scsi_mod              119936  5 sg,st,sr_mod,sd_mod,usb_storage
ide_core              118988  5 usb_storage,ide_cd,ide_generic,sis5513,ide_disk
root@machine:~ # ls /lib/modules/2.6.10-5-386/kernel/drivers/usb/core/usbcore.ko
/lib/modules/2.6.10-5-386/kernel/drivers/usb/core/usbcore.ko
root@machine:~ # ls /lib/modules/2.6.10-5-386/kernel/drivers/usb/input/
aiptek.ko      kbtab.ko      powermate.ko    usbhid.ko  usbmouse.ko  xpad.ko
ati_remote.ko  mtouchusb.ko  touchkitusb.ko  usbkbd.ko  wacom.ko
root@machine:~ # ls /lib/modules/2.6.10-5-386/kernel/drivers/usb/media/
dsbr100.ko  konicawc.ko  pwc       sn9c102.ko  ultracam.ko  vicam.ko
ibmcam.ko   ov511.ko     se401.ko  stv680.ko   usbvideo.ko  w9968cf.ko
root@machine:~ # lshw | less
...
     *-firmware
...
capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
...
        *-usb:0 UNCLAIMED
             description: USB Controller (OHCI)
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@00:03.0
             version: 0f
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: irq=10
(ditto for 1-3 - different irq numbers, bus numbers increment)

```

No luck, and no love in getting USB to work on my machine.  I'm thinking the work around will be to go back to Hoary, where it was working.

Also:
```

root@machine:~ # dmesg | tail
HighMem: empty
Swap cache: add 568048, delete 568048, find 220118/272512, race 0+2
Out of Memory: Killed process 3360 (nautilus).
SCSI subsystem initialized
usbcore: registered new driver usbfs
usbcore: registered new driver hub
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
st: Version 20041025, fixed bufsize 32768, s/g segs 256

```

Has changed after all that those different attempts/probes/etc.

---

### Post by ender42 on 2007-03-13
WORKAROUND

Get a Warty or Hoary Live CD, and boot from that.

```
fdisk -l
```

To show the location of the USB,

```

sudo su
mount -t vfat /dev/location /mnt/location

```

It doesn't show as a file system graphically (ie: folders on your memory card are unclickable, detail-less files with unknown properties), but you can console into it, mount your real drive partition, and copy files over.  However, I cannot view them on the Warty live CD, at least with gimp or eye of gnome (different errors).  But it looks like the data transfered over, so we'll see after reboot.  Rebooted into Dapper, and images (after chown and stuff) are all viewable, so successful work-around!

```

-rwxr--r--    1 user    user      718600 Dec 30 22:04 101_2544.jpg

```

I've also tried moving my system to the partition on the other drive (issues with rsync), but hopefully I'll be reinstalling an earlier version of Ubuntu, Warty or Hoary, (or something else that works) on the main drive, so that I can access my USB card reader without this work-around...

---

### Post by ender42 on 2007-03-14
[http://ubuntuforums.org/showthread.php?t=384134](http://ubuntuforums.org/showthread.php?t=384134)

Says that 

```
sudo udevmonitor
```

Should show some details when you plugin, pull out your USB stuff.  Mine comes up with no events in dapper for the external camera card reader.

---

### Post by muiredachau on 2007-03-19
I Loaded Warty on my system and I have a [COLOR="Red"]hotplug subsystem[/COLOR] failure @ boot so I can't use my usb drives. :( :confused: 

I've tried a [COLOR="Blue"]xubuntu live[/COLOR] disk from the dec 06 APC mag and it recognized my usb's but it froze trying to install :confused:

---

### Post by ender42 on 2007-03-20
So, have you got any flavor of debian (or linux for that matter) running on your box?

What does lshw show?

Do you have the text of this failure you've gotten from Warty?  I'm assuming you tried Dapper or Edgy....

---

### Post by ender42 on 2007-09-24
So, it looks like a solution for Dapper is to do this:

root@machine:~ # modprobe usbcore
root@machine:~ # modprobe usb_storage
root@machine:~ # modprobe ohci_hcd
root@machine:~ # modprobe uhci_hcd <- allows to mount w/o specifying filesystem type (it appears)
root@machine:~ # modprobe usbhid <- not needed
root@machine:~ # modprobe ehci_hcd <- not needed / alleged to be a factor preventing automount
root@machine:~ # modprobe ohci1394 <- not needed

I ran an lsmod in Warty (from the live CD solution I was using earlier), then did a comparision lsmod in Dapper, and then added willy-nilly some things which looked like they might be relevant. 

I can mount it on a mount point, even if it doesn't automount... and it may automount on boot, but I've not tried that yet.

If Warty hadn't automatically detected it, and put in the correct modules, there's no way I would've been able to figure this out on my own.  If anyone knows how to go about figuring out which modules to use, that'd be helpful information to add.  Now, as to why Dapper can't do this.... well, you've got me :D

According to my notes for fixing my ethernet card via a similiar procedure, I'll need to edit /etc/modules in order to get USB working from bootup - of course my notes don't mention specifically how to do that, but I've got some places to go looking for that.

---

### Post by ender42 on 2007-09-25
root@machine: ~$ apt-get install hotplug
Reading package lists... Done
Building dependency tree... Done
Package hotplug is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  udev module-init-tools
E: Package hotplug has no installation candidate

So yeah, hotplug is apparently no longer in existence.

I had something working, when I mounted my card reader last night, it added an icon to my desktop.  Not ideal, but workable.

Had to reboot because my machine locked up (screensaver?), or course I hadn't finalized the module selection that got my USB hardware recognized.  So had to re-put those in after rebooting (several times).  Put in all but the one that was suggested not to, in order to get automounting.  It appears I don't need all of them, but even after trying adding all of them, mounting the drive doesn't give me an icon.  Bummer.

Looking around the net, finding some things to try - but some of that information is outdated, as there is no hotplug subsystem anymore....  Maybe it's been replaced by HAL?

---

