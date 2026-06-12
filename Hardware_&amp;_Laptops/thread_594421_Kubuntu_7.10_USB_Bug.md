---
title: "Kubuntu 7.10 USB Bug"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by Tanker Bob on 2007-10-28
I've been working on this issue for 2 days, including searching this site and googling many, many others. I've seen others mention this problem in various forms, but no solutions for Kubuntu Gutsy. I performed a fresh install to a new RAID 1 array with Gutsy x86 using the alternate CD.

Short description is that no USB removable file system will automount in my Kubuntu Gutsy. I have a USB external FAT hard drive, several flash sticks, and a USB card reader. The USB external hard drive connects directly to the motherboard port, the sticks and card reader through a hub. 

I have tried adding the USB HD to /etc/fstab, but Kubuntu also tries to create a drive out of the 1K marker for the extended partition on another ext3 internal hard drive. It seems that whatever is next in line, be it the USB HD's entry (usually sdd or sdi) or the floppy drive (fd0), that bogus partition captures other devices' entries. The other mounts on that other disk are hda1, hda5 (only entry in the extended partition), and hda3 (linux swap partition). I can manually create the mounting for the USB drive only if the 1K extended partition marker doesn't steal the mounting point. At the moment it is squatting on the floppy's mounting point, but the floppy works fine.

The workaround for the flash sticks and cards uses Dolphin''s Storage Media, which notes the insertion of the sticks/cards/USB HD even though they are not mounted. Opening the stick/card/HD in Dolphin correctly automatically mounts the devices. This gets pretty annoying of one is swapping sticks or cards a lot. I can also see all the inserted devices using "lsusb" when they are not auto mounted. The problem is not one of detecting the devices--all are detected immediately upon insertion, just not auto mounted.

I tried using usbmount, but it created a usb device for every USB slot whether empty or not. That's no particularly useful. I tried usbmgr, but it caused a disaster which took an hour from which to recover. I also tried reinstalling hal, mount, pmount, and udev, but that had no effect.

I saw a workaround involving deletion of a "usefree" setting in Gnome, but I can find no corresponding setting in KDE. "usefree" does not appear in any error messages that I've seen. I also tried to disable the usb autosuspend feature with the kernel switch, but that also made no difference.

My old Kubuntu 7.04 Feisty setup is still operational on the other hard drive, and it still works fine. I've tried comparing a number of configuration files between the two setups, but found nothing remarkable. What that did tell me is that there is not a hardware issue. There's something wrong in the USB automounting system in kubuntu gutsy.

I'm wide open to ideas at this point. If someone thinks that I missed something, please let me know. I know from my monitoring of the usb autosuspend issue that the kernel team did a substantial rewrite on the USB routines in the current kernel. I'm now wondering if the code freeze preceded their completion of the rewrite. While Gutsy added some nice features, it seems to have lost some core ones.

Added: I forgot to mention that my USB printer and Bluetooth has no problems with auto mounting, and the latter also connects through the USB hub.

---

### Post by megamania on 2007-10-28
> **Tanker Bob said:**
> Short description is that no USB removable file system will automount in my Kubuntu Gutsy. I have a USB external FAT hard drive, several flash sticks,
I clean-installed Ubuntu 7.10, then added KDE.

In KDE (and Gnome, too) usb sticks are automatically mounted and an icon appears on the desktop.

---

### Post by Tanker Bob on 2007-10-28
OK, that makes one of us. Search this site and google for "usb automount fail" and see how many hits you get. I'm glad that yours works, but I need some ideas on what could be wrong with mine.

---

### Post by megamania on 2007-10-29
> **Tanker Bob said:**
> OK, that makes one of us. Search this site and google for "usb automount fail" and see how many hits you get. I'm glad that yours works, but I need some ideas on what could be wrong with mine.
I had no doubt it was a general issue, I was just trying to help by letting you know that for some people it works.

I don't know if the fact that I installed Ubuntu first and then KDE can make a difference, to be honest.

---

### Post by UbuntuniX on 2007-10-29
Same problem, but for me it was also an issue under gnome, several months ago.

---

### Post by Tanker Bob on 2007-10-29
Did you find a resolution? If so, what was it?

---

### Post by Tanker Bob on 2007-10-29
> **megamania said:**
> I had no doubt it was a general issue, I was just trying to help by letting you know that for some people it works.

I don't know if the fact that I installed Ubuntu first and then KDE can make a difference, to be honest.
Thanks. Interesting thought about the installation order. Given my experience with the usb autosuspend issue, my current assumption is that this is a kernel issue which would transcend flavors. I came to that assumption after reinstalling all the related programs and scripts. That could still be a bad assumption, though, especially if I missed something.

