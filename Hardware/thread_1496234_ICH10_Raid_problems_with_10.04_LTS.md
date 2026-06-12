---
title: "ICH10 Raid problems with 10.04 LTS"
date: 2010-05-29
forum: Hardware
---

### Post by skozzy on 2010-05-29
I have a Gigabyte P55A-UD4P mainboard in my desktop PC, the 6 Intel ICH10 Ports I have configured as Raid with 6x 1TB Drives, when I attempt to load the LiveCD it disables all the drives in the array, doing so the boot time of the LiveCD can be several minutes. After shutting down Ubuntu and rebooting by Bios Post Screen reports ALL the Raid drives as offline, following another reboot the array is back online but this time the array is in an error state and begins to do a Verify (which takes over 6 hours).

Very annoying issue, is there someone here that can explain what might be going on and how to get around it.

---

### Post by ronparent on 2010-06-01
How is the raid defined in bios?

---

### Post by skozzy on 2010-06-02
6x 1TB Western Digital Drives as a single array with a raid0 128gb bootable partition and a 4.6tb raid5 data partition. Partiton 1 is GPT and partition 2 is GUID <-(I think, well what ever Microsofts =>2TB format is). Both partitions are also formatted as NTFS

---

### Post by dino99 on 2010-06-02
[http://neildecapia.wordpress.com/2010/05/15/ubuntu-lucid-10-04-on-a-raid-0%C2%A0array/](http://neildecapia.wordpress.com/2010/05/15/ubuntu-lucid-10-04-on-a-raid-0%C2%A0array/)

[http://ubuntuforums.org/showthread.php?t=1474950](http://ubuntuforums.org/showthread.php?t=1474950)

---

### Post by skozzy on 2010-06-02
Thanks Dino, but everything in those threads isn't giving me an answer to why 10.4 LTS is disabling my raid and causing it to rebuild and verify the raid5 partition each attempt to boot it. I am not installing anything yet till I find out why. If I do take the step to install it I won't be putting it on the raid drives, it will go on a ssd drive which is on a serperate controller.

If this version of ubuntu isn't able to make sence of the hardware in this pc then I won't push my luck installing it.

---

### Post by ronparent on 2010-06-02
I think I am beginning to make some sense now of what your setup is planned. Your raid is defined in bios but has it yet been partitioned in any OS?

I have no experience specifically with a raid5 in any version of ubuntu. I was hoping someone with that specific experience would jump in by now. What I can state is that gparted does not recognize partitions in any flavor of raid in 10.04. If you have established raid partitions, they should be seen and mountable in nautilus as of 10.04 . Also you should be able to verify partitions with dmraid in a terminal and the presence of symbolic links for those partitions by looking in /dev/mapper/. 10.04 may be otherwise be essentially useless in trying to partition an unpartitioned drive. I don't see however that dmraid would  have any particular difficulty assembling or recognizing an established array. Maybe some useful advice would be more forthcoming in the server forum?

---

### Post by skozzy on 2010-06-02
Thanks ronparent

The computer is a working Windows Vista 64bit computer. The onboard raid is enabled in bios and all 6 drives are assembled in 1 array divided into 2 virtual drives in bios, one drive is a 128gb raid0 and the other is a 4.6tb raid5. The formats are NTFS from Vista, drive 1 (the raid0) is GPT and drive 2 (the raid5) is GUID.

'If' I can get ubuntu to not disable this above setup during the livecd startup I might be able to use it and install it. The Vista OS is installed on a 64gb SSD and that is where I want to put ubuntu.

---

