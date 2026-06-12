---
title: "RAID5 using mdadm, how to mount /dev/md0?"
date: 2005-11-29
forum: General Help
---

### Post by ggduff on 2005-11-29
After using mdadm to configure 3 identical IDE drives in a RAID5 array as /dev/md0, how do I now 'mount' this array and start using it? The [mdadm tutorial]("http://www.linuxdevcenter.com/lpt/a/2776") that I used to make the array stopped short of telling me how to do that.

The OS is Ubuntu 5.10, on hda1 (80GB Maxtor with default partitions.) This is the master drive on the primary IDE controller.

The RAID5 drives are all 300GB Maxtors (3), each with a single primary ext3 partition as: /dev/hdb1, /dev/hdc1, and /dev/hdd1

I partitioned them first, then formatted them with their filesystems, and then created the RAID using the tutorial listed here: [http://www.linuxdevcenter.com/lpt/a/2776](http://www.linuxdevcenter.com/lpt/a/2776)

I did not use the optional mdadm.conf file.

I go into Disk Administrator and the 'enable' option does not mount the drive, nor can I mount it manually. Also, in the Disk Administrator I notice that the first two drives do not say ext3 filesystems, but rather *unknown* and the third disk in the array now says unformatted. All 3 said ext3 before setting up the RAID. I'm assuming this is normal, as I know RAID5 needs that 3rd disk for parity.

Thanks for any suggestions! :smile:

---

### Post by f1d094 on 2005-11-29
The filesystem for each should not be ext3 prior to creating the raid device. If you do: cfdisk /dev/hdc for instance, you should see "Linux raid autodetect".

To make the device:
mdadm --create /dev/md0 --level=raid5 --force /dev/hdb1 /dev/hdc1 /dev/hdd1

To format it:
mkfs.ext3 /dev/md0

To make it available to mount, add the following to /etc/fstab:
/dev/md0   /mymountpoint  ext3  defaults 0 0

To mount:
mount /mymountpoint


Enjoy.

---

### Post by ggduff on 2005-11-30
that worked perfectly. Thank you! ;)

---

