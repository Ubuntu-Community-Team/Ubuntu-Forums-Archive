---
title: "Unusable Partition"
date: 2008-04-28
forum: Hardware
---

### Post by LitusMayol on 2008-04-28
Hi everyone!

I'd like to install Kubuntu in my computer and then turn it to KubuntuStudio. I've 2oGb partition that appears as "unusable", I'd like to install my OS there. But I don't know how to give it "ext3" format and how to mount it as "/". I'm using the Gutsy LiveCD but as I said the 2oGb partition appears as "unusable" and it don't give me the normal options: "edit partition" and "delete partition".

Does anyone know how to give format to this partition in the way to use it after as "/"? I think that if I give it the "ext3" format I'll be able to install the OS with the LiveCD myself.


Thanks everyone and pardon the newbie!

---

### Post by overdrank on 2008-04-28
> **LitusMayol said:**
> Hi everyone!

I'd like to install Kubuntu in my computer and then turn it to KubuntuStudio. I've 2oGb partition that appears as "unusable", I'd like to install my OS there. But I don't know how to give it "ext3" format and how to mount it as "/". I'm using the Gutsy LiveCD but as I said the 2oGb partition appears as "unusable" and it don't give me the normal options: "edit partition" and "delete partition".

Does anyone know how to give format to this partition in the way to use it after as "/"? I think that if I give it the "ext3" format I'll be able to install the OS with the LiveCD myself.


Thanks everyone and pardon the newbie!

HI and how many partition are on that drive? You are allow 4 partitions to a drive unless you create a extended partition.

---

### Post by LitusMayol on 2008-04-28
> HI and how many partition are on that drive? You are allow 4 partitions to a drive unless you create a extended partition.

I've:

1.Windows
2.Windows Recover Disc
3.Ubuntu 8.o4
4.Swap
5.Unusable

So, am I not allowed to have more than 4? 
Shall I erase the "Windows Recover Disc" to put my Kubuntu? How I retrieve the unusable partition? 


Thanks man!

---

### Post by overdrank on 2008-04-28
> **LitusMayol said:**
> I've:

1.Windows
2.Windows Recover Disc
3.Ubuntu 8.o4
4.Swap
5.Unusable

So, am I not allowed to have more than 4? 
Shall I erase the "Windows Recover Disc" to put my Kubuntu? How I retrieve the unusable partition? 


Thanks man!

HI and you can only have 4 primary partitions. You will have to delete one and if you have a windows install disc then that would be my choice. once you delete the partition then you will be able to create a extended partition. Now if the Windows recovery is at the beginning of the drive then it may be unable to move you other partitions to recover that space. I am not a expert on partitioning and this link may help
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by LitusMayol on 2008-04-28
Ok man!

Thanks **overdrank**! ;) I'll take a look to the link and decide what exactly I do. 

Thanks again. ;)

:guitar:

---

### Post by vanadium on 2008-04-28
From a live CD, delete your swap partition. Then create an extended partition occupying the total remaining free space on your drive. In the extended partition, recreate your swap. Now, you will be able to create additional partitions in the remaining space. Indeed, a drive can hold at most four primary partitions. To fit more partitions on a drive, logical partitions within an extended partition must be used.

You will need now to update the UUID of the swap partition in the fstab file of your Ubuntu installation. Still from the live session, open the fstab from the system partition of your Ubuntu 8.o4 partition in an editor. Your swap will be announced with a line such as (the first line preceeded with # is just a comment)

```

# /dev/sda5
UUID=17053c24-7853-42ba-af90-b8275742dd0b none            swap    sw              0       0
/
[code]

Use the command "sudo blkid" to reveal the new UUID of your swap partition. It will look like

[code]
/dev/sda1: UUID="c9cb8b29-152a-47ac-b952-5b9909a290ba" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="17053c24-7853-42ba-af90-b8275742dd0b" 

```

The second line is the one of my swap. For me, the numbers match, but for you not anymore: that is what you are correcting. You can just copy the UUID="...." part of that line (Highlight and Ctrl+Shift+C in the terminal) and paste it over the "UUID=..." part in your fstab.

After loading Ubuntu 8.04, check whether your swap is correctly recognized and used: open an terminal and type "cat /proc/swaps"

It should be listed like

```

 cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	3028212	36564	-1
f

```

If not, double check wether the UUID in fstab and that of the swap match.

---

### Post by LitusMayol on 2008-04-28
Sorry man, but I'm a newbie and i don't really understand this...

> You will need now to update the UUID of the swap partition in the fstab file of your Ubuntu installation. Still from the live session, open the fstab from the system partition of your Ubuntu 8.o4 partition in an editor. Your swap will be announced with a line such as (the first line preceeded with # is just a comment)

Thanks anyway! ;)

---

