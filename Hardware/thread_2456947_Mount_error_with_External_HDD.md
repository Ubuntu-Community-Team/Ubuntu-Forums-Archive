---
title: "Mount error with External HDD"
date: 2021-01-22
forum: Hardware
---

### Post by ankitsub96 on 2021-01-22
The specific error is: "internal error no mount object for mounted volume"
I don't have windows right now, and the data in the HDD is very precious to me, so please help me with a way with minimal intrusion to the HDD data.

---

### Post by CelticWarrior on 2021-01-22
Welcome.

If the data is precious you should have backups. Recommendation is the same as always has been, one or more local copies in external drives, one in the cloud. Nowadays there's a plethora of services to choose from and most are free with a small storage space, up to 50GB with Mega.nz, or more spce if you want with a commercial plan.

This is to say that situations such as the one you're asking help for shouldn't exist, period.
And question so vague and missing any useful information shouldn't be asked either. So, please, give us something to work with. 

What OS and hardware specification?
Where is the data stored (medium) and file system type?
How exactly are you trying to access it and in what context there's a error message? And, please, the exact error message (it isn't the one you posted for sure).

Also keep in mind that very likely there's no remedy for hardware failure and also if only logical errors on a NTFS partition you may need Windows to correct it. This is to NOT give you false hope.

---

### Post by SeijiSensei on 2021-01-22
First, did you create a "mount point," an empty directory to which the volume will be attached?

For the moment, let's use one of the standard mount points that are included with Ubuntu.  

Start by locating the name of the device by using the command:
```
sudo blkid
```
You'll see something like this:
```

/dev/sda1: UUID="0d4de807-11eb-4093-a845-20bcb207a011" TYPE="ext4" PARTUUID="4544701d-01"
/dev/sdb1: UUID="117E-3816" TYPE="vfat" PARTUUID="d7351c5f-a98e-4322-a3f0-530a17ddfa52"
/dev/sdb2: UUID="09B621792A4E8D1E" TYPE="ntfs" PTTYPE="dos" PARTUUID="2ee42b46-7d71-45d8-96ed-2add4af5221d"
/dev/sdb6: UUID="c63247ef-2746-4c9a-b019-74201996bb7d" TYPE="ext4" PARTUUID="4c4941fe-30d0-4e2c-99fc-9b984969e015"
/dev/sdd1: LABEL="GAMES" UUID="887236057235F910" TYPE="ntfs" PARTUUID="5e191f5f-01"
/dev/sdc1: UUID="fb43230b-68ab-47d2-883c-c5bf0eed5e7e" TYPE="ext2" PARTUUID="1a3f0dfb-01"
/dev/sde1: LABEL="Windows USB" UUID="6034427303F02878" TYPE="ntfs" PTTYPE="dos" PARTUUID="76a7fe5c-01"
/dev/sde2: SEC_TYPE="msdos" LABEL_FATBOOT="UEFI_NTFS" LABEL="UEFI_NTFS" UUID="32F8-F627" TYPE="vfat" PARTUUID="76a7fe5c-02"

```
Here you see five devices, labelled /dev/sda through /dev/sde.  The numbers refer to partitions, e.g., /dev/sda1 refers to the first partition ("1") on the first drive ("sda").  Run the same command and identify your drive.  If this is an older, non-SATA drive, you'll see entries like /dev/hda1 instead.  Let's assume that you want to mount /dev/sdb1, the first partition on the second (SATA or SCSI) hard drive.  Run the command
```
sudo mount -v /dev/sdb1 /mnt
```
which should attach the filesystem in that partition to the directory /mnt.  Do you get errors?  If not, what does "ls /mnt" show?

---

