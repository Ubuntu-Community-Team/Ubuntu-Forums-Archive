---
title: "Western Digital My Book Studio Edition II w/8.04.1"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by supercell on 2009-01-02
Will the aforementioned external hard drive work with Ubuntu 8.0.4.1? I plan to format it as an ext3 drive and use it as a backup for all Ubuntu servers I host. Will this work with Kubuntu as well?

---

### Post by Excedio on 2009-01-02
I currently use this exact same external hard drive (500gb). I personally use it for storing pictures and can easily access it from my desk where it sit as well as remotely via sftp.

Hope this helps in your decision making. :-)

~Lorenzo

---

### Post by supercell on 2009-01-02
So you are using ext3 on this drive?

---

### Post by supercell on 2009-01-02
So you are using ext3 on this 500G?

---

### Post by SeanHodges on 2009-01-02
I have the 1TB version, works fine for me using XFS, ext3 should work fine. By default it appears as a USB hotplugged device in Kubuntu.

---

### Post by supercell on 2009-01-02
Will I be able to backup 8G virtual OSes without a hitch, or is there a size limit when moving files to the external hard drive?

---

### Post by Excedio on 2009-01-02
I never formatted the drive when I plugged it in. Just plugged in in to the usb slot and am using it as another (external) storage drive.

~Lorenzo

---

### Post by ubersolid on 2009-01-02
> **supercell said:**
> Will I be able to backup 8G virtual OSes without a hitch, or is there a size limit when moving files to the external hard drive?

FAT32 has a limit of 4GB, ext3 and ntfs etc do not have this limitation as far as I know.

---

### Post by hjallen on 2009-01-23
Supercell,
I am also considering this drive.  Did you purchase it?  I am a fairly simple user but can follow directions.  Did you format to ext3?  If so, what steps did you follow?
Thanks

---

### Post by timcredible on 2009-01-23
i have a 500gb mybook, i formatted it with 100gb as fat32 and the rest as ext3.  i use the ext3 partition for backing up my linux systems, and the 100gb partition for backing up my ps3.  both partitions work with 8.04 and 8.10 (and probably every other version of ubuntu and linux made since 2004).  little advice with the ext3 partition - name it so that it mounts in the same place all the time if you're going to do backups, make it easier to config rsysnc or whatever you use.

also, to answer your question about partitioning, install gparted via synaptic and use it to partition, pretty easy, make sure you are on the correct drive though, and hit 'apply' after each step that you do.

---

### Post by supercell on 2009-01-23
It works perfectly! In Vista I used Acronis Disk Director Suite 10.0 to format the Western Digital My Book II to ext3 (worked flawlessly). The only problem was that I was unable to utilize the RAID 0/1 features, so in essence, it works fine but only as a 1.8 TB drive. I mounted it on Ubuntu (LABEL=WD1TB  /mnt/WD1TB  ext3  suid,dev,exec  0  0). I have had it up for over a week and I haven't had a single issue yet. I have also recovered a virtual machine from the drive with zero issues.

---

### Post by hjallen on 2009-01-23
Thanks for the responses.  Have any of you used it as an esata drive?

---

### Post by supercell on 2009-01-23
No I have not. I am using it strictly as usb 2.0. The server it is connected to does not have an on board eSATA and I don't foresee purchasing a PCIx eSATA any time soon (USB 2.0 is working just fine. Moving 8 GB virtual machines transfers quite quickly!). I hope this helps.

---

