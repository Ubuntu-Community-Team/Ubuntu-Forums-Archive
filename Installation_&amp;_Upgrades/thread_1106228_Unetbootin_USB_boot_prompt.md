---
title: "Unetbootin USB boot prompt"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by nathand28 on 2009-03-25
I can make a bootable USB with Unetbootin, but when it comes to booting, it brings up a boot prompt, which basically says:
```
Copyright Peter Anvin *** etc.
boot:
```
I can enter any words here, but it says cannot find kernal image.
So, how would I load the kernal?
This is with [Sugar on a stick]("http://wiki.sugarlabs.org"), by the way. It happens with any distro.

---

### Post by pastalavista on 2009-03-25
I have made several live usb distros with unetbootin and I only have to press 'enter' as the distro bootup is already selected as 'default'. Haven't tried any other selections except 'boot from hdd'. Possibly you have a bad copy.

---

### Post by nathand28 on 2009-03-25
I tried pressing enter:
Brings the error " Couldn't find the kernel image: Linux."
I have reinstalled Unetbootin 3 times, and tried on multiple USB's.
Maybe try an older version?
I know using the Ubuntu LiveUSB creator works.

---

### Post by pastalavista on 2009-03-25
Unetbootin should be installed on your hard disk. There are Linux and Windows versions available. Run Unetbootin from your main OS to create a bootable USB 'disk' from an .iso (disk image) file. It will download many different distro files for you or you can use an .iso you have already downloaded to "burn" them (extract and install the disk image.. in your case, Sugar-on-a-stick.iso) to a USB flash drive. Don't just save the .iso on the USB drive... it must be extracted there. That's what Unetbootin does. It isn't easy to make a bootable flash drive.

---

### Post by visibletrap on 2009-05-21
I have got the same problem to you.

For me, as you say switch to usb-creator is instanly work.

---

