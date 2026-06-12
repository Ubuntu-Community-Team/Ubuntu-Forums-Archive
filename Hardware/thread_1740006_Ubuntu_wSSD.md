---
title: "Ubuntu w/SSD"
date: 2011-04-26
forum: Hardware
---

### Post by nova47 on 2011-04-26
This question is a bit general but is there some sort of incompatibility with Ubuntu on SSD's? I currently have a desktop with two SSD's; one running Ubuntu and one running Windows. I have tried two different SSDs one 32GB Onyx OCZ drive and one 64GB Corsair drive. I ended up returning the Onyx thinking it was the problem but I've actually been having the exact same problems with the corsair (albeit the corsair is not suffering from the root delay dropping to busybox issue that the Onyx did while booting god knows that was annoying). I now have the 64GB corsair with Ubuntu on it and a 64GB OSZ with Windows.

1) Frequent hangs. During no particular task everything will just freeze and whatever sound was playing in the last three seconds will repeat.

2) All programs will cease opening. All programs currently open will function but I'm suddenly unable to open any new programs other than terminal.

3) I will suddenly be able to write anything to disk. Most programs lock up and Ubuntu tells me it is unable to write to the root disk. When I restart Grub craps on itself and says that the root drive can't be found and Grub rescue starts.

I'm running Ubuntu 10.10 x64. The problem only seems to occur when Ubuntu occupies the entire SSD. When windows was on part of the SSD everything worked fine. My suspicions are that Ubuntu is the culprit as Windows ran flawlessly without complaint on both drives. Is this a problem I'm inventing in crazy town or are other people having this problem?

EDIT: I cave. I've spent upwards of 18 hours trying to get this to work and Ubuntu just crapped itself again. Grub can't find the drive, can't get it going, I'm done. Think I'll just run everything in VMware on Windows for a while.

---

### Post by jespdj on 2011-04-27
Are you sure the problem has to do with the SSD?

Things like random hangs etc. sound like there might be something wrong with the RAM of your computer. Try booting it into memtest86+ mode and let it test the memory for a few hours.

Maybe it's some combination of things, where the SSD interferes with some other device in your computer.

---

### Post by aphatak on 2011-04-27
I installed SSD on two laptops, both are dual-boot and have Windows and Ubuntu on them.
One of these has been running sweetly, and takes whatever I care to throw at in its stride.  The other has had intermittent trouble at boot time.  Let alone Grub, the BIOS didn't find the drive!  I had to switch it off and the on again, and the problem would vanish.  The same laptop with a conventional, spinning hard-disk never hesitated once - it always found the drive and worked flawlessly.
I haven't figured out what the problem is yet, but it appears to be with the SSD, not with Ubuntu.

---

### Post by dabl on 2011-04-27
There is a phenomenon referred to as "stuttering" on some SSDs -- you can google it and learn which ones have the problem -- it affects performance in both Linux and Windows.  Also the most popular SSD OEMs have support forums and user forums, for example:

[http://www.ocztechnologyforum.com/](http://www.ocztechnologyforum.com/)

Look down the left and you'll see there is a Linux forum there.

I have 3 SSDs running on Linux systems at the moment.  Two are SATA interface and one is a PCI-e interface.  I used fdisk to partition them and make the filesystems, and after reading about the partition "alignment" isse that can happen, I followed this guide to align the partitions to 512K cylinders:

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

It's daunting, I'm sure, and somewhat of a PITA.  However, you only need to do it once for each SSD.  Mine have been running trouble-free since last October.

---

