---
title: "[SOLVED] USB drive problem"
date: 2008-08-26
forum: General Help
---

### Post by Dejavou42 on 2008-08-26
This problem just recently started happening. When I boot up Ubuntu, the usb drives will not work automatically. Infact, linux doesn't even see that they are connected other than an entry I found from dmesg. 

```
[13099.907922] usb 6-7: new high speed USB device using ehci_hcd and address 2
[13100.019621] usb 6-7: device descriptor read/64, error -32
[13100.235046] usb 6-7: device descriptor read/64, error -32
[13100.450466] usb 6-7: new high speed USB device using ehci_hcd and address 3
[13100.562165] usb 6-7: device descriptor read/64, error -32
[13100.777587] usb 6-7: device descriptor read/64, error -32
[13100.993004] usb 6-7: new high speed USB device using ehci_hcd and address 4
[13101.399907] usb 6-7: device not accepting address 4, error -32
[13101.511610] usb 6-7: new high speed USB device using ehci_hcd and address 5
[13101.918506] usb 6-7: device not accepting address 5, error -32

```

Anyway, I can fix this by running:
```
sudo modprobe -r ehci_hcd
```

That works great, usb is seen and automounts perfectly. 

However, I didn't want to have to run this everytime at boot up, so I found another post that said I should run this command:

```
 sudo echo "blacklist ehci_hcd" > /etc/modprobe.d/blacklist-ehci


```

but I get the following error after running the previous command:
```

bash: /etc/modprobe.d/blacklist-ehci: Permission denied

```

Now to the question... I don't like the idea of disabling usb 2.0 so, does anyone know of a better fix? if not then how may I blacklist ehci without getting the permission denied message?

oh yes and uname -r give this result:
2.6.24-19-generic



Thanks!

---

### Post by aysiu on 2008-08-26
How about this? ```
sudo -i
echo "blacklist ehci_hcd" > /etc/modprobe.d/blacklist-ehci
```

---

### Post by Dejavou42 on 2008-08-28
Running "sudo modprobe -r ehci_hcd" works, but I don't want to have to run this everytime I boot up. 

I tried the recommended add "blacklist ehci_hcd" to the end of /etc/modprobe.d/blacklist file, but ehci_hcd still runs with boot up.

I also tried to add "acpi=noirq" to the end of /boot/grub/menu.lst, this also didn't work. 

however, I did find this thread [http://ubuntuforums.org/showthread.php?t=691701](http://ubuntuforums.org/showthread.php?t=691701). which said this command would also blacklist ehci_hcd:

```

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r` 

```

The previous code worked for me. USB works from bootup now, but I don't know how much it slowed it down. Hopefully a kernel with a fixed usb will be out soon. Thanks for the help!

---

### Post by Bill_Zaumen on 2008-09-05
I got messages like the following:

[ 1161.618473] usb 4-3: new high speed USB device using ehci_hcd and address 5
[ 1161.756474] usb 4-3: configuration #1 chosen from 1 choice
[ 1161.792457] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1161.798388] usb-storage: device found at 5
[ 1161.798395] usb-storage: waiting for device to settle before scanning
[ 1166.790508] usb-storage: device scan complete
[ 1166.791868] scsi 4:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[ 1166.806087] sd 4:0:0:0: [sdb] 7929856 512-byte hardware sectors (4060 MB)
[ 1166.807338] sd 4:0:0:0: [sdb] Write Protect is off
[ 1166.807345] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1166.807347] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1166.810311] sd 4:0:0:0: [sdb] 7929856 512-byte hardware sectors (4060 MB)
[ 1166.811188] sd 4:0:0:0: [sdb] Write Protect is off
[ 1166.811193] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1166.811196] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1166.811202]  sdb: sdb1
[ 1166.863247] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1166.863309] sd 4:0:0:0: Attached scsi generic sg2 type 0

and the flash disk I had plugged in did not mount.  Curiously,
the command

             pmount sdb1 CORSAIR

then mounted the disk.  I could read from it and write to it.  I tried
pmount because it worked with floppy disks, which would not automatically
mount themselves, so it seemed to be worth trying given the minimal
effort.

Hopefully the problem will be fixed at some point fairly soon. It was
kind of critical for me as I had used two USB disks to back up personal
files before upgrading to Ubuntu 8.04.  Haven't tried disabling the
driver others mentioned yet.

---

### Post by Dejavou42 on 2008-09-06
Using the command that I used above fixed my problem....kind of. I don't have USB 2.0 and I think it caused an issue for my Zune in my Virtual Machine. However, I did find a workaround for that. The weird thing though is that USB 2.0 worked when I first installed Ubuntu. Oh well, from what I understand, its a kernel issue, when a new kernel comes out, hopefully it will be fixed.

---

### Post by manatlan on 2008-09-08
happy ;-)

I've got exactly the same trouble for some days ;-)
happy : I'm not alone, I'm not mad

I've got a recent "2.6.24-19-generic" kernel ... and all USB UMS(universal mass storage) are not mounted anymore ;-( (lsusb don't show them anymore too).

Using "sudo modprobe -r ehci_hcd" do the job. They are now mounted, in usb1.1 ;-(

---

