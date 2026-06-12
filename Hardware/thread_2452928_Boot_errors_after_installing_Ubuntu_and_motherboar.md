---
title: "Boot errors after installing Ubuntu and motherboard splash screen appears twice"
date: 2020-10-30
forum: Hardware
---

### Post by danwgrace on 2020-10-30
I'm new to Ubuntu having come from Linux Mint 18.3, which was on my computer previously. I never had any problems on Linux Mint except for the key ring daemon was always running at shutdown. This was annoying and one of the reasons I switched to Ubuntu.

I installed Ubuntu 20.04.1 without any reported error messages in the GUI. However when I start up the computer the splash screen for the motherboard appears twice and then it appears cut in half before the Ubuntu logo comes up.

Also sometimes, but not always, when I boot up I get an error message that appear to be referring to the BIOS. The messages pass by quickly. I tried pressing pause/break or scroll lock keys but the messages do not pause. I would like to know how to pause the computer so that I can write down the messages, as I assume that these are not stored in a log. Nonetheless the system appears to start up ok even with these errors.

The boot log is clear of errors, except for this:

```

$ cd /var/log
$ sudo cat boot.log
...
[FAILED] Failed to start GRUB failed boot detection.
See 'systemctl status grub-initrd-fallback.service' for details.
```

I don't know if this is related to the boot errors, but I tried that command anyway:
```
$ systemctl status grub-initrd-fallback.service
&#9679; grub-initrd-fallback.service - GRUB failed boot detection
     Loaded: loaded (/lib/systemd/system/grub-initrd-fallback.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Fri 2020-10-30 17:05:56 GMT; 54min ago
    Process: 730 ExecStart=/usr/bin/grub-editenv /boot/grub/grubenv unset initrdfail (code=exited, status=0/SUCCESS)
    Process: 771 ExecStart=/usr/bin/grub-editenv /boot/grub/grubenv unset prev_entry (code=exited, status=0/SUCCESS)
   Main PID: 771 (code=exited, status=0/SUCCESS)

Oct 30 17:05:55 daniel-MS-7817 systemd[1]: Starting GRUB failed boot detection...
Oct 30 17:05:56 daniel-MS-7817 systemd[1]: grub-initrd-fallback.service: Succeeded.
Oct 30 17:05:56 daniel-MS-7817 systemd[1]: Finished GRUB failed boot detection.
```

I looked at my motherboard "MSI Military Class 4":
```
$ sudo dmidecode|grep Product
    Product Name: MS-7817
    Product Name: H81M-E33 (MS-7817)
$ sudo dmidecode -s bios-version
V6.7

```

And there appears to be a security related update at the manufacturers website:
```
https://www.msi.com/Motherboard/support/h81m-e33
```

However I'd rather not flash the BIOS. Besides there are two options, one of them is with "ME" and I don't know what that means.

[HTML]https://www.msi.com/page/biosflash[/HTML]

I'm not sure how to progress. I guess I could try to memorise the boot messages. But the problem is that they're intermittent, so I'd rather write them down.

Worth mentioning: I have an NVIDIA Corporation GM107 GeForce GTX 750 Ti video card, and I'm not currently using a proprietary driver. I'm not sure which one would be best if I were to go with one:

```
$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001380sv00001462sd00008A9Bbc03sc00i00
vendor   : NVIDIA Corporation
model    : GM107 [GeForce GTX 750 Ti]
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-435 - distro non-free
driver   : nvidia-driver-440-server - distro non-free
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-450 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
```

**Update**
I think the error messages are the same as the ones in dmesg:
```
$ dmesg|grep error
[    0.843518] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
...

```

I flashed the BIOS to version 6.8. I still get the double boot screen/logo cut in half, but the error seems to have disappeared, at least for now.

If I use the proprietary "450" driver then the Ubuntu logo appears over the top of second boot splash page, which looks kind of weird.

[B]Further

[/B]Looking into this it seems that Ubuntu support for this graphics card is not as straight forward as on Linux Mint.

I found this page which may be the correct way to install the drivers for this graphics card:
[URL="https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux"]https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux
[/URL]
However it has a warning at a stage of the process: "After the reboot you may end up without GUI at all". Much as I'd like to try this procedure out, it is not a good time for me to lose my GUI. I don't know how difficult it would be to get back the GUI if something went wrong.

---

