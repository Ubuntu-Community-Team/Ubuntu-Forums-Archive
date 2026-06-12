---
title: "Empty Trash Problem"
date: 2009-09-08
forum: Hardware
---

### Post by jeeshank on 2009-09-08
I have made a silly mistake while using UBUNTU. My USB TwinMOS 4GB was plugged in. I wanted to unmount it and clicked on a command Unmount volume and a menu popped up saying "Empty trash , Do not Empty Trash or Cancel" .

I clicked on "Empty trash" and i am unable to use my pendrive now.
When i connect that in Windows,it says memory 0. Can anyone help me???

Plz do reply.

---

### Post by jeeshank on 2009-09-09
hello ...!!

Plz someone do respond.
If it's not possible to use that pendrive plz tell me that at least..!!

Thanks.

---

### Post by drs305 on 2009-09-09
jeeshank,

Does this pendrive have data on it that cannot be replaced?

_If you don't care if the data is lost_, and mounting/unmounting from Windows still doesn't work, you could try to 'repair' it in Ubuntu. Try plugging it in, running Gparted (System, Admin, Partition Editor) and see if Gparted finds it. If so, select the drive and then Partition and Check. 

This assumes it is NTFS format: I believe Gparted runs the ntfsfix app, but if it's different you can install ntfsprogs and then try ntfsfix from the command line.
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXX  # make sure this reflects the proper device

```


Using either of these won't necessarily corrupt data on the drive, but I'd only use the options once you accept that as a possibility.

---

