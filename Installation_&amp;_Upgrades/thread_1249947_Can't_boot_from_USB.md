---
title: "Can't boot from USB"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by candklasvegas on 2009-08-26
Hello everyone! I am new to the forums but not new to Linux. I am trying to boot V9.04 from a USB. I think I have everything installed on the USB. Used unetbootin to install on the usb. 
 
This is what I get when booting from usb. It loads and looks like it is going to boot but then at the bottom is says "loading boot sector... booting... boot error".
 
After the boot error then nothing else happens.
 
What could be going on? I have searched and searched but found nothing.
 
Any help would be appreciated.
 
Thanks

---

### Post by dstew on 2009-08-26
Has the USB stick been set up to boot from the boot sector? Usually you need to boot from the MBR, not a partition boot sector.

---

### Post by Mighty_Joe on 2009-08-26
> **dstew said:**
> Has the USB stick been set up to boot from the boot sector? 

I'd think unetbootin would do that.
I've had some problems with unetbootin.  I'll get a USB drive to boot once and that's it.  
@candklasvegas: you tagged your post with "ubuntu netbook remix".  Are you sure that's the version of Ubuntu you are using?  It gets distributed as an IMG file. I don't think unetbootin would work with that format.  You should use ImageWriter, as detailed in the [UNR install instructions]("https://wiki.ubuntu.com/UNR/Installation/Easy").
unetbootin should work fine with the regular Ubuntu ISO.  I ran into a problem with the [USB Creator]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865") where it would not work without a partition table.  Try deleting the existing partition and creating a new FAT32 partition, then use unetbootin.

---

