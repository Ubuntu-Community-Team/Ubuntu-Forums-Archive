---
title: "SLOW Internal hard drive transfer speeds"
date: 2013-11-08
forum: Hardware
---

### Post by Jimstehrman on 2013-11-08
Hi all,

I am experiencing internal hard drive transfer speeds on the order of 65 kb/s. This particular drive used as an external which had not great, but acceptable transfer speeds of 1.6 Mb/s. I removed the drive and again used it as an external over USB 2 and got similar speeds again, so it is not an issue with the drive itself. Using my windows partition I consistantly get speeds of 86 Mb/s or higher on reads and writes when the drive is used internally.

I am running Ubuntu 12.04 on a Lenovo Thinkpad T520, my main disk a solid state which has had no issues and is occupying the main hard drive bay. The external, turned internal drive inhabits the ultrabay, which used to house a DVD player. I used this ([http://www.ebay.ca/itm/Ultrabay-SATA-2nd-HD-Hard-Drive-Caddy-Tray-Lenovo-ThinkPad-T420i-T510-W510-T520-/300675409367](http://www.ebay.ca/itm/Ultrabay-SATA-2nd-HD-Hard-Drive-Caddy-Tray-Lenovo-ThinkPad-T420i-T510-W510-T520-/300675409367)) ultrabay adapter. The drive is a WD3200BEKT - 08PVM formatted NTFS so I can read it on my Windows partition as well.

The only potential answer I have come across thus far is that the partition is misaligned (really not sure what that means), which would require me to reformat the drive (I'd probably go FAT32, I've heard NTFS can have transfer speed issues???), and make sure I hit the "allign to MB" check box. I found this solution here ([http://askubuntu.com/questions/122512/slow-writing-hdd-speed-dues-to-a-misaligned-partition](http://askubuntu.com/questions/122512/slow-writing-hdd-speed-dues-to-a-misaligned-partition)), although I'm not sure it will work.
I am also suspicious of how Ubuntu handles the bay itself, that it might somehow be stuck in thinking that a DVD drive should be there and curtails transfer speeds.

Does anyone have more info or potential solutions that would not require a re-format? I have a lot of data on this drive and would rather not reformat a copy it all back.

Thanks so much!

---

### Post by Jimstehrman on 2013-11-08
more info: I have the drive auto mount with the following fstab entry:
UUID=8EDA1ED6DA1EBA83 /media/NTFS ntfs-3g uid=1000,gid=1000,umask=0022,sync,auto,rw 0 0

---

### Post by tgalati4 on 2013-11-08
Use the command *lshw* and see how the Ultrabay is handled.  Also check the BIOS for any switches.  Since the Ultrabay is a hot-swap device, it's possible that Ubuntu is constantly polling it, which would reduce speeds.  Removeable drives are treated differently than internally mounted drives because of the hotswap checking.

---

### Post by Jimstehrman on 2013-11-08
This is the output I get, nothing jumps out at me...

```
 
          *-disk:1
                description: ATA Disk
                product: WDC WD3200BEKT-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 02.0
                serial: WD-WXN1A8188729
                size: 298GiB (320GB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=a0ed29a9-5b11-4c4b-a23d-9a8323ada526
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/NTFS
                   version: 3.1
                   serial: 10049b36-3cee-d347-8c74-ad3f645da03e
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: ntfs initialized
                   configuration: clustersize=4096 created=2013-10-13 03:09:07 filesystem=ntfs label=NTFS mount.fstype=fuseblk mount.options=rw,sync,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted

```

---

### Post by tgalati4 on 2013-11-10
Perhaps find an old drive lying around and put ext4 on it and measure the transfer speeds.  I don't use Windows so I don't know how ntfs affects file transfer speeds.  Your Ultrabay should be a fully-compliant SATA device.  I have a T43p which has a funky IDE/SATA hybrid Ultrabay and using IDE would be slower than SATA transfer.

Perhaps the disk drive is a PATA/IDE drive with a SATA-to-IDE adapter internally?  That would slow down transfers as well.

---

