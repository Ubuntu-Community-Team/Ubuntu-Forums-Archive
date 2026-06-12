---
title: "Memorex Flash Drive -- Not Bootable"
date: 2009-01-02
forum: Hardware
---

### Post by Rohan Kapoor on 2009-01-02
I got a memorex 512mb traveldrive (silver) for the purpose of creating a bootable usb stick. I know my BIOS (HP Compaq V2000 v.27) supports USB booting as my 2GB Sony Microvault boots fine. I also have tested with a memorex 1gb traveldrive (silver) which doesn't work.

The problem: Memorex USB sticks aren't bootable. I've tried making it bootable with Windows and Linux and the system refuses to accept any of the above mentioned Memorex drives as bootable drives. I've tried on a custom made system with a Foxconn motherboard and the USB drive isn't bootable there either.

I'm wondering if there is something special which has to be done to a memorex drive to make it bootable or are mine just defective.

Thanks!

---

### Post by psb6m on 2009-01-03
I'm also interested in an answer to this. What makes a USB stick bootable? If a non-bootable one can't be fixed, how can I make sure I'm buying a bootable one when I get another? Or what brands have Ubuntu users had success with?

Peter

---

### Post by Rohan Kapoor on 2009-01-03
> **psb6m said:**
> I'm also interested in an answer to this. What makes a USB stick bootable? If a non-bootable one can't be fixed, how can I make sure I'm buying a bootable one when I get another? Or what brands have Ubuntu users had success with?

Peter
I just wanted to add, that I've given the memorex drives bootable flags and 1 single fat32 partition and they aren't detected as bootable.

---

### Post by psb6m on 2009-01-03
I have no idea whether this will work with your Memorex USB stick, but it just worked with my 4GB Sony Microvault.

I wiped the USB stick entirely by making myself root and writing zeroes over the whole thing:

```
sudo -s
dd if=/dev/zero of=/dev/sdb
```

CAUTION: Make sure you've got the right device, since this command is extremely destructive! This will take a while.

Next use fdisk or cfdisk to make yourself a new partition:

```
cfdisk /dev/sdb
```

and set the type (I did FAT32, but I suppose others would work as well), the bootable flag, and whatever else needs setting. Bravely write the result to the stick.

Finally fire up the good old System-->Administration-->Create USB startup disk. It will offer to format the partition on your USB drive. Let it do that, and then proceed as usual.

The result booted on my ancient Dell Inspiron 600m, where earlier it would not.

---

### Post by psb6m on 2009-01-03
I'll just add that my Dell would not boot from this USB stick on restart, but only with a cold boot. But I'm guessing that that is the fault of the computer, not the drive.

---

### Post by Rohan Kapoor on 2009-01-03
> **psb6m said:**
> I'll just add that my Dell would not boot from this USB stick on restart, but only with a cold boot. But I'm guessing that that is the fault of the computer, not the drive.
Thanks I'm running the dd command now, will let you know how it goes!

---

### Post by Rohan Kapoor on 2009-01-03
Nope the memorex still doesn't work! It may be of note that the sony drive doesn't show up as a USB device but as a harddrive!

---

### Post by handydan918 on 2009-01-03
> **darth-vader said:**
> Nope the memorex still doesn't work! It may be of note that the sony drive doesn't show up as a USB device but as a harddrive!
Do these stick have one of those #$*@##$# U3 partitions? I've seen those cause problems. You can use a windows utility to remove them. You can [get it here.]("http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe")

---

### Post by Rohan Kapoor on 2009-01-03
Thanks for the thought but there the plainest sticks you can buy!

---

### Post by psb6m on 2009-01-03
That's too bad. It seems there are more possible fubars here than I would have thought.

---

### Post by Rohan Kapoor on 2009-01-03
> **psb6m said:**
> That's too bad. It seems there are more possible fubars here than I would have thought.
fubars?

---

