---
title: "Bootable USB for BIOS upgrade"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-02-02
I want to upgrade my BIOS using [Lenovo's BIOS update in the form of an iso](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63027) but I don't want to burn a CD.  I've made bootable usb's of Ubuntu before using uNetBootin.  Is there a way to make a bootable usb just for upgrading my bios?

I also partitioned and formatted the usb drive using fat32, mounted the iso, and then extracted the files to the usb drive.  I made sure my laptop was set to boot from USB.  However, when I booted it said the USB drive was not bootable and to install a bootable disk to continue.

---

### Post by cariboo on 2009-02-02
I would use K3b to create a bootable iso using dos.

Open K3b and create a new data cd, then go to Project-->Edit Boot Images add your boot.img to the cd then add the files needed to flash your bios.

You can get boot images [here]("http://www.bootdisk.com/bootdisk.htm") they are an exe file, but you can use file-roller to extract the image file.

Once you are ready to burn, click the burn button and select create image only. After the image is finished use dd to copy the image to your use device:

```
dd if=bios_update.iso of=/dev/usbdevice
```

I've done the above with cd's many times, but haven't tried it with a usb device, but it should work the same.

Jim

---

### Post by MaindotC on 2009-02-03
I tried your directions and when I boot with the USB drive I get the message "Missing Operating System" (MOS) and then it boots to my hard drive.

First I tried using the dd command and the bootable iso from Lenovo.  I did this while the device was mounted, so when I listed the contents of what was on the device I got those weird, distorted charachters that messed up my terminal.  I tried booting and I got MOS.

I booted to my hard drive, tried the same thing but unmounting the device first.  This time the contents of the iso were extracted to the device, but when I booted I got MSO.

Finally, I actually read and followed your directions.  I still get MSO :(

---

