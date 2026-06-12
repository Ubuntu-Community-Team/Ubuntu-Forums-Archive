---
title: "Won't boot after removing LUKS Encrypted drive"
date: 2020-02-26
forum: Hardware
---

### Post by ragge1234 on 2020-02-26
I had a separate SSD encrypted with LUKS, with nothing important on it, I was just playing around with it. 
I ended up physically removing the SSD from my system, and when i tried to boot back into ubuntu it wouldnt post. See image

---

### Post by yancek on 2020-02-26
The last two lines in the image you posted indicated the system time out waiting for a specific device.  Make a note of that device UUID and check it with the output of sudo blkid.  Also check to see if you have an entry for it in /etc/fstab.

---

### Post by TheFu on 2020-02-26
Those last number on the end of each fstab line matter.
**man fstab** explains.
```
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism availâ
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.
```

The options field has some nice capabilities:
```
              noauto do not mount when "mount -a"  is  given  (e.g.,  at  boot
                     time)

              user   allow a user to mount

              owner  allow device owner to mount

              nofail do  not  report  errors  for  this  device if it does not
                     exist.
```

This assumes the missing storage isn't part of the boot.

---