---

### Post by Tanker Bob on 2007-10-30
Here's an update. When I run 

```
dmesg | grep usb
```

after inserting a flash stick, it produces the following new lines:

```
[117008.216420] usb-storage: device found at 14
[117008.216422] usb-storage: waiting for device to settle before scanning
[117013.205095] usb-storage: device scan complete
```

This confirms that it sees the new USB device inserted, but unfortunately it does not mount it automatically.When I remove the stick without ever manually mounting it, I get:

```
[117397.098741] usb 2-2.4.3: USB disconnect, address 14
```

as expected.  Both my PDA and camera were correctly discovered and mounted. Here's the output after connecting my PDA:

```
[115371.563129] usb 1-1: new full speed USB device using ohci_hcd and address 4
[116721.037551] usb 1-1: new full speed USB device using ohci_hcd and address 5
[116721.244159] usb 1-1: configuration #1 chosen from 1 choice
[116721.251211] usb 1-1: PocketPC PDA converter now attached to ttyUSB0
```

and the camera:

```
[117775.289868] usb 1-4: new full speed USB device using ohci_hcd and address 6
[117775.513511] usb 1-4: configuration #1 chosen from 1 choice
```

Additionally, Kubuntu produces the dialog to offer to carry out a menu of actions with the camera connected, including running digiKam.

So the problem seems to be limited to removable mass storage devices. This is all perfectly repeatable.

---

### Post by Tanker Bob on 2007-10-30
Oh, and I found another work-around for flash devices and cards that I use regularly. I create mount points for them using Dolphin. These disappear when the devices disconnect, but then reappear when they reconnect. An example dmesg output of such a connection is:

```
[118294.122078] usb-storage: device found at 16
[118294.122080] usb-storage: waiting for device to settle before scanning
[118299.110149] usb-storage: device scan complete
```

The output is identical to the one that doesn't mount.

---

### Post by chejrw on 2007-10-30
I get the same behaviour under Gnome -  my output is:

```
[   20.522612] usbcore: registered new interface driver usbfs
[   20.522657] usbcore: registered new interface driver hub
[   20.522692] usbcore: registered new device driver usb
[   21.634901] usb usb1: configuration #1 chosen from 1 choice
[   21.737804] usb usb2: configuration #1 chosen from 1 choice
[   22.434955] usb usb3: configuration #1 chosen from 1 choice
[   22.569186] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   22.723598] usb 2-2: configuration #1 chosen from 1 choice
[   23.511640] usb usb4: configuration #1 chosen from 1 choice
[   24.049111] usb usb5: configuration #1 chosen from 1 choice
[   24.440872] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   24.574248] usb 5-4: configuration #1 chosen from 1 choice
[100727.666655] usb 5-4.1: new high speed USB device using ehci_hcd and address 3
[100727.772187] usb 5-4.1: configuration #1 chosen from 1 choice
[100727.903634] usbcore: registered new interface driver libusual
[100727.996804] usb-storage: device found at 3
[100727.996807] usb-storage: waiting for device to settle before scanning
[100727.996826] usbcore: registered new interface driver usb-storage
[100732.994450] usb-storage: device scan complete
[100953.879105] usb 5-4.1: USB disconnect, address 3
[100970.948468] usb 5-4.1: new high speed USB device using ehci_hcd and address 4
[100971.053994] usb 5-4.1: configuration #1 chosen from 1 choice
[100971.054821] usb-storage: device found at 4
[100971.054825] usb-storage: waiting for device to settle before scanning
[100976.052328] usb-storage: device scan complete

```

As my Stick is plugged into a hub.  It doesn't work without the hub, either.  I would appreciate a heads up if anyone resolves this problem.  I havn't been able to force-mount it, either.  Very frustrating.

---

### Post by agent-s on 2007-10-30
i'm having problems as well... bump

---

### Post by Tyl3r on 2007-10-30
Hal is bugged in gutsy.
Installing HAL version of Feisty worked for me, download [from here]("http://na.mirror.garr.it/mirrors/ubuntu-archive/pool/main/h/hal/hal_0.5.9-1ubuntu2~feisty1_i386.deb")

---

### Post by Tanker Bob on 2007-10-30
> **Tyl3r said:**
> Hal is bugged in gutsy.
Installing HAL version of Feisty worked for me, download [from here]("http://na.mirror.garr.it/mirrors/ubuntu-archive/pool/main/h/hal/hal_0.5.9-1ubuntu2~feisty1_i386.deb")
Thanks! Did the retrograde have any other side effects?

