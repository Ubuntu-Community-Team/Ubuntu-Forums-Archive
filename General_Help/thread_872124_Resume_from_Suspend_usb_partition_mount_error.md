---
title: "Resume from Suspend usb partition mount error"
date: 2008-07-27
forum: General Help
---

### Post by toppknott on 2008-07-27
Hi all,

Is there some tweak that will get my USB disk's partitions to be re-mounted properly on resume? The improperly mounted partition in question is mounted as type "fuseblk" and it's an NTFS partition. My home folder is just a bunch of symbolic links to that NTFS partition, so when the NTFS partition isn't mounted properly, and I resume from suspend, my desktop icons come up as default gray paper symbols and I have no background (not to mention I can't access my linked files). 

I have to "sudo mount -a" at the command line every time I resume from suspend, then log in again to my desktop for things to return to normal. Any ideas?

---

### Post by DagMan on 2008-07-29
I haven't done this so I can't say if it will work, but one solution would be to adapt the solution here [http://www.array.org/ubuntu/post-install.html](http://www.array.org/ubuntu/post-install.html) ("USB persist" at the bottom of the page) to your situation.

That doesn't sound ideal as from the brief look it seems like it keeps the power on to the USB devices during a suspend.
Another way at looking to do what you're wanting is to add a script to /etc/pm/sleep.d that will remount your usb device at the correct mount point with the same permissions and options as the one's you want.
The script would look something like this, and there's a section in case you find you need to unmount it on suspend for some reason, otherwise just take that part out:
```
#!/bin/bash

case $1 in 

    resume|thaw)
    your mount command
    ;;

    suspend|hibernate)
    unmount command here if you find you need it
    ;;

esac

```

You can find more info on mount options here [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
and the fstab article has some good info on mount options [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you end up finding that the best way is to remount on resume, and want to look at when during the resume process to best do it, the scripts go by order of number and are here  /etc/pm/sleep.d/ for custom ones that you want to keep track of, usually empty to begin with, but also here /usr/lib/pm-utils/sleep.d/
It looks like they run from lowest to highest number on suspend, then highest to lowest on resume.  You can see what happened in what order in the log file /var/log/pm-suspend.log

---

