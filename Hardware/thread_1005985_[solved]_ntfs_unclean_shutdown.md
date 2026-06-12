---
title: "[solved] ntfs unclean shutdown"
date: 2008-12-08
forum: Hardware
---

### Post by pepperlim on 2008-12-08
I was transferring files via a USB portable drive (NTFS format). Unfortunately when I plugged it into Ubuntu it said:

"$LogFile indicates unclean shutdown (0, 0)        

Failed to mount /dev/yadayada    

Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly."

**But I found an easy solution via "http://linuxevangelist.blogspot.com/2008/07/fixing-ntfs-mount-error-in-gnulinux.html"**

After you follow the instructions, you just unplug the USB, and plug in back in and voila! its reads perfectly!

(This is a follow up from an archived thread which asked for feedback but unfortunately the user did not so I'm writing to say it works!)

---

### Post by rhcm123 on 2008-12-08
> **pepperlim said:**
> I was transferring files via a USB portable drive (NTFS format). Unfortunately when I plugged it into Ubuntu it said:

"$LogFile indicates unclean shutdown (0, 0)        

Failed to mount /dev/yadayada    

Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly."

**But I found an easy solution via "http://linuxevangelist.blogspot.com/2008/07/fixing-ntfs-mount-error-in-gnulinux.html"**

After you follow the instructions, you just unplug the USB, and plug in back in and voila! its reads perfectly!

(This is a follow up from an archived thread which asked for feedback but unfortunately the user did not so I'm writing to say it works!)

Or you can just force the mount with the included command, which i'll repeat here:
```
sudo mount -t ntfs-3g /dev/sda1 /media/portable -o force
```

Replace /dev/sda1 with whatever the heck you want to mount, and /media/portable with whatever the mount point is.

---

### Post by psusi on 2008-12-08
Forcing the mount except for read only mode is not a good idea since linux will not replay the journal, which can lead to data loss.  You really should just boot back into windows, and cleanly unmount the volume.

---

### Post by rhcm123 on 2008-12-09
> **psusi said:**
> Forcing the mount except for read only mode is not a good idea since linux will not replay the journal, which can lead to data loss.  You really should just boot back into windows, and cleanly unmount the volume.

NTFS is not journaled, and why not just mount it in read only with the -ro (i think that's it) flag and then unmount, then let HAL mount it.

---

### Post by psusi on 2008-12-09
> **rhcm123 said:**
> NTFS is not journaled, and why not just mount it in read only with the -ro (i think that's it) flag and then unmount, then let HAL mount it.

Yes, it is journaled.  And the reason linux refused to mount it when it was dirty was specifically because it knows it does not understand the journal so it will likely make a mess of things.

---

### Post by rhcm123 on 2008-12-11
> **psusi said:**
> Yes, it is journaled.  And the reason linux refused to mount it when it was dirty was specifically because it knows it does not understand the journal so it will likely make a mess of things.

:O, i did not know it was journaled... hmm... then again, the last file system i studied in depth was fat16... :) , and when i force the mount i've had no hiccups. Just brand this as a USE AT OWN RISK, but i've done it literally dozens of times (after windows crashes :) ) and had no problems.

And I should also note, NTFS is not a truly well supported filing system on linux. Apt-get ntfs-tools or whatever the package is called now to make this easier on you.

---

