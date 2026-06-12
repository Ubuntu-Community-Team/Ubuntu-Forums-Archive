---
title: "mpt2sas module in kernel 2.6.31?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jiggiday on 2009-10-29
Hi. Installing a Ubuntu 9.10 Server, 64-bit. I am trying to find the mpt2sas module, which was supposed to ship with kernel 2.6.30 or higher, but it is not available on the install media. Does anyone know if this module is available in Koala?

---

### Post by jiggiday on 2009-10-30
<bump>anyone?</bump>

---

### Post by jiggiday on 2009-10-31
If anyone is interested, CentOS 5.4 includes this module.

---

### Post by tomcarly on 2010-03-22
Having the same problem. It seems that it's still not included with the 10.04 beta release version. Does anyone know how to install ubuntu on such machines?

---

### Post by klajklaj on 2010-04-09
AFAIK there are two methods of installing 10.04 beta1 on these boxes.

First one, is booting up the DVD in the LIVE mode (in first menu choose something in line of "Try ubuntu without installing). It will boot up X, and load up mpt2sas kernel module automatically. Then on desktop you have graphical installer which will be able to recognize the drive and perform the install. It will bring you to the point that the box is installed but not able to boot up afterwards, since it's lacking mpt2sas module in kernel itself and in initramfs. That one can be solved pretty easily by rebuilding the initramfs (just after the install is finished, before you reboot the box), by adding the scsi_transport_sas and mpt2sas modules into initramfs.

Another one, for the ones used to textual installer, one just needs to copy the two kernel modules (scsi_transport_sas.ko and mpt2sas.ko) on a floppy or basically any removable storage. Only thing to bear in mind that the modules HAVE to be from the same kernel build as the kernel used in the installer (at the moment of writing this, it is 2.6.32-16-generic). Once the textual installer is started, you need to login to second VT, mount up the device having drivers on it, and insmod them (first injecting scsi_transport_sas). The device will initialize, and you will be able to go back to VT1 and finish up the install procedure. Same principle of rebuilding the initramfs with modules needed applies as for the first method.

I hope you will have luck with it - I tried both just yesterday on a Dell R710

---

### Post by jfabrizio on 2010-04-09
I would install Ubuntu on my server (this my [post problem]("http://ubuntuforums.org/showthread.php?t=1439402")).

Can you better explain this part:
> That one can be solved pretty easily by rebuilding the initramfs (just  after the install is finished, before you reboot the box), by adding the  scsi_transport_sas and mpt2sas modules into initramfs.

1) initramfs is a directory?
2) where I find the directory or file scsi_transport_sas and mpt2sas?

Thank klajklaj in advance.

---

### Post by klajklaj on 2010-04-09
@jfabrizio: Just heard back from my colleague that the rebuild od initrd is not needed, seems that the stock one which gets installed during ubuntu setup is already containing these modules. He said that after passing the disk detection (by manually loading kernel modules) and installing, the box worked just fine

Regarding the location of the kernel modules, they can be found in a package linux-image-<version>.deb. In my case, the package was called linux-image-2.6.32-16-generic_2.6.32-16.25_amd64.deb, found on install media in folder pool/main/l/linux.
One needs to unpack the deb file (using dpkg -x on another linux box for example), and copy scsi_transport_sas.ko and mpt2sas.ko to a removable media, to be found in lib/modules/2.6.32-16-generic/kernel/drivers/scsi and lib/modules/2.6.32-16-generic/kernel/drivers/scsi/mpt2sas respectively.

---

### Post by jfabrizio on 2010-04-09
Thank, but I don't exactly understand in which consist the operation
> 
adding the  scsi_transport_sas and mpt2sas modules into initramfs

initramfs is a directory? or is a script? Where I can find it?

Thank klajklaj in advance.

---

### Post by zyx007 on 2010-04-16
I managed to do it :

Copied mpt2sas.ko  and scsi_transport_sas.ko  to usb stick from a pc running 2.6.31-14 x86_64 kernel. Connected usb stick to  PE R710 and started installation of 9.1 x86_64. During installation extecuted shell, at #, loaded both .ko files, exited shell, successfully detected disks

---

### Post by djoh on 2010-09-30
.

---

