---
title: "Upgrade to SSD?"
date: 2012-11-21
forum: Hardware
---

### Post by PDA1 on 2012-11-21
I'm thinking of upgrading my harddrive to an SSD one.

My machine is a Dell Inspirion E1505.

What's your opinion?

---

### Post by ahallubuntu on 2012-11-21
GShould be a nice improvement.  A standard SATA SSD drive will work fine.  My friend has an E1505 and replaced his HD with an SSD.  I used to have one too.  Replacing the hard drive is super easy.

However, know that the E1505 is pretty old now, and you're still stuck with an old machine.  RAM MAXes out at 2GB.  No webcam/built-in microphone.  My friend reports that he was slightly disappointed with the improvement in performance on his E1505 with the upgrade: much faster than the HD for sure but I guess he was expecting instant on/off.  Maybe the E1505 has only 1.5Mbps SATA only, not sure.

You might dig up a USB hard drive adapter or enclosure for 2.5" drives so you can attach both drives at the same time to clone your existing drive to the SSD.  The 2.5" enclosures can be had for about $5 USD give or take perhaps on eBay or elsewhere.

If your E1505 doesn't have at least a Core Duo CPU, it's probably not worth spending any money on unless you also upgrade the CPU.  If you have a Celeron CPU, an upgrade to a Core Duo or Core 2 Duo would make a nice speed improvement.  But the CPU is buried under the keyboard in this  model and a bit of a pain to get to - I have upgraded a couple of them.

---

### Post by PDA1 on 2012-11-21
Thanks for the ideas. Yes, my machine is a little slow for doing fancy stuff but it's perfect for watching youtube videos, email and related.

I've only spent around $100 on the machine as I did have to replace the motherboard. 

I suppose a spinning disk would be cheaper and I like your idea of an external box for the thing.

Thanks again.

---

### Post by gordintoronto on 2012-11-21
The external box is for the old thing, of course.

An SSD should make booting and loading programs faster, but that's all. For example, when I load Chrome, the load time on my system is a second or two, but then it does some (I assume online) Chrome stuff which takes several seconds before I can use it.

---

### Post by PDA1 on 2013-02-02
What program would I use to Clone the existing SATA drive to the new SSD?

The drive to be upgraded/changed is dual boot- it has windows and Ubuntu 10.04 on it.

I want the transfer to be as painless as possible.

---

### Post by cybrsaylr on 2013-02-02
Heard that GParted will clone an OS but haven't used it for that purpose as yet.

---

### Post by PDA1 on 2013-02-02
I would not want to try it with my system!

---

### Post by ahallubuntu on 2013-02-02
Yes, I have used Gparted a few times to clone systems using a live CD or live USB.  (Don't try cloning a live filesystem.)  Gparted can copy partitions easily in a very friendly way.  Navigate to the partition you wish to copy, right-click and choose "Copy."  Navigate to the destination partition, right-click and choose "Paste."  Then apply.  Works for ext3/4 partitions but also for Windows partitions too!  And it's fairly fast - faster than dd I believe.

The downside is, there's some manual work involved in cloning this way - not that much if you know what to do but there are a few steps.  If you have a new disk, you'll have to create the new partitions manually first, then copy.  And I'm not sure you can clone a swap partition automatically - not that you need to, there's no data to save from it but otherwise you have to create a new swap partition on your new disk.  That's easy too, but you must then edit the /etc/fstab of your new disk (after you cloned the / partition) and update the reference to swap.  The UUID will change because the new swap partition will have a different UUID than the old one.  You can find the UUID of each partition with the command "sudo blkid" though.  Just copy and paste it in a text editor.

The other thing you'll have to do after cloning with Gparted is probably install/update grub on the new disk.  I like the "chroot" method for that - has worked reliably for me:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

If you don't have a RAID array or a separate boot partition, it boils down to doing this:

#figure out which is your new / partition with "sudo fdisk -l"
#If your new disk is /dev/sdb and new / partition is on /dev/sdb1  
#replace "XXX" below with "b" and "YYY" with 1 or whatever yours #turn out to be.

Then:

```
sudo mount /dev/sdXXXYYY /mnt
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
install-grub /dev/sdXXX
update-grub
exit

```

Then shutdown, swap disks etc. - or use this last line to unmount stuff you mounted above:
```

for i in /run /sys /proc /dev/pts /dev; do sudo umount /mnt$i 

```

---

### Post by ahallubuntu on 2013-02-02
You could also try Clonezilla to clone.  I have not had perfect luck with it - if it works, it works, but sometimes the clone fails in my experience.  And it is not a very friendly tool to use.

---

