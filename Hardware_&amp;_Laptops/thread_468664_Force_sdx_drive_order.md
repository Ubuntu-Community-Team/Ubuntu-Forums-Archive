---
title: "Force sdx drive order"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by B-Con on 2007-06-09
Every time I boot my computer, Feisty decides to reorder my SATA drives, as listed by /dev/sd*, into some new, random permutation. This is quite obnoxious and makes writing scripts that rely on a drive being at a consistent location somewhat difficult. Is there a way to force Ubuntu to create the drives in a specific order? (And, as a side note, *why* on this bloody earth does it randomly order them on each boot?)

---

### Post by neptho on 2007-06-09
What type of hardware are you using?  I know that this happened to me with Adaptec card when 'SCAM' mode was on.. but aside from dropping udev and hardcoding paths, I'd like to suggest you use the UUID disk notation.

Here's mine as an example:

```
%ls -l /dev/disk/by-uuid
lrwxrwxrwx 1 root root 10 2007-06-08 14:10 07D7-0317 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-08 14:10 4ca63889-0784-4309-b517-44b9a3a54e43 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-06-08 14:10 a8de1ad3-1fa0-459c-aab9-1e71be6bee8e -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-06-08 14:10 da430233-e545-4ed0-a58c-4445540cc93d -> ../../sda4
```

---

### Post by neptho on 2007-06-09
Here's what the grub options would look like if you go this route:

```
# kopt=root=UUID=da430233-e545-4ed0-a58c-4445540cc93d ro
..
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=da430233-e545-4ed0-a58
c-4445540cc93d ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

---

### Post by B-Con on 2007-06-09
For some reason, one of the more recent Feisty updates made it such that the hard drive I boot from is now an hd* drive, rather than an sd* drive. So I have no problems booting to the drive.

I can use the UUID for /etc/fstab to choose my mount points, but the problem is that my drives are encrypted with Truecrypt and I need to mount one of them manually with a password.

---

### Post by neptho on 2007-06-09
> **B-Con said:**
> For some reason, one of the more recent Feisty updates made it such that the hard drive I boot from is now an hd* drive, rather than an sd* drive. So I have no problems booting to the drive.

I can use the UUID for /etc/fstab to choose my mount points, but the problem is that my drives are encrypted with Truecrypt and I need to mount one of them manually with a password.

The hdx/sda change is due to a change in libata upstream.  It hit a couple of my REMOTE machines which I did not have console access to; I was not very happy, either.

You should be able to rewrite your scripts to use /dev/hdX rather than /dev/sdX.  I'd like to say this is the only time you'll run into this, but Linux is as Linux does.

Update your fstab with the UUID for these drives, and the problem should go away.  I know it's possible to load TrueCrypt disks from fstab.

---

### Post by B-Con on 2007-06-09
I have four drives, two IDE (including my OS drive) and two SATA (my data drives, one of which is encrypted and I hate having the device number changed on me). The OS drive is called hda, but the other IDE and the two SATA are all randomly named sd* devices. The problem is that I need to map one of the SATA drives, which is randomly assigned it's device letter each boot-up, via TrueCrypt.

I've looked around a bit, and I think it's only possible to mount a TrueCrypt volume automatically with /etc/fstab if you use a keyfile, but I'm using a user-supplied password. But this still requires that I know which device I want to mount with TrueCrypt, which I don't since it's randomly changing on me.

**Question changed:**

I suppose what I need is a way to be able to write a script to look up what disk device name is associated with a specific UUID. Then I can use that script to dynamically determine which device name is associated with the UUID of the device I want to use, then use that device name as input to TrueCrypt (because TC won't recognize UUIDs).

$ ls -l /dev/disk/by-uuid 
only returns the UUIDs for devices that are mounted, which sucks. Is there a way to get the UUID listing for ALL drives that exist? Then I figure I could just grep the output for the UUID I know I'm looking for and use awk to isolate the specific device name.

---

### Post by neptho on 2007-06-09
> **B-Con said:**
> $ ls -l /dev/disk/by-uuid 
only returns the UUIDs for devices that are mounted, which sucks. Is there a way to get the UUID listing for ALL drives that exist? Then I figure I could just grep the output for the UUID I know I'm looking for and use awk to isolate the specific device name.

Temporarily mount the partitions to get the UUIDs.  awk and sed are your best friend.  Perl, however...  ;)

---

### Post by B-Con on 2007-06-18
> **neptho said:**
> Temporarily mount the partitions to get the UUIDs.  awk and sed are your best friend.  Perl, however...  ;)
I can get the UUIDs by temporarily mounting them, but the problem is that they won't show up in the UUID list when they're not mounted, thus I can't grep for them until they are mounted.

For future reference, I found a solution:

Both 
$ ls /dev/disk/by-id 
and 
$ /dev/disk/by-path 
list all drives connected, mounted or unmounted. Figure out which one corresponds to yours. I used "by-id", just seemed nicer. An ls -l of the direction you chose (by-id or by-path) will show which name/path corresponds to which device. Then grep it out and cut the field containing the block device. Stick this in a script and it looks like this:

```
#! /bin/bash

my_var=`ls -l /dev/disk/by-id | grep "scsi-1ATA_Maxtor_7H500F0_H81E4GAH-part1" | cut -d / -f 3`
vol_path="/dev/${my_var}"
# Use vol_path as the path for your drive, now.
```
Now no matter what block device Ubuntu chooses to use, you can get the volume's device and use it. :)

---

