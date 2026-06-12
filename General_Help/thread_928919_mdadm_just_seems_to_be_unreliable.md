---
title: "mdadm just seems to be unreliable"
date: 2008-09-24
forum: General Help
---

### Post by Azzuron on 2008-09-24
[edit] The below problem was resolved by:

```
# aptitude remove mdadm
# reboot
# aptitude install mdadm
# reboot
```

After the above was run, the array was detected at boot time, and i was able to add the failed disk and rebuild the array. All is well and happy now. not sure how this originally occurred but glad its resolved for now.

---Original----
Hello. I have a mdadm built raid 5 array across 3 usb disks. Every time i reboot the server it seem to have a problem rebuilding the array. generally i can get it running again one way or another, but it is always a scary experience. Today i rebooted and it says that there is only one disk and it cannot start the array there are not enough disks. i know that there are 2 good disks, because when i shut down the array was working. I used to use EVMS and it worked great, never had any trouble with it. i was unable to figure out how to use cryptsetup with evms arrays, so i moved to mdadm. at first it was working great, but its getting rougher and rougher all the time. ive even taken all the disks and blanked all the drives. dd if=/dev/zero of=/dev/sd(a/b/c). no luck though. same trouble still. I guess im wondering what the hell i could be doing wrong to get this sort of behavior.  ive also been troubleshooting a problem where one of the disks after one of these recent failures of the array would not re-add to the array. even after blanking the disk with zeros it would come back saying it couldn't open the device, it was to busy. Please advise! thanks.

---

### Post by fjgaude on 2008-09-25
One of the things I've learned is that to pull a drive you first have to stop the array, then unmount it, else the drive will stay busy, with mdadm thinking it is part of an array. I've never zeroed a drive, but have used this command:

```
sudo mdadm --zero-superblock /dev/sd[n]
```

I've found mdadm to be super reliable, once you know what to do, when to do it.

---

