---
title: "ASUS 901 optimal set-up?"
date: 2009-10-10
forum: Hardware
---

### Post by gcday on 2009-10-10
I am trying to install Ubunutu 9.04 on a friend's ASUS 901 and have got into a bit of a mess, I have ended up with two OSes because of the fact that (which I didn't know) has two hard drives - the 4gb ssd and the 16gb flash drive.

What is the optimal set-up for the ASUS - I guess the OS goes on the 4g and files on the 16gb and I'm told no swap file?

Can someone explaining what I need to do at the partition stage as I can't make any sense of the terminology used at that part of the process.

---

### Post by HankB on 2009-10-10
> **gcday said:**
> I am trying to install Ubunutu 9.04 on a friend's ASUS 901 and have got into a bit of a mess, I have ended up with two OSes because of the fact that (which I didn't know) has two hard drives - the 4gb ssd and the 16gb flash drive.

What is the optimal set-up for the ASUS - I guess the OS goes on the 4g and files on the 16gb and I'm told no swap file?

Can someone explaining what I need to do at the partition stage as I can't make any sense of the terminology used at that part of the process.
Yes, 
System on the 4GB drive and user files on the 16GB drive. When you get to disk setup, select the last option (custom) and set up the partitions this way. Select '/' for the 4GB drive (and yes to format) and '/home' for the 16 GB drive. If you this is your first Ubuntu install, you may want to back up files on the /home partition that were created under Xandros and format that partition during install (*). On subsequent installs, you will generally not reformat the /home partition.

I did some further tuning to optimize my 901 for Ubuntu. I upgraded to 2GB RAM (easy and not very expensive) since there was no swap. Then I moved some active file directories to what is essentially a RAM drive to reduce disk writes. (SSD reads fast but writes slow - at least on the Eee.) I've added the following to /etc/fstab:

```
# netbook tuning
tmpfs /tmp tmpfs defaults,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults 0 0
tmpfs /var/log tmpfs defaults 0 0
tmpfs      /var/log/apt    tmpfs        defaults           0    0

```

I have to admit that the last line looks redundant to me, but it's there and I'm not sure why I did that. ;) Also note that putting /var/log in RAM means it will be empty following reboot, so if you want to preserve that information you may not want to do this.

I have also added some options (in /etc/fstab) to the other mounts to reduce I/O to the SSD:

```
# / was on /dev/sdc5 during installation
UUID=a4219f42-45af-4ecc-8001-106b70c37d55 /               ext4    [COLOR="Red"]noatime,relatime[/COLOR],errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=4add4c10-fc36-4d20-8ca4-3615ebf9a716 /home           ext4    [COLOR="Red"]noatime,relatime[/COLOR] 0       2
```

I have also modified the I/O scheduler to be more appropriate for an SSD by adding the following to my /etc/rc.local script:
```
# netbook tuning
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch
echo deadline > /sys/block/sdb/queue/scheduler
echo 1 > /sys/block/sdb/queue/iosched/fifo_batch
echo deadline > /sys/block/sdc/queue/scheduler
echo 1 > /sys/block/sdc/queue/iosched/fifo_batch
```

Finally, I have gone into the browser (Firefox) and modified it to put it's cache in /tmp. That means that the browser cache will be gone when I reboot, but it won't be writing to the slower 16GB SSD every time I open a page.

It would probably be wise to research these tweaks and try them out one at a time in case you have any difficulty. Since they are all file based settings (except perhaps for browser configuration), it should be easy to back them out by booting a live USB and editing the files on the Eee 901.

Without knowing what terminology you do not understand during the installation process, it is hard for me to help with that. Perhaps if you continue to have difficulty you could post something more specific or look through the various installation guides that are available.

(*) The factory Xandros installation also puts user files on the 16GB SSD but I don;t recall if I migrated that directly from Xandros or backed up and reformatted. Different Linus distros may use different user ID numbers for the first and subsequent user and migrating from one to the next can be a bit of a pain. I ran into that moving from Debian to Ubuntu years ago.

HTH,
hank

---

### Post by gcday on 2009-10-12
That worked fine - thanks!

---

