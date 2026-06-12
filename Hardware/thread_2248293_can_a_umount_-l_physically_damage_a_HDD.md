---
title: "can a umount -l physically damage a HDD?"
date: 2014-10-13
forum: Hardware
---

### Post by david169 on 2014-10-13
Hi everyone,

just a quick bit of advice from you veteran Linux users would be grand!

Can a 'umount -l' do any physical damage to a drive as I'm getting some odd behaviour after doing that, even after deleting the filesystem and creating a new one in gparted?

They were jfs file systems, fsck_jfs managed to repair one of them and I've copied the data off but have resigned to the fact I've lost the other one. In Gparted I'm creating new filesystems on the two drives, one drive (sdg) makes a new jfs partition immediately , the other (sdf) takes about 5 minutes for the same size partition. Gparted says it's completed and then gives an error and both the drives disappear from /dev not to reappear until after a reboot. This also happens also if I just try to create the new partition on sdf only.

After gparted says it's done, it sits there 'Scanning all devices...' for a few mins then fails with: "Error fsyncing/closing /dev/sdg: input/output error"  giving me the options to Retry or ignore. Retry doesn't do anything, ignore gives me another error: "input/output error during read on /dev/sdg" with retry, cancel or ignore. again nothing but ignore does anything which then takes me back to gparted which then doesn't show the drives in it's list and they're no longer present in /dev.

So, any thoughts, other than don't umount -l in the future!

It's odd that sdg was the drive I was able to recover data from, formats fast as it should but this is the one gparted complains about.

thanks,
David

---

### Post by weatherman2 on 2014-10-13
No, unmounting a partition on a drive cannot damage a drive in any way I can imagine.  Forcing an unmount when not safe to do so could in some cases corrupt the filesystem (and maybe result in data loss) but not hurt the hard drive itself.

Have you checked the drive's S.M.A.R.T. status?  Have you tried GSmartControl and looked at S.M.A.R.T. Attributes?  Note that some of the names of healthy Attributes may be "pre-failure" which is a normal name for the type of Attribute, not indicating any problem.  GSmartControl will highlight any suspect Attributes in pink or red. (e.g. Pending Sector Count, which should have a RAW value of 0.)

---

### Post by david169 on 2014-10-14
hi,

yeah that's what I thought, reading the man for umount says it should clean up after itself. Thanks for the info on GSmartControl, I've installed it and had a cursory look at the drives which seem to report ok but I've not had time to investigate further. I'll look into it after work,

Thanks,
Dave

---

### Post by naradezza on 2014-10-14
I think you must format first, but your data will be lose

---

### Post by david169 on 2014-10-14
> **naradezza said:**
> I think you must format first, but your data will be lose

I know, I'd formatted it a half dozen times but it was still giving errors which is why I started this thread!

Forgot to mention that the two drives were attached to a 4-port PCI-E SATA card as I'd run out of SATA ports on my motherboard. Having plugged them directly into the motherboard the 'dodgy' drive has now taken a new JFS filesystem quite happily in the expected time so I'm wondering if that might have been part of the problem but it could also have been coincidence the PCI-E card is a Lycom PE-120 if anyone's used one before.

GSmartControl said the drive was fine although did flag up 100's of warnings about my system drive so might consider changing that before too long!

Just plugged the drives back into the SATA card and it's not mounting one of the disks again, swapping to other ports on the card and its fine.... looks like I might have found the culprit. will need to do some more digging

---

### Post by david169 on 2014-10-14
A little more digging and it seems that the drive and SATA card just don't like each other.

Plugging the drive I've had issue with into my motherboard SATA socket and it works, can be formatted fine and is happy.
Plugging in a different HDD into the SATA card and that drive can be formatted and is happy

I actually ordered 2x off the SATA cards and didn't end up using one so I've swapped that over and the same behaviour. It seems it can read the drive ok as it was content to mount a filesystem created when my motherboard made it but gets upset when I try and create one on that drive via the card.

Just downloaded the linux drivers so will have a go installing them instead of the default ones that came with the kernel so we'll see if that makes any difference.

---

### Post by weatherman2 on 2014-10-14
> **david169 said:**
> GSmartControl said the drive was fine although did flag up 100's of warnings about my system drive so might consider changing that before too long!


Depends on which Attribute is flagging.  If you have pending sectors, you should be really worried about the system drive.  Some warnings are bogus and can be ignored.  #196 "Reallocation Event Count" seems to be a false error as I've seen it on even brand new drives, even two identical brand new drives that worked fine showed the same "error."

---

### Post by david169 on 2014-10-15
> **weatherman2 said:**
> Depends on which Attribute is flagging.  If you have pending sectors, you should be really worried about the system drive.  Some warnings are bogus and can be ignored.  #196 "Reallocation Event Count" seems to be a false error as I've seen it on even brand new drives, even two identical brand new drives that worked fine showed the same "error."

System drive has #197 "Current Pending Sector Count" Raw value = 3, was this what you were referring to!? I've bought a new system drive for this anyway, I think I pulled it out a laptop someone was throwing away so it doesn't owe me anything!

I've decided to return the Lycom SATA cards and should be receiving a [Highpoint R640L SATA]("http://www.scan.co.uk/products/highpoint-rocket-640l-lite-4-internal-port-hdd-controller#") card tomorrow (I know it's a RAID card but it's hard to find one that isn't a Lycom that isn't a RAID card!) I think it should work as a host adapter and at about 2x the price and good reviews so there's hopefully 2x the engineering in the card and it works with this drive!

---

### Post by weatherman2 on 2014-10-15
Yes, that means 3 sectors on that drive can't be read.  In theory that means up to three files may be corrupted - if one sector is in each file - or the sectors may not be in any file, may be in unused space.  If it's just a system drive with no data, the worst that could happen is that you experience weird system issues or crashes.  But if the surface of the drive is failing, you may eventually wind up with more bad sectors and more issues.

---

### Post by david169 on 2014-10-17
Thanks for the info.

Regarding my earlier problem I think I've tracked the problem down to the cables I was using... very strange but swapped the brand new sata3 cable for an old one and the behavior was back to normal. So it seemed that it only caused problems when writing a new filesystem - it could read and write data just fine in normal operation- and the problem only occurred with an external interface card. It was also only limited to my Seagate drives, my WD drives worked fine on the same cables to either SATA card which is why I never thought until now to check them... 

Very strange but I've got it working ok now.

---

