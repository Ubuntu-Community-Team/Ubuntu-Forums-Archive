---
title: "Slow USB transfer on 8.04"
date: 2008-05-14
forum: Hardware
---

### Post by speakeasy on 2008-05-14
I've noticed since I recently upgraded to 8.04 that my USB transfer speed has severely dissipated. It doesn't matter what device (2 external HD, Flash Drives, and an external CD Drive seems to write a little slower) I'm only getting between 4MB/s and 8MB/s when I was previously getting 20 close to 30!!!  And it's starts at around 8MB/s then by the end of the file its down to 4MB/s. Is there anything I can do?

---

### Post by hermes0710 on 2008-05-14
Does this happen whatever the size of the file is?

---

### Post by speakeasy on 2008-05-18
the bigger the file the worse the speed (4-5), but even smaller files only get up to around 10... 10.6 was the highest...

---

### Post by _x_MaD_x_ on 2008-07-03
I've the same problem in my laptop but I know people with the same Ubuntu and the USB works fine...
It is a bug a driver problem???

---

### Post by grss1982 on 2008-07-16
A Gud Day to everyone. :)

First and foremost I would like to apologize to the mods for bumping this thread. :)

With that out of the way I wanted to report here that I'm also encountering the same problem as the author of this thread.

Like the author my USB transfer speed has been slow no matter the device.  I'm actually getting speeds of when I start copying the file 5.3MB/S and slowly drops to 3MB/S.

BTW my motherboard is an K9N Neo-F V3(MS-7369): [http://www.msicomputer.com/product/p_spec.asp?model=K9N_Neo-F_V3](http://www.msicomputer.com/product/p_spec.asp?model=K9N_Neo-F_V3)

It has the Nforce 560 Chipset.

FULL Specs:

A64 x2 4000+
2gb ddr533
256MB Geforce 7300GT (PCI-E)
K9N Neo-F V3(MS-7369)
80GB Western Digital SATA HDD

---

### Post by grss1982 on 2008-07-18
BTW, here is my lspci output:
```

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

```

As everyone can see every device is detected. No "Unknown Device" is shown. :)

---

### Post by merlin051 on 2008-07-22
I am also having this problem, the larger the file the worse it gets, speeds  drop slower than 3.3mbs.

The devices I'm using are 

Buffalo 8gb USB 2.0
Lexar 2gb USB 2.0
unbranded USB2.0 SDHC reader/writer with class 4 8GB card
Sandisk USB 2.0 SD reader/writer 2gb SD card

All of the above hardware works flawlessly in windows XP on my laptop, it seems its something in 8.04 that's messing things up.

Copying a 700mb file, i might aswell not bother as its faster to burn it onto a cd!

Any solution to this?

---

### Post by detroit/zero on 2008-07-23
I've just noticed the same problem as of late. I'm getting speeds of around 3 or 3.5 Mb/s for USB transfers. Transferring a 3.5GB .avi movie file to my external drive came in at just under 10 solid minutes. A week or two ago it wouldn't have taken more than 3 or 5 tops.

lspci:
```
zero@zero-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```lsusb with all my USB devices attached:
```
zero@zero-laptop:~$ lsusb
Bus 005 Device 008: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 005 Device 007: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 005 Device 006: ID 4971:ce03  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```Well, that turned out funny. The SanDisk Cruzer Micro 4GB is actually a [1GB U3 drive]("http://www.sandisk.com/Products/Item%281919%29-SDCZ6-1024-A11-SanDisk_Cruzer_Micro_1GB_Black.aspx"). The Kingston 1GB drive is actually a 2GB drive that says GFM on it, but that could be made by anybody. The unidentified drive at Bus 005/Device 006 is actually a [320GB SimpleTech external hard disk]("http://www.simpletech.com/parts/spu35320.htm"). I also have a 256MB SanDisk MMC card from a digital camera that doesn't show up in the list at all. (I thought those counted as USB memory.. I guess not.)

Anywho.. As I said, I've only noticed this for about the last week or two. It's definitely not something that came about with my switch to Hardy from Gutsy; I did a clean install of Hardy.

Hope someone comes up with some answers.. spending 45 minutes to move 10GB worth of files around is a real pain.

