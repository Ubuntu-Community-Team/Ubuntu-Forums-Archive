---
title: "3Ware card - executing a command at boot time"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by jthompson on 2006-12-06
I have just recently come over from Gentoo, and I would like to know how to execute a command at boot time.  I have a 3Ware RAID controller and I've found that if you do:

sudo blockdev --setra 16384 /dev/sda

Then you can seriously enhance your disk performance on a 2.6 kernel.  So, how can I execute this command on boot?

In Gentoo there was a file called /etc/conf.d/local.start, and you would just insert the command in there...

---

### Post by jthompson on 2006-12-06
I found a place:

/etc/init.d/bootmisc.sh

I inserted the command before the last colon at the very end of the script.  I wonder should I put it after the colon at the bottom, or does that signify the end of the script?

---

### Post by dughutch on 2007-03-17
[http://www.3ware.com/kb/article.aspx?id=11050](http://www.3ware.com/kb/article.aspx?id=11050)

-------
Q11050 - Software Configuration:  How can I improve performance using 3ware controllers with the Linux 2.6 kernel?

For Linux kernel 2.6, If you enter the following command:

blockdev --setra X /dev/sda

i.e.

blockdev --setra 16384 /dev/sda

(Note: 16384 is just an example value.  You will have to do testing to determine the optimal value for your system).  The OS will read-ahead X pages, and throughput will be higher. 

To make the change available every time you boot, you can add the 'blockdev --setra 16384 /dev/sda', 'blockdev --setra 16384 /dev/sdb', 'blockdev --setra 16384 /dev/sdc', etc. to /etc/rc.d/rc.local .

You can also put a setting in /etc/sysctl.conf which will set the read-ahead on boot: /sys/bus/scsi/drivers/sd/[DEVICEID]/block/queue/read_ahead_kb

The following parameter is used to enhance the 3ware 9500S and 9550SX/9590SE/9650SE’s (with code sets older than 9.4.1) sequential write performance with Linux kernel 2.6.

 

When using RAID 5 or RAID 6 arrays, limiting the maximum sectors per IO to 64k allows the IO pattern to interact better with the 3ware cache algorithm during sequential writes.  Enter the following command to limit the max sectors per transfer to 64k (modifying the device, /dev/sda, as appropriate):

 

echo “64” > /sys/block/sda/queue/max_sectors_kb

 

Note: You must re-apply any read-ahead settings (from a command such as blockdev

          --setra 16384 /dev/sda) after applying the above setting.

 

 

The following parameter is also used to enhance the 3ware 9500S and 9550SX/9590SE/9650SE’s sequential write performance with Linux kernel 2.6.

 

When doing heavy I/O to a Linux block device with a large queue depth (such as a 3ware array), the Linux 2.6 kernel has some congestion control algorithm shortcomings.  Enter the following command to work around the issue and provide increased write throughput (modifying the device, /dev/sda, as appropriate):

 

            echo “512” > /sys/block/sda/queue/nr_requests

 

 

The following parameter increases the 3ware 9500S and 9550SX/9590SE/9650SE’s performance with Linux kernel 2.6 by selecting the ‘deadline’ I/O scheduler.

 

Sequential I/O results can be slightly increased by changing the default I/O scheduler to be the ‘deadline’ I/O scheduler.  Enter the following command to select the deadline

I/O scheduler (modifying the device, /dev/sda as appropriate):

 

            echo “deadline” > /sys/block/sda/queue/scheduler

 

            OR

 

            Kernel command line addition:  elevator=deadline

 

 

 --------

---

