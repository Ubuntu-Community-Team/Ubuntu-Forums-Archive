---
title: "Intel 6300ESB 'hardware' RAID"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by Breepee on 2006-08-17
I use the hardware RAID in the 6300ESB southbridge of my board to create a RAID0 array of two disks. I know that it isn't really hardware RAID and many would say I should use Linux' software RAID instead. For compatibility reasons with Windows I can't use Linux' softraid. I still would like to access the drive in Linux though. How can this be done?

---

### Post by Breepee on 2006-08-18
Anyone an idea? Ubuntu now just ignores the BIOS and detects the two seperate drives.

---

### Post by Breepee on 2006-09-01
I can't believe there's _no way_ this can't be done... Linux surely must support Adaptec BIOSses which Intel uses for it's integrated RAID functionality (on this board). Anyone? I need to rescue some data so any help is appreciated.

---

### Post by Breepee on 2006-09-02
There are some old Redhat 9 and Suse 8.2 drivers on the manufacturers website (the board is an Asus PCH-DL). Can those be used in Ubuntu?

---

### Post by HAARP on 2006-09-02
There's a tool called 'dmraid' in the repos. That should do the job.
If you need help setting it up, tell me.

---

### Post by Breepee on 2006-09-02
dmsetup ls shows no arrays or drives. This should list any arrays, shouldn't it?

---

### Post by HAARP on 2006-09-02
Try
```
dmraid -r
```

---

### Post by Breepee on 2006-09-03
It says: ```
No RAID Disks
```:(
The RAID array was built by Adaptec HOSTRaid contained in the board's BIOS.

---

### Post by HAARP on 2006-09-03
Looks like dmraid doesn't support Adaptec or Intel-RAIDs. Sorry, I don't know any other solution :/

Type ```
man dmraid
``` to get more information abotu this tool, you can try fiddling with the settings there. But I doubt it will work...

---

