---
title: "Toshiba A505-s6033 Unable to boot from CD or USB"
date: 2010-02-16
forum: Hardware
---

### Post by flamesbladeflcl on 2010-02-16
Unable to boot any os from cd or usb, I've tryed multiple different Linux live CDs and live USBs, and a osx instal CD, none will boot. (these usbs and cds will boot on other laptops so it isn't a problem with them)

---

### Post by sanderj on 2010-02-16
You have to instruct your laptop to boot from CD (or USB).

See [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) specifically [here]("https://help.ubuntu.com/community/BootFromCD#BIOS%20is%20not%20set%20to%20boot%20from%20CD%20or%20DVD%20drive")

---

### Post by flamesbladeflcl on 2010-02-16
it is set to boot from a cd/usb and it will start to boot. it just fails before it finishes. on ubunutu it fails around "begin finding root filesystem..."

---

### Post by sanderj on 2010-02-16
> **flamesbladeflcl said:**
> it is set to boot from a cd/usb and it will start to boot. it just fails before it finishes. on ubunutu it fails around "begin finding root filesystem..."

Please be more precise; the message "begin finding root filesystem" is not found by Google, so I guess it's not the exact message.

---

### Post by flamesbladeflcl on 2010-02-16
It was "Begin:waiting for root file system...."
after that it said something about improper irq? (scrolled to fast to write down)
then "gave up waiting for root device" and went to busy box.

---

### Post by sirflyalot on 2010-03-02
I have the Toshiba A505-S6030, which is quite similar to your laptop.  I believe that the problem is with the Insyde H20 bios.  Some sort of IOMMU problem.

Here is something that I found, but does not completely apply.
[http://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling](http://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling)

None of the USB ports work with any current distribution of Linux on these laptops.  I have tried Ubuntu 9.10, and the most recent 10.04, and Fedora 12.

I have been through two different methods to get the wifi to work, as there is a lot of excellent documentation on how to get the Realcrap RTL8172/8192 to work.  It does not work.

There are also problems with the Intel core i series processors.  The processor problem will not be fixed until the kernel that comes with Ubuntu 10.10.

No idea what else is not working, I am sure quite a lot of other things don't function.

If it has not been too long since you purchased it, you should return this laptop.  It is too late for me, I am stuck with this piece of c**p.  Avoid any of the new Toshiba laptops like the plague.

---

### Post by flamesbladeflcl on 2010-03-06
I see well it has been too long. it is sad that it soundslike it is useless for linux until future notice >_<

---

### Post by brauliobo on 2010-05-06
same here.
With a USB stick it starts to boot and then give the error:
Unable to find a medium containing a live file system

---

### Post by dpcole72 on 2010-05-10
> **flamesbladeflcl said:**
> Unable to boot any os from cd or usb, I've tryed multiple different Linux live CDs and live USBs, and a osx instal CD, none will boot. (these usbs and cds will boot on other laptops so it isn't a problem with them)

I'm able to install on my A505-S6033, albeit with all powersave options (ACPI, et al) turned off at the pre-boot menu on the CD.

The remaining problem is, after installing, I get a blank screen or an error about not being able to read a table.  (I was trying to dualboot with Windows and that MIGHT be why.  I'm restoring with Toshiba's system restore discs and will try again AFTER defragmenting the machine after finishing the recovery setup.)  Well, that and the powersave options of course...  then again, if I run into problems like USB compatibility like you mentioned...  As I just bought mine I hope I can get a return if it doesn't work out.  A shame, the Toshiba is a nice model all around... at least for Windows.

---

### Post by theviking10 on 2010-05-11
Same problem, Toshiba A505-S6005. Booting 10.4 and Fedora 13 beta on USB, sends me to busy box with a "Unable to find a medium containing a live file system" error.


I think openSUSE will use a compatible Kernel - new one out in July. I'd hate to have to wait for 10.10. :(

---

### Post by HeX0R on 2010-05-11
i installed Ubuntu 10.04 64bit on this laptop but without ACPI suppurt... for now...

---

### Post by Lord Arctic on 2010-06-24
[http://ubuntuforums.org/showpost.php?p=9317100&postcount=11](http://ubuntuforums.org/showpost.php?p=9317100&postcount=11)
 
is where I found support for this problem, although you have to install from CD because the USBs wont work untill after the recompile

---

### Post by soad6 on 2010-11-28
This issue is fixed as of 10.10. It has to due to some improper irq handling in the BIOS or something like that. However as I stated its fixed in Ubuntu 10.10. I know this because I have this computer and I am running Linux on it.

---

