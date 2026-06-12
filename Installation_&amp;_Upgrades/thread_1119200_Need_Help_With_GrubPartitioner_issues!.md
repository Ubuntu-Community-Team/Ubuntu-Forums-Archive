---
title: "Need Help With Grub/Partitioner issues!"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by fr0sty on 2009-04-07
Alright, well I had a dualboot machine with vista and ubuntu 8.04 on the same machine in different partitions. Then i decided to install Kubuntu 8.10 in a third partition. I crashed the Kubuntu one and then decided to wipe the partition with a Kill Disk. After I had done this, my computer would no longer boot. So I popped in a Super Grub disk and did the restore MBR or sumthing and I got my original grub menu back. But the problem is that when i go to GParted or any other partitioner, it shows my entire Harddisk being empty. I know that Vista took up like 125 Gb and Ubuntu about 80, but there is absolutely no partitions showing up in my partitioner. I can boot from the grub menu into both vista and ubuntu fine, but the lack of partitions really has me unnerved. Any help would be greatly appreciated. Thanks!

Frosty

---

### Post by fr0sty on 2009-04-07
I think i fixed it. When i used the kill disk to wipe out the kubuntu partition, it left an unformatted partition or something, so i booted into vista and with the use of the vista partitioner ( it saw the partitions) i deleted the left over kubuntu partitioner. So i solved my own problem. Thnx for all the help though.

---

### Post by 123456789123456789123456 on 2009-04-07
I would not use kill disk to wipe a partition.  Using any partition editor, would do the same thing.  You may have to edit the menu.lst file to get grub to not list it, if it still does, don't know, I know that ntldr would still have the option to boot from the partiton that is no longer there, the file must be physically edited.  Grub seems to be slightly differnt, but have not had to worry about that particular problem so far.

---

