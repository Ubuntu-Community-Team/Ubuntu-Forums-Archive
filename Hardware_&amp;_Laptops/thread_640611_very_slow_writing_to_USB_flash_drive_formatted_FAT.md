---
title: "very slow writing to USB flash drive formatted FAT16"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by lusth on 2007-12-14
Hi,

I'm trying to make a bootable usb flash drive to run linux (slax). I am running edgy desktop. I have formatted the USB drive to FAT16. When I copy over the file system from the cdrom iso, I get a transfer rate of about 125K bits per second. So it takes a looong time to perform the copy. If I am patient enough, the copy completes and I am able to boot off the USB stick. 

If I format the USB drive to ext3, for example, the copy doesn't take very long.

Here are some questions...

Am I doing something wrong (like mounting the USB incorrectly)?

Must I use FAT16 to make a bootable USB stick?

Is there a release of a tiny ubuntu out yet?

Thanks,

john

---

### Post by Thanoulis on 2007-12-14
I made s DSL bootable USB with FAT32 partition...it didn't take too long...
I believe that in order to keep your USB stick compatible with other OSes (Windows,BSD) its better to keep the FATxx not the ext3 partition.
As for the tiny Ubuntu, i do not know. Last time i've checked there wasn't.

---

### Post by lusth on 2007-12-14
Works! 7.5 Mbps instead of 0.125 Mbps.

Also, it boots!

Thanks for the fix. Do you know why the FAT32 writes
were faster?

john

---

