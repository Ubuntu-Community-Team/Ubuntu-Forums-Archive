---
title: "Dual boot M.2 NVMe UEFI RAID0 isn't recognized in Bionic (18.04.2 LTS)"
date: 2019-06-12
forum: Hardware
---

### Post by ashansol on 2019-06-12
Greetings! First post...

For starters, this issue isn't a deal breaker or anything.  More a fact finding mission.

While the title pretty much says it all, here are the specifics:

I'm dual booting Windows 10 Pro + Ubuntu 18.04.2 on an Intel Optane 900p.  That part is working just fine.  However, I also have a pair of Samsung EVO 970 M.2 NVMes installed on a UEFI based RAID0 (again, obvious from title).

The motherboard is an Asus Strix X299-E Gaming, and the RAID is Intel RST.  The RAID is by necessity formatted as NTFS, as the 280Gb Optane drive isn't enough for the storage hungry Windows 10, games and data + the Ubuntu partition.  Thus, I'd like to be able to mount the NTFS RAID under Ubuntu since I allocated only about 40Gb for the system.

Windows 10 is also a requirement, so pure Ubuntu isn't an option either (sadly).

Can anyone tell me if there is a workaround for Bionic, or if this has been addressed/corrected in Cosmic/Disco? I'd rather not upgrade from a LTS unless I know it's fixed.

Thanks!

---

### Post by oldfred on 2019-06-12
Are you booting from a drive that is not part of the RAID?
And can you separately change that drive to AHCI from Intel RST? Some systems allow different settings for different drives.
       Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)
Maximize SATA Capabilities with AHCI
[http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/whitepaper/whitepaper02.html](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/whitepaper/whitepaper02.html) 
    
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by ashansol on 2019-06-13
@oldfred Thanks for the reply!

I boot from the split Windows/Ubuntu Optane 900p drive. That drive is AHCI, and thus recognized by Ubuntu (clearly, since Ubuntu is installed on it) :).

The 2 Samsung M.2 NVMe Evo 970's are in RAID0 for performance, not redundancy.  I don't keep any critical data on them - just games and development trees (Chromium, et al).  I'm not contributing to the development of such projects, but having a lightning fast RAID drastically reduces compilation times, and is cheaper than having multiple Optane drives.  They are also in PCIe mode as my Intel i9 9900X has lanes to spare, and is faster than using the SATA bus.

I do appreciate you taking the time to point out those articles.  I'm aware of the ramifications of the various RAID modes.

What I'm really looking for is: do newer versions of Ubuntu recognize a UEFI controlled Intel RST RAID array? OR
if the LTS kernel doesn't support it, are there any known patches that can be compiled in?

FYI, I've also read Intel's approach to RAID on linux -- they are pretty much throwing their resources into md software raid.  Unfortunately, as Windows doesn't support software raid that doesn't help me.

Again, thank you for you time!

---

### Post by oldfred on 2019-06-13
I do not use nor know RAID.

But older BIOS RAID was called fakeRAID.
       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 
    
Does not the dmraid driver mount your RAID?
       [http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)
sudo mdadm --detail-platform
[http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)

---

### Post by docdoc2 on 2019-08-27
I have the same problem. The Intel link doesnt work anymore. Any ideas how i can make Ubuntu recognize the nvme RAID 0? mdadm seems to recognize it but gparted does not. I have two 512gb nvmes in one 1tb raid.

```
ubuntu@ubuntu:~$ sudo mdadm --detail-platform

Platform : Intel(R) Rapid Storage Technology
        Version : 14.8.0.2377
    RAID Levels : raid0 raid10 raid5
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 7
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:17.0 (SATA)
          Port1 : - non-disk device (MATSHITA BD-CMB UJ172 S) -
          Port0 : /dev/sda (WCC313X5)
```

---

