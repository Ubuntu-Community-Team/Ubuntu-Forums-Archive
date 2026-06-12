---
title: "Computer Semi-Failure"
date: 2008-11-23
forum: General Help
---

### Post by Thedjatclubrock on 2008-11-23
My laptop is running both OS X and Ubuntu. It's great. A few days ago, the boot process got longer, and gave errors while trying to load CUPS. It would eventually boot, but it would take a much longer time. When I ran an fsck, "it" gave no errors, but it seems like the kernel did. The errors are similar to what I get while loading CUPS, and is shown below. If anyone has any ideas, I thank you in advance.:confused:


[IMG]http://farm4.static.flickr.com/3174/3034935516_1fd3a41756_b.jpg[/IMG]

---

### Post by Thedjatclubrock on 2008-11-23
Well, I've been on it for a few minutes, and apps get sluggish and fail to run. Is this a bad HD, or a bad partition. Mac OS X *seems* to run fine. Either way, this is a pain in the rear, and I hope I'll be able to fix it soon! :(

---

### Post by Thedjatclubrock on 2008-11-23
:(

---

### Post by Herman on 2008-11-23
Try running a more specific file system check.
fsck is a great program and it can run a nice safe file system check on almost any type of file system by running another file system checking program fro you.

If you have an ext2 or ext3 file system, fsck runs e2fsck for you, but unless you're specifying some options for fsck, it only runs e2fsck with generic options.

Why not try running e2fsck yourself, from a live cd, and give it some options that will let it actually fix something? :)

First, from your live CD, run 'sudo fdisk -lu' to check which partition contains your Ubuntu operating system, 'sudo blkid' is also very good.
Then run something like: [SIZE=-1][FONT=Bitstream Vera Sans Mono]sudo e2fsck -C0 -p -f -v /dev/sda4
[/FONT][/SIZE]```
sudo e2fsck -C0 -p -f -v /dev/sda4
```Where '/dev/sda2' is the partition containing the file system to be checked, otherwise, replace '/dev/sda4' with some other partition number as per your 'fdisk' output.

 That runs a fairly safe and mild (but effective)  file system check but which will probably fix it for you.
If it can't, it will report back to you and tell you why hot, and probably what to do next.
If that doesn't fix it look here for what other e2fsck commands to run next, (depending on what the error message you received after the first file system check),  [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") .

Regards, Herman :)

---

