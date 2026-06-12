---
title: "[SOLVED] Need to make device name persistent or change uuid of harddrives in a mdam r"
date: 2008-08-02
forum: General Help
---

### Post by Biochem on 2008-08-02
I've got a problem with my hardy server. Mainly, the device name (sda,...) of my hard drives shuffles at reboot. For ordinary partitions it's not a problem since I fixed my fstab to use UUID instead of /dev/sda1.

However, I also have a raid5 array. It doesn't prevent me from using it since it uses scan to assemble the array. I was thinking, what happen if one of the drives failes? I will get a email telling me that /dev/sdx has failed. But which drives is /dev/sdx?

I though I could just write the UUIDs of my drives somewhere but they seems to be all the same.

Here is the output of blkid

```
sudo blkid /dev/sd?
/dev/sda: UUID="c54ad01b-56bc-ac84-9c71-5a34b4830eee" TYPE="mdraid" 
/dev/sdb: UUID="c54ad01b-56bc-ac84-9c71-5a34b4830eee" TYPE="mdraid" 
/dev/sdc: UUID="c54ad01b-56bc-ac84-9c71-5a34b4830eee" TYPE="mdraid" 
/dev/sdd: UUID="c54ad01b-56bc-ac84-9c71-5a34b4830eee" TYPE="mdraid"
/dev/md0: UUID="V83m23-vvIw-YvZB-cQkS-Ja2a-IrsR-66Giyu" TYPE="lvm2pv"  
```

Anyone got an idea on how to either make the device name persistent so /dev/sda won't become /dev/sdb or to change the uuids of the drive to make them unique.

Of course any other suggestion are more than welcome.

---

### Post by Biochem on 2008-08-05
Anyone?

Not even a slight hint toward a clue, a pertinent reading or question that might help pinpoint the problem?

:(

---

### Post by fjgaude on 2008-08-05
When a drive fails you use the Serial Number of the drive related to the /dev/sd[n] to remove the drive. There are several ways to find the SN of a drive, here's one:

```
sudo hdparm -i -v /dev/sd[n]
```

You might have to install **hdparm** from the repository. And then you migth wish to make a list of the SNs for the drives you have, keep it.

Hope this helps.

---

### Post by Biochem on 2008-08-05
Thanks fjgaude, That is ezactly the kind of information I was looking for.

---

