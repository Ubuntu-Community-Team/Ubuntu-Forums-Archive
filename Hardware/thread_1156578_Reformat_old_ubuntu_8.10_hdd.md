---
title: "Reformat old ubuntu 8.10 hdd"
date: 2009-05-11
forum: Hardware
---

### Post by alliance1975 on 2009-05-11
HP laptop. New hdd with ubuntu 9.04 loaded and operational. Using old hdd as an external backup. Old hdd has ubuntu 8.10. Current 9.04 can see old hdd but i cannot delete old files, cannot reformat. Some reason i can see but cannot alter original files. i would like to use as a clean backup disk to store home files. Can someone help me to get from a to b.

---

### Post by taurus on 2009-05-11
Install gparted and use it to delete all the partitions on that drive.  Make sure you have unmount the swap partition first before you can delete it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by orange-wedge on 2009-05-11
what are the file/directory permissions for the old hard drive?  i suspect you did a clean install of ubuntu on your new hard drive...  if you do this your user id could possibly be different from your old one thus making the permission incompatible.

if you don't need any of the data off the old hard drive i would suggest just reformatting and setting up your default admin user as the owner, ie your user.

if you do want to keep the files you can run the following on the hard drive, but be very careful where/how you run this.  MAKE SURE YOU USE THE CORRECT PATH TO THE OLD HARD DRIVE:

[HTML]
sudo find /old/hard/drive/path -type f -exec chown yourusername:yourusername \{} \;

sudo find /old/hard/drive/path -type d -exec chown yourusername:yourusername \{} \;
[/HTML]

the above will modify the owner of every file and every directory under the old hard drive.  i would first test it out on a nest of dummy directories in /tmp to see how it works.  

DO NOT RUN THE FOLLOWING:

[HTML]
sudo find / -type f -exec chown yourusername:yourusername \{} \;

sudo find / -type d -exec chown yourusername:yourusername \{} \;
[/HTML]

that could do damage to your entire system.

---

### Post by alliance1975 on 2009-05-11
> **taurus said:**
> Install gparted and use it to delete all the partitions on that drive.  Make sure you have unmount the swap partition first before you can delete it.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

Worked to perfection. Now have clear unallocated partition. Do you recommend ext2 or ext3 or other for reformatting. I will use for backup of 9.04 files.

---

