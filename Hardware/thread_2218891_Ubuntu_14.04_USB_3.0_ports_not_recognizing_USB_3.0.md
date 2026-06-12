---
title: "Ubuntu 14.04 USB 3.0 ports not recognizing USB 3.0 external hard disk"
date: 2014-04-22
forum: Hardware
---

### Post by Rahul_Thakar on 2014-04-22
Hi Experts,

I am now to Ubuntu. Please help.

I have dell Inspiron 15 3537. and I believe its Intel motherboard.

If I attached my usb 3 hard drive in usb 3 port, then I am not getting any message in dmesg and its not getting recognize.

but if I plug into usb 2 port its works fine and I am getting below message in dmesg.

```
[  747.284392] usb 1-1.3: new high-speed USB device number 7 using ehci-pci
[  747.466591] usb 1-1.3: New USB device found, idVendor=0bc2, idProduct=50a1
[  747.466601] usb 1-1.3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[  747.466606] usb 1-1.3: Product: FA GoFlex Desk
[  747.466610] usb 1-1.3: Manufacturer: Seagate
[  747.466613] usb 1-1.3: SerialNumber: NA0L4ND5
[  747.519977] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[  747.520020] scsi4 : usb-storage 1-1.3:1.0
[  747.520069] usbcore: registered new interface driver usb-storage
[  748.519226] scsi 4:0:0:0: Direct-Access     Seagate  FA GoFlex Desk   0D12 PQ: 0 ANSI: 0
[  748.519902] sd 4:0:0:0: Attached scsi generic sg3 type 0
[  748.520339] sd 4:0:0:0: [sdc] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[  748.521586] sd 4:0:0:0: [sdc] Write Protect is off
[  748.521595] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  748.527486] sd 4:0:0:0: [sdc] No Caching mode page found
[  748.527500] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  748.531449] sd 4:0:0:0: [sdc] No Caching mode page found
[  748.531453] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  748.552357]  sdc: sdc1
[  748.552364] sdc: p1 size 3907040067 extends beyond EOD, enabling native capacity
[  748.555208] sd 4:0:0:0: [sdc] No Caching mode page found
[  748.555212] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  748.558332]  sdc: sdc1
[  748.558337] sdc: p1 size 3907040067 extends beyond EOD, truncated
[  748.561706] sd 4:0:0:0: [sdc] No Caching mode page found
[  748.561709] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  748.561712] sd 4:0:0:0: [sdc] Attached SCSI disk

```
Thanks in advance.

Regards,
Rahul

---

### Post by Rahul_Thakar on 2014-04-23
Additional information if I plug ubs 2 device in usb 3 port then it get recognize I get following message

```
[ 2431.471386] usb 2-2: new full-speed USB device number 3 using xhci_hcd
[ 2431.490133] usb 2-2: New USB device found, idVendor=046d, idProduct=c52f
[ 2431.490143] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2431.490148] usb 2-2: Product: USB Receiver
[ 2431.490152] usb 2-2: Manufacturer: Logitech
[ 2431.492597] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/input/input16
[ 2431.492986] hid-generic 0003:046D:C52F.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-2/input0
[ 2431.495488] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.1/input/input17
[ 2431.495835] hid-generic 0003:046D:C52F.0004: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-2/input1

```
so USB2->USB2 works fine
    USB3->USB2 Works fine
    USB3->USB2 works fine
    USB3->USB3 does not work... and this is issue.

Please help.

Regards,
Rahul

---

### Post by giandnt on 2014-04-28
same problem to me! any help?

---

### Post by keith-k on 2014-05-04
> **Rahul_Thakar said:**
> Additional information if I plug ubs 2 device in usb 3 port then it get recognize I get following message


so USB2->USB2 works fine
    USB3->USB2 Works fine
    USB3->USB2 works fine
    USB3->USB3 does not work... and this is issue.

Rahul

Exactly same. Clean installs Ubuntu 14.04 64bit. (Alienware x-51 and HP Pavilion)

---

### Post by sadafrasheed on 2014-05-14
Same issue. HP Envy 6 and WD Passport. Has anyone found a fix for that?

> **keith-k said:**
> Exactly same. Clean installs Ubuntu 14.04 64bit. (Alienware x-51 and HP Pavilion)

---

### Post by mfreyt on 2014-06-01
Exactly same issue here. Clean install of 14.04. If I connect my LACIE as a USB 2.0 device it just works properly. If I connect it to USB 3.0, its not gonna be recognized.... Any help appreciated...Thank you in advance....

---

### Post by Jafix on 2014-06-16
Same Problem here.
Worth to mention: no Problems on Ubuntu Gnomeshell which i had till today...

---

### Post by davidvandoren on 2014-06-16
At start-up push the delete button and enter the bios.

Go to the advanced menu.  Go to usb configuration and change the xHCI mode from enabled to disabled.
Set the EHCI Hand-off to enabled. 
Legacy usb support enabled