_**EDIT:**_As soon as I finished writing that, I copied a few more files over to my 320GB drive - close to 3.5GB worth of files. The transfer started out at just shy of 20MB/s (the fastest I've seen it go in a while) and an ETA of 3 minutes. It's now close to five minutes later, the transfer speed is down to 7.7MB/s (and dropping steadily) with the same ETA of 3 minutes shown. In the time it took me to write that last sentence, I'm down to 6.7MB/s.

(I should also add that even though the 320GB SimpleTech drive doesn't identify, I've used it across three versions of Ubuntu - Feisty, Gutsy, and now Hardy - and it's always worked flawlessly. It also works under Vista and XP installs I have on other machines.)

---

### Post by detroit/zero on 2008-07-23
I just did a little experiment.

I took a (close to) 1GB .avi file from my external 320GB drive. I checked the read/write times for both cut/paste and copy/paste to and from all my USB devices.

Obviously the difference between cut and copy is rather negligible, but the difference between read and write times for all my devices is significant.

To cut the file from my drive and write it to my desktop took under one minute. The transfer started out at the slow, 8 or so mb/s speed and worked its way up to 18 or so by the time it finished. To write it back to the drive had the same advertised 1 minute ETA, but took around 2.5 to 3 minutes to complete.

The read/write discrepancies are similar for my 1 & 2GB thumb drives, too. They move even slower than the hard disk, but the write time is much longer than the read times.

I'm not sure what that means, but I'm sure it means something.

---

### Post by Roostey on 2008-07-24
I'm not sure if it's the same problem as I've been having, since some of you appear to have only just started experiencing it, but I've had slow USB and network since I installed Hardy, ie. months.

The exact symptoms were this: copy files to or from any USB device and it would start off at normal speed then fall to around 2MB/s, with large files being affected worse.  If I let a slow file copy continue for a very long time then my GUI would become laggy.  Cancelling a slow copy, then restarting it would often see the new instance start off at full speed before slowly falling back to 2MB/s again.

Today, I finally found a solution that works for me, I added "pci=routeirq" to my boot options in grub and got both working again at full speed.  If you've got the same symptoms, then the following might help.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Now edit the boot options

```
gksudo gedit /boot/grub/menu.lst
```

Search for "kopt=" (without quotes).  It should look something like this

```
# kopt=root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro
```

Now, put a space at the end and add "pci=routeirq" at the end, so it looks like this

```
# kopt=root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro pci=routeirq
```

That sets the default options, so that when you upgrade your kernel the fix gets copied, otherwise it will revert.

Next, change the options on your current kernel, search for

```
End Default Options
```

Following this will be the boot options for the currently installed kernels.  I added the option to the end of each of my current kernels, but I left alone the recovery ones, just in case.

Before

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic
```

After adding "pci=routeirq" to the non recovery options (first and third entries)

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro quiet splash pci=routeirq
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro quiet splash pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=efd264eb-0f54-4d58-953a-d89a85a696e4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

```

Reboot, and hopefully you'll have USB working again.  If it causes problems, then you can restore the old menu.lst with

```
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

[Here]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762") is the bug report.

---

### Post by danwood76 on 2008-07-24
This is a known gvfs (possibly) bug:
[https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)

I just did a test using cp and gvfs-copy on a 1GB file to a flash card I had laying around and the results were:
```

cp: 6m47.729s (2.34 MB/s avg)
gvfs-copy: 14m50.654s (1 MB/s avg)

```
This obviously points to a gvfs bug as cp was so much faster than gvfs, the bug has been triaged upstream so we will have to wish for a backport to fix the issue.

A few posts opn that bug report point at non intel chipsets, my laptop (which I did these tests on) is an ATI chipset so this may be true.
I will have to test when I get home to my intel desktop.

---

### Post by danwood76 on 2008-07-24
Ok I just tried the pci=routeirq thing mentioned above and it has sped things up somewhat.

gvfs-copy now transfers the file in 7m31s which has halved the time but is still not as good as standard cp.

---

### Post by detroit/zero on 2008-07-24
I made the pci=routeirq changes to the boot options and did notice an increase in file transfer time, but it still hovers below 20MB/s.

I noticed a kernel update that came through today includes the pci=routeirq option in the kernel boot string. Maybe somebody noticed the problem, or the routeirq has other applications unrelated to this problem?

---

### Post by danwood76 on 2008-07-24
20MB/s is still good for USB and fast.
You will only see a maximum of around 30MB/s to USB hard disks and less to flash drives.

---

### Post by detroit/zero on 2008-07-24
> **danwood76 said:**
> You will only see a maximum of around 30MB/s to USB hard disks and less to flash drives.
Right, right.. I guess I should have explained a little better. That "(close to) 20MB/s" was actually around 17 or 17.5, and that was to a USB external hard disk, not a flash drive. The speed did vary while the copy was in progess, dipping as low as 12MB/s and hitting as high as 18.6MB/s that I noticed.

It's better than it was, yes. But it's still not as good as it could (should) be.

---

### Post by merlin051 on 2008-07-24
pci=routeirq has sped things up for me a ton, its still not as fast as i think it is in windows, but damn better!

thanks alot, many thanks!!

---

### Post by grss1982 on 2008-07-24
> **Roostey said:**
> I'm not sure if it's the same problem as I've been having, since some of you appear to have only just started experiencing it, but I've had slow USB and network since I installed Hardy, ie. months.

The exact symptoms were this: copy files to or from any USB device and it would start off at normal speed then fall to around 2MB/s, with large files being affected worse.  If I let a slow file copy continue for a very long time then my GUI would become laggy.  Cancelling a slow copy, then restarting it would often see the new instance start off at full speed before slowly falling back to 2MB/s again.

Today, I finally found a solution that works for me, I added "pci=routeirq" to my boot options in grub and got both working again at full speed.  If you've got the same symptoms, then the following might help.


WOW!!! =D>

It REALLY WORKED!!! :p

From my previous 5.3MB/S that slowly drops to 3MB/S speed a few days back, I'm now getting between 16MB/S to 17MB/S.

Thanks a MILLION **Roostey.**

YOU ROCK!!! :guitar:

---

### Post by detroit/zero on 2008-07-29
Well, it *was* working:

[IMG]http://img390.imageshack.us/img390/5733/screenshotfileoperationaj6.png[/IMG]

Wonder what went wrong.

---

### Post by merlin051 on 2008-07-31
just tried xfering about 1gb in BT3(slax based live distro) and i was getting 27mb xfer speeds with the same hardware that ubuntu is giving me 9 max then dropping to 3mb(better than 300k like it used to before this tweak)

So this problem (for me) is still very much at large

---

### Post by detroit/zero on 2008-07-31
> **merlin051 said:**
> So this problem (for me) is still very much at large

I second that motion. That 49 minute transfer I pictured above actually ended up taking close to an hour and a half, and gave me an average speed of around 750K/sec.

What gives?

---

### Post by merlin051 on 2008-07-31
It seems that although the xfer speed might be XXmbps it doesnt make a difference if the xfer keeps pausing for a while, then xfering a blast of data, then paused again.

This is starting to bug the hell out of me, dealing with portable media for large files has become a headache its come to the stage I'd rather boot into something else to xfer the files.

---

### Post by detroit/zero on 2008-08-01
I'm not sure if it's related or not, but my MMC card reader is acting goofy. I just pulled a memory card out of my digital camera and tried moving pictures off of it and onto my computer. I can copy & paste from it, but it won't let me cut&paste or just delete files. Subsequent investigation shows my memory card has somehow been switched to user:root and group:root, with read-only access to myself and my usergroup. When I sudo nautilus, I still don't have write permissions. I can't change permissions either from the Properties>Permissions dialog, or from terminal using chown. Even using gparted, the system shows up as a read only filesystem. 

I checked to make sure the physical device lock wasn't activated, and I can take pictures, delete pictures, and do whatever else I want while the card is in the camera.

Weird, weird stuff.

_**EDIT:**_ I used the camera itself to re-format the card. Everything is cool, now. I don't know how my root account (and I) lost my write privileges, but it's restored.

---

### Post by Potted Meat on 2008-08-01
I am experiencing the same slow transfer rates both with USB and from partition to partition.

My USB plugs away at a few MB / sec as does the HD transfers.

I copied several GBs between partitions last night and averaged around 2-3 MB / sec.  That's definitely not right.  The drive is a 60MB SATA2 in a year-old laptop.


Any help appreciated.

PM

---

### Post by ohgodnotanother1 on 2008-08-19
Hello everyone. I encountered the same problems as described above, so I decided to sign up and report it here - I hope it's the right place.

Recently transferring a 1,4 GB file from my notebook to my USB 2GB pen drive slows down from around 30 MB/s to 3 MB/s. It looks like the writing always stops for a small time and continues again ... and so fort.

Executing the "lsusb" and "lspci" commands gives me the following results:

```
# lsusb
...
Bus 004 Device 012: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB Flash Drive
...
```

```
# lspci
...
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
...
```

The "/var/log/messages" file contains nothing except some line with "-- MARK --" at the end.
I didn't yet try the boot kernel parameter, but having read the previous posts I seriously doubt that it will result in any success.

I found a bug report related to "gvfs" on launchpad.net:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762")

But this doesn't seem to affect me as there is no "gvfs" or related copy commands available on my system.

Any chance that this will get solved soon? It is a huge pain in the ****!:(

---

### Post by danwood76 on 2008-08-20
It is a problem with gvfs.
In Intrepid Ibex Alpha 4 the problem doesnt seem to be there so with a bit of luck they will provide a backport for everyone looking to stay on Hardy Heron.

---

### Post by detroit/zero on 2008-08-20
When copying files to my USB devices, I've gotten in the habit of booting off the live CD and doing it from there. Even with all the extra RAM & CPU usage that goes with running off the CD, my transfers run at over 20MB/s and take far, far, far less time than they do from inside my install.

Here's a thought: Is it possible to use synaptic to install the gvfs package from the CD? A sort of time-machine to take it back to before it got this catastrophically deranged update? What about SVN or something?

---

### Post by ohgodnotanother1 on 2008-08-20
I am not sure that this is a gvfs issue. Actually I have no gvfs or whatsoever packet installed on my linux system.

Some more details I can provide:

```
# sudo lsusb -D /proc/bus/usb/004/013
Device: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB Flash Drive
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x13fe Kingston Technology Company Inc.
  idProduct          0x1d00 DataTraveler 2.0 1GB Flash Drive
  bcdDevice            1.00
  iManufacturer           1 USB     
  iProduct                2 Flash Disk      
  iSerial                 3 9076030004AD
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

**EDIT: I was able to get new insights when testing the copy operation to a 250 GB external 3.5" HD. The 1.4 GB file took under 1 minute to transfer to the external HD. So for me it must be an issue related to the USB stick. I'll try to defragment or check the filesystem on it and report back later with the results of that.**

[b]EDIT #2: Using chkdsk on the USB stick under windows didn't show any problems. I tried the stick again and it looks like there has been an improvement in speed, though it is still slower than it should be (waited 2 minutes for 50% of the file, beforehand it only transferred 20% in 2 minutes). However trying the same copy procedure with the USB stick under Windows 2000 yielded a similar slow speed.

Here is some additional information about the external 3.5" HD that has the proper speed when copying data to it:[/b]
```
Device: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x6830 USB-2.0 IDE Adapter
  bcdDevice            0.01
  iManufacturer          56 Cypress Semiconductor
  iProduct               78 USB2.0 Storage Device
  iSerial               100 DEF10B5C5335
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
```

---

### Post by fugative on 2008-08-20
OK guys hate to be a party pooper but i've had a generally sluggish experience with hardy on my old zv5000 (yes i know its not a piece of A4 paper with the power of HAL) but it should be more sprightly than this. usb transfers drop to kbps even after the pci=routeirq tweak, yes it worked for the first time then dropped back again. The net is an opportunity to go for a pee while pages load (tried disabling ipv6, no joy) torrents peak at about 25 KiBs even with the population of China seeding.
I've been with Ubuntu since edgy but i'm going to give Mint another try, I only left it because of the new hardy release. 

think maybe canonical are rushing to keep up the 6 month promise. slow down guys get it right not quick as my wife always says.

please diss me i feel a little guilty, least i'm not going back to 'doze.

sorry also for bumping the thread but i always find the "starting a thread" button hard to find.

---

### Post by daleclarke on 2008-08-21
Just a update to a similiar problem I had with Firewire hard drive. I have Gparted it into a Ext3 and set the drive for my user name instead of Root and I now have a fully functioning HD with speeds of 20mb/s...

---

### Post by detroit/zero on 2008-09-01
Has anybody solved this problem?

I'm still plagued by ridiculously slow transfer speeds to my USB devices.

I started this [thread over here]("http://ubuntuforums.org/showthread.php?p=5705138") asking if it's possible to re-install the gvfs version that comes on the Hardy CD, but I haven't gotten any replies yet.

---

### Post by Hiperi0n on 2008-09-06
Hi. I have been having the same slow transfer speed problems on my external hard disks. I have been searching the web for solutions and I thought the cause could be a synchronous r/w. I mean, when my drives automatically mount, I can't manage to change their mount options, even in the volume tab of the properties of the device in Computer, and always mount as sync.

I have tried the pci=routeirq solution and works for me, but can it be because of that synchronous mode? I haven't been able to change it, even if I change the fstab options, in the volume tab always show the same mount options (even writing different options below). What do you think? Try using the async option in fstab.

---

### Post by detroit/zero on 2008-09-07
Possible explanation for slow transfers and definite fix here:_ [http://ubuntuforums.org/showthread.php?t=911052](http://ubuntuforums.org/showthread.php?t=911052)_[]("http://ubuntuforums.org/showthread.php?p=5743158#post5743158")

---

### Post by ohgodnotanother1 on 2008-09-09
Like I said before I don't think it is "gvfs" causing this phenomenon. I don't have it installed.

Neither do I have "nautlius" installed as I use xubuntu which comes with "thunar".

So it must be something else causing these symptoms.:(

EDIT: I tried to remove the ehci-hcd module from the kernel to see if I get similar problems when it had to fallback using the uhci-hcd (USB 1.x) module instead. Indeed the problem remained the same.

---

### Post by detroit/zero on 2008-09-09
Well, I've got some definite answers that lead to a million more questions.

I've been fighting this problem tooth and nail for over a week now. I've done multiple reinstalls of Hardy, Gutsy, Kubuntu Hardy,  Xubuntu Hardy **and** an upgrade to Intrepid Ibex - all of them end up with the same problem.

I'm running now on a less than 24-hour-old fresh install of Hardy Heron. Before I connected to my network and did all the requisite post-install updates, I went in through synaptic and locked my Nautilus and GVFS versions (and their dependencies). Even after the updates, I was cruising along with almost 30MB/s read speeds and write speeds that never dipped below 24.5MB/s. 

Not even one full day - and not one update - later, I'm back to my super slow (4.5MB/s max) USB file transfer speeds.

I thought I was on to something there.

I've been Googling for some time now and one thing I've found is that this problem isn't distro-specific and it's not dependant on any window manager. I've seen this problem reported in Debian, Ubuntu, Mint, Arch, and Suse forums (along with some generic Linux forums) and it's reported by people using GNOME, KDE, busybox, and XFCE.

A [Google.Linux]("http://www.google.com/linux") search of "[linux slow usb speeds]("http://www.google.com/linux?num=20&hl=en&safe=off&q=linux+slow+usb+speeds&btnG=Search")" or "[hardy slow usb speeds]("http://www.google.com/linux?num=20&hl=en&safe=off&q=hardy+slow+usb+speeds&btnG=Search")" will turn up page after page after page of people reporting the same problem.

From all my reading, the problem lies either in the kernel, a conflict between the ehci and uhci modules, synchronous/asynchronous auto-mount options, or as one user suggests, it's possibly [a hardware issue with a particular chipset]("http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17032.html").

I've got a lot of investigating to do to figure out where I fit into this grand scheme of things, along with what can be done about it, and I'm not the most knowledgable linux user in the world.

I guess that's where it stands now.

---

### Post by ohgodnotanother1 on 2008-09-15
I also think that this is something hardware related.

Like I mentioned before: I don't have this problem with my external 3.5" HDD. It's just my handy 2GB USB stick that's causing me headache.:(

It's a pain to use that HDD instead of the stick, because it needs an external power source (which means additional cabling). Maybe I buy a 2.5" HDD, but yet again I might run into the same trouble with that one.:mad:

Geez, I don't see anything we could do right now. ](*,)

---

### Post by euphemus on 2008-10-19
Roosty - thanks - I weep with joy. This fix worked - still a little clunky but at least it gets the file across! - my transfers got so slow they stalled half way and aborted the transfer - had to use mv/cp in console. Now lowest speed on 540MB file was 2.7MB/s - mainly higher. I suspect the clunkiness is down to hardware (don't ask). I found this problem started after an Ubuntu update - it was fine when I first installed hardy (I had no internet) and then I installed the updates... Thanks again.

---

### Post by euphemus on 2008-10-19
Correction - I am now getting +11MB/s speed in drop/drag copies - that is way fast for my old laptop. I think I launched Firefox in the background when testing it first time. Thanks again Roosty.

---

### Post by detroit/zero on 2008-10-19
Since the slow USB write problems aren't limited to Ubuntu, and seem to apply to various distros and kernel versions over the last few years, I started [a thread over at Linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")

Maybe the people who are having this problem can all get together and find a fix, rather than wait to see what trickles down from on high.

Come over there and chime in with your experiences with the slow USB write speeds.

---

### Post by arimakun on 2008-10-21
I discovered this thread because i was having slow burning speeds, reading this led me to discover also had slow usb transfers. Read this topic and other related and decided to reinstall my desktop pc.

the first thing I deactivated was the option relatime in /etc/fstab since is the first thing that came to my mind different in HArdy from gutsy and related to filesystem handling.

By the way maybe the problem is not writing to USB but READING since I noticed high CPU usages wile reading my internal HD for both burning and writing to USB devices, I'm aware is something related tu users space (or something like that i don't remember where i read that) and it is somehow normal, but these were insane, even hanging up the system, I wasn't even able to open a new tab in fire fox.

Up to now I had a clean system from reinstall with no relatime. Everything ok, fast burning (arround 30MiB/sec) and fast USB transfers.

The next thing I do normally when reinstalling a system is activating file indexing, in this case built-in tracker. And now for some tweaking: installing preload for faster boot and activated "sudo perl -i -pe 's/CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc" (for parallel init in dual core processors).

Let tracker index a little, got bored and decided to restart.
Until now no updates were installed

First thing next to reboot was burning another dvd of data and voilá, fast burning for a while and then dropping to 1-2x paired with high cpu usage. next USB transfer to external ntfs HD: same thing, slow transfer and high cpu usage.

So decided to deactivate indexing and uninstall preload, then reboot

now everything seemto be back to normal. fast burning and USb transfer with cpu between 60%-90%. have been runing like that for half a day.


now decided to look at my Laptop, never tested USB transfer speeds, gave it a try and yes... they were slow. started fast and then dropped and CPU went like crazy.

laptop is like 6 month old installation, with preload, concurrency=shell, relatime on, and beagle for indexing, all updates up today with latest kernel 2.6.24-21 and 2.6.24-21-rt (has ubuntu studio).

decided to uninstall beagle and preload (not very patient to uninstall-test one by one), rebooted and now speed is back! (arround 20 Mib/sec average) and normal CPU usage (60%-90%) with sporadic peaks (maybe due to the bunch of applications installed) but just for a second or two which seems reasonable to me.

So this is it. Will be looking how the system goes for a while, so give it a try:

- Uninstall indexing software
  or/and
- Remove preload if you have it
  or/and
- Deactivate relatime in /etc/fstab

additional note: already installed all updates up today in desktop PC and everything seems to be fine (in except for a "segmentation fault" running "sudo nautilus" but that is another unsolved mystery that seems to appear and disappear in seamless mysterious ways)

another note: the one who seems to be dragging more CPU is the ntfs fuse 3g driver (from "sudo top" command in terminal while copying files to USB-HDD).

---

### Post by detroit/zero on 2008-10-21
> **arimakun said:**
> So this is it. Will be looking how the system goes for a while, so give it a try:

- Uninstall indexing software
  or/and
- Remove preload if you have it
  or/and
- Deactivate relatime in /etc/fstab
Sounded promising, but removing the relatime option from fstab for devs sda5 and sda7 (root and home, respectively) made my system unbootable. Rather, I couldn't log in because it said my home dir did not exist; I made it as far as the GDM and had to go undo the change from terminal. I did turn off preload and removed all the tracker software, but that didn't change anything.

To look further at your post, though: I'm not sure about burning cd's or dvd's because I haven't done that for a while, but my read speeds from USB devices and my HDD are just fine - right around 30MB/s. 

I only have problems with the write cycle to USB devices and when transferring files between partitions. For example, I was in Nautilus one day getting set to move a bunch of files to my USB hard disk. After selecting all, I accidentally bumped my delete key and sent them from ~/Videos to the trash bin. I went into the trash, selected all, and was going to move them back to ~/Videos. My home directory is on its' own partition, and I had the same super-slow >5MB/s transfer rate.

Like you, though, I've never noticed this problem until after an update sometime last June. I've been using Ubuntu since the days of Edgy Eft, but in all my searches on this problem I've seen posts going back to 2004 across a dozen different distros. I've tried re-installing both Gutsy and Feisty, and they always degenerate to the same behavior (even though they didn't act like that when they were the current version). I thought it had something to do with the Kernel or some of the modules used (uhci, ehci, etc..) because this problem never occured until I picked up Kernel 2.6.24-19. I've tried re-compiling that kernel and using it, though, and that didn't work.

Popular opinion seems to state that changing mount options from synchronous to non-synchronous or asynchronous or whatever is the answer to the problem. I've yet to find a definitive answer or guide on how this is done.

I have a [post over at LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/") where I'm trying to find some answers, and some clown is trying to tell me that this is how USB is supposed to work on all operating systems - always has and always will. 

What a crock.

I'm debating doing a fresh re-install, and locking the versions of every installed package on the system to see if that does it. I hate this.

---

### Post by ACGarib on 2008-11-02
I have a similar problem. I can write to my external firewire drive pretty fast (10 to 14 MB/s), but copying files from my external Seagate drive (freeagent pro) is dreadfully slow. (not even 100 KB/s) There seems to be a threshold for normal speed. If the file is under 50 MB or so, it copies at normal speed, but over that, it takes forever. I could copy a 48 MB folder instantly, but a 53 MB folder would take 5 minutes. There are exceptions to these numbers, but there definitely seems to be a threshold.

It is also unstable. Copying files usually results in nautilus freezing, or if I use the cp command in the terminal, I get input/output errors a few minutes after it started.

Like other people mentioned, It starts out fast for the 1st second, then crawls along at a snails pace for most of the rest of the time. Every now and then, it will jump up to full speed for a second then immediately drop back down.

The instability eventually got so bad that I had to reformat. I chose FAT32 and it is a lot more stable now, but still just as slow.

The next day, intrepid came out, and the HDD is still slow as ever.

Switching to USB doesn't change anything.

EDIT: I forgot to mention, reading files from the external HDD is slow also. Nowhere near as slow as copying, but slow none the less. If I try to watch something like a DVD ISO or an HD trailer, I get stuttering and VLC or any other media player will freeze.

Hopefully this gets fixed soon.

---

### Post by detroit/zero on 2008-11-02
> **ACGarib said:**
> I have a similar problem. I can write to my external firewire drive pretty fast (10 to 14 MB/s), but copying files from my external Seagate drive (freeagent pro) is dreadfully slow. (not even 100 KB/s) There seems to be a threshold for normal speed. If the file is under 50 MB or so, it copies at normal speed, but over that, it takes forever. I could copy a 48 MB folder instantly, but a 53 MB folder would take 5 minutes. There are exceptions to these numbers, but there definitely seems to be a threshold.

It is also unstable. Copying files usually results in nautilus freezing, or if I use the cp command in the terminal, I get input/output errors a few minutes after it started.

Like other people mentioned, It starts out fast for the 1st second, then crawls along at a snails pace for most of the rest of the time. Every now and then, it will jump up to full speed for a second then immediately drop back down.

The instability eventually got so bad that I had to reformat. I chose FAT32 and it is a lot more stable now, but still just as slow.

The next day, intrepid came out, and the HDD is still slow as ever.

Switching to USB doesn't change anything.

EDIT: I forgot to mention, reading files from the external HDD is slow also. Nowhere near as slow as copying, but slow none the less. If I try to watch something like a DVD ISO or an HD trailer, I get stuttering and VLC or any other media player will freeze.

Hopefully this gets fixed soon.
I have "thresholds" on mine, too, but they're a little different than yours.

For single files, 700MB is the line. Even a 699.5MB .avi file will transfer at blazing fast speeds, completing in under 30 seconds. A 700.1MB .avi file will take right around six solid minutes from start to finish.

Folders - especially ones containing more than one item - always go as slow as possible, usually coming in under the 5MB/s mark. The more items in the folder, the slower it goes.

I think it's definitely tied to the kernel and the ehci module. Just a week or so ago , out of sheer frustration, I did a fresh re-install of Hardy Heron and had lightning-fast USB transfer speeds on files and folders of all sizes (topping 25MB/s) until I updated the kernel to the current version - 2.6.24-21.43

If I load Ubuntu into my old kernel from Grub, I still have those speeds.

---

### Post by Telecaster72 on 2008-11-12
I also have this exact problem, adding "pci=routeirq" didn´t help either.
I read your post at linuxquestions, what a thick douche you ran into ;-)
If i come up with anything i´ll post back in this thread!

---

### Post by detroit/zero on 2008-11-12
> **Telecaster72 said:**
> I also have this exact problem, adding "pci=routeirq" didn´t help either.
I read your post at linuxquestions, what a thick douche you ran into ;-)
If i come up with anything i´ll post back in this thread!
Yeah, that guy was something else. Even after I complained like two or three times, they gave me an infraction and locked my thread.

I haven't been back since.

---

### Post by chinchillart on 2008-11-13
> **detroit/zero said:**
> Yeah, that guy was something else. Even after I complained like two or three times, they gave me an infraction and locked my thread.

I haven't been back since.

Ciao Detroit! :)
I've read the complaints from Electrosomething...
I think he's not completely on the wrong side. USB still sucks. And the next standard, USB3.0, will suck without any doubt.

My experience is quite similar to yours: external USB HD are even faster on Windows than on ubuntu.

I've bought an USB external HD by Lacie (Desktop Media 750GB) this morning. I've done some testing. From Gnome Desktop write speed doesn't exceed 10 MB/sec, whereas read speed doens't exceed 18-20 MB/sec.

Tested with many large files like debian DVD iso.

But I don't get the speed dropping during read/write operations.

I'm using Hardy 8.04.1 32 bit.
I've improved a little USB read/write with some parameter in fstab:
```

#Entry for LaCiE 750GB
LABEL=SAM2 /media/SAM2 ext3 defaults,noauto,noatime,user,errors=remount-ro 0 0

```

My PC does have an NVIDIA chipset (560SLI or something), an AMD X2 and a NEC chipset USB PCI card.

I think there is some issue related to hardware: the speeds I claim refers to USB PCI card.

When I connect the LaCiE to the Motherboard USB port, read/write speeds are almost double. For example, when I copy a 4.3 GB iso on the LaCiE HD, write speed raises 28 MB/sec, then falls to 22-23 MB/sec, then raises to 25 MB/sec. 

lspci
```

rob@ubuntu:/media/DATA1$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:0a.0 USB Controller: NEC Corporation USB (rev 43)
02:0a.1 USB Controller: NEC Corporation USB (rev 43)
02:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

lsusb
```

rob@ubuntu:/media/DATA1$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05fe:3002 Chic Technology Corp. 
Bus 001 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 059f:1010 LaCie, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 059f:1019 LaCie, Ltd 
Bus 002 Device 001: ID 0000:0000  

```

If you have any question, feel free to ask! :KS

Rob

---

### Post by walpurgiss on 2008-11-19
Glad I found the threat without the idiocy of the linuxquestions forum I found last week :p

Hi, I don't use ubuntu, I use Fedora 9 with KDE4.
I've found that during USB transfers via drag & drop in dolphin, the transfer usually 'bursts' quick at first, 20-30MB/s, then pretty much chokes out.  It doesn't matter if it is a large file, or many small ones.  

Last time I tried to use my 8GB corsair stick and transfer about 2.5GB of files onto it, it took over 30 minutes.  Afterwards, the files I transferred were not on it, and it would only mount read only, in both windows and linux, so I had to reformat it.

On my system removable media are automounted by HAL, and for the USB disk it chooses these options:
```
Nov 19 13:17:58 HTPC-L ntfs-3g[13004]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096
Nov 19 13:17:58 HTPC-L hald: mounted /dev/sdc1 on behalf of uid 500

```

It is odd though, as I have six or seven USB hard disks that work fine, transfer fine; only the handful of USB flash sticks I've used have had problems.  Not sure if it is a KDE thing, kernel thing, uhci thing, or what.   Anyway I'm going to try some of the noatime nosync things, and see if I can come up with anything to help.  I have a laptop that is running the same fedora 9 x64 flavor as the desktop machine, but using KDE3 so maybe I can rule something out there.

Oh yeah.  The stalling transfers to the USB stick are not limited to drag & drop dolphin/kde operations, using cp & mv in console does it to, watched the change in free disk space from another terminal during transfers and saw long pauses between changes (>15sec in some cases)
Additionally, when the USB writes stall, it hangs up my KDE4 panels/desktop environment.  But only partly.  task switching still works and such, but shortcuts, the menu, clock, task manager, pager, etc are all unresponsive to mouse events.  Dunno if that info can help.

Anyway, good luck to me and all of you.  Hope this can be solved.

---

### Post by walpurgiss on 2008-11-19
```
Nov 19 13:53:33 HTPC-L ntfs-3g[13516]: Cmdline options: rw,noatime,nosync
Nov 19 13:53:33 HTPC-L ntfs-3g[13516]: Mount options: rw,nosync,silent,allow_other,nonempty,noatime,fsname=/dev/sdc1,blkdev,blksize=4096

```
Mounted with these options manually, transfers still started fast, then sharply dropped after 300MB or so.  The delays between transfers were much shortened.  Still had periods of no activity, but rather than some being 15sec or more, the most I noticed was maybe 3 sec.  Avg speed, including with skips was reported to be about 5MB/s after slowdowns started.  Still not a smooth transfer though, and still interfered with the response of my KDE4 panels.

Both machines dual-boot with windows XP sp2, and in windows there are no slowdowns in transfers, so I think that rules out faulty hardware/chipsets.  It does not rule out faulty OSS implementations of software interfacing with that hardware though. 

On the laptop, which is not KDE3, but gnome (hadn't used it in a while) the automount does not specify relatime or sync, and exhibits the same behavior as my KDE4 box when I did norelatime and nosync.  The transfer still has skips and halts, but they are breif, and the average transfer speed reported by gnome never drops below 5MB/sec.  Around 80% through though, the transfer failed, and I had a bunch of errors in /var/log/messages.  I'll copy/paste them into here in an edit from the other machine. 

Transferring 1GB on my KDE4 system takes about 4 minutes, on the Gnome system said about 3.5 minutes before it failed, and in windows XP in either system, less than 1 minute.  It seems like on the two linux systems, the first 300-400MB goes fast, as expected prior to the drop in throughput.  Copying off of the stick is also slowed down, maxed out at about 10MB/s in linux, and 35-50MB/s on Windows.

I don't think the ntfs-3g driver is to blame, as I have some internal NTFS drives in both the laptop (the windows partition) and in the desktop (same), to which read and write operations do not appear any slower than writing to the ext3 partitions.  It seems only USB is affected.

I don't have any problems with slow CD/DVD burning, though on maybe half of DVD burns with k3b on the desktop system, it fails to Flush the write cache, and gives burn failures (but the write is complete, and the discs work fine.)

Ok here's Edit:
> Nov 19 14:23:11 craptop kernel: usb 1-5: new high speed USB device using ehci_hcd and address 8
Nov 19 14:23:21 craptop kernel: usb 1-5: device not accepting address 8, error -110
Nov 19 14:23:21 craptop kernel: hub 1-0:1.0: unable to enumerate USB device on port 5
Nov 19 14:23:22 craptop kernel: usb 2-3: new full speed USB device using ohci_hcd and address 2
Nov 19 14:23:37 craptop kernel: usb 2-3: device descriptor read/64, error -110
Nov 19 14:23:38 craptop kernel: __ratelimit: 39977 callbacks suppressed
Nov 19 14:23:38 craptop kernel: Buffer I/O error on device sdb1, logical block 5
Nov 19 14:23:38 craptop ntfs-3g[3298]: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Nov 19 14:23:38 craptop ntfs-3g[3298]: Error reading $Mft record(s): Input/output error
Nov 19 14:23:38 craptop ntfs-3g[3298]: ntfs_mft_record_read failed: Input/output error

This is the tail of /var/log/messages after the transfer failed and nautilus's file transfer window told me it failed.
I could no longer access the mounted volume, so I unmounted it.  When I remounted it, I tail'd /var/log/messages again, and got this:
> Nov 19 14:25:51 craptop kernel: Buffer I/O error on device sdb1, logical block 1353629
Nov 19 14:25:52 craptop ntfs-3g[3856]: Error reading attribute value: Input/output error
Nov 19 14:25:52 craptop kernel: end_request: I/O error, dev sdb, sector 5019880
Nov 19 14:25:52 craptop kernel: Buffer I/O error on device sdb1, logical block 627481
Nov 19 14:25:52 craptop ntfs-3g[3856]: Error reading attribute value: Input/output error
Nov 19 14:25:52 craptop kernel: end_request: I/O error, dev sdb, sector 15486696
Nov 19 14:25:52 craptop kernel: Buffer I/O error on device sdb1, logical block 1935833
Nov 19 14:25:52 craptop ntfs-3g[3856]: Error reading attribute value: Input/output error
Nov 19 14:25:52 craptop kernel: end_request: I/O error, dev sdb, sector 8701008
Nov 19 14:25:52 craptop kernel: Buffer I/O error on device sdb1, logical block 1087622

Now while mounted, All the folders on the volume appear empty to nautilus, and some of the folder names are corrupted.  I'm going to boot back into windows and see if I can recover the files there, if I can't fsck the stick.

---

### Post by chinchillart on 2008-11-19
> **walpurgiss said:**
> Glad I found the threat without the idiocy of the linuxquestions forum I found last week :p

Hi, I don't use ubuntu, I use Fedora 9 with KDE4.
I've found that during USB transfers via drag & drop in dolphin, the transfer usually 'bursts' quick at first, 20-30MB/s, then pretty much chokes out.  It doesn't matter if it is a large file, or many small ones.  

Last time I tried to use my 8GB corsair stick and transfer about 2.5GB of files onto it, it took over 30 minutes.  Afterwards, the files I transferred were not on it, and it would only mount read only, in both windows and linux, so I had to reformat it.

On my system removable media are automounted by HAL, and for the USB disk it chooses these options:
```
Nov 19 13:17:58 HTPC-L ntfs-3g[13004]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096
Nov 19 13:17:58 HTPC-L hald: mounted /dev/sdc1 on behalf of uid 500

```

It is odd though, as I have six or seven USB hard disks that work fine, transfer fine; only the handful of USB flash sticks I've used have had problems.  Not sure if it is a KDE thing, kernel thing, uhci thing, or what.   Anyway I'm going to try some of the noatime nosync things, and see if I can come up with anything to help.  I have a laptop that is running the same fedora 9 x64 flavor as the desktop machine, but using KDE3 so maybe I can rule something out there.

Oh yeah.  The stalling transfers to the USB stick are not limited to drag & drop dolphin/kde operations, using cp & mv in console does it to, watched the change in free disk space from another terminal during transfers and saw long pauses between changes (>15sec in some cases)
Additionally, when the USB writes stall, it hangs up my KDE4 panels/desktop environment.  But only partly.  task switching still works and such, but shortcuts, the menu, clock, task manager, pager, etc are all unresponsive to mouse events.  Dunno if that info can help.

Anyway, good luck to me and all of you.  Hope this can be solved.

I see a ntfs-3g in your log. I'm wondering if it refers to your corsair stick. I'm not sure, but I've read somewhere that NTFS doesn't work fine with some kind of NAND flash. Have you try to format the stick in VFAT (fat32)?

---

### Post by walpurgiss on 2008-11-19
I'll try formatting it with vfat next.  I think windows wont want to let me do that since the volume is large, but I'll try there first, then with linux.

But that's a good idea.  I think I remember that NTFS is partially journaled, similar (but probably weaker) than ext3.  Definitely worth a shot.

Edit:
Ok formatted it fat32 in windowsXP.  It was the default option, surprisingly.  Took about 15-20 seconds.  Transfer speeds on windows remained fine, as expected.

Back on the KDE4 box, transfers still choke down to a maximum of 5MB/s after about 300MB of a transfer.  Tried with a 700MB video file, the 1GB dummy file, and about 500MB worth of pictures (small files), and it seems like 300MB is a threshold over which the transfers get rate limited ridiculously.

> Nov 19 15:16:16 HTPC-L kernel: sd 12:0:0:0: [sdc] Assuming drive cache: write through
Nov 19 15:16:16 HTPC-L kernel: sd 12:0:0:0: [sdc] 15728640 512-byte hardware sectors (8053 MB)
Nov 19 15:16:16 HTPC-L kernel: sd 12:0:0:0: [sdc] Write Protect is off
Nov 19 15:16:16 HTPC-L kernel: sd 12:0:0:0: [sdc] Assuming drive cache: write through
Nov 19 15:16:17 HTPC-L kernel: sdc: sdc1
Nov 19 15:16:17 HTPC-L kernel: sd 12:0:0:0: [sdc] Attached SCSI removable disk
Nov 19 15:16:17 HTPC-L kernel: sd 12:0:0:0: Attached scsi generic sg3 type 0
Nov 19 15:16:22 HTPC-L kernel: FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Nov 19 15:16:22 HTPC-L hald: mounted /dev/sdc1 on behalf of uid 500
Nov 19 15:16:23 HTPC-L gnome-keyring-daemon[3192]: adding removable location: volume_uuid_981F_DB9E at /media/SURVIVOR

mounted with options:
> /dev/sdc1 on /media/SURVIVOR type vfat (rw,nosuid,nodev,uhelper=hal,uid=500,codepage=437,iocharset=utf8)

Rules out NTFS-3G as problem, and probably rules out vfat.  Now I'm kind of worried about trying to plug in one of the USB hard drives though, since the laptop corrupted the memory stick.  Not hard to back up the pictures that were on that, but more hard to back up a hard disk worth of stuff to test with. :/

---

### Post by chinchillart on 2008-11-19
> **walpurgiss said:**
> I'll try formatting it with vfat next.  I think windows wont want to let me do that since the volume is large, but I'll try there first, then with linux.

But that's a good idea.  I think I remember that NTFS is partially journaled, similar (but probably weaker) than ext3.  Definitely worth a shot.

Well, maybe I'm not too much lucky, but a bunch of applications made me totally crazy using NTFS with ntfs-3g.

For example, Deluge and Transmission used to keep an entire CPU core at the highest usage during large file download (distro related DVD iso).

Talking about aMule: same problem. A lot of CPU usage.

When I've formatted the entire partition from ntfs to ext3, everything started working great (under linux).

ntfs is journaled only for the metadata and file descriptors. ext3 is completely journaled.

Finally, I've installed Ext2 IFS under XP, to share common partitions between the two OS. It works also with ext3, but without journaling support.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Hope this will help.

---

### Post by walpurgiss on 2008-12-15
Still no joy :/ It's faster for me to plug in my USB hard disks to windows and use FTP to transfer files over wifi, than to copy over USB.  Something is broken and I don't know what.  I am going to try a fresh live ubuntu CD or FC10 and see if it still occurs.

---

### Post by dr. detroit on 2008-12-15
> **walpurgiss said:**
> Still no joy :/ It's faster for me to plug in my USB hard disks to windows and use FTP to transfer files over wifi, than to copy over USB.  Something is broken and I don't know what.  I am going to try a fresh live ubuntu CD or FC10 and see if it still occurs.

It's way faster to drop in the Hardy CD and copy files that way - even including the time it takes to shut down, reboot into the live session, copy the files, and reboot into your normal system. That's a pretty creative solution you've found, using FTP. Maybe I'll try something like that with SSH and my wife's XP laptop.

I haven't bothered downloading or trying Intrepid Ibex yet, but I suspect you'll find an Intrepid CD to show the same problems as you already have. (Intrepid comes with kernel 2.6.27 if I'm not mistaken.)

Something's definitely broken in the kernel and it only effects certain chipsets or motherboards, otherwise this problem would be more widely reported and something would be getting done about it faster.

I just had kernel update 2.6.24-22 come through last week some time, and I went from an 8-12MB/s average to a 2-5MB/s average. The problems becoming more pronounced with each update.

I'm on the verge of doing another re-install of Hardy and locking everything kernel-related to 2.6.24-16. I know from past experience that a fresh install of 8.04 doesn't exhibit these problems, but once you start updating the kernel you're screwed and the damage can't be reversed. The problem obviously lies in the kernel (and/or headers/modules) itself, or drivers for a certain chipset/motherboard.

---

### Post by hunter186 on 2008-12-23
I've been having the same problem for months now.  As others have mentioned, it seems to be limited to flash memory.  Within minutes of a large file transfer, speed drops to less than 1 MB/sec.  This happens on thumb drives, my Cowon D2 MP3 player, and SD cards in the built-in card reader.

---

### Post by detroit/zero on 2008-12-24
> **hunter186 said:**
> I've been having the same problem for months now.  As others have mentioned, it seems to be limited to flash memory.  Within minutes of a large file transfer, speed drops to less than 1 MB/sec.  This happens on thumb drives, my Cowon D2 MP3 player, and SD cards in the built-in card reader.
It's not just flash memory. I use almost exclusively an [external 320GB HDD]("http://www.simpletech.com/parts/spu35320.htm") and I've been screaming about this problem since june or july.

---

### Post by nicolas314 on 2008-12-24
Same here, though I would like to detail a bit:

I have two external hard drives, same capacity: one is running fine with speeds up to 20MB/s, the other one peaks at 3MB/s and performance drops dead after a short while. Also two USB thumb drives: 2GB capacity and 8GB. The former runs with 20MB/s, the latter goes 2-3MB/s. All these devices run fine with max speed under the other OS. I have also noticed filesystem errors with the 8GB USB key. I systematically include MD5 sums with all large files and I occasionally get errors. Never so with the 2GB key.

It does not seem to be related to mount options or a device driver mismatch. Also not related to filesystem: I see the same with vfat, ntfs and xfs.

It was noticeable but manageable with Ubuntu 8.04, it has become a real pain in 8.10. Searching the Net for solutions brought me here, there is little about that in other forums.

---

### Post by Hated On Mostly on 2009-01-12
The problem appears to be a linux kernel problem because other distributions face this same problem. This bug really needs to be fixed, but nobody seems to know how to contact the "USB guys" of the linux kernel team. Also it appears posting of this bug on multiple bugzillas for distributions goes ignored as well for years. Sad that multiple operating systems which are supposed to be high quality and superior cannot handle safe transferring of files over USB 2.0. Especially since this bug has been around since 2004/2005 if you do a search for "slow usb" with various distributions like Mandriva, Ubuntu, Opensuse, Debian, etc.


Try this solution that I got from people having the same problem on opensuse. It worked for me using Ubuntu v8.10 Intrepid Ibex.

1 - create a document named "95-storage-nosync.fdi" (without quotes) in the folder "/usr/share/hal/fdi/policy/20thirdparty/"

```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/95-storage-nosync.fdi
```

2 - copy and paste the following into the document:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- disable sync for mount -->
<deviceinfo version="0.2">
<device>
<match key="block.is_volume" bool="true">
<match key="volume.fsusage" string="filesystem">
<match key="@info.parent:storage.bus" string="usb">
<merge key="volume.policy.mount_option.sync" type="bool">false</merge>
</match>
</match>
</match>
</device>
</deviceinfo>
```

3 - save the file and reboot

References:

[https://bugzilla.novell.com/show_bug.cgi?id=105871](https://bugzilla.novell.com/show_bug.cgi?id=105871)
[https://bugzilla.novell.com/show_bug.cgi?id=105871#c50](https://bugzilla.novell.com/show_bug.cgi?id=105871#c50)
[https://bugzilla.novell.com/show_bug.cgi?id=105871#c113](https://bugzilla.novell.com/show_bug.cgi?id=105871#c113)
[https://bugzilla.novell.com/show_bug.cgi?id=105871#c41](https://bugzilla.novell.com/show_bug.cgi?id=105871#c41)
[http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2006-10/msg00456.html](http://linux.derkeiler.com/Newsgroups/alt.os.linux.suse/2006-10/msg00456.html)

---

### Post by Hated On Mostly on 2009-01-12
Has anybody tried installing Ubuntu v8.04.1 Hardy Heron with no updates and doing transfers? When I ran the live CD my USB devices showed up as USB 2.0 and transferred files with no problems. I am wondering if a full install of 8.04.1 and never updating the kernel would solve this problem without any of these patches. I wouldn't have a problem going back to 8.04.1 if I knew this problem would not show up in the future as long as I don't update the system.

---

### Post by bsmith1051 on 2009-01-14
> **Hated On Mostly said:**
> Has anybody tried installing Ubuntu v8.04.1 Hardy Heron with no updates and doing transfers? When I ran the live CD my USB devices showed up as USB 2.0 and transferred files with no problems.
Better yet, do you have a spare hard-drive?  If so, do a regular install of 8.04.1 with no Internet connection.  Test and confirm the proper operation.  Be sure to do a long transfer of a big file, in case it's initializing the flash drive ok but can't sustain it.  Then plug-in the Internet cable and upgrade.  Repeat the test.  If you can demonstrate that the change in kernels causes the problem, then the developers can look at what changes were including between those kernel versions.

To check the exact kernel in-use,
```
> uname -a
```

---

### Post by Hated On Mostly on 2009-01-16
Notice in Ubuntu v8.04.1 Hardy Heron the drive properties show USB 2.0 at 480 Mbps.

In Ubuntu v8.10 Intrepid Ibex the drive properties just shows USB.

Kernel version is 2.6.24-19 on the Live CD for 8.04.1

Kernel version is 2.6.27-11 in my currently running 8.10 system.

---

### Post by Hated On Mostly on 2009-01-16
USB file transfers are more stable and consistent using the Live CD (8.04.1) then with Intrepid even with the patch I posted in place. The Intrepid transfers will finish without error, but the Live CD speed stays the same through the whole transfer and never pauses.

I don't want to have to do a full re-install, but unless linux kernel 2.6.28 solves this problem I probably will go back to 8.04.1 and just update Nautilus and other components to the Intrepid versions and keep it like that until someone decides to actually care about this critical bug.

If there was a BSD distribution with easy-to-setup whole disk encryption I would just switch to a BSD OS.


Bunch of links referring to this linux problem:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/88746](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/88746)
[https://bugs.launchpad.net/ubuntu/+bug/177235](https://bugs.launchpad.net/ubuntu/+bug/177235)
[http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=7054](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=7054)
[https://bugs.launchpad.net/gvfs/+bug/197762](https://bugs.launchpad.net/gvfs/+bug/197762)
[http://www.linuxforums.org/forum/suse-linux-help/61311-painfully-slow-write-speeds-usb-card-reader.html](http://www.linuxforums.org/forum/suse-linux-help/61311-painfully-slow-write-speeds-usb-card-reader.html)
[http://www.slawek.com/news/article/alt.os.linux.suse/293149](http://www.slawek.com/news/article/alt.os.linux.suse/293149)
[http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/](http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/)
[http://forums.debian.net/viewtopic.php?t=34127&highlight=&sid=c8d51037100978f5f4bef6d4adbe1722](http://forums.debian.net/viewtopic.php?t=34127&highlight=&sid=c8d51037100978f5f4bef6d4adbe1722)
[http://osdir.com/ml/user-groups.linux.vlug/2005-01/msg00515.html](http://osdir.com/ml/user-groups.linux.vlug/2005-01/msg00515.html)
[http://kerneltrap.org/node/6933](http://kerneltrap.org/node/6933)

---

### Post by nicolas314 on 2009-01-18
The bug reported on Launchpad is getting a longer list of "me too" every day, but apparently it has not been reported upstream. I tried sending an e-mail to the Linux USB guys directly but get an automatic answer back telling me to go play on a newbie web site.

I guess our only hope will be to identify a working kernel and stick to it until somebody reports it has been corrected. So anyone with a confirmed working kernel that can be worked out on Intrepid?

---

### Post by danwood76 on 2009-01-18
After reading many of the bugs associated with this I think its quite clear that the bug is caused by the filesystems as opposed to the actual USB side of things.
(or possibly a combinatiuon of the two)

In one of the debian bugs it was proven that, at least on the fat32 filesystem, that it was to do with the way hal mount the filesystems with the sync option where they used to be mounted async.
The difefrence in the two is basically that in sync mode the data gets written at that time and that is where the communication breaks down whereas in async it will be written later.
I think Ubuntu Intrepid uses the flush type of mounting which is better but still not that great with large file transfers.

The bug is being tackled but these things can take some time if the right parties aren't enthusiastic about it.
Im sure any fix will get backported if and when it becomes available.

Certainly writing 'me too' on a bug report makes the bug un-readable and less likely that it will get fixed sooner as you have to trawl through the useless posts to find the useful infos.

---

### Post by nicolas314 on 2009-01-18
> After reading many of the bugs associated with this I think its quite clear that the bug is caused by the filesystems as opposed to the actual USB side of things. (or possibly a combinatiuon of the two)

I re-formatted a USB thumb drive (8Gb) under ext3, FAT32, and xfs and observed the same behaviour in all cases. Several people have suggested various mount options, to no avail. Besides, the same bug has been reported at least on Fedora and SuSE. This does not suggest an Ubuntu-specific bug or bad default mount options.

You may want to elaborate about what leads you to think it is filesystem-related?

---

### Post by chinchillart on 2009-01-19
> **nicolas314 said:**
> The bug reported on Launchpad is getting a longer list of "me too" every day, but apparently it has not been reported upstream.[B] I tried sending an e-mail to the Linux USB guys directly but get an automatic answer back telling me to go play on a newbie web site.
[/B]
I guess our only hope will be to identify a working kernel and stick to it until somebody reports it has been corrected. So anyone with a confirmed working kernel that can be worked out on Intrepid?

This is very interesting...
They simply don't care..

---

### Post by danwood76 on 2009-01-19
Its not that they don't care its that they can't be bothered answer every email they get from a newbie so they have a default response to send out.
They probably get hundereds of emails a day about various bugs, the only way they get noticed is through bug reporting.

The problem with this bug is that the many bug reports out there are full of useless newbie 'me too' support posts, some of them being quite rude about the effort these people go to.
Bug reports are not support threads they are places where information can be found relating to the bug so that someone can fix it!

It is a community project after all, you cant just expect someone to spend hours and hours debugging thousands of lines of code.

Just be patient, like all things in the open source realm it will be fixed eventually if you just wait. (a lot of attempts to fix this have already bneen made at it by the various GNU/Linux distributions out there)
Unless of course you are a linux developer then I suggest you get cracking on it and fix it!

---

### Post by chinchillart on 2009-01-19
> **danwood76 said:**
> Its not that they don't care its that they can't be bothered answer every email they get from a newbie so they have a default response to send out.
They probably get hundereds of emails a day about various bugs, the only way they get noticed is through bug reporting.

The problem with this bug is that the many bug reports out there are full of useless newbie 'me too' support posts, some of them being quite rude about the effort these people go to.
Bug reports are not support threads they are places where information can be found relating to the bug so that someone can fix it!

It is a community project after all, you cant just expect someone to spend hours and hours debugging thousands of lines of code.

Just be patient, like all things in the open source realm it will be fixed eventually if you just wait. (a lot of attempts to fix this have already bneen made at it by the various GNU/Linux distributions out there)
Unless of course you are a linux developer then I suggest you get cracking on it and fix it!

You're right.
I'm sorry.. Too fast to judge..

Rob

---

### Post by unimatrix on 2009-01-19
Hi guys. I'm having the same problem with my 1TB WD external drive on my Ubuntu 8.04 server (that means no gvfs or anything). It's just slow as hell:
```

# hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:     2 MB in  2.25 seconds = 910.37 kB/sec
 Timing buffered disk reads:    4 MB in  4.63 seconds = 884.11 kB/sec

```

It literally takes like a WEEK to copy all the crap to it.

Anyway, I've just stumbled upon this:
[http://www.linuxquestions.org/questions/linux-hardware-18/ext3-usb-hd-slow-transfer-rates-ubuntumanual-mount-646506/](http://www.linuxquestions.org/questions/linux-hardware-18/ext3-usb-hd-slow-transfer-rates-ubuntumanual-mount-646506/)
This guy fixed the problem by using the noapic option. Has anyone tried it here?

EDIT: Just tested both "noapic" and "pci=routeirq". Nothing worked :(

---

### Post by danwood76 on 2009-01-19
To back up my idea about the filesystem mount options I mounted my disk using the flush and sync options.
Then used a timed DD to check transfer speeds of a 1GB zero file, results are below:

1GB Flush:
```

danny@danny-desktop:/proc$ cat mounts | grep /dev/sdf3
/dev/sdf3 /media/disk-1 vfat rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush 0 0

danny@danny-desktop:~$ time dd if=/dev/zero of=/media/disk-1/1GiB_file bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 37.2782 s, 28.8 MB/s

real	0m37.282s
user	0m0.004s
sys	0m2.716s

```
1GB Sync:
```

danny@danny-desktop:/proc$ cat mounts | grep /dev/sdf3
/dev/sdf3 /media/disk-1 vfat rw,sync,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 0 0

danny@danny-desktop:~$ time dd if=/dev/zero of=/media/disk-1/1GiB_file bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 98.6891 s, 10.9 MB/s

real	1m38.694s
user	0m0.008s
sys	0m4.856s

```

When using the flush option the USB disk is 3x faster.
Im not sure if the flush option is available in Ubuntu Hardy but it is in Intrepid.
By default in Hardy I think they are mounted sync.

The default hal mount options can be changed in the gconf-editor and you can check how your disks are mounted in the /proc/mounts file.

Also there are various things that can cause slow USB speed like dodgey ACPI and other things that should not be confused with the real guts of this bug.
That is also what makes debugging this a lot harder.

---

### Post by nicolas314 on 2009-01-19
Just tried some tests on a USB thumbdrive (8Gb).
Dumping 10 megs is instantaneous, dumping 100 megs, less so.
EDIT: wrong measurements removed

That is a factor 1000 for 10 times more data. I got the same results with xfs and ext3 filesystems on the same device.

---

### Post by danwood76 on 2009-01-19
Well mine was on a USB sata hard disk as opposed to flash.
So is a little ambiguous in comparison.

I will try and find a flash drive, I have one somewhere and I will test the various mount options in intrepid.

---

### Post by nicolas314 on 2009-01-19
Just re-formatted the USB thumbdrive with an ext3 filesystem, got the same results as with vfat.

I think we can decently rule out mount options. Now this might very well be specific to my key but I doubt it. I also observe considerably longer copy times for big files on USB SATA disks that fly under the other OS.

---

### Post by nicolas314 on 2009-01-20
Strike what I said earlier, I was wrong.

I have repeatedly measured a 100Meg file transfer on the same USB key with different OS's and machines and consistently got the same speed. The discrepancy I observed on Linux was due to the fact that dd reports finishing its job immediately but the following 'sync' takes a while to finish. By measuring both dd+sync times I get consistent results and copying 100 megs takes 10 times longer than copying 10 megs, as expected.

So no bug on this key, it is just slow. Will continue testing on my external USB/SATA hard drive.

Sorry about that.

---

### Post by thomas228 on 2009-01-20
> **detroit/zero said:**
> It's not just flash memory. I use almost exclusively an [external 320GB HDD]("http://www.simpletech.com/parts/spu35320.htm") and I've been screaming about this problem since june or july.


Hi everyone

As usb drives increase in size (I've seen as large as 256 GB) it is becoming more important for the linux community to solve this problem.

Please consider this a bug worthy of "Help stomp Ubuntu bugs at the Global Bug Jam taking place February 20th - 22nd. " I would love to see Detroit/zero take the lead on this as he has spent a great deal of time and research on this subject.

Tom

---

### Post by Bablefish on 2009-01-20
I wonder if Ubuntu will be able to handle the promised USB 3.0. For what I read up the transfer rate of 3.0 is somewhere around 650 mbps.

---

### Post by danwood76 on 2009-01-21
This is off topic but linux will see USB 3 before windows:
[http://sarah.thesharps.us/2008-12-07-13-35.cherry](http://sarah.thesharps.us/2008-12-07-13-35.cherry)

---

### Post by Hated On Mostly on 2009-01-23
After a lot of testing it appears that only the original release kernels work well for me.

8.04 (2.6.24-16), 8.04.1 (2.6.24-19), and 8.10 (2.6.27-7), USB transfers go smoothly as long as I don't update the kernel. Every single kernel update messes up USB transfers for me. I have tried all of the Intrepid proposed and Jaunty kernel updates and none of them worked well for me including the new 2.6.28.x series.

In order to lock down the kernel so you don't see updates in the update manager, make sure you lock the versions of everything in synaptic including for versions you don't have installed for the following items.

linux-generic
linux-headers
linux-image
linux-restricted-modules

Once I locked all of these down (both installed and uninstalled), I was able to do updates without seeing any updates for the kernel.

---

### Post by detroit/zero on 2009-01-24
> **Hated On Mostly said:**
> After a lot of testing it appears that only the original release kernels work well for me.

8.04 (2.6.24-16), 8.04.1 (2.6.24-19), and 8.10 (2.6.27-7), USB transfers go smoothly as long as I don't update the kernel. Every single kernel update messes up USB transfers for me. I have tried all of the Intrepid proposed and Jaunty kernel updates and none of them worked well for me including the new 2.6.28.x series.

In order to lock down the kernel so you don't see updates in the update manager, make sure you lock the versions of everything in synaptic including for versions you don't have installed for the following items.

linux-generic
linux-headers
linux-image
linux-restricted-modules

Once I locked all of these down (both installed and uninstalled), I was able to do updates without seeing any updates for the kernel.I can vouch that this works, but for me (and my laptop) only kernel 2.6.26-16 in a fresh 8.04 Hardy Heron install works. If you do a search of my posts, my problems didn't start until kernel 2.6.24-19, an update I got for Hardy sometime last summer. (June or July, I think.)

I have three versions of Ubuntu that I ordered CDs for (Feisty, Gutsy, Hardy) that all have 'normally' (optimally?) functioning USB until the kernel is upgraded.

One time I somehow managed to not lock the version of linux-headers, and when I did my post-install updates, I ended up with slow USB transfers again.. Maybe that narrows down the problem some, maybe it was just a fluke. I've since unlocked all the other kernel packages and have just been silently suffering with this bug.

Side note: I had a kernel update come through a couple weeks ago for Hardy that moved me from .24-22 to .24-23. Up until that time, I was experiencing slow speeds when writing *to* a USB device (flash or external HDD, makes no difference), but when reading *from* a USB device and writing to my internal HDD, the speeds were close to 'normal'; i.e., >20MB/s. Since my kernel has been updated, I now suffer painfully slow transfer speeds in both directions; i.e., <15MB/s and slower as time passes.

---

### Post by Hated On Mostly on 2009-01-24
> **detroit/zero said:**
> I can vouch that this works, but for me (and my laptop) only kernel 2.6.26-16 in a fresh 8.04 Hardy Heron install works. If you do a search of my posts, my problems didn't start until kernel 2.6.24-19, an update I got for Hardy sometime last summer. (June or July, I think.)

I have three versions of Ubuntu that I ordered CDs for (Feisty, Gutsy, Hardy) that all have 'normally' (optimally?) functioning USB until the kernel is upgraded.

One time I somehow managed to not lock the version of linux-headers, and when I did my post-install updates, I ended up with slow USB transfers again.. Maybe that narrows down the problem some, maybe it was just a fluke. I've since unlocked all the other kernel packages and have just been silently suffering with this bug.

Side note: I had a kernel update come through a couple weeks ago for Hardy that moved me from .24-22 to .24-23. Up until that time, I was experiencing slow speeds when writing *to* a USB device (flash or external HDD, makes no difference), but when reading *from* a USB device and writing to my internal HDD, the speeds were close to 'normal'; i.e., >20MB/s. Since my kernel has been updated, I now suffer painfully slow transfer speeds in both directions; i.e., <15MB/s and slower as time passes.

detroit/zero, see if this works for you:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/467](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/467)

I didn't get to try it out more with the non-working kernels, because I just decided to start from scratch and lock everything down, but it did appear to work when I tried it. If it works, it would be a decent workaround until this thing gets fixed (if ever).

---

### Post by minsf on 2009-01-28
same problem here.
i'm running 8.10 with 2.6.27-9-generic kernel
lshw shows that the usb port uses uhci_hcd modlue/driver

_**problem:**_ when running the low level command dd from my internal HD to the external HD, tranfer rate starts with more than 4MB/s, but decays to 2MB/s after 30-60 sec, and to 1.2MB after 300 sec and eventually stabilizes at the poor 1MB/s. 

_**NOT a hardware problem:**_ I know my hardware was capable of at least 6MB/s a couple of months ago when i ran XP. When running on a different XP box, this drives works like a panther... When changing to a different external HD and a different cable, i still get the same lame transfer rate.

_**I tried but didnt work:**_
a) boot with pci=routeirq (also tried with noapic, together and separately)
b) running from a live CD
c) running from a live CD of 8.04.2 (this has a newer kernel than the original 8.04, but i couldnt get the original yet)
d) running from Fedora live cd, from slackware live cd (slax)
e) formatting the external to ext3, fat, ntfs same rate
f) reloading the modules with "sudo modprobe -r XXX" and "sudo modprobe XXX" where XXX=uhci_hcd XXX=ehci_hcd XXX=usb-storage
g) different external hard drive and usb cable give same lame rate.

my next step is to try an old kernel, but all live CDs that i was able to get so far run latest kernels. I hope to report results of old kernel run by tomorrow here

any idea will be greatly appreciated

EDIT: I have another thread that I am planning to continue here (i was not aware of your thread before):
[http://ubuntuforums.org/showthread.php?t=1051080](http://ubuntuforums.org/showthread.php?t=1051080)

EDIT2: somebody voted thumbs down on the explicit dd comand, so i remove it. my goal is to wipe out the external, but i dont want any newbie trying this command accidently...

---

### Post by detroit/zero on 2009-01-28
> **Hated On Mostly said:**
> detroit/zero, see if this works for you:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/467](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/467)

I didn't get to try it out more with the non-working kernels, because I just decided to start from scratch and lock everything down, but it did appear to work when I tried it. If it works, it would be a decent workaround until this thing gets fixed (if ever).
No luck on that one. It did seem promising.

 I still have kernel .24-16 in my system. I figured that even if it ended up being a kernel issue rather than GVFS or Nautilus or whatever, that I'd always have the kernel from my default install that I could boot into for doing large transfers.

Once an update has been performed, from my experience, the USB speed rates are hosed. Even if I boot into kernel .24-16 from Grub, I'm still stuck with those slow speeds. If I do a fresh install from my Hardy CD, I'm back in action with consistently >24MB/s speeds.

I remember I got slipped an update when I had my guard down - it was either the modules (which that "c&p ehci.hcd" fix tries to deal with) or the headers.

I don't know enough about how the kernel is put together to know which one it was or which might need to be looked at. I've read plenty of threads from as far back as 2005 where ehci took the blame, though.

So I don't know.

---

### Post by Bablefish on 2009-01-28
Hey I have 7.04 currently and the transfer rate is the same as everyone reported. Maybe it's a bug with Ubuntu. Lets hope they fixed it, when the new version comes out in April.

---

### Post by detroit/zero on 2009-01-28
One thing I forgot to mention (maybe it was in this thread, maybe one of my other ones..):

This doesn't just affect USB transfers - for me, at least - writing between partitions on my internal HDD has these problems.

I have /home on its' own partition (ext3 for everything in Ubuntu), and I have a Vista partition (ntfs) on this drive. To C&P something from ~ to C: goes with the same slow rate of around 5MB/s. 

One time, after un-rarring a video file, I right clicked it and accidentally sent it to the Trash. To C&P it from the trash back to ~/Videos was at the same slow 5MB/s.

That's another thing I noted somewhere along the line: After this bad update (of whatever), small things like extracting archives (and moving files around) seriously slows down my system. If I'm extracting an archive (or moving something from /home to USB or C:, for example) and try to launch Firefox from an AWN launcher, it takes upwards of 30 seconds for FF to start. Same with TBird.. same with even piddly little things like Solitaire or a terminal. All this, even though my Conky readout and System Monitor both say my processor is between 19% and 23% usage. Heck, it takes between 11 and 14 just to run the GUI with Compiz and all that. If I have a System Monitor graph in my panel, looking at the colors, the boxes go almost solid with the color for I/O Wait Time.

There's more to this than just USB is all I'm saying. I think it's a serious flaw in the way the kernel is handling/processing certain kinds of information.

This may be true for some/all of you and you just haven't noticed, or maybe it's just me... Maybe some of you check out moving files between partitions and trying to open apps while an archive extracts and see what you find out.

---

### Post by danwood76 on 2009-01-28
> **minsf said:**
> same problem here.
i'm running 8.10 with 2.6.27-9-generic kernel
lshw shows that the usb port uses uhci_hcd modlue/driver

_**problem:**_ when running the low level command dd from my internal HD to the external HD, tranfer rate starts with more than 4MB/s, but decays to 2MB/s after 30-60 sec, and to 1.2MB after 300 sec and eventually stabilizes at the poor 1MB/s. 

_**NOT a hardware problem:**_ I know my hardware was capable of at least 6MB/s a couple of months ago when i ran XP. When running on a different XP box, this drives works like a panther... When changing to a different external HD and a different cable, i still get the same lame transfer rate.


You describe something that's out of scope of the original start to the thread like many people posting here.

The original bug dealt with the fact that transfers started at, for example 30 MB/s, and ended up after around 30 seconds at 5 KB/s.
1 MB/s is pretty good and is well out of scope of the original bug.
The original bug was squashed and fixed in Intrepid, and now backported to hardy I think.

With the current configuration and drivers I can transfer data to my external HD at 30MB/s (Max USB data transfer). USB Hard disk data transfer speeds are not driver dependant as the USB controllers have to adhere to a specification, so each piece of hardware should have the same throughput.
My drive for example uses a very cheap 'made in china' controller that cost me next to nothing but runs flawlessly.

I believe that the problem is with your hardware (drive + PC) and not with Ubuntu (GNU/Linux) itself.

You compare XP, and 8 year old OS, to Ubuntu Intrepid, which is only 3 months old.
XP was designed for primary use on much slower hardware whereas the latset version of ubuntu is designed to run on rescent hardware although still maintain compatibility with older hardware.

At the end of the day flash memory is very slow to write, 1 MB/s isnt that bad.
But all of this and your post is off topic to the original bug!

---

### Post by danwood76 on 2009-01-28
@detroit/zero

Personally it sounds like you have low RAM or some other thing that is holding your system back like a duff hard drive or something.

5 MB/s between drives is terrible, you must have a hardware issue!

But again this thread doesn't deal with that!!

---

### Post by detroit/zero on 2009-01-28
> **danwood76 said:**
> @detroit/zero

Personally it sounds like you have low RAM or some other thing that is holding your system back like a duff hard drive or something.

5 MB/s between drives is terrible, you must have a hardware issue!

But again this thread doesn't deal with that!!
1GB of RAM on a 1.73GHz dual-core Intel is plenty of memory. It's no gamers machine, but it should be more than enough to browse, read emails, and copy files.

There's nothing wrong with my internal or external drives - everything performs the way it should when I run off of a live cd, even with the extra mem usage that comes with that. 

File copies between partitions inside my comp work fine in Vista and XP with ext2IFS installed.

File copies from this same computer to my external HDD under Vista and XP installs, a BackTrack3 CD, an old BLAG cd I have laying around, and any Ubuntu CD version 8.04 (kernel 2.6.24-16) and before (Hardy, Gutsy, Feisty and Edgy) all work fine. Hardy worked fine until I got kernel .24-19 back in June or July.

And by fine, I mean <30 seconds to transfer a 1gb file, as opposed to 3 or 5 minutes in my Hardy install with Kernel 2.6.24-23 

I don't have a hardware issue.

---

### Post by grss1982 on 2009-02-13
Just read on the main site about the maintenance release......[http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release](http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release)


So uhmmm did that release address the issue of slow USB transfer speeds? :confused:

---

### Post by detroit/zero on 2009-02-13
> **grss1982 said:**
> Just read on the main site about the maintenance release......[http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release](http://www.ubuntu.com/news/ubuntu-8.04.2-lts-maintenance-release)


So uhmmm did that release address the issue of slow USB transfer speeds? :confused:
Well, the list of changes made is linked to right off the page you provide:
[https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2](https://wiki.ubuntu.com/HardyReleaseNotes/ChangeSummary/8.04.2)
I don't see anything about USB speeds.. I might have missed it, though.

---

### Post by bsmith1051 on 2009-02-14
> **grss1982 said:**
> did that release address the issue of slow USB transfer speeds? :confused:
I don't think anyone's figured-out the source of the problem yet.  The general symptom is clear -- the USB2 'ehci' driver fails and so you fall-back to USB1 'ohci'.  It seems to be a compatibility issue with specific (but frequent/common) hardware.  Some people also report that everything works correctly off the LiveCD but not from a regular install.  Personally, my ATI motherboard doesn't work properly with the regular LiveCDs either -- but the 9.04 Alpha 3 LiveCD seemed ok??  So maybe the next release will finally fix it?

---

### Post by detroit/zero on 2009-02-15
> **bsmith1051 said:**
> I don't think anyone's figured-out the source of the problem yet.  The general symptom is clear -- the USB2 'ehci' driver fails and so you fall-back to USB1 'ohci'.  It seems to be a compatibility issue with specific (but frequent/common) hardware.  Some people also report that everything works correctly off the LiveCD but not from a regular install.  Personally, my ATI motherboard doesn't work properly with the regular LiveCDs either -- but the 9.04 Alpha 3 LiveCD seemed ok??  So maybe the next release will finally fix it?
Yeah, but, using myself as the example:

I had no problems until kernel 2.6.24-19 came out for Hardy last summer. I've had no issues with any LiveCD of any distro, and never had any issues with an Ubuntu install until Hardy.

I could do a clean wipe of my HDD and re-install 8.04 from the official cd right now and have no USB speed issues until I let the kernel (and/or modules, and/or headers, and/or whatever else) update to a more recent version. Whenever that update happens, even the default install kernel (2.6.24-16) doesn't work properly any more. (The original and the most recent versions are all I have in my install at the moment..)

It could be this, it could be that.. it could even be the other. Whatever it is, I don't know squat about how to tackle the problem.

If anybody in the know wants access to a machine where the problem can be triggered and tracked at will, talk to me. I'll gladly wipe my drive and do a fresh install of Hardy so it can be studied and dissected in whatever way. Hell.. I've been meaning to do another re-install for a while now - that would just give me the reason.

---

### Post by danwood76 on 2009-02-15
@detroit/zero

I have a 1.7 GHz Dual core Intel with 1GB RAM and ATI chipset on my laptop.
I get the same USB speeds on that as on my desktop, my USB stick is slow to write (flash memory is very slow to write so this is normal) but my USB hard disk is 30 MB/S.
This is using Intrepid.

You speak of not a USB issue, as the original post stipulates, but a hardware issue.
Try the latest version of Ubuntu and see if it helps.
If it doesn't post in your own thread!
This thread has no similarities to your problem and so is unrelated!

You speak of a general internal data slowness as opposed to USB slowness.
Don't discount your hardware as the drivers are different from windows to Linux!

---

### Post by detroit/zero on 2009-02-16
> **danwood76 said:**
> If it doesn't post in your own thread!
This thread has no similarities to your problem and so is unrelated!

You speak of a general internal data slowness as opposed to USB slowness.
Don't discount your hardware as the drivers are different from windows to Linux!
Did you get promoted to moderator and somebody forgot to tell us all?

For the second time, danwood, it's not a hardware problem. Let me type this slowly so you're sure to understand:

**My USB transfers work at a certain speed on the same computer on a default install of four different versions of Ubuntu - Edgy, Feisty, Gutsy, and Hardy. When the default installs are updated to a newer kernel version, my USB speeds drop to 15M/s (max) and decrease from there. After the latest updates (2.6.24-23.43 I believe) I'm now stuck at 1M/s and less for _all_ USB transfers when writing to the USB device, whatever that may be.**

Just because I stated I saw the same speed problems between partitions doesn't mean I have an unrelated problem and need my own thread.


My first post showed up in this thread on [July 23, 2008]("http://ubuntuforums.org/showpost.php?p=5444145&postcount=8") - when I first noticed the problem with transferring files to my USB hard disk...  RIGHT AFTER UPDATING MY KERNEL.

I do have my own thread. About five of them:
[http://ubuntuforums.org/showthread.php?t=895386](http://ubuntuforums.org/showthread.php?t=895386)
[http://ubuntuforums.org/showthread.php?t=933705](http://ubuntuforums.org/showthread.php?t=933705)
[http://ubuntuforums.org/showthread.php?t=949748](http://ubuntuforums.org/showthread.php?t=949748)
[http://ubuntuforums.org/showthread.php?t=911052](http://ubuntuforums.org/showthread.php?t=911052)
[http://ubuntuforums.org/showthread.php?t=909158](http://ubuntuforums.org/showthread.php?t=909158)

Plus I'm taking part in three others, including this one:
[http://ubuntuforums.org/showthread.php?t=826775](http://ubuntuforums.org/showthread.php?t=826775)
[http://ubuntuforums.org/showthread.php?t=991794](http://ubuntuforums.org/showthread.php?t=991794)

And have another one here:
[http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/](http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/)

I've been searching and researching this problem and talking to people about it  for seven months now. I don't know who you are to decide what problem applies to who, but methinks you overstep your bounds, danwood.

---

### Post by danwood76 on 2009-02-16
No I'm obviously no moderator.
If you have 5 threads and hijack this one and are still having issues maybe you do have a problem.

Have you tried Intrepid Ibex?
I found USB transfers to be faster than hardy due to the added filesystem optimisations with the newer kernel.

---

### Post by detroit/zero on 2009-02-16
> **danwood76 said:**
> No I'm obviously no moderator.
If you have 5 threads and hijack this one and are still having issues maybe you do have a problem.

Have you tried Intrepid Ibex?
I found USB transfers to be faster than hardy due to the added filesystem optimisations with the newer kernel.

<snip>

Hijacked this thread? Like I just pointed out: My first post in this thread was July 23rd of last year - back when you were swearing up & down to everyone that it was a GVFS bug. Remember that?

Judging by the title, this thread is about slow USB transfers. Period. I don't know who you are to come in and say what it's about and who can & can't post what their experiences are with the problem, but until somebody tells me that you got appointed Forum Daddy and get to tell us all what to do, you can kindly take a hike.

Yes, I've tried Intrepid. From Alpha all the way to the current, released version. Even on the livecd I still have the problem of slow USB write speeds to both flash memory and an external HDD. I haven't gotten around to trying Jaunty yet, but I'm not expecting much from it. (Read speeds are always fine; averaging a steady 27MB/s.)

Livecd and installed versions of Edgy, Feisty, Gutsy and Hardy don't show the symptoms, though. I prefer to stick with Hardy, it being LTS and all.

Like I said: I'm getting around to doing another fresh install of Hardy, and it'd be cool if someone more in the know about USB and kernel workings wanted to see how it happens and what causes it.

If not, oh well. I'll have my kernel and modules locked at 2.6.24-16 and I'll be rockin... Best of luck to the rest of you.

Over & out.

---

### Post by grss1982 on 2009-02-17
> **detroit/zero said:**
> 

...snip

Livecd and installed versions of Edgy, Feisty, Gutsy and Hardy don't show the symptoms, though. I prefer to stick with Hardy, it being LTS and all.

Like I said: I'm getting around to doing another fresh install of Hardy, and it'd be cool if someone more in the know about USB and kernel workings wanted to see how it happens and what causes it.

If not, oh well. I'll have my kernel and modules locked at 2.6.24-16 and I'll be rockin... Best of luck to the rest of you.

Over & out.

Just curious is 2.6.24-16 the default of Ubuntu Hardy Heron 8.04 or 8.04.1 or 8.04.2?

Thanks for the replies. You've been very helpful. :) 

P.S. I might even try your way of locking yourself to 2.6.24-16 kernel and modules if it helps in the USB problems I'm having with 8.04. ;)

---

### Post by detroit/zero on 2009-02-17
> **grss1982 said:**
> Just curious is 2.6.24-16 the default of Ubuntu Hardy Heron 8.04 or 8.04.1 or 8.04.2?

Thanks for the replies. You've been very helpful. :) 

P.S. I might even try your way of locking yourself to 2.6.24-16 kernel and modules if it helps in the USB problems I'm having with 8.04. ;)
Plain-Jane 8.04  As far as I can tell, it has to be an install from an original 8.04 CD. Any of the newer versions have the messed up functionality, at least for me & my system.

I can't guarantee that that will solve the problem for you, though. It's worth a try. If it works, we may be on to something.

---

### Post by chinchillart on 2009-02-17
> **detroit/zero said:**
> Plain-Jane 8.04  As far as I can tell, it has to be an install from an original 8.04 CD. Any of the newer versions have the messed up functionality, at least for me & my system.

I can't guarantee that that will solve the problem for you, though. It's worth a try. If it works, we may be on to something.

Hi Detroit,

at the moment I can say I've gained full speed usb support. As far as we  can talk about "speed" with USB hardware..

Anyway: I've just tried a transfer from my Lacie external usb hd (Samsung 501lj internal drive) to my internal sata WD1000EAS (or something..).
Trasfering an HD movie of 4.3 GB TO internal SATA:
- initial speed: ~14 MB/s
- final speed: ~17.4 MB/s

Then copied the movie (Fight Club...) from SATA TO external LACiE:
- initial speed: ~24 MB/s
- final speed: ~22,3 MB/s
- total time: approximately 2'40''

So I can claim IT WORKS!

Now my configuration:

- LACiE USB 500GB connected to my bulky Nvidia motherboard usb hub(nForce 520 chipset).
- the only two other  USB-connected devices are the keyboard and the mouse.

I've keep Hardy updated to 8.04.2:

- linux-image-2.6.24-23-generic (2.6.24-23.49)
- linux-restricted-modules-2.6.24-23 (2.6.24.16-23.56)

This kernel was updated on february 5. Have you tried this ?

I've made an lsmod command:
```

rob@ubuntu:/boot$ lsmod | grep usb
snd_usb_audio          83936  0 
snd_pcm                78596  4 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            18432  1 snd_usb_audio
snd_hwdep              10500  1 snd_usb_audio
snd_rawmidi            25760  3 snd_ca0106,snd_usb_lib,snd_seq_midi
snd                    56996  16 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_usb_lib,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            73792  1 
libusual               19236  1 usb_storage
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
usbcore               146412  9 snd_usb_audio,gspca,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd

```


If you need more info let me now.. 
Good luck!

rob

---

### Post by Hated On Mostly on 2009-02-20
I don't know why anyone is questioning whether detroit/zero actually has the problem or not. He definitely does. His system is not even close to slow. A dual-core with a 1 GB of RAM can't handle Ubuntu and file transfers? If that were true then I need to switch back to Windows XP ASAP.

I originally saw the problem on a much slower system, a P4 with 2 GB of ram that had very fast USB transfers in Windows XP and when using the live CDs.

I still see the problem on a much more modern system. Exact problem on a dual-core (2.5 MHz, 6 MB L2 cache) with 4 GB of RAM.

As far as general system slowness caused by this bug, I vaguely remember mp3 files skipping every now and then when switching from one window to another and other small but noticeable performance issues that I felt should not have been there. When I did fresh installs of Ubuntu, without updating the kernel, I don't remember those problems being there. This was back when I had the USB transfer problem but didn't know about it yet, so there might be more to the bug as detroit suggests.

I would try out Jaunty Alpha 3 myself like bsmith suggested worked for him, but I will wait until Jaunty final to try out another kernel. Don't want to keep playing around with my machine. I just want 8.10 (Intrepid Ibex) features with a super-stable kernel and I will be satisfied. If Jaunty doesn't do it I will just reinstall 8.04 and update individual packages like Nautilus and other software to the latest versions and see if that works without trashing my system.

By the way detroit, I posted a link to your offer of help on the launchpad page for this bug in Ubuntu. Hopefully a developer will take notice, contact you, and analyze this bug thoroughly, but I am not holding my breath. [-o<

Thanks anyway

---

### Post by detroit/zero on 2009-03-05
I don't believe it, but it seems to be true: The most recent kernel updates fixed my problems.

Well, not exactly "fixed" in the purest sense of the word, but things are a lot better than they were.

I have read speeds averaging around 20MB/s and write speeds that hang between 24 and 25 Mb/s, but still slowly degrade to around 19 or so.

There does seem to still be a file size associated with how this works. Historically, since I first fell victim to this bug, files that came in under 7000MB (think: AVI files) in size seemed to go pretty much as fast as anything, but once that 700MB line was crossed it was slowville all the way. Read speeds always appeared to be completely unaffected, up until the previous kernel update, which sent my read speeds down the same toilet.

I've tested the transfer speeds with AVI files of various sizes, and then I grabbed a big batch of around 14GB worth (like 10 or 12 files) and moved them off & back onto my drive. Single files work normally. The big batch took a little longer than Nautilus said it was taking, but it still went faster than it used to.

I don't know... I just wish it was something I did so I would know it's a lasting, permanent change and not just dumb luck.

---

### Post by bsmith1051 on 2009-03-06
> **detroit/zero said:**
> There does seem to still be a file size associated with how this works. Historically, since I first fell victim to this bug, files that came in under 7000MB (think: AVI files) in size seemed to go pretty much as fast as anything, but once that 700MB line was crossed it was slowville all the way.
That sounds like a memory-related issue then, i.e., the file-size went above the size of the available memory.  How much memory does your machine have?

More importantly, do you (did you?) see errors in the system log?
```
> dmesg | grep usb
```
I don't have to run speed tests, I just look for the errors, which occur immediately on my system.

---

### Post by waldgeist_di on 2009-03-09
I have similar problems. I did my tests with a 200 GB harddisk (NTFS partition) in a 2,5" enclosure with both SATA and USB interface.

Connected to the SATA interface I managed to transfer a 2 GB and a 15 GB file with almost 52 MB per second on my 64 bit Intrepid box (2.6.27-13-generic). Before anyone thinks the box is too old or slow: it's a dual quadcore Xeon with 8x 3 GHz and a total of 16 GB RAM, the internal drives are rather fast 1 TB ones.

The same files transferred via the USB connection slow down to a steady 10 MB per second.

@detroit/zero: I can confirm the high CPU utilization during file transfers even from one internal partition to the other, i.e. without the USB issue.

Will now boot the system with the 8.04.1 live cd to test the speed with that kernel.

---

### Post by detroit/zero on 2009-03-09
> **bsmith1051 said:**
> How much memory does your machine have?

More importantly, do you (did you?) see errors in the system log?
1.73GHz dual core with 1GB RAM. Should be enough to handle file transfers..

> **waldgeist_di said:**
> @detroit/zero: I can confirm the high CPU utilization during file transfers even from one internal partition to the other, i.e. without the USB issue.
Good to know I'm not the only one. Thanks

---

### Post by waldgeist_di on 2009-03-09
I just finished the test with the live CD 8.04.1. As already posted by others the same constellation yields a steady 28 MB per second with this lice CD kernel.

The copy process starts at ridiculously high 83 MB/s because the kernel seems to put the whole stuff in RAM first. After 1.5 GB the transfer rate drops sharply to 30 MB/s, when the actual writing to the external disk starts. Thereafter, during the whole 17 GB the speed decreases only very slightly to the abovementioned 28 MB/s.

---

### Post by minsf on 2009-03-10
@detroit: not a solution, just as a workaround, maybe you can use something like "dd if=/home/detroit/filename of=/media/usb_mount_point/filename bs=8M &" or any bs<700M to baypass the 700M threshold. then to monitor the speed use "sudo kill -USR1 dd_process_number" (the process number will probably be output after the dd command if you used the "&" at the end). 
anyways, what kernel exactly "solved" the problem? 
good job with your responses to danwood by the way

---

### Post by detroit/zero on 2009-03-11
> **minsf said:**
> @detroit: not a solution, just as a workaround, maybe you can use something like "dd if=/home/detroit/filename of=/media/usb_mount_point/filename bs=8M &" or any bs<700M to baypass the 700M threshold. then to monitor the speed use "sudo kill -USR1 dd_process_number" (the process number will probably be output after the dd command if you used the "&" at the end). 
anyways, what kernel exactly "solved" the problem?
The latest updated kernel for Hardy did the trick. It included headers, modules, and the kernel itself.```
zero@zero-laptop:~$ uname -a
Linux zero-laptop 2.6.24-24-generic #1 SMP Thu Feb 19 08:00:07 UTC 2009 i686 GNU/Linux
```It's not entirely "fixed," though, as you've noted. I'm still happy as a lark to have it working as well as it does.

I'll give that command a try and see if it improves anything or not. I don't think it's just file sizes that affect the speeds though - folders with lots of files inside also seem to run kind of slow (relatively speaking).

> **minsf said:**
>  good job with your responses to danwood by the wayOne comment in particular got me an infraction, but I'd say it was worth the one point;)

---

### Post by Hated On Mostly on 2009-03-11
> **detroit/zero said:**
> 
I'll give that command a try and see if it improves anything or not. I don't think it's just file sizes that affect the speeds though - folders with lots of files inside also seem to run kind of slow (relatively speaking).

Just about all of the user reported problems related to this bug report large numbers of files being a problem and files 700 MB and larger being a problem (the bigger the file, the bigger or more likely for there to be a problem). I have seen the same thing when I am dealing with the bug.

I highly doubt it is a memory issue. All of the machines I see this bug on have 4 gigs of RAM, pass all memory tests, and transfer just fine in any version of Windows.

---

### Post by rainwalker on 2009-03-11
I've been having problems like this for a while, too. My laptop only has a 60 GB hard drive, so I got a 320 GB Western Digital external to put stuff on. As far as I can remember, copying files seems to go in "bursts" of 40-60 MB or so, stopping for a few minutes in between. Obviously this gets extremely annoying when trying to back up data (music, movies, or even just documents), so it's good to know I'm not the only one. Smaller files seem to go a bit faster, but it's just not reasonable to have to copy my music over to the drive artist-by-artist.

I'm running 8.10 with kernel 2.6.24-23-generic
I don't know what other info would be useful, so just ask.

Anyways, the only unique bit I can contribute is this:
I got a suggestion from someone on the Ubuntu IRC channels to try copying /dev/zero to the drive using Nautilus (drag-and-drop) because it just creates the "zero" file in the target location, getting bigger and bigger until you tell it to stop. Interestingly, when I did this, the transfer went at full speed (around 29 MB/sec) the entire time until I said to stop. All in all, I copied about 616 MB in around 19 seconds.

I'll post back in a little while with times from copying folders/files normally, and hopefully test the live CD, too.

---

### Post by rainwalker on 2009-03-22
For some reason, my USB tranfers to my external (same one as in my last post) are going steady and a bit faster today. I've successfully copied two files, one slightly under and one slightly over 700 MB at a constant speed anywhere from 1.9-2.9 MB/sec (it slowed down when doing anything other than letting it transfer, such as rapidly opening firefox to hurry to this thread and report this happening).
I know I've installed updates since my last post, but I don't see how these would affect USB transfers...
**March 16th:**> Upgraded the following packages:
ffmpeg (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
gstreamer0.10-plugins-good (0.10.7-3ubuntu0.1) to 0.10.7-3ubuntu0.2
libavcodec-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libavcodec1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libavformat-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libavformat1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libavutil-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libavutil1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libglib2.0-0 (2.16.6-0ubuntu1) to 2.16.6-0ubuntu1.1
libglib2.0-dev (2.16.6-0ubuntu1) to 2.16.6-0ubuntu1.1
libpostproc-dev (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libpostproc1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
libswscale1d (3:0.cvs20070307-5ubuntu7.1+medibuntu1) to 3:0.cvs20070307-5ubuntu7.3
**March 17th:**
> Upgraded the following packages:
amarok (2:1.4.9.1-0ubuntu3.1+medibuntu1) to 2:1.4.9.1-0ubuntu3.2
amarok-xine (2:1.4.9.1-0ubuntu3.1+medibuntu1) to 2:1.4.9.1-0ubuntu3.2
ffmpeg (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavcodec-dev (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavcodec1d (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavformat-dev (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavformat1d (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavutil-dev (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libavutil1d (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libnss3-1d (3.12.0.3-0ubuntu0.8.04.4) to 3.12.0.3-0ubuntu0.8.04.5
libpostproc-dev (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libpostproc1d (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
libswscale1d (3:0.cvs20070307-5ubuntu7.3) to 3:0.cvs20070307-5ubuntu7.3+medibuntu1
**March 20th:**
> Upgraded the following packages:
libjasper1 (1.900.1-3) to 1.900.1-3ubuntu0.8.04.1

So, transfers are faster now and steady(ish), but not as fast as they should be and still use a lot of CPU power.

---

### Post by detroit/zero on 2009-03-23
I noticed the last kernel update sort of did the trick for me. ([See my last post.]("http://ubuntuforums.org/showpost.php?p=6875615&postcount=104")) It didn't fix every problem I've been having, but USB transfers do work a lot better ever since.

---

### Post by Hated On Mostly on 2009-03-26
If anybody wants to test out the officially released Linux Kernel 2.6.29, here you go:

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

I have not tried it and don't plan on it. I am still waiting for the official Jaunty (v9.04) release.

---

### Post by rainwalker on 2009-03-26
Alright, I don't know what happened, but suddenly the issues are back. And of course, at the WORST possible time (Banshee just messed up my stored music trying to re-sync all 17 gigs to this external drive).


This is totally unacceptable.

---

### Post by rainwalker on 2009-03-26
Out of curiousity, am I the only one who thinks they recall reading somewhere that Ubuntu tries to limit the number of read/write cycles to/from external drives (flash and hard-drive media)? I don't remember where, I think it might have been in the Ubuntu Wiki, but I swear I read something about that at one point.
Do you think that could also be having an adverse affect on transferring files?

---

### Post by rainwalker on 2009-03-27
Okay, now my speeds are back up to around 2.8 Mb/sec...I didn't do anything different, except I booted up my computer with the external hard drive plugged in, rather than plugging it in after logging in. I don't know if this would have had an effect; Would someone be able to try and duplicate it?

---

### Post by LowSky on 2009-04-01
Im having the very same issue using the last 3 releases, Hardy, Intrepid and Jaunty.

heres the thread I justed start in the developement section
[http://ubuntuforums.org/showthread.php?t=1112701](http://ubuntuforums.org/showthread.php?t=1112701)

---

### Post by ph5077 on 2009-04-02
Hi, 
my system spent around 12hr to copy a 42G file.
After reading your messages, I doubted the USB subsystem may work at USB 1.1 for some reason, ex HDD wakeup and sleep, I guessed.

So I stopped the copy and unmounted, mounted the HDD again.
Then the 42G file copy completed in half hour.

Hope this help!

---

### Post by LowSky on 2009-04-02
> **ph5077 said:**
> Hi, 
my system spent around 12hr to copy a 42G file.
After reading your messages, I doubted the USB subsystem may work at USB 1.1 for some reason, ex HDD wakeup and sleep, I guessed.

So I stopped the copy and unmounted, mounted the HDD again.
Then the 42G file copy completed in half hour.

Hope this help!
Tried your trick and still mounts as usb 1.1
I should just plug in and go. Doing extra steps or figuring out what the issue is or additional lines of code is not what a polished operating system is supposed to do. For an issue that has plagued linux for years why is this such a taboo problem. I don't think many notice as they dont try to use USB for large data transfers but many still do, and I can't believe the issue hasn't been resolved.

---

### Post by Aviendha09 on 2009-04-07
I guess I won`t replace my existing usb? ports with new usb 2.0 ones just yet. But I might replace ubuntu if another distro fares better than this. My Puppy linux didn't, but its only half-configured. Has anyone tried other distros with more successful results ? In other words, is it Ubuntu? Is it Debian? Is it the kernel(s)? or is it Linux? (ouch!) Whatever happens, I'd rather starve a month a buy a Mac than go back to M$. (I'd rather stick with linux :) )

---

### Post by rainwalker on 2009-04-16
This thread seems kinda dead, but I figured I'd post back anyway.

Things were working just fine for a while, speeds around 2-3 MB/sec (slow, but an improvement) and the drive always mounted fine. However, I installed some updates this morning relating to GVFS and just found out that almost 20 GB of data spontaneously disappeared from my external hard drive. The folders the files had been in were still there, but they were empty.
Not only that, but I couldn't copy the stuff back into those folders; I would get input/output errors. However, if I deleted the folder and copied the files back over in a new folder, it would work. Actually, for a little while it was up in the 20 MB/sec speeds, jumped down to 15...10...9...8..7...and is now transferring at 5.2 MB/second. 
This is seriously unacceptable. I don't understand how more people haven't been afflicted, or how those of us who have are being ignored.
Pardon my language, but this is really starting to piss me off.

For more about the issue I'm now having (and hopefully someone will have answers), here's [my thread]("http://ubuntuforums.org/showthread.php?t=1127788").

---

### Post by el_chupacabra on 2009-04-25
> **rainwalker said:**
> Pardon my language, but this is really starting to piss me off.

I have this problem too. Copying big files via USB under my Ubuntu 8.10 is a big no no. I takes half an hour to copy a file with around 1GB.

What I don't understand is, that this problem seems to be so old and still it hasn't been not solved yet. That's very awkward imho.:confused:

The problem however only appears when I use removable USB drives, like pen-drives. When I connect my external USB HDD, everything works fine.

---

### Post by detroit/zero on 2009-04-25
> **el_chupacabra said:**
> I have this problem too. Copying big files via USB under my Ubuntu 8.10 is a big no no. I takes half an hour to copy a file with around 1GB.

What I don't understand is, that this problem seems to be so old and still it hasn't been not solved yet. That's very awkward imho.:confused:
I don't think it's a priority because it only affects a small minority of users. (It's probably more than most people think, but for many it's not an issue because they either A. Don't use USB devices that often; or B. Don't know any better and think that's just how it works.)

I'm not sure what the catalyst is, but I personally have been all over Hell's Half Acre trying to get someone to do something about this. The closest I ever got was emailing someone who develops the USB kernel driver, who promptly told me that there was nothing wrong with the module and that it was all in my head.

I think development really dropped the ball on USB issues. People can say what they will about how USB isn't meant to be used for file storage, USB and Linux have always had issues, etc, etc. The fact is that USB **is** used for file storage, and has been for a long time. The fact that Linux and USB have always had problems functioning together just proves that Linux development is focusing on all the wrong things.

Never mind that USB file transfers suck; just look at how those windows wobble when you enable Compiz.

And look! There's an aquarium in your desktop cube, too!










Yay.

---

### Post by rainwalker on 2009-04-27
Well I upgraded to Jaunty the day it came out, and I'm now getting around 20 MB/sec, consistently. I don't know what changed, but so far it's working.
However, I still have the issue of that data disappearing off my drive. The "Properties" window shows that I've used about 20 gigs less than the pie chart (in that window) shows has been used. I don't know if this is related to the issues with USB drives, though.

---

### Post by rainwalker on 2009-05-05
Okay, I lied, the issue isn't totally fixed seeing as I'm having the same issue again with slow speeds. This doesn't seem to be an easily-reproducible thing, at least when compared to when it does work right.

---

### Post by Hated On Mostly on 2009-05-08
One person seems to note that when the USB device is plugged in before boot the problem doesn't show its face.

[https://bugs.launchpad.net/linux/+bug/88746/comments/516](https://bugs.launchpad.net/linux/+bug/88746/comments/516)

That would explain why most people are experiencing the bug with USB flash drives primarily since for me, my external hard drives connected to my computers are always on and plugged in before I boot the machine, whereas I am always removing and reinserting my USB flash drive without restarting the machine.

I wish the bug actually got fixed but that might be a temporary workaround. Reboot whenever you actually want to use a USB device that wasn't plugged in at boot... :-|

---

### Post by rainwalker on 2009-05-08
> **Hated On Mostly said:**
> One person seems to note that when the USB device is plugged in before boot the problem doesn't show its face.

[https://bugs.launchpad.net/linux/+bug/88746/comments/516](https://bugs.launchpad.net/linux/+bug/88746/comments/516)

That would explain why most people are experiencing the bug with USB flash drives primarily since for me, my external hard drives connected to my computers are always on and plugged in before I boot the machine, whereas I am always removing and reinserting my USB flash drive without restarting the machine.

I wish the bug actually got fixed but that might be a temporary workaround. Reboot whenever you actually want to use a USB device that wasn't plugged in at boot... :-|

That seemed to happen to me too.

---

### Post by rainwalker on 2009-05-11
Alright, I'm fairly sure I can verify that the problem does not happen when the computer boots up with the drive already plugged in. I don't know how much this helps, but at least it (sort of) narrows it down to a problem related to what goes on with mounted media during startup vs. what goes on after login.

---

### Post by rainwalker on 2009-05-12
> **rainwalker said:**
> Alright, I'm fairly sure I can verify that the problem does not happen when the computer boots up with the drive already plugged in. I don't know how much this helps, but at least it (sort of) narrows it down to a problem related to what goes on with mounted media during startup vs. what goes on after login.

Nevermind, it's slow again even after booting up with it :?
Guys, please don't let this thread die, we need a fix for this problem!

---

### Post by Hated On Mostly on 2009-05-15
> **rainwalker said:**
> Nevermind, it's slow again even after booting up with it :?
Guys, please don't let this thread die, we need a fix for this problem!

At this point it seems the only real fix available now is to buy a separate USB add-on card for your system which doesn't show this problem and use those USB ports instead.

For desktops that means a PCI or PCI-Express card with USB ports.

For laptops that means PCMCIA (PC Card) or ExpressCard with USB ports.

A hardware solution is the only fix available until developers decide to find this bug and fix it...if ever.

---

### Post by unclejac on 2009-05-17
> **Hated On Mostly said:**
> At this point it seems the only real fix available now is to buy a separate USB add-on card for your system which doesn't show this problem and use those USB ports instead.

For desktops that means a PCI or PCI-Express card with USB ports.

For laptops that means PCMCIA (PC Card) or ExpressCard with USB ports.

A hardware solution is the only fix available until developers decide to find this bug and fix it...if ever.

Is this true? if I buy a PCI USB card whip it in I'll not get this painful issue when I use those slots? :o

If so I'm doing it.

---

### Post by Hated On Mostly on 2009-05-17
> **unclejac said:**
> Is this true? if I buy a PCI USB card whip it in I'll not get this painful issue when I use those slots? :o

If so I'm doing it.

On this bug report related to this bug:

[https://bugs.launchpad.net/linux/+bug/88746?comments=all](https://bugs.launchpad.net/linux/+bug/88746?comments=all)

A few people report buying a separate PCI USB card and transfers working as they are supposed to.

This person bought a 5-port PCI USB card with a VIA VT6212 chipset and it worked fine.

[https://bugs.launchpad.net/linux/+bug/88746/comments/491](https://bugs.launchpad.net/linux/+bug/88746/comments/491)

Another person bought a different card based on the same chipset and it worked:

[https://bugs.launchpad.net/linux/+bug/88746/comments/492](https://bugs.launchpad.net/linux/+bug/88746/comments/492)
[https://bugs.launchpad.net/linux/+bug/88746/comments/494](https://bugs.launchpad.net/linux/+bug/88746/comments/494)

This person bought a PCI card with a NEC chipset and it worked:

[https://bugs.launchpad.net/linux/+bug/88746/comments/368](https://bugs.launchpad.net/linux/+bug/88746/comments/368)

---

### Post by Hated On Mostly on 2009-06-04
A person reports that using a powered USB hub worked as a workaround.

[https://bugs.launchpad.net/linux/+bug/88746/comments/526](https://bugs.launchpad.net/linux/+bug/88746/comments/526)

> Greetings Everybody,

I recently found a new work-around that works for my system. I stumbled on this by accident. I ran out of USB ports on my desktop box, and purchased a CyberPower (Powered USB Hub) off Buy.com.

I then thought, I should try the powered USB drive that was giving me a headache under Intrepid and Jaunty. Low and Behold, I was able to now transfer 27 GB's with out a hiccup at USB 2.0 speeds. I was hitting about 20+ MB/s write.

Here is the model number of the hub:
CP-H720P

I'm thinking its a cheap and easy solution while waiting for a bug fix in the kernel.

Good Luck and YMMV
btanoue


---

### Post by detroit/zero on 2009-06-04
> **Hated On Mostly said:**
> A person reports that using a powered USB hub worked as a workaround.

[https://bugs.launchpad.net/linux/+bug/88746/comments/526](https://bugs.launchpad.net/linux/+bug/88746/comments/526)
That's all well and good, but I don't exactly consider going out and buying new hardware so a simple task like file transfers to a USB device work the way they should a 'workaround'. 

Shouldn't developers have 'workarounds' for common enough hardware? We're just not taking our problems to the right people, is all. More people need to complain about this, and complain in the right places.

---

### Post by Hated On Mostly on 2009-06-06
> **rainwalker said:**
> Nevermind, it's slow again even after booting up with it :?
Guys, please don't let this thread die, we need a fix for this problem!

Rainwalker,

Are your USB external drives self-powered/bus-powered or do they use an external power supply?

---

### Post by jtc611 on 2009-07-02
I have the same problem.  I finally abandoned Vista after having fought with it for over a year.  To my disappointment, transferring my files (~50 GB) has taken ~20 hours and counting.  All I did was drag and drop from a LaCieHD 600 GB usb hard drive to my documents folder.  I thought things like that would have been thoroughly tested years ago. The same transfer from Vista  (which was not functioning properly) to the hard drive took about 2 hours.  I'm running 9.0.4 which I just installed yesterday.  Any help would be greatly appreciated.

---

### Post by detroit/zero on 2009-07-02
> **jtc611 said:**
> Any help would be greatly appreciated.
You won't get any here.

This thread is over a year old, and nobody's made any headway in repairing this functionality. Not everybody seems to be affected by it, so it's not a priority.

Personally, I still have an old Feisty Fawn livecd laying around. I shut down, boot to that, transfer my files, and reboot into Jaunty faster than it would take to just move files from Jaunty.

Sad, really.

---

### Post by rainwalker on 2009-07-02
> **Hated On Mostly said:**
> Rainwalker,

Are your USB external drives self-powered/bus-powered or do they use an external power supply?

Sorry for the late reply, I missed your post somehow.
Anyways, my external is powered by USB, not a power supply.

---

### Post by Hated On Mostly on 2009-07-03
> **rainwalker said:**
> Sorry for the late reply, I missed your post somehow.
Anyways, my external is powered by USB, not a power supply.

You may find that your transfers are stable if your external uses a power supply instead of USB self-powered.

If your external enclosures have a power port, then you might be able to get a power supply like the following to power the drives:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812270002](http://www.newegg.com/Product/Product.aspx?Item=N82E16812270002)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812186003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812186003)

There are also power cables which use a USB port to power the external enclosure, but they don't work as well depending on the hard drive.

---

### Post by detroit/zero on 2009-07-03
> **Hated On Mostly said:**
> You may find that your transfers are stable if your external uses a power supply instead of USB self-powered.
You may also find that sprinkling it with a little pixie dust will help, too.

The power source has nothing to do with the data transfer rate.

I have the same exact problem with the same exact data transfer rates to any number of USB devices, including thumb drives and an external HDD with external power. The transfer caps at around 5MB/s.

Maybe I should try running it off a potato clock like in 6th grade science class? I'll score environmental points, pick up a carbon credit or two, and be able to crack 1024 bit encryption while running the entire SETI@home project from my laptop and watching a movie in VLC.

---

### Post by jtc611 on 2009-07-06
I tried the pixie dust method and that worked, but fairies are hard to catch.  I have discovered a superior work around to the good 'ol drag 'n drop.  Do this:

rsync -av /folder/you/want/to/back/up/ /folder/with/your/data/

You can also reverse the order of the directory trees.  This function will sync up the two folders.  It restored my 50 gb of data to my hard drive from my usb drive (which was externally powered btw) in less than an hour, compared to about 24 hours with drag and drop.  And, rsync let's me do future backups and only updates new and modified files using the syntax above.  Hope this is helpful to somebody.

---

### Post by Graham1982 on 2009-08-05
Thanks for the tip ftc611.

Not that this post will be of any good, but I had this problem in Ubuntu 8.04, 8.10, and now Debian Sqeeze/SID.

I transfer lots of files to multiple devices on a regular enough basis that this has caused me a major inconvenience.

If it were just a one off temporary problem I wouldn't really care that much, but the fact that this thread is over a year old and 14 pages long, with no resolution in sight, is enough to almost sway me toward switching away from the Debian branch entirely.

Don't get me wrong!  I've always been happy in all other ways with Debian and Ubuntu, and will continue to use Debian for some servers while recommending Ubuntu for new Linux desktop users, but this sort of regression has been lingering for longer than I thought it had been.

I have this problem transferring files to my 8GB Datatraveller, a 2GB Datatraveller, a 2GB SD Card, my GPS that has 12 GB of memory, my external 500GB HDD, and my 8 GB MP3 player.

I've noticed that regardless of which device I'm copying to, the first 500-600 MB copy at ~30MB/s before falling off the proverbial cliff.

When I'm trying to sync up certain sets of files between certain devices this becomes a huge pain in ***.

Anyway, from my experience, since I'm running Debian SID now, it doesn't look like this is as much of a Ubuntu problem as it is a problem affecting any Debian based distros.

*hopes this gets fixed soon*

---

### Post by Arup on 2009-08-05
Turn off usb legacy support in BIOS and enable AHCI mode for hdd and then check.

---

### Post by canthus13 on 2009-08-05
rsync didn't do anything.  However, dmesg came up with this during the transfer:


```
[ 1825.628615] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1825.628629] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1825.628631]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1825.628633]          res 50/50:50:50:50:50/00:00:00:00:00/50 Emask 0x2 (HSM violation)
[ 1825.628637] ata3.00: status: { DRDY }
[ 1825.628660] ata3: soft resetting link
[ 1825.937983] ata3.00: NODEV after polling detection
[ 1825.937990] ata3.00: revalidation failed (errno=-2)
[ 1825.937995] ata3: failed to recover some devices, retrying in 5 secs
[ 1830.941261] ata3: soft resetting link
[ 1831.253320] ata3.00: NODEV after polling detection
[ 1831.253327] ata3.00: revalidation failed (errno=-2)
[ 1831.253331] ata3: failed to recover some devices, retrying in 5 secs
[ 1836.256600] ata3: soft resetting link
[ 1836.568641] ata3.00: NODEV after polling detection
[ 1836.568647] ata3.00: revalidation failed (errno=-2)
[ 1836.568652] ata3.00: disabled
[ 1837.072507] ata3: soft resetting link
[ 1837.228516] ata3: EH complete
```



Transfer rate for 3 gigs:

```

sent 3064579415 bytes  received 129 bytes  2559147.84 bytes/sec
total size is 3064204962  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.4]

real	19m57.684s
user	0m31.478s
sys	0m22.929s

```

--Me

---

### Post by Hated On Mostly on 2009-10-05
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746?comments=all)

> [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/554](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746/comments/554)

After some file transferring, daily use as host of a thunderbird profile, some videos seen and a partition format mi USB 2.0 disk is still working like a charm. This with the chipset VIA VT6214 PCI bridged.

I'm now testing the Nvidia nForce2 integrated in the motherboard.


According to 3 people on this previously posted bug report, kernel v2.6.31 solves the problem for them.


This kernel is available in 9.10 (Karmic Koala). I wouldn't try to install it into a previous version of Ubuntu. I am currently using the daily build of Karmic from 2009.10.04 and so far so good. Still have more testing to do, but the problem is not appearing for me. I also tested openSUSE 11.2 M8 and Fedora 11 with an updated kernel and did not see the problem.

---

### Post by BuMRK on 2009-10-14
I use ubuntu 9.10 on earlier kernels I had no problems after the upgrade but they were gone after sypalo

Linux bum-laptop 2.6.31-14-generic #46-Ubuntu SMP Tue Oct 13 16:47:59 UTC 2009 i686 GNU/Linux

[ 1237.548049] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1237.696079] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1239.357062] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 1239.490288] usb 1-2: configuration #1 chosen from 1 choice
[ 1239.586860] Initializing USB Mass Storage driver...
[ 1239.588588] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1239.588863] usb-storage: device found at 4
[ 1239.588872] usb-storage: waiting for device to settle before scanning
[ 1239.588898] usbcore: registered new interface driver usb-storage
[ 1239.588908] USB Mass Storage support registered.
[ 1244.585060] usb-storage: device scan complete
[ 1251.245213] gvfsd-metadata[14843]: segfault at 8 ip 0804d2ea sp bff6edf0 error 4 in gvfsd-metadata[8048000+c000]
[ 1266.113051] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1266.436046] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1272.769054] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.105067] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.445079] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.644447] scsi 6:0:0:0: Device offlined - not ready after error recovery

---

### Post by Hated On Mostly on 2009-10-17
> **BuMRK said:**
> I use ubuntu 9.10 on earlier kernels I had no problems after the upgrade but they were gone after sypalo

Linux bum-laptop 2.6.31-14-generic #46-Ubuntu SMP Tue Oct 13 16:47:59 UTC 2009 i686 GNU/Linux

[ 1237.548049] usb 1-2: new high speed USB device using ehci_hcd and address 3
[ 1237.696079] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1239.357062] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 1239.490288] usb 1-2: configuration #1 chosen from 1 choice
[ 1239.586860] Initializing USB Mass Storage driver...
[ 1239.588588] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1239.588863] usb-storage: device found at 4
[ 1239.588872] usb-storage: waiting for device to settle before scanning
[ 1239.588898] usbcore: registered new interface driver usb-storage
[ 1239.588908] USB Mass Storage support registered.
[ 1244.585060] usb-storage: device scan complete
[ 1251.245213] gvfsd-metadata[14843]: segfault at 8 ip 0804d2ea sp bff6edf0 error 4 in gvfsd-metadata[8048000+c000]
[ 1266.113051] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1266.436046] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1272.769054] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.105067] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.445079] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 1273.644447] scsi 6:0:0:0: Device offlined - not ready after error recovery

BuMRK,

please run in the terminal the following commands and post the results.

```
lspci
```

```
lspci -v
```

---

### Post by detroit/zero on 2009-10-18
I finally found the source of the problem, at least as far as my setup goes. Here's how I did it:

I got frustrated with the Ubuntu/Mint slow transfer rates and decided to check out Fedora. I installed it and ran it for a week or so. Fedora has excellent file transfer speeds, both to and from USB devices and SATA partitions. I copied the kernel config from my Fedora install.

I loaded Mint back into my system and compared the kernel config there with the one I pulled from Fedora. After compileing a half dozen kernels, *Kernel I/O Scheduling* turned out to be the answer.

By default, since I don't know when, Ubuntu started using CFQ (Completely Fair Queuing) for it's Kernel I/O Scheduling default, but there are a few other options available. Anticipatory and Deadline are the two that seem to work best.

I recompiled a new kernel with the Anticipatory I/O Scheduling and, lo and behold, I had my old 30MB/s USB transfer speeds back, and SATA performance was improves two or three times. (Though it's still not as fast a I think an intra-partition transfer should be on a single SATA hard drive, 10 or 12 megs a second is a lot better than two or three.) There's a noticeable drop in system performance while transfers are taking place, but, at least for me, it wasn't half as bad as it was with CFQ enabled.

Take all that with a grain of salt, though, because I've found [forum posts from as far back as 2006]("http://ubuntuforums.org/showthread.php?t=119546") that show people enabling CFQ for the exact same reasons we'll want to disable it here.

Due to some unrelated experiments I was running with Xorg and the catastrophic fail that is the current Intel Video driver setup, I borked my install beyond repair and had to re-do it. Further research into the solution showed me that you can select a default I/O Scheduler at boot up by passing an option on to the kernel.

I found that by appending the string ***elevator=as*** to the end of the kernel parameters in /boot/grub/menu.lst, you can enable anticipatory I/O scheduling. The strings ***elevator=deadline*** and ***elevator=noop*** can be used as well, though I'm not so sure about their effects.
```
title        Linux Mint 7 Gloria, kernel 2.6.28-15-generic
root        (hd0,7)
[COLOR=Blue] kernel        /vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash elevator=as[/COLOR]
initrd        /initrd.img-2.6.28-15-generic
quiet
```It is also possible to change the I/O scheduler for certain devices without making it a system default, as can be found in [these two]("http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/") [blog posts]("http://planet.admon.org/howto/how-to-change-default-io-scheduler/").

I'd be interested in seeing if any of you get similar results by trying these solutions.

---

### Post by bsmith1051 on 2009-10-18
Good work!  Still, I'm about ready to jump ship to Windows 7, I mean this is RIDICULOUS.  Forget transfer speed, I can't even get my USB to work reliably.  I've had problems ever since the upgrade from 8.10 > 9.04.  I disabled the built-in USB and installed an add-on card, and that worked better... for a while.  But now I lose the ability to (re-)mount ext drives after a couple days, and have to reboot to make it all work again.

---

### Post by Hated On Mostly on 2009-10-19
Very interesting post detroit/zero. Good find.

In the Karmic Beta without updates, CFQ is not enabled for me. My system is using deadline by default. I wonder what the final version of Karmic will use? I am also curious about what openSUSE is using by default.


bsmith be careful about jumping to Windows 7. There are a lot of reports of slow USB transfer speeds for Windows 7. When I installed Vista for a few people the USB did seem slow compared to Windows XP, but I didn't pay much attention since I was only handling installation.

[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=%22windows+7%22+%22slow+usb%22](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=%22windows+7%22+%22slow+usb%22)

[http://social.technet.microsoft.com/Forums/en/itprovistahardware/thread/60a7b507-9bda-4e66-8693-b85498cd860c](http://social.technet.microsoft.com/Forums/en/itprovistahardware/thread/60a7b507-9bda-4e66-8693-b85498cd860c)

[http://www.tomshardware.com/forum/110-63-slow-transfer-rate](http://www.tomshardware.com/forum/110-63-slow-transfer-rate)

[http://www.sevenforums.com/performance-maintenance/14797-usb-performing-extremely-slow.html](http://www.sevenforums.com/performance-maintenance/14797-usb-performing-extremely-slow.html)

---

### Post by Hated On Mostly on 2009-10-19
If people could post whether or not CFQ is enabled and whether they still have the slow usb problem that would be great info:

From detroit's link

[http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/](http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/)

> Task: View Current Disk scheduler

Assuming that your disk name /dev/sda, type in a terminal:

```

cat /sys/block/sda/queue/scheduler
```



Copy and paste the output of the above command.

My system shows:

noop anticipatory [deadline] cfq

Which means my system (9.10 Karmic Koala beta with no updates) is using deadline by default and I am currently not experiencing the problem. I was experiencing the slow USB transfer speeds in 8.04 Hardy Heron and 8.10 Intrepid Ibex.

---

### Post by Hated On Mostly on 2009-10-19
My kernel version is the following:

```
uname -r
```

2.6.31-11-generic

---

### Post by detroit/zero on 2009-10-19
> **Hated On Mostly said:**
> My kernel version is the following:

```
uname -r
```2.6.31-11-generic
I'm currently running with
```
$ uname -r
2.6.28-15-generic
```

I also had much better results with kernel 2.6.31.4 when I compiled it myself and had the anticipatory scheduling built into it by default.

I've been running with deadline scheduling since some time last night, and while things do work better than with cfq, the speeds still vary and are only about half throttle compared to normal.

I still haven't tried noop scheduling. There is a post here in the forums archive from like 2006 or 7 where some guy set up a poll and swears up and down that noop is the way to go. It's probably going to turn out that whatever setting works best on the individual setup is going to depend on hardware.

---

### Post by BuMRK on 2009-10-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451107]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451107")

After fasting detroit/zero tried to change the CFQ I noticed a significant improvement in my performance USB only after restarting the system returns the default CFQ how to set it up permanently. As someone has installed grub2 it should be changed in /boot/grub/grub.cfg

---

### Post by ohgodnotanother1 on 2009-11-21
> **detroit/zero said:**
> I finally found the source of the problem, at least as far as my setup goes.

I found that by appending the string ***elevator=as*** to the end of the kernel parameters in /boot/grub/menu.lst, you can enable anticipatory I/O scheduling. The strings ***elevator=deadline*** and ***elevator=noop*** can be used as well, though I'm not so sure about their effects.

I'd be interested in seeing if any of you get similar results by trying these solutions.

Thanks for all the effort you put into helping us.

I tried all of the settings and the "deadline" option worked best.
Although writing to my USB stick still occasionally stops for a few seconds it finished transferring 1.1 GB in about 4 minutes. The speed was probably somewhere between 6 and 7 MB/s. That's fine with me.:)

While searching for the "elevator" kernel parameter I found a thread about how you can make this setting persist through kernel updates: _[COLOR="Blue"][Here is it](http://forums.sidux.com/PNphpBB2-viewtopic-t-1832-view-previous.html)[/COLOR]_
(Basically you only have to add the elevator setting to the end of the line starting with "# kopt". Oh and don't remove the "#" from that line!)

---

### Post by timominous on 2009-12-11
I'm having the same problem.
At first my speeds go up to 10Mbps but after about 20% of the file it drops to below 1Mbps..
Is there any way to resolve this? I really hate it..

---

### Post by spadron on 2010-01-21
> **Hated On Mostly said:**
> If people could post whether or not CFQ is enabled and whether they still have the slow usb problem that would be great info:

From detroit's link

[http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/](http://www.cyberciti.biz/faq/linux-change-io-scheduler-for-harddisk/)





Copy and paste the output of the above command.

My system shows:

noop anticipatory [deadline] cfq

Which means my system (9.10 Karmic Koala beta with no updates) is using deadline by default and I am currently not experiencing the problem. I was experiencing the slow USB transfer speeds in 8.04 Hardy Heron and 8.10 Intrepid Ibex.

Sorry to bump but I don't think it's fixed in 9.10.

My output also reads:

noop anticipatory deadline [cfq]

I'm currently transferring 5.8gb at 250KB/sec (screenshot [http://imgur.com/o3hoF.png](http://imgur.com/o3hoF.png))


edit: apologies, I just realised our brackets don't match. I assume this means it's set to cfq. When the transfer is finished I'll switch to deadline and post results.

---

### Post by Troya.one on 2010-02-02
Same thing on 9.10. Yesterday it was enough time to watch few episodes of Californication, while copying 3,5 Gb file...
One more point to get back on windows%) but i dont wanna it..

---

### Post by junglist313 on 2010-02-02
I am also still having this issue. Very frustrating. I have noticed that if i go into a terminal and use cp the transfer rate stays around 6 MB/s.

---

### Post by LucasCosta on 2010-02-03
Hey, guys, I was having the same problem, but just found a workaround to it:

[https://bugs.launchpad.net/ubuntu/+bug/177235](https://bugs.launchpad.net/ubuntu/+bug/177235)

Good luck!

It's a shame Ubuntu being stable as it is having issues like this one. I hope it gets fixed soon!

---

### Post by MGR1 on 2010-02-13
Amazing! It works! 

```
 pci=routeirq elevator=as
```The above as kernel parameters did the trick on a HP/Compaq NX8220 running Ubuntu 8.10. Transfer speed with a Sandisk Cruzer 8GB now reaches 16-20 MB/s, tested with a 560MB sized file. Previously the speed started around 6MB/s and slowed down to 1MB/s or virtually halted after 100MB had been transferred.

---

### Post by chiwi on 2010-05-30
> **MGR1 said:**
> 
```
 pci=routeirq elevator=as
```

What do those parameters mean exactly?

---

### Post by chiwi on 2010-05-30
never mind:

routeirq=Do IRQ routing for all PCI devices.                              This is normally done in pci_enable_device(),                               so this option is a temporary workaround                               for broken drivers that don't call it.

elevator=       [IOSCHED]
                        Format: {"as" | "cfq" | "deadline" | "noop"}
                        See Documentation/block/as-iosched.txt and
                        Documentation/block/deadline-iosched.txt for details.

---

### Post by drewsus on 2010-06-01
> **chiwi said:**
> What do those parameters mean exactly?

where and how do I add this?

---

### Post by enoman on 2010-06-01
I've got the same problem on 10.04.  I used Nautilus to transfer files from my laptop to a USB attached MP3 player.  It would start ok then pause for a few minutes then resume copying for a few seconds then again pause, it did this about 5 times.  It takes a least 10 to 15 minutes to transfer over 500megs of data.    I notice that my laptop (Ubuntu 10.04) is very slow to transfer files to my FreeNAS server compared to my windows machine.  
 
Any help on this?
Thanks.
 
Newbee.

---

### Post by chiwi on 2010-06-01
same problem here.

The last time I had to use 'cp' in the command line, instead of nautilus, but that's just a workaround. I'd like a 'real' solution :)

---

### Post by AintJoe on 2010-06-07
Just tried setting to the anticipatory scheduler in 10.04, ant it hasn't helped at all.

My issue might be a little different. It appears to get to about 300MB, then pauses then goes another 300MB or so, and then a longer pause, and so on. 

This makes me think there is some buffer that is filling up at ~300MB. I've seen other people post this issue and complaining of other sizes around 100MB.

---

### Post by hickwillie on 2010-08-23
Same problem here. :(

 Ubuntu 10.04 LTS 64bit

If I leave it long enough it sometimes finishes...

---

### Post by skogs on 2010-10-04
Bump.  Problem still persists with 10.10 RC on 64bit.  

Moving the 10.10 rc of edubuntu from fileserver to desktop max speed of 4.6MB/sec over 100Mbit line.  I should expect over double that.  

Frequently doing small large quantities of files I've witnessed as slow as 1.3MB/sec...I love ubuntu, but sometimes when I'm doing work for other people and doing big data transfers I want to tear my hair out.

---

### Post by vdubhack on 2010-10-19
I am seeing this as well with 10.10 64bit. Never been this bad, 200kbs is my transfer speed even with disabling nautius preview. I have noticed if you get rid of nautilus SO many issues are fixed at least for me. I am also having a memory leak issue with nautilus, copying a 10MB file uses up all 4gb of memory and locks up hard and no way to reset but hard reset. I am thinking its time to finally ditch ubuntu for something else, as its just becoming a free windows with to much bloat and crap that isnt needed and to many bugs popping up.. Been running fed13 64bit on the same machine for 2 weeks now and have yet to run into a hitch its nice.

---

### Post by -gator- on 2010-10-26
After some houres of searching i found a solution on the Dutch forum:

sudo gedit /etc/initramfs-tools/modules
just add the module: ehci_hcd
save it and run: sudo update-initramfs -u

However the usb protocol is made for bulk information. If you copy a lot of small files the speed will be very slow. If you would copy a file of some Gb, the speed will be much higher.

---

### Post by Hated On Mostly on 2010-11-02
This was posted on another thread:

[http://ubuntuforums.org/showpost.php?p=10044906&postcount=132](http://ubuntuforums.org/showpost.php?p=10044906&postcount=132)

> **mercier said:**
> the solution is not to use nautilus in gnome. i use double commander and have no problems any more.

to me it seems that it's nautilus' problem

Is this true? Anybody have this problem using Kubuntu (KDE), Xubuntu (Xfce), or some other distribution that does not use the GNOME desktop environment with Nautilus?

---

### Post by Hated On Mostly on 2010-11-03
Never mind, went through some of the old links I posted and this problem has been reported with desktop environments other than GNOME. This bug is not limited to the GNOME DE.

I switched from Linux since this bug became a problem for me so I can't do any testing myself.

---

### Post by Tripwire32 on 2010-12-08
I had the same problem and have been researching solutions and workarounds for the past 3 months. I used to get speeds of 500-900 kb/s but now get speeds ranging between 10-23 mb/s !!! This is what worked for me:

I initially tried disabling file previews in nautilus (among other workarounds in this thread) but this didn't help. What this did do however was make my desktop usable while copying (not click and wait a few minutes for a response). 

At a later stage, quite by chance I happened to be fiddling with BIOS settings. The whole time my USB 2.0 setting had not been enabled! Since I got usb 2.0 speeds with Windows, I thought, like everyone else that it was a linux problem. When I installed ubuntu 10.04 it must have set the usb 2.0 setting back to 1.1. 

I hope my 2 cents helps someone with this very frustrating problem.

---

### Post by realmrealm on 2011-02-01
Just so that you all are aware this is not a problem with Nuatilus (or so it seems)

There are people [here]("https://bugs.launchpad.net/ubuntu/+bug/177235") and [here]("https://bugzilla.kernel.org/show_bug.cgi?id=12707") reporting the bug in other ditros and in server (no gui) versions.

It seems to be a kernel issue that is sporadic

I am having this issue with a brand new install of 10.10 ubuntu server 64bit on new hardware (usb2.0 ports) with new external drives (usb2.0) that have their own power source (it shouldn't be that the hub can't power it)

...... for what it's worth

---

### Post by Clancy_s on 2011-05-29
> **-gator- said:**
> After some houres of searching i found a solution on the Dutch forum:

sudo gedit /etc/initramfs-tools/modules
just add the module: ehci_hcd
save it and run: sudo update-initramfs -u

However the usb protocol is made for bulk information. If you copy a lot of small files the speed will be very slow. If you would copy a file of some Gb, the speed will be much higher.

All this does for me (10.04 64 bit) is start the slowup about 2/3 of the way in instead of in the last 3-4 megs.

It slowed incrementally (from 34 to 9 Mb/s and has sat on 2 meg to go, listed as 9Mb/s and to take 0 seconds for the last 5 minutes.

I also checked my bios- usb legacy support had becomen enabled at some stage, I disabled it but the problem persists.

---

### Post by dtach on 2011-06-30
From what I've read on[ this page]("http://ubuntuforums.org/showthread.php?t=1330727&page=18"), this seems to actually be a bios-kernel miscommunication error similar to the power-munching problem reported by phoronix [here]("http://www.phoronix.com/scan.php?page=news_item&px=OTU2MA"). Basically, it seems that the kernel is just assuming that the usb ports in question are usb1 ports rather than usb2 ports because of a sloppy communication from the bios. If you run lspci, look carefully at your usb controllers and see if they are registered as "USB UHCI Controller" (usb1) or "USB EHCI Controller" (usb2). 



For me, I've been suffering this problem since I first came back to ubuntu, which was at karmic's launch. What sucks about it is that there doesn't seem to be a current workaround for people that don't have a way of switching the setting through their bios. and unfortunately, I'm not nearly educated enough on bootup and bios processes to figure out how to do this manually. 

If anyone is more educated on this specific topic and willing to expound, PLEASE help us all out, this would be a great workaround that would greatly affect the ubuntu community if found.

here is my lcpi output (the part regarding my usb controllers)

> 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)


00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)




---

### Post by jackbkjack on 2011-07-01
I am also having this problem, the larger the file the worse it gets, speeds  drop slower than 3.0mbs.

---

### Post by jcd29 on 2011-07-12
Having this problem in 10.04 too.

---