---

### Post by Tyl3r on 2007-10-30
No because it requires older versions of the dependencies, and since in gutsy it's all updated it will install perfectly. I'm using it without problem since days.

---

### Post by Tanker Bob on 2007-10-30
I just installed the Feisty hal and rebooted. It didn't make any difference. Anything else that you did perhaps?

---

### Post by Tyl3r on 2007-10-31
Be sure the hal daemon is running.

---

### Post by agent-s on 2007-10-31
how do i force it to install the feisty version of hal?

---

### Post by chejrw on 2007-10-31
It won't let me install the older version because the new version is still installed - should I uninstall the gutsy HAL?

---

### Post by Tanker Bob on 2007-10-31
> **chejrw said:**
> It won't let me install the older version because the new version is still installed - should I uninstall the gutsy HAL?
Use KPackage to install the Feisty version (right click on the deb file and select "Open with..." and pick KPackage" and check the box on the install page that says something like "Allow Downgrades". That worked for me.

---

### Post by Tyl3r on 2007-10-31
sudo dpkg -i /path/to/package.deb

---

### Post by Tanker Bob on 2007-11-02
This has been filed as a bug [here](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/102097). Hopefully we'll see some resolution or at least a reason for the bug soon.

---

### Post by agent-s on 2007-11-03
none of the methods for forcing the installation of feisty version of hal work for me.

also, i hope the submission as a bug fixes it too.  I just noticed that Kubuntu no longer controls the CPU frequency (i left it on dynamic before the update) or has any info on the battery life.

---

### Post by Tanker Bob on 2007-11-05
My OS crashed big time today, taking the \ partition down. I had to rebuild the \ partition from scratch, but my \home partition survived relatively intact. After a reinstall and rebuild, the USB automounting problem remains unchanged. That was a bit disappointing.

---

### Post by tsmets on 2007-12-03
On my laptop my external USB drive was discovered & made accessible in a matter of a few seconds while on my 7.10 server .... it is not seen 

On my server here is the result of the command !
>  tsmets@puffy:~$ dmesg | grep usb
...
[ 1658.817725] usb 1-1: new full speed USB device using uhci_hcd and address 3
[ 1658.989745] usb 1-1: configuration #1 chosen from 1 choice
[ 1659.445675] usbcore: registered new interface driver libusual
[ 1659.755195] usbcore: registered new interface driver usb-storage
[ 1659.755301] usb-storage: device found at 3
[ 1659.755319] usb-storage: waiting for device to settle before scanning
[ 1664.748552] usb-storage: device scan complete
[ 2243.713878] usb 1-1: USB disconnect, address 3
[ 2258.741888] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 2258.914505] usb 1-1: configuration #1 chosen from 1 choice
[ 2258.917623] usb-storage: device found at 4
[ 2258.917645] usb-storage: waiting for device to settle before scanning
[ 2263.912543] usb-storage: device scan complete
 

On my laptop :
>  tsmets@ubuntu:~$ dmesg | grep usb
...
[625975.560000] usb 5-3: new high speed USB device using ehci_hcd and address 2
[625975.692000] usb 5-3: configuration #1 chosen from 1 choice
[625977.140000] usbcore: registered new interface driver libusual
[625977.240000] usb-storage: device found at 2
[625977.240000] usb-storage: waiting for device to settle before scanning
[625977.240000] usbcore: registered new interface driver usb-storage
[625982.240000] usb-storage: device scan complete
[703653.564000] usb 5-3: USB disconnect, address 2
 

I installed autofs & tried other packages but I did not find any relevant other posts that could be installed ... ?

Any idea ... ?

\T,

---

### Post by maxminimum on 2007-12-09
> **Tyl3r said:**
> Hal is bugged in gutsy.
Installing HAL version of Feisty worked for me, download [from here]("http://na.mirror.garr.it/mirrors/ubuntu-archive/pool/main/h/hal/hal_0.5.9-1ubuntu2~feisty1_i386.deb")

This works!!!!  Thanks a lot!

install and make sure the hal daemon is runs on startup


first post is a thanx, from a week old kubuntu user :)

---

### Post by Tanker Bob on 2007-12-09
Loading Feisty's hal didn't work for me, but there's a suggestion [here](http://ubuntuforums.org/showthread.php?p=3922763#post3922763) that seems to work so far.

---

### Post by Grundair on 2007-12-10
THANKS. That finally got my usb sticks to work. Now if I could get my palm TX to work in Gutsy I would be styling

Chuck

---

