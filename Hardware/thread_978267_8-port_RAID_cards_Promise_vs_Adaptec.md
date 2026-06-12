---
title: "8-port RAID cards: Promise vs Adaptec"
date: 2008-11-10
forum: Hardware
---

### Post by McLogic on 2008-11-10
Promise and Adaptec 8-port hardware RAID cards cost about the same, at $520 (USD). **Both companies give no .deb support** (Ubuntu/Debian), just .rpm support (RedHat/SUSE). I need to know people's experience with these cards on Ubuntu. 

I'm looking to run a RAID-5 or RAID-6 system, 5 disks at first.

[Promise STEX 8650](http://www.promise.com/product/product_detail_eng.asp?product_id=195)[LIST]
[*] Supports Fedora/OpenSUSE officially (along with pay rpm-based-distros)
[*] Web-browser-based config utility  
[/LIST]

[Adaptec RAID 3805](http://www.adaptec.com/en-US/products/Controllers/Hardware/sas/value/SAS-3805/)[LIST]
[*] Only supports "Enterprise" rpm-based distros
[*] Java-based config utility
[/LIST]

Both have:[LIST]
[*] "Open source" driver (whatever that means to them)
[*] 512 megabyte DDR2 cache
[*] Hardware parity processing
[/LIST]

Can't tell if both have:[LIST]
[*] Spin down drives that are not in use
[*] Use all drive space, even when replacement drives are larger
[*] Run many arrays off one card
[/LIST]


More:
I would be happy with software RAID, as speed is not important. Reliability and ease-of-use matter most then cost matters a little and speed matters less. **The 100/T network will be the bottleneck. **Software RAID appears to need a lot of skill to replace disks and rebuild. 

Hardware maintenance (like replacing failed disks) will be given to someone local to the system. So they need to get _a blinking light_ on the drive bay when a disk fails, and an easy-to-use interface to start rebuilds (auto-rebuild would be best).

---

### Post by ilrudie on 2008-11-11
Soft raid will probably be the most reliable.  You will be able to rebuild the array from the disks in the event of controller failures or even total system failure.  You should be able to stick the disks in a new box and as long as the box can accept all the disks rebuild a working array.  That being said it can be more complicated to administer a soft raid but once you learn what do you can have very nice reliability.  

I have not worked with promise hardware raid but I have built a CentOS server on a hardware raid mirror off an adaptec card.  It was essentially trivial.  I configured the card at boot and installed CentOS without problems.

Edit:  Not sure if it will matter but for the record this was a scsi raid controller.

---

### Post by psusi on 2008-11-11
Another nice thing about software raid is you can set up mdadm to email you in the event of a disk failure, so you can call whoever is physically near and tell them to go power down the machine and swap the bad disk, then you can just ssh in and tell mdadm to add the new disk to the array and rebuild.

---

### Post by McLogic on 2008-11-12
> **ilrudie said:**
> Soft raid will probably be the most reliable[...] That being said it can be more complicated to administer a soft raid but once you learn what do you can have very nice reliability.

I need to have a blinking light on a hot-swap bay. Anything less and they risk pulling the wrong drive. None of these people are going to open a case. I don't know of any product that could give me a blinking light on the drive bay for a failed drive.

I don't know how to administer software RAID. I'm willing to learn to save 5 x $520 but I'm more worried about reliability then cost. Errors cause data loss, or at a minimum lost time.

> **ilrudie said:**
> I have not worked with promise hardware raid but I have built a CentOS server on a hardware raid mirror off an adaptec card.  It was essentially trivial.  I configured the card at boot and installed CentOS without problems.

Edit:  Not sure if it will matter but for the record this was a scsi raid controller.

It should not matter that it was SCSI. It matters that it is CentOS, as that is an rpm-based distro (and they make it as close as possilbe to the adaptec-supported RHEL).

---

