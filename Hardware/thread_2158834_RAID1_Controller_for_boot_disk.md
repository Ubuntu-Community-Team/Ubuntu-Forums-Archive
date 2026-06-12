---
title: "RAID1 Controller for boot disk"
date: 2013-06-30
forum: Hardware
---

### Post by pneumatic on 2013-06-30
Because the kernel devs are so pedantic about what should be, Linux does not support "fake RAID", which is essentially a group of drives that perform as one with the help of the CPU.  The kernel devs apparently believe that, because there isn't dedicated hardware performing the RAID calculations, there should be no support of such devices, no matter how useful.

In leiu of such pedantry, I need to build some servers that will reside in offices without IT staffing so things need to be as easy as fake RAID under Windows:

1) Two disks must serve as a single boot disk for the system (RAID1).
2) If either disk goes bad, the system should still boot (even if one disk is partially bad).
3) An email notification with bad disk detail needs to be sent upon detection of the bad disk.

I had purchased a Highpoint RocketRAID 2720SGL for this task but this controller disables the mvsas driver that my other disks are using (Supermicro MVSAS2LP JBOD with ZFS).

So many people seem to think that mdadm and scripting can be made to perform the above goals but I have spent weeks trying to pull it off.  It comes down to the issue of getting the system to boot when the primary disk fails.  Additionally, the boot loader can be installed on both disks but updates will only apply to one.

I really hate to see Microsoft so far ahead when it comes to simple things.  They don't discriminate against fake RAID and this stuff becomes a non-issue.

Please help!

---

### Post by Cheesemill on 2013-06-30
Linux has supported FakeRAID for years.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

However I would recommend using software RAID using mdadm instead of FakeRAID. Grub2 can happily boot from a RAID0 without the need for a separate boot partition on each drive.

---

### Post by pneumatic on 2013-07-02
Your link is to a document that lists instructions for 10.04 and 10.10.  I am trying to install a supported/modern version of Ubuntu on a fake raid.

But it doesn't work.

---

### Post by pneumatic on 2013-07-02
Here's an overview from someone who spent 200 hours trying to get this working:[URL="http://kevinmccaughey.org/?p=182"]

http://kevinmccaughey.org/?p=182[/URL]

I'll try FreeBSD.

---

### Post by pneumatic on 2013-07-07
> **Cheesemill said:**
> Grub2 can happily boot from a RAID0 without the need for a separate boot partition on each drive.

Also note that RAID0 has nothing to do with what I am trying to accomplish as originally posted.  I need a RAID1 system that will boot if there is a drive failure - something that the kernel devs have ignored because they are too pedantic to support a simple "fakeraid".

Windows does this trivially.

I don't care if "fakeraid" is low performance.  I just want to boot a server from a standby disk if the primary fails - without spending $200 on a RAID card.

---

