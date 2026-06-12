---
title: "Transfering Large Amounts of Data to USB External Drives"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by macbuzz on 2007-01-05
This is a huge problem for me and I have seen the question asked in many different ways on this forum with no answers.  Are there no really bright Linux gurus out there with the answer?  I have a hard time believing that.  Come on help the newbies.

I have two external USB hard drives connected to a laptop P4 2GhZ.  Running Kubuntu 6.10
with all current updates.

The goal is to consolidate lots of data 300Gb+ onto one external hard drive from other sources.  All are USB external HD.  The target and source USBs are connected to the USB ports of the computer.

What I have tried.

The target HD has been formated ext3, xfs and currently ext2.  I have tried these different file systems to see if I could speed up the transfer of files to the USB.  All with little impact.

Essentially, the problem is that the copying of a folder (16Gb of data - one example folder) is still running after 7 hours. There was no difference between drag and drop or using the shell.

Are there any thoughts on this problem??

Thanks

---

### Post by ethan@xmlstandards.org on 2007-01-05
I am currently transferring about five hundred gigs of data between two LaCie Big Disks with no real slowdown.

What kind of HD are you using?

---

### Post by RandomJoe on 2007-01-05
I have had serious speed issues with USB drives when transferring a whole bunch of smaller files.  (Although Windows was where it was worst - ABYSMAL transfer rates.)  Copying a single large file such as a tarball moves much faster.

I seem to have better performance when using something like rsync to make the copies, although I'm not too sure why (don't know what rsync uses that's different - if it is at all - when copying files on a local machine).  Maybe it's just because I can get status-feedback with the -v switch...!

Another option that might help, especially since you are copying between two USB drives, would be to try putting the target drive on a different networked machine then transfer across the network connection.  (Using rsync or scp, not NFS.)  Granted, you'll be limited to the NIC speed but perhaps dividing the USB handling (all done by CPU) would still make it faster than what you are seeing.

My _real_ solution doesn't help you much - I just put a firewire card in everything and only use firewire drives...!

---

### Post by macbuzz on 2007-01-06
Both drives ar Maxtor drives in 3.5 USB enclosures.

I am still waiting for the transfer of the same 16Gb at the time of this writing which is coming up on almost 20 hours.  I can see that the copying process is still running.  Things have not frozen, it is just incredibly slow.

I am wondering if the fact that my laptop is formated ext3 while the external USB drives are formated ext2 makes a difference.  My understanding is ext3 uses journaling while ext2 does not.  Could journaling be slowing the process down to a crawl.

This is 16Gb of data with lots of files and folders.

Thanks

---