Safe changes and reboot. 

See if it works now.

---

### Post by duub on 2014-06-23
This did not correct the problem for me either - ASUS N56VJ on Ubuntu GNOME 14.04 64bit - also a clean install

---

### Post by neelson2 on 2014-07-02
Same here and the suggestion above also didn't help.

Please use [https://bugs.launchpad.net/ubuntu/+bug/1242321](https://bugs.launchpad.net/ubuntu/+bug/1242321) to mention solutions.

---

### Post by drew314 on 2014-09-14
>  Set the EHCI Hand-off to enabled. 
This worked for me. I am using a usb3 via a pcie expansion card. I did not think BIOS would be applicable for USB ports on an expansion card but it is with ubuntu 14.04.

---

### Post by TheFu on 2014-09-15
I can confirm that **disabling EHCI hand-off in BIOS** (old style, not UEFI) **worked** to allow an Anker 4-port USB3 PCIe card to work (no extra drivers needed). Prior to that, no USB3 devices worked at all.  A new HDD wasn't even recognized.

Anker USpeed USB 3.0 PCI-E Card PVU3-2021
Ubuntu 14.04 Server x64.

Nobody was more shocked than I.

Hopefully the OP will mark this thread as solved, assuming it is solved.  I have another system with the same issue - need to try this. That other system has mixed USB2 and USB3 storage. May have to decide which is more important.

---

### Post by AA27 on 2015-03-07
> **TheFu said:**
> I can confirm that **disabling EHCI hand-off in BIOS** (old style, not UEFI) **worked** to allow an Anker 4-port USB3 PCIe card to work (no extra drivers needed). Prior to that, no USB3 devices worked at all.  A new HDD wasn't even recognized.

Anker USpeed USB 3.0 PCI-E Card PVU3-2021
Ubuntu 14.04 Server x64.

Nobody was more shocked than I.

Hopefully the OP will mark this thread as solved, assuming it is solved.  I have another system with the same issue - need to try this. That other system has mixed USB2 and USB3 storage. May have to decide which is more important.


I have a MSI 970 A Gaming board with two VIA USB 3.0 ports and I tried the solution with EHCI and did not work at all.

---

### Post by TheFu on 2015-03-08
If the USB3 ports are built into the MB, that is a completely different issue.

This is about adding a USB3 card to a USB2-only system.

---

### Post by AA27 on 2015-03-13
> **TheFu said:**
> If the USB3 ports are built into the MB, that is a completely different issue.

This is about adding a USB3 card to a USB2-only system.


Well, with cards is another issue, but the problem still there...

There is no 100% recognition of hardware for 3.0 USB ports and I would love to see a solution. I guess we have to wait until developers can update the kernel so this and other hardware can be recognized.

---

### Post by TheFu on 2015-03-13
Actually - you should start your own thread to get help.

A "me too" inside another thread that isn't the same issue ... doesn't get many eyes. The solution I proposed won't work on motherboards with USB3 included.

Thread-jacking is to be avoided, when possible.  When you start your own post, please include some **lspci** output and perhaps **lsusb**?

---

### Post by AA27 on 2015-03-13
Fu, that has be done already and the question has been asked not only here but other Linux forums. I usually do not get that many problems with hardware in Ubuntu, that is why I always install it, but this problem with USB is one that as a community we do not have a concrete solution.

---

### Post by kinisia on 2015-05-09
> **TheFu said:**
> Actually - you should start your own thread to get help.

A "me too" inside another thread that isn't the same issue ... doesn't get many eyes. The solution I proposed won't work on motherboards with USB3 included.

Thread-jacking is to be avoided, when possible.  When you start your own post, please include some **lspci** output and perhaps **lsusb**?

Hi, i am new and i am sorry if i have not made any presentation but i couldn't find the dedicated section.
 i decided to write in this thread because i have a similar issue but slightly different. I took from an old HP Laptop the 250Gb hdd. I decided to make it an external HDD but first of all i would like to backup from there some data. The problem is that the HDD is configured with only 1 bootable partition of Windows Vista. So when i plug the USB it recognizes the disk in the utility but i can't do anything with it in terms of seeing what's inside. Is there any method to surf files inside the HDD without formatting it?

---

### Post by coffeecat on 2015-05-09
Thread closed to prevent further necromancy and hijacking.

@kinisia, welcome to the forum.

You do not appear to have read the post you quoted. Posting to an old thread, especially about something that is not relevant to the original thread topic, won't get you an answer. Simply go to a section appropriate for your problem and click on the orange Post New Thread button to create a new thread. As you are new to Ubuntu, I suggest the New to Ubuntu sub-forum here:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

By the way, do not use Disk Utility to try to read the contents of a formatted partition. Simply open a file browser and click on where it shows in the left pane.

---

