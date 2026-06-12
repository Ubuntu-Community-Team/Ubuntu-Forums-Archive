---
title: "Stopping Tasks Failed (RAID problem)/How to rebuild RAID arrays"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by lozzd on 2005-06-06
My RAID is currently running degraded. Its a RAID1 array, with normally two drives.
One failed, I rebooted, and when it said "md0 is running with 1 out of 2 drives, starting background reconstruction" or words to that effect, it stopped for a few seconds and then said "stopping tasks failed (1 remaining)"

So I unplugged that drive, which allowed me to boot again. I removed the drive from the array, phyiscally removed the drive, and put a new one in. 

Once back into Linux, I hot added the drive, and it showed up as a spare. I tried everything I could to make it start rebuilding straight away, knowing that if i rebooted, i'd just get that same error message again. 
Unfortuantely, i don't know enough about Linux to get it to rebuild, so i thought, what the hey, i'll reboot anyway. And sure enough, back to that error again! 
So now i've unplugged the new drive, and it looks like unless I can fix this problem, or learn how to make linux rebuild the RAID array without rebooting, i'm stuck in this 1 drive degraded state.
Anyone got any suggestions?
Thanks in advance
Laurie  ](*,)

---

### Post by debianfirefox@gmail.com on 2005-06-29
Hi, this seems to be an issue with acpi in combination in raid.  I boot ubuntu from a raid1 array, and if ubuntu ever crashes, I cannot boot normally, and receive the same boot error as you.  I have to boot another instance of ubuntu on another partition, and let that resync the array, before I can run my main, raid1 instance of ubuntu again.

See also here : [http://lists.ubuntu.com/archives/kernel-bugs/2005-May/001467.html](http://lists.ubuntu.com/archives/kernel-bugs/2005-May/001467.html)

In short: set "acpi=off" in the boot string of grub, and the boot will not hang, and recontruct normally in the background.

Probably an Ubuntu specific problem, since my Debian Unstable setup did not have this problem with the same setup.

---

### Post by alastair on 2005-06-29
You should be able to do something like :

mdadm /dev/md0 -a /dev/sdb1

Where "sdb1" is one (previously missing) partition making up "md0". You will need to do this for every (previously missing) partition on "md0".

Does this make sense?

EDIT : P.S. I have an Ubuntu server with 2 disks in RAID-1 - I did test the above by unplugging each disk and rebooting. I could reboot and login fine with one disk missing. To start a reconstruct, I did the above.

---

### Post by lozzd on 2005-06-30
Shag!!! I cant believe it was that simple! I missed off the "1" on sdb so it hot added the whole bloody drive as a spare instead of instatnly recreating the array!

Thank you SO MUCH!

---

