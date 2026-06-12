---
title: "Software raid1 causing hard freeze"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Jimmy The Clown on 2007-09-08
I recently built a new system and have been getting frequent hard freezes. No mouse, no ctrl-F*, no ctrl-bksp. The first time I saw a freeze was in moving a large amount of files from my usb HD to my new comp. Tried multiple times and every time it froze after 200 or 300 MB (roughly). Have also caused a freeze by copying a dvd to HD and by using bonnie++, a hard drive benchmark util. Interestingly, after a failure when I reboot and do a "cat /proc/mdstat" I see at least one of my raids "active resyncing".

This is the first time I have ever set up raid. I am using two WD 320 GB drives partitioned identically into swap, /, and home. The drives are mirrored in a raid1 setup.

As a test I just faulted out all 3 partitions on one drive and then removed them from the array. With only one drive active, I ran bonnie++. It passed with no problem -- so this is definitely bring caused by the raid.

Any linux software raid experts out there? Other diagnostics I should try? I could really use some help here and a forum search isn't showing up much.

-JTC

---

### Post by Jimmy The Clown on 2007-09-11
Bump* Can anyone lend a hand? This is a pretty serious issue for me. I even spent some time answering posts for newbs to try to gather some forum answering post karma. :-)

Anyone else out there using a software raid1? Is it stable?

-Jody

---

### Post by Selfish Meme on 2007-09-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/75681) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See bug report, software RAID seems borked for some applications, especially putting boot drives on arrays. I have not managed to get it working properly yet after two days trying.

---

### Post by Jimmy The Clown on 2007-09-30
Just sat  down and deleted my raid and reinstalled to just one hard drive in a simple configuration. Still experiencing lock ups. I am going to start a new thread since this no longer appears to be a raid issue. :-(

-JTC

---

