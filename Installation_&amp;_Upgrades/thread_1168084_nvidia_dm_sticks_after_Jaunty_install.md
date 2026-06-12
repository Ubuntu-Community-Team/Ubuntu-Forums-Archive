---
title: "nvidia dm sticks after Jaunty install"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by RainKap on 2009-05-23
My setup: Tyan Thunder MoBo with nvidia "RAID" controller, 2 x Opteron dual core, 8GB RAM, 150GB Western Digital Raptor on SATA port 1 for /, /home & swap, 2 x Seagate Barracuda 320GB on SATA ports 2 & 3 for a RAID0 array. I was running Hardy, and decided to upgrade from RAID0 to RAID5, so I put in another 2 x Seagate Barracuda 320GB on SATA ports 4 & 5, after backing up the data from my RAID0 array (fortunately not a great deal on it), setting up the RAID5 array worked OK.

Decided to do an upgrade to Jaunty (so I could run Unison to keep files synchronised between my laptop, which is happily running Jaunty, and my desktop). Upgrade Hardy -> Intrepid -> Jaunty eventually completed, but the RAID array would no longer mount. Tore hair, did a clean install of Jaunty from the Alternate CD; RAID array still wouldn't mount. Tried rebuilding the RAID array while running Jaunty, but mdadm told me that sdb1 and sdc1 were in use by the system. gparted showed the nvidia device mapper as one of the devices. Tried adding "nodmraid" to the end of the "kernel" line in /boot/grub/menu.lst but that had no effect.

I'd really prefer to avoid using the nvidia "RAID" device mapper because this box doesn't dual boot - it's a pure Ubuntu AMD64 system. However I'm at my wit's end trying to get rid of the nvidia device mapper. The "nvidia raid" is disabled in the BIOS (though when I bought the system it was enabled for the RAID0 array), but Jaunty still seems to see it as enabled, I think.

Can anyone *please* point me to how to persuade Jaunty to run software RAID5 on those 4 Seagate disks? If the worst comes to the worst I could try enabling the nvidia "RAID" in the BIOS for SATA ports 2, 3, 4 & 5, but I'm reluctant to go down that road if I don't have to...

Thanks in advance

Ian

---

### Post by ronparent on 2009-05-24
I'm not completely clear on your setup, but it appears that you want to salvage those old raid drives to add to a mddam raid setup. If that is the case you probably still have dmraid installed and active at some level.  Also the raid metadata as defined by the riad bios is still present on those disks. I sounds to me that what you will have to do is erase the metadata and uninstall dmraid. You would erase all existing dmraid metadata with the command sudo **dmraid -E**. At his point you can verfy that the data is gone with **sudo dmraid -r** (The rsponse will be blank). Then, if you have not further use for dmraid, uninstall it with **sudo apt-get purge dmraid**. This last step should eliminate all the fakeraid references in /dev/mapper and eliminate all possibility that dmraid would run in conflict with mddam. At this point you should be able to use mddam to configure and get your array up and running as you please. I hope this response is useful to you.

---

### Post by RainKap on 2009-05-24
Thanks very much, ronparent - I'll give that one a whirl when I'm next allowed to get on to my desktop PC. She Who Must Be Obeyed wants some help in the garden tomorrow so I don't know when that will be... I'm downstairs with my little laptop (Aspire One running Jaunty Netbook Remix) to compose this. I was on the point of saying, "Stuff it, I'll drop back to Hardy on my desktop", because I'd hit another gotcha, which will be the subject of another post...

To clarify a bit on my setup: I bought the PC with no OS installed, but made the mistake (in hindsight) of telling the company who built it for me that I wanted the two 320GB drives set up as a RAID 0 array. When I installed Hardy (after playing with some earlier releases of Ubuntu) I switched off the nvidia RAID in the BIOS, and used the alternate install CD to set up a 2-disk RAID 0 array, not knowing whether I was using true software RAID or dmraid. When I added the two extra 320GB disks about a month ago, with the aim of setting up a 3 + 1 RAID 5 array, I definitely succeeded in using mdadm under Hardy to set up the array. The grief started when I went along the upgrade path from Hardy -> Intrepid -> Jaunty; the immediately obvious symptom was that the UUID for md0 in /etc/fstab wasn't recognised :( After deciding to re-install from the Jaunty Alternate CD (because opening a terminal failed, with an error message that the child process couldn't be created, and Synaptic couldn't commit any changes to installed packages), I *still* couldn't persuade the system to recognise the RAID array, and I noticed that syslog was reporting that the mdo array disappeared at bootup! That was what led me to try to wipe out all the metadata on the RAID array and try to start again from scratch...

Anyway, thanks again for the pointer - I'll try it out and report back.

Ian

---

### Post by RainKap on 2009-05-25
Hi again Ronparent

*YOU ARE A STAR* - I followed the recipe you gave me, to use dmraid to delete the nvidia raid metadata from my two older 320GB drives, removed dmraid and restarted, then it was a piece of cake to use gparted to set up the 4 partitions on my 320GB drives, and kick off mdadm to create the RAID5 array - it's running at the moment, with a bit over an hour to go. After that, I'll edit /etc/fstab and I should be go with 900GB(ish) of RAID5 to store my audio files.

Thanks again

Ian

---

