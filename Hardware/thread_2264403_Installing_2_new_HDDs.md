---
title: "Installing 2 new HDDs"
date: 2015-02-07
forum: Hardware
---

### Post by uaebuntu on 2015-02-07
I need some help in installing 2 HDDs to a working system as I am getting errors partitioning and formatting the second drive.

I had two spare 1TB disks left over from my SAN when I upgraded it. Wanted to add these to an existing Ubuntu 14.10 machine which has 1 SSD already installed. So I added the 2 SATA disks there was already the CDRom and SSD attached so I used the next two SATA ports on the Motherboard, the system rebooted OK

```
sudo lshw -C disk 
```

gave me

*_disk:0
logical disk  /dev/sdb
PATRIOT 128GB SSD

*_disk:1
logical disk /dev/sdc
WDC 1TB Hard Disk

*_disk:
logical disk /dev/sda
WDC 1TB Hard Disk

so I proceeded with gparted, as the disks had previously been used in the SAN they were already partitioned (EXT3), I deleted all the existing partitions and created 1 primary partition on each which I formatted as EXT4. When trying to logout of gparted I got  **Error fsyncing/closing/dev/sdb:Input/Output error** this wouldn't go with **retry** and the original screen still showed it was scanning. when I tried to** ignore** I got similar errors on sdc1 and scd.

I couldn't get back into gparted or use the onscreen shutdown, did

```
sudo shutdown now
```

and got the following sudo errors

sudo:unable to open /var/lib/sudo/jim/1
sudo:unable to execute /sbin/shutdown: Input/Output error

did an "engineer's reset" and it rebooted just fine, I checked the BIOS and it recognised the 3 hard disk drives

1st [SATA: SM-PATRIOT PS]
2nd [SATA: PS-WDC WD1001]
3rd [SATA: SS-WDC WD1001]

Only one of the ITB disks was recognised by the filemanager so I ran lshw again and gparted to re partition and format the second disk again. same results. Both disks were working OK when I took them out of the SAN so I don't know what to do next.

When I get the second disk recognised by the system, the aim is to set them up as a RAID combo as I have tons of space on the SAN and only wanted to add some space to the PC as the SSD takes too much looking after, moving stuff to the SAN to prevent it filling up, so I'll keep the SSD for system tasks and a few other performance things I want but move all the /home/ directories to the HDD/RAID

---

### Post by uaebuntu on 2015-02-07
Looking at the lshw output, a version attached to the original post, I see that both HDD have the same physical address..... could this be at the root of the problem?

---

### Post by oldfred on 2015-02-07
I do not know RAID, but if drives were RAID that can interfere with standard partitioning.
And you cannot have duplicate UUID or if gpt duplicate GUIDs.

       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdc


 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by uaebuntu on 2015-02-07
Thanks,

haven't got as far as building the RAID yet, its the **Input/Output errors** and the fact **only one of the new disks is recognised** that I'm trying to fix.

If necessary I could fall back to just one disk. to cure the over capacity of the SSD, I have a regular backup policy to the SAN, then I copy the SAN and store that at work.

If I can get both HDD recognised by the system,  then I will experiment with RAID after. If I was sure there were no other roblems I could also do a fresh install and restore, but at this point I think I may have some underlying issue I need to fix.

---

### Post by uaebuntu on 2015-09-22
Not really solved.

I gave up and just installed 1 drive and reinstalled Ubuntu 15.04 from scratch and used the partioning at install time to mount the single HDD at /home.

Not ideal but it saves all the messing about I wa doing rather than using the system for fun which is what it is really all about.;)

---

