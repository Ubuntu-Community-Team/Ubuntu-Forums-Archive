---
title: "Misaligned Partition - How To Solve?"
date: 2013-06-02
forum: Hardware
---

### Post by Daniel Zi on 2013-06-02
Hi everyone,

I am trying to partition a 3rd hard disk for my desktop running 10.04. It's a Seagate Barracuda 2 TB hard drive.
Ubuntu runs on the first HD which is 500gb. I only want to use the 3rd HD for storage. I would like to move all my data
from my 1st HD to the 3rd one so that I can install 12.04.

I've been searching and trying for hours but can't seem to get anything to work (I am also a newb). 

I keep getting the warning: "the partition is misaligned by 512 bytes." Sometimes it's 3584 bytes, depending on what I do.

Does anyone have a solution for this or advise?

Thank you so much

---

### Post by Daniel Zi on 2013-06-02
I've deleted the partition so atm this is what appears:

> 
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c45f1


---

### Post by Irihapeti on 2013-06-02
From memory, since it's over a year since I used 10.04, GParted on 10.04 doesn't have the ability to create partitions aligned to MB. That's what you need if you want to avoid the problem.

You should be able to partition your new drive using GParted on the 12.04 liveCD, or any recent liveCD, and have the partitions align correctly. The Disk Utility tool doesn't do this, although it complains if you've got it wrong.

I have a 500GB Seagate Barracuda drive with similar issues. To be honest, I can't say that I notice any difference in performance between properly aligned partitions and misaligned ones. In fact, I think that Seagate has built something into the drive to handle this. But then, I'm not using my machine for anything particularly demanding.

See [http://www.seagate.com/tech-insights/advanced-format-4k-sector-hard-drives-master-ti/](http://www.seagate.com/tech-insights/advanced-format-4k-sector-hard-drives-master-ti/) for further information.

---

### Post by Daniel Zi on 2013-06-02
> **Irihapeti said:**
> From memory, since it's over a year since I used 10.04, GParted on 10.04 doesn't have the ability to create partitions aligned to MB. That's what you need if you want to avoid the problem.

You should be able to partition your new drive using GParted on the 12.04 liveCD, or any recent liveCD, and have the partitions align correctly. The Disk Utility tool doesn't do this, although it complains if you've got it wrong.

I have a 500GB Seagate Barracuda drive with similar issues. To be honest, I can't say that I notice any difference in performance between properly aligned partitions and misaligned ones. In fact, I think that Seagate has built something into the drive to handle this. But then, I'm not using my machine for anything particularly demanding.

See [http://www.seagate.com/tech-insights/advanced-format-4k-sector-hard-drives-master-ti/](http://www.seagate.com/tech-insights/advanced-format-4k-sector-hard-drives-master-ti/) for further information.

Thanks, I will try that now...I hope I don't accidently format the HD I want to backup:)

---

### Post by Irihapeti on 2013-06-02
Make sure that you choose "align partition to MiB".

---

### Post by Daniel Zi on 2013-06-02
> **Irihapeti said:**
> Make sure that you choose "align partition to MiB".

Works!!!! Thank you so much!!!!

---

### Post by Daniel Zi on 2013-06-02
Only problem now is that I can't read/write to it. Says I'm not the owner...any ideas?

Thanks

---

### Post by Irihapeti on 2013-06-02
=D>
Please mark the post solved. [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

### Post by benzarti on 2013-06-02
It must be aligned to physical sectors, then the number of logical sectors must be a multiple of 4096/512=8 and the number of logical sectors is x*512= desired partition size in bytes

---

### Post by Irihapeti on 2013-06-02
> **Daniel Zi said:**
> Only problem now is that I can't read/write to it. Says I'm not the owner...any ideas?

Thanks

That will be a permissions thing. Open a terminal, go to the place where the drive is mounted and run the command

```
sudo chown username .
```

"Username" is your login name. Make sure you include the final dot.

---

### Post by Daniel Zi on 2013-06-02
> **Irihapeti said:**
> That will be a permissions thing. Open a terminal, go to the place where the drive is mounted and run the command

```
sudo chown username .
```

"Username" is your login name. Make sure you include the final dot.

Sorry, what's the command to get there? Thanks

---

### Post by Irihapeti on 2013-06-02
cd /the-directory-name

so if you're in 12.04, that's likely to be /media/uuid
where uuid is a horrible long string of letters and numbers.

If you're working with external drives and multiple partitions, it's worth giving your partition a label in gparted. It's much easier to find!

---

### Post by Daniel Zi on 2013-06-03
> **Irihapeti said:**
> cd /the-directory-name

so if you're in 12.04, that's likely to be /media/uuid
where uuid is a horrible long string of letters and numbers.

If you're working with external drives and multiple partitions, it's worth giving your partition a label in gparted. It's much easier to find!

Hi, didn't manage that way, but I found something that worked as well

I went to terminal and put in:

> 
[COLOR=#000000][FONT=courier bold]gksudo "nautilus --no-desktop"[/FONT][/COLOR]


I then had access to the HD and changed the permissions from root to my username.

Thanks for all the help, really appreciate it :)

---

