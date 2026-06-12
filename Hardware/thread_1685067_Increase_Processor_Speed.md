---
title: "Increase Processor Speed?"
date: 2011-02-10
forum: Hardware
---

### Post by Mr. Matt on 2011-02-10
I just got a new Asus G73JW laptop.

I do web development and the laptop is fast in most things however, one thing it is incredibly slow.

In my work I have a large MySQL database that sometimes needs to alter table definitions.  On my old desktop and on our server, it takes about 10 minutes to perform this task.

On my new laptop, this is taking HOURS.

Is there anything I can do to temporarily increase processor speed?  I think Ubuntu may be limiting it.  Viewing the System Monitor, there are 8 CPUs listed but it looks like only 2 are being utilized during this process and only between 10-20%.

---

### Post by P4man on 2011-02-10
Its probably not the CPU, but the harddisk (and/or a lack of RAM?). notebook harddrives are notoriously slow compared to proper desktop drives, but unless your desktop had an SSD (or proper raid), I wouldnt expect the difference to be more 3 or 5x at most.

Have a closer look in system monitor, are you your running out of ram? Also try running ```
iotop
``` to get an idea of whats going on on the disk. 

If it turns out its a disk IO bottleneck, consider buying an SSD for your laptop. It will make a tremendous difference.

---

### Post by Mr. Matt on 2011-02-10
> **P4man said:**
> Its probably not the CPU, but the harddisk (and/or a lack of RAM?). notebook harddrives are notoriously slow compared to proper desktop drives, but unless your desktop had an SSD (or proper raid), I wouldnt expect the difference to be more 3 or 5x at most.

Have a closer look in system monitor, are you your running out of ram? Also try running ```
iotop
``` to get an idea of whats going on on the disk. 

If it turns out its a disk IO bottleneck, consider buying an SSD for your laptop. It will make a tremendous difference.

Thanks for the suggestion.  This laptop has 8 GB of RAM and only 2-3 GB are being used even when I have a lot of programs open so I don't think that is the problem.

I have installed iotop and will look into that more.

---

### Post by asmoore82 on 2011-02-10
+1 for hard disk bottleneck.

I've just began my development journey proper in the last few months -
Here's what I think I've picked up &#8230;

InnoDB tables cause much more disk I/O than MyISAM tables.
This combined with key constraint checks equals insanely slower
at maintenance operations and data imports.

But, InnoDB's row level locking will lead to better throughput in
realistic read/write scenarios. Also, realistically, the key constraints
are the only thing that keeps the database from turning into just a
steaming pile of bytes - or worse, yet another useless spreadsheet.

For the time being, I'm using MyISAM for development/alpha testing and
converting to InnoDB for the beta test site. If this is a bad idea
I'm sure I'll learn that the hard way eventually.

---

### Post by gordintoronto on 2011-02-10
What disk format are you using? I think EXT3, for example, would slow this process down a lot.

---

### Post by Mr. Matt on 2011-02-10
> **gordintoronto said:**
> What disk format are you using? I think EXT3, for example, would slow this process down a lot.

I am using Ext4.  And my old desktop is also using Ext4.

I thought Ext4 was supposed to be a good format no?  The hard drive is 7200RPM SATA.

---

