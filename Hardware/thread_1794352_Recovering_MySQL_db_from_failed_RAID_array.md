---
title: "Recovering MySQL db from failed RAID array"
date: 2011-06-30
forum: Hardware
---

### Post by zoomiest on 2011-06-30
I recognize that this isn't the typical question, but I have a problem with my Linux webserver, and I thought I would prevail on the community for some guidance.

I have this Linux webserver with an important MySQL server on it. The RAID array seems to have died while I was moving. (did someone drop it? dunno) Now it can't find any boot device.

It has 4 old SCSI drives. 

So, I know how to mount a IDE or SATA drive as a slave, in a Linux environment to read data off of it (to copy the MySQL files off of it.)

But, how do I do that with a SCSI drive?

Also, I have an additional (identical) server to the crippled one. What will happen if I just slide one of the scsi drives into the operating server? Is this second identical server going to help me at all? I don't even know what is on it. Can I reconfigure the RAID, so it's not using a drive, and then slide in a disk from the crippled server, and copy the data off of it?

How shall I configure the good server? Its pretty important that I recover the files.

Thanks in advance.

Zoomiest

---

