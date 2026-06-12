---
title: "External Hard Drive stopped working"
date: 2008-11-26
forum: General Help
---

### Post by LostAngel on 2008-11-26
Hey guys, I have a Dell laptop with the a dual boot of Windows XP Pro and Ubuntu.  I just updated Ubuntu to the latest version, and my external iomega hard drive has stopped being recognized by ubuntu.  When I boot into windows, it sees if fine.  Now here is the weird part.

If I have the drive plugged into my USB port, and boot ubuntu...it hangs at the 'UBUNTU' loading screen for approx 5 minutes. Once the desktop loads, when I goto my Computer...I see 'usb drive'  When I double click it, it says 'Unable to Mount Location' and below that 'Can't mount file'.

If I unplug the drive, then start ubuntu...ubuntu loads normally (not taking 5 minutes), but when I plug the drive back in...nothing happens at all.

---

### Post by sedawk on 2008-11-26
Before plugging in the drive clear the message buffer with
"dmesg -c" or "sudo dmesg -c".
Plug in the drive, wait a few seconds.
Post the (new) output shown by "dmesg".

(It should show the new drive, e.g. /dev/sdc and a list of
 partitions, e.g. sdc1, sdc2. You can try to manually mount
 the partition(s) using "sudo mount /dev/sdc1 /mnt" [You might
 have to create /mnt first ...])

---

### Post by LostAngel on 2008-11-26
I get a bunch of lines of this:

dmesg
 [current] 
[ 1790.856382] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.857460] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.857464] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.858485] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.858489] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.859580] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.859584] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.860713] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.860717] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.861710] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.861714] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.862708] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.862712] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.863705] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.863709] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.864745] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.864750] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.865834] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.865838] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1790.866838] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1790.866842] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information

---

### Post by seren6ipity on 2008-11-26
Make sure you have usbmount installed. I had had the same issue and installing usbmount fixed it.
sudo apt-get install usbmount

---

### Post by LostAngel on 2008-11-26
> **seren6ipity said:**
> Make sure you have usbmount installed. I had had the same issue and installing usbmount fixed it.
sudo apt-get install usbmount

Just installed....same result.

---

### Post by LostAngel on 2008-11-26
I saw the following bug and fix:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983)

I applied this, and now I can get the 'USB drive' to appear in my Computer when I plug it in, and go away when I unplug it.  But, when I try accessing it it says 
Unable to mount location
Can't mount file.

---

### Post by LostAngel on 2008-11-27
Anyone?

---

### Post by pistol.pavel on 2008-11-29
I have 250Gb Iomega prestige drive. when i first plugged it (ubuntu 8.10 64bit) there was no response from the system.

istalling "usbmount" package, from the synaptic manager, as seren6ipity wrote, solved the problem

---

### Post by LostAngel on 2008-12-01
Tried reinstalling that, still same thing.

---

### Post by LostAngel on 2008-12-04
Anyone? This is the only problem I am having with Ibex...and it's a PITA.

---

