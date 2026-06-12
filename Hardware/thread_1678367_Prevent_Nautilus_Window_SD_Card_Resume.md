---
title: "Prevent Nautilus Window SD Card Resume"
date: 2011-01-30
forum: Hardware
---

### Post by frogotronic on 2011-01-30
Hello,

  Using Karmic Koala 9.10 and an HP6910p with an SD/MMC card reader.  If I have an SD card in the reader during suspend, the machine hangs on the way down (won't complete the suspend cycle).  The bug is reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706124](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706124)

and the workaround here:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/468298/comments/8](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/468298/comments/8)

and reproduced here:

[COLOR="Navy"]Create a file in gedit, using

```
sudo gedit
```

Then, type this into the text editor;

```
#!/bin/sh

case "${1}" in
        suspend|hibernate)
          for MOUNTPOINT in `mount | grep vfat | awk '{print $3}'` ;
          do
            umount $MOUNTPOINT ;
          done
                ;;
        resume|thaw)
          # nothing
                ;;
esac
```

Save the file as */etc/pm/sleep.d/20_umount-fat* and make the file executable with the appropriate permissions.

In a terminal;

```
sudo chmod 755 20_umount-fat
```[/COLOR]

After doing this,the suspend and resume now works perfectly with an SD card in the reader.

My question is **how do I have the SD card auto-mounted during the resume cycle *_without_* having nautilus popping up a new window each time I resume?**

Thanks,
CH             :-k

---

