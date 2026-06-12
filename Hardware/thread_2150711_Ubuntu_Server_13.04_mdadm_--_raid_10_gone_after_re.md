---
title: "Ubuntu Server 13.04 mdadm -- raid 10 gone after reboot"
date: 2013-06-02
forum: Hardware
---

### Post by T Whatley on 2013-06-02
[FONT=arial]I created a raid 1+0 via mdadm by the following...

[/FONT][INDENT][FONT=arial]***mdadm -v --create /dev/md2 --level=raid1 --raid-devices=2 /dev/sde1 /dev/sdf1***[/FONT][/INDENT]
[INDENT][FONT=arial][I][B]mdadm -v --create /dev/md3 --level=raid1 --raid-devices=2 /dev/sdg1 /dev/sdh1

mdadm -v --create /dev/md1 --level=raid0 --raid-devices=2 /dev/md2 /dev/md3[/B][/I][/FONT][/INDENT]
[FONT=arial]
...then finished it off by adding the output of [COLOR=#000000]***mdadm --detail --scan*** to ***/etc/mdadm/mdadm.conf*** and did a mkfs.xfs on md1.

All was going well... md1 resync'd fine and I copied all my data to the new md1 and used it for a couple days.

I then decided to physically move my server to another location in the room, requiring a reboot.

md1 disappeared and md2 and md3 seemingly were renamed to md126 and md127.

Any idea what happened here?

Here's the output of blkid:
[/COLOR][/FONT][FONT=arial]
[/FONT][INDENT]***[FONT=arial]/dev/md127: UUID="09201334-78fd-5e73-9d9b-5e172ead0fdf" UUID_SUB="939f502d-e049-7e34-0092-b515eab5421f" LABEL="tobias:1" TYPE="linux_raid_member"[/FONT]***[/INDENT]
[INDENT]***[FONT=arial]/dev/md126: UUID="09201334-78fd-5e73-9d9b-5e172ead0fdf" UUID_SUB="84500208-99ee-9bb0-1887-2ff87fe05ce4" LABEL="tobias:1" TYPE="linux_raid_member"[/FONT]***[/INDENT]
[FONT=arial]
[/FONT]
[FONT=arial][COLOR=#000000]...no mention of md1. I have another raid1 setup, md0, and that is fine as well. It appears that it doesn't like something when combining two raid1's into a raid 1+0.

Here's the output of ***cat /proc/mdstat***:

[/COLOR][/FONT][INDENT]***Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]***[/INDENT]
[INDENT]***md126 : active (auto-read-only) raid1 sde1[0] sdf1[1]***[/INDENT]
[INDENT][I][B]      1953382336 blocks super 1.2 [2/2] [UU]

[/B][/I][/INDENT]
[INDENT]***md127 : active (auto-read-only) raid1 sdh1[1] sdg1[0]***[/INDENT]
[INDENT][I][B]      1953382336 blocks super 1.2 [2/2] [UU]

[/B][/I][/INDENT]
[INDENT]***md0 : active raid1 sda2[0] sdb2[1]***[/INDENT]
[INDENT][I][B]      124937088 blocks super 1.2 [2/2] [UU]

[/B][/I][/INDENT]
[INDENT]***unused devices: <none>***[/INDENT]


[FONT=arial][COLOR=#000000]
It isn't the end of the world if I lose my md1 raid 1+0, but I'd really prefer not to. Any suggestions to recover it and any suggestions to prevent this from happening again?

[/COLOR][/FONT]

---

### Post by T Whatley on 2013-06-02
If I do...

mdadm --assemble --scan
mount -a

It reassembles the missing md1 and remounts it... and everything functions fine.

Problem is, if I reboot the same situation happens again and again.

Has to be something simple I'm missing. I'm a mdadm rookie.

---

### Post by SaturnusDJ on 2013-06-02
Try:
```
update-initramfs -u
```
It'll add /etc/mdadm/mdadm.conf somewhere in the early boot stage.

If that doesn't work, the md devices probably aren't ready soon enough.

Why not create a native mdadm raid10? (--level=raid10)

---

### Post by T Whatley on 2013-06-02
I forgot to mention, I did do the [FONT=Ubuntu Mono, monospace][COLOR=#000000]update-initramfs -u which correctly renamed the md126/127 devices back to md2/3, but it still left the md1 device out of the loop.[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]I believe I was looking at older howto's that said to configure a raid 10 this way (two raid 1's first, and then an encompassing raid 0).[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]Is there a way I can convert my current raid 10 setup to the native raid 10, without the need for shuffling data around to destroy and rebuild it? Could I stop md1/2/3 and then do a create for the native level=raid10?[/COLOR][/FONT]

---

### Post by Cheesemill on 2013-06-02
> **T Whatley said:**
> [FONT=Ubuntu Mono][COLOR=#000000]Is there a way I can convert my current raid 10 setup to the native raid 10, without the need for shuffling data around to destroy and rebuild it? Could I stop md1/2/3 and then do a create for the native level=raid10?[/COLOR][/FONT]

Can you not just destroy and recreate the array and then restore all the data from your backups?

---

### Post by T Whatley on 2013-06-02
> **Cheesemill said:**
> Can you not just destroy and recreate the array and then restore all the data from your backups?

I could, which is where I'm guessing this is heading... but I don't have any backups to restore from. I'm in the process of copying all the data to other drives now to restore from, but it'll be hours... so I'm seeing what other options there are while I'm waiting.

---

### Post by Cheesemill on 2013-06-02
> **T Whatley said:**
> but I don't have any backups to restore from

If any of your data is important then ***please*** sort out a backup strategy.

RAID isn't an alternative to backing up your data, it was never designed to be. There are plenty of situations that could wipe out an array and all of its data.

---

### Post by T Whatley on 2013-06-02
It's not important. I'm asking for if there are ways to convert mdadm arrays.

No **** raid isn't a backup. If you actually read any of my posts, and didn't go off on your raid isn't a backup nerd tangent, you'd see that I know that.

This is a discussion about mdadm, not backup. Please excuse yourself from this thread.

---

