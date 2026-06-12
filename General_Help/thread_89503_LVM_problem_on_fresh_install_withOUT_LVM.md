---
title: "LVM problem on fresh install withOUT LVM"
date: 2005-11-12
forum: General Help
---

### Post by ttrygve on 2005-11-12
Alright, I'm trying to work through my "Incorrect metadata area header checksum" errors.  So I unplugged all my drives but hda, I zeroed it, and then ran a completely default install (5.10 i386) on it, booted up, ran the security updates, and then opened a terminal and ran these commands:

```

root@ent:~# lvdisplay
  Incorrect metadata area header checksum
root@ent:~# vgdisplay
  Incorrect metadata area header checksum
root@ent:~# pvdisplay
  Incorrect metadata area header checksum
  Incorrect metadata area header checksum
  Incorrect metadata area header checksum
  Incorrect metadata area header checksum
  --- NEW Physical volume ---
  PV Name               /dev/hda1
  VG Name
  PV Size               233.76 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               lxpgsV-MxsK-bc5K-XP0z-F42V-mgAN-10I4q8

```

If zeroing the drive before a default install (*not* using LVM) still causes those errors, what in the heck do I have to do to get rid of these problems?  I can't possibly be the only person encountering this.

---

### Post by tonym on 2005-11-13
What partition type have you used for this partition.  Is it still set to LVM?

Have you tried pvremove /dev/hda1?

How did you zero the drive?

---

### Post by ttrygve on 2005-11-13
[QUOTE=tonym]What partition type have you used for this partition.  Is it still set to LVM?

Have you tried pvremove /dev/hda1?

How did you zero the drive?[/QUOTE]

I'm sorry, I was getting my many installs of the day mixed up, and I should not have said "zeroed".  I had run "badblocks -vw" (which does a write,read test to every block of the disk with four different data patterns, 0xaa, 0x55, 0xff & 0x00) much earlier in the day (but that was the last time the drive was technically "zeroed"), and I had reformatted various different sized partitions as ext3 or reiserfs (usually making them different sizes from what I used the previous run).  But on that install I had not zeroed the drive, and though I didn't even try to use LVM in that install or the previous, some of the LVM data clearly survived somehow/where.

I just finished installing again, this time after actually zeroing the drive by running "dd if=/dev/zero of=/dev/hda", and this time I get no "Incorrect metadata area header checksum" messages, so I plan to set up LVM manually.

Where is this lvm metadata stored, though?  There must be an easier way to clean it out than waiting 5hrs on dd.  If I decide I want to get a fresh start again, is there a quicker way to just overwrite the relevant bits?  That would be *tremendously* helpful!

Thanks, and sorry about my confusion earlier!

---

### Post by sundancer on 2005-11-13
What about the 'normal' way:
o Delete your partition and create it as (i.e. 8[23]) or 
o set the partition type to anything other than 8e

That should do it and you don't have to wait more than just a second.

---

### Post by ttrygve on 2005-11-13
[QUOTE=sundancer]What about the 'normal' way:
o Delete your partition and create it as (i.e. 8[23]) or 
o set the partition type to anything other than 8e

That should do it and you don't have to wait more than just a second.[/QUOTE]

I've done several installs without any partitions of type 0x8e, but the "Incorrect metadata area header checksum" errors always came back until I zeroed the drive.  Believe me, I thought that should have been sufficient as well.

---

### Post by ttrygve on 2005-11-13
[QUOTE=sundancer]What about the 'normal' way:
o Delete your partition and create it as (i.e. 8[23]) or 
o set the partition type to anything other than 8e

That should do it and you don't have to wait more than just a second.[/QUOTE]

From [TLDP](http://tldp.org/HOWTO/LVM-HOWTO/initdisks.html):

>  When using LVM 1 on PCs with DOS partitions, set the partition type to 0x8e using fdisk or some other similar program. This step is unnecessary on PPC systems or when using LVM 2.

---

