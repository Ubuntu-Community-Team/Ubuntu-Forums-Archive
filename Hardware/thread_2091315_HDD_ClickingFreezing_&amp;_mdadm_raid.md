---
title: "HDD Clicking/Freezing &amp; mdadm raid"
date: 2012-12-04
forum: Hardware
---

### Post by Saicho on 2012-12-04
Hi all,

I have two drives in a raid1 using mdadm where my /home is mounted. One of them started periodically clicking freezing when trying to access data from it.

mdadm says the raid is fine, I've forced a few redundancy checks and all went fine
SMART says the drives are fine too, I've also done some drive tests and those come out positive as well...

(I've read that sometimes this can be an overloaded PSU issue, but I haven't changed/added any hardware in a long time, so as long as it isn't capacitor aging, and I don't think it is since my PSU is from a reputable source, isn't very old, and has way more wattage output than the hardware connected to it needs, then it shouldn't be the PSU).

Right now I can't even tell which one of the two drives is messed up. Is there a way to diagnose which drive is failing?

Since I bought both at the same time, I'm going to replace both too. I don't really have any other machines to play with, so how does mdadm do with swapping SATA ports on the motherboard? I want to get 2 (at least) more drives, build a second raid, and do a copy. Do I need to be careful to make sure the SATA cables are plugged into the same ports, or does that not matter much?

Thanks in advance!

---

### Post by ahallubuntu on 2012-12-04
You do need to be careful about swapping SATA ports on those drives in your RAID array.  Look in the file /etc/mdadm/mdadm.conf (or /etc/mdadm.conf).  See how your partitions are referenced.  If they are referenced by device numbers (/dev/sda1), then you would have to adjust the mdadm.conf file if you change the ports around.  If the partitions are instead referenced in that file by block ID ("UUID"), you can swap them without issue.

I'd run extended S.M.A.R.T. tests on both drives that you already have.  You could try to do this with your existing installation (you can run the S.M.A.R.T. tests while the drives themselves are in use but it may not be a good idea), but it might be a better idea to burn/boot a Parted Magic Linux CD and run the tests from there.  The tests may take a few hours, and you won't of course be able to use the computer while the tests are in progress.

---

### Post by Saicho on 2012-12-05
Sounds good, I will run the extended S.M.A.R.T. tests overnight off the CD and see what they say. My fear is that they will come back inconclusive. Thanks for the advice!

---

### Post by Saicho on 2012-12-10
Unfortunately the extended tests on all 3 drives (2 raid storage /home drives, and 1 man OS / drive) passed.

Only the main OS drive had any (previous) errors in the Errors tab, and those weren't very specific. I think I'd like to replace that drive first and see what happens.

Can anyone recommend a good way of cloning(?) the OS drive in order to replace it? I have extra drives of the same size lying around.

---

### Post by tentimes on 2012-12-19
In my experience (over 30 years) clicking from a drive usually indicates an impending hardware failure. It might say it's fine, but have a mechanical fault.

If you have anything important on that drive make sure it's backed up ;) Apart from that I would say just wait for it to fail.

Google "clicking hard drive" and I am sure you will get more information.

Good luck :)

---

### Post by Saicho on 2012-12-19
Yep, I want to replace it, the problem is I don't know which one of the 3 drives is at fault, and (miraculously) it hasn't died yet.

I started previously that I wanted to start with the main OS drive. I don't have much experience with this. What would be the best way to copy an existing OS installation (grub and all) on an HDD to another HDD of similar size and partition layout?

---

### Post by ahallubuntu on 2012-12-19
If you have a spare drive (check it's current S.M.A.R.T. status first, you don't necessarily have to run any tests maybe the short test), you can always copy it with the dd command using a live CD (BE CAREFUL!  Improper use of "dd" can result in immediate data loss!).

For example, if your original drive is sda and the new one is sdb (let's assume you have your two other drives disconnected to be safe), you could simply do this:

```
sudo dd if=/dev/sda of=/dev/sdb bs=2048
``` 

This would probably work automatically if the drives are exactly the same make/model/size.  If the new one is even a little larger, it will still work but you should adjust the size with Gparted once (resize it by 1MB or something) to correct the partition table size.

Actually, you can use Gparted (from a live CD) to copy the partition(s) too.  You can basically navigate to the partition you want to copy, right click and say "Copy" and then "paste" somewhere else.  That will probably be faster and more user-friendly than dd.  But you may have to re-install Grub on the new drive afterward or copy just the boot sector like this, after all partitions are copied:

```
sudo dd if=/dev/sda of=dev/sdb count=1 bs=446
```

Again, BE CAREFUL with the dd command!  The syntax is extremely sensitive.  Make sure you have the devices correct!!!

Finally - you could try Clonezilla, a Linux-based cloning tool you can boot from its own disc.  I've had mixed luck with Clonezilla, but if it works, it will probably work perfectly.

---

