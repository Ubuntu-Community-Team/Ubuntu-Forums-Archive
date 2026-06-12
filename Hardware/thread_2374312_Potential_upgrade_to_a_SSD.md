---
title: "Potential upgrade to a SSD"
date: 2017-10-14
forum: Hardware
---

### Post by flipper8827 on 2017-10-14
I am ujsing a second hand HP Elite Book 8470w Mobile Workstation and would eventually like to upgrade the current 500gb conventional HDD to a 1tb SDD. Could any onm recommend an ssd and a m,method for transferring my existing   xubuntu installation to the now ssd?

---

### Post by oldfred on 2017-10-14
I have two smaller Samsung, one 840 which I have had for about 2 years and one 850 which I have used for 1 year. No real issues.

I suggest just doing a new clean install. 
Are you dual booting?
UEFI install or old BIOS type install?

You cannot dd gpt partitions only a gpt drive as both partition tables & partition itself has data that must match. & Backup partition table is to be at end of drive, a dd from a smaller drive will put it in middle of larger drive. May be repairable with gdisk & sgdisk, but do not know details.

And since new SSD drive you want to make sure partitions are on correct boundaries. All newer partition tools do that.

I suggest a new install using gpt whether you want UEFI or BIOS unless you have Windows in BIOS mode as that can only boot from the 36 year old MBR(msdos) partitioning. Then you can restore from your backups. You do have good backups that would let you easily re-install and restore system anyway, right?
But you will have old drive, so anything you forgot to include in backup is still on old drive.

---

### Post by flipper8827 on 2017-10-15
> **oldfred said:**
> I have two smaller Samsung, one 840 which I have had for about 2 years and one 850 which I have used for 1 year. No real issues.

I suggest just doing a new clean install. 
Are you dual booting?
UEFI install or old BIOS type install?

You cannot dd gpt partitions only a gpt drive as both partition tables & partition itself has data that must match. & Backup partition table is to be at end of drive, a dd from a smaller drive will put it in middle of larger drive. May be repairable with gdisk & sgdisk, but do not know details.

And since new SSD drive you want to make sure partitions are on correct boundaries. All newer partition tools do that.

I suggest a new install using gpt whether you want UEFI or BIOS unless you have Windows in BIOS mode as that can only boot from the 36 year old MBR(msdos) partitioning. Then you can restore from your backups. You do have good backups that would let you easily re-install and restore system anyway, right?
But you will have old drive, so anything you forgot to include in backup is still on old drive.

I would be doin a clean legacy or bois install probably to a mi nimum of a 512GN ssd with Zesty.

---

### Post by oldfred on 2017-10-15
Even with my very first 60GB OEM SSD, I used only gpt partitioning.
And since that system was BIOS only, but I then hoped to soon update to a new system with UEFI, I included both an ESP - efi system partition for future use and the required bios_grub partition to boot in BIOS mode from gpt.
I still do the same with larger flash drives, both an ESP & bios_grub. Both are relatively small, so not much space used and gives flexibility later.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[/LIST]

---

