---
title: "Auto Mounting NTFS partitions"
date: 2009-09-30
forum: Hardware
---

### Post by Plasma_Snake on 2009-09-30
I'm using Ubuntu 9.04 on my laptop. I intend to use it as my DL rig. Right now I use uTorrent in Win 7 but would like to shift to Transmission for the said purpose. Since the current partition for torrents is NTFS and Transmission runs at system startup, I want to know as to how to make the needed partition auto-mount so that the full process is automated and there are no errors regarding file location found with Transmission?

---

### Post by cyrus_the_virus on 2009-09-30
Install pysdm:
```
sudo apt-get install pysdm
```
Then go to System -> Admin -> Storage Device Manager and select the disk you want to mount and check "mount on boot time" and unselect "mount in read only". 

Check [this]("http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14") site for more info

---

### Post by drs305 on 2009-09-30
You can install ntfs-config. It will automatically make the mount point during setup and edit fstab to allow for automounting.

```

sudo apt-get update
sudo apt-get install ntfs-config  ntfsprogs

```

Once installed, you can start it via System, Administration, NTFS Configuration Tool.

---

