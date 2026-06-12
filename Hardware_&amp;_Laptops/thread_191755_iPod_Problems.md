---
title: "iPod Problems"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by Klebon on 2006-06-07
I'm trying to get my iPod to work in Dapper. The iPod connects to the computer and charges untill  GRUB boots into linux. Then, the iPod doesn't show that it's even connected. Ubuntu shows no sign of detecting the iPod. Thanks for any help.

---

### Post by stalefries on 2006-06-07
I'm probably wrong, but I know that iPods hide themselves from Windows so that iTunes can have complete control over them. Could this be it?

Also, is your iPod mac-formatted or Windows-formatted?

---

### Post by Klebon on 2006-06-08
My iPod is windows formatted. Fedora Core 5 detected it and automounted it fine, Could it be that Ubuntu is not configured correctly for the USB ports?

---

### Post by myddrin on 2006-06-08
My iPod (30Gb 5g) works fine in ubuntu, however I always plug it in after I'm logged in.  Try that.

---

### Post by Klebon on 2006-06-08
It makes no difference. If I plug it in before the computer starts, it displays the "don't disconnect" message untill GRUB boots to linux. If i plug it in while Dapper is running, it doesn't connect. I've tried it with my 4g ipod and a friend's mini. Nothing shows up in dmesg about a USB device, so I think it's how my USB ports are configured (I've tried it in all 4 with the same results). I'm on a laptop, but the hardware browser shows the USB ports, but not my iPod.

---

### Post by cheuschober on 2006-06-09
My ipod does not automount in Dapper (xubuntu) as is did in Breezy however that doesn't mean it's not recognized.

ls /dev/

To get the devices listed in your system. Generally an iPod acts an a SCSI device so you'll see it in your /dev as sdX (where X is a letter a-z). If you have your ipod plugged in and only see one sdX device that's very likely your ipod.

What you then want to do is mount the music partition. <i>Usually</i> this is partition 2 (so if your device is sda then this would be sda2). Best way to find out is mount it as vfat and find out:

sudo mount /dev/sda2 -t vfat /media/ipod -o rw,umask=000

If you go to your mountpoint and you see the ipod folders it has mounted sucessfully.

Best,
~Chad

---

### Post by Klebon on 2006-06-09
there are no sd_ files in the /dev directory. dmesg doesn't show anything at all when I plug in my iPod, wither while dapper is runnung or from boot. I know how to mount it in fstab and all that, but there doesn't appear to be anything to actually mount

---

### Post by Guex on 2006-06-10
[QUOTE=Klebon]there are no sd_ files in the /dev directory. dmesg doesn't show anything at all when I plug in my iPod, wither while dapper is runnung or from boot. I know how to mount it in fstab and all that, but there doesn't appear to be anything to actually mount[/QUOTE]

check with "dmesg" what the kernel is logging, when you plug it.

same for me here with a 3G ipod (neither USB nor IEEE1394). i'm missing the device in /dev, but this caused by the kernel (2.6.15-23-k7)

IEEE1394 Mode:

even after loading the modules (ieee1394, ohci1394, sbp2) nothing is detected.

USB Mode:

Jun 10 16:43:37 localhost kernel: [4311731.754000] usb 1-4: new high speed USB device using ehci_hcd and address 33
Jun 10 16:43:40 localhost kernel: [4311734.856000] usb 1-4: device descriptor read/64, error -110
Jun 10 16:43:55 localhost kernel: [4311750.059000] usb 1-4: device descriptor read/64, error -110
Jun 10 16:43:56 localhost kernel: [4311750.265000] usb 1-4: new high speed USB device using ehci_hcd and address 34
Jun 10 16:43:59 localhost kernel: [4311753.367000] usb 1-4: device descriptor read/64, error -110
Jun 10 16:44:14 localhost kernel: [4311768.576000] usb 1-4: device descriptor read/64, error -110
Jun 10 16:44:14 localhost kernel: [4311768.779000] usb 1-4: new high speed USB device using ehci_hcd and address 35
Jun 10 16:44:19 localhost kernel: [4311773.792000] usb 1-4: device descriptor read/8, error -110
Jun 10 16:44:24 localhost kernel: [4311778.904000] usb 1-4: device descriptor read/8, error -110
Jun 10 16:44:24 localhost kernel: [4311779.107000] usb 1-4: new high speed USB device using ehci_hcd and address 36
Jun 10 16:44:29 localhost kernel: [4311784.119000] usb 1-4: device descriptor read/8, error -110
Jun 10 16:44:35 localhost kernel: [4311789.231000] usb 1-4: device descriptor read/8, error -110

is all get, again according module is loaded (usb_storage)

:-k 

solution?

NO, did not found anything really helpful, except some googled pages, which refer to some changes is the 2.6.15 kernel......

cheers
guex

---

### Post by Klebon on 2006-06-10
I've figured out the problem guys. I'm using an Averatec C3500 tablet PC, and the new BIOS apparently doesn't support USB or PCI in linux at all, which explains why nothing showed up in dmesg. Thanks for the help anyway.

---

### Post by Guex on 2006-06-23
[QUOTE=Klebon]I've figured out the problem guys. I'm using an Averatec C3500 tablet PC, and the new BIOS apparently doesn't support USB or PCI in linux at all, which explains why nothing showed up in dmesg. Thanks for the help anyway.[/QUOTE]

bad to hear about your bios issue, cause my problem went away with the newest kernel-image (linux-image-2.6.15-25-k7) and my ipod is again properly detected.

guex

---

