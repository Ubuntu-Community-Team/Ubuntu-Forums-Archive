---
title: "Location of USB Buffer"
date: 2008-12-27
forum: Hardware
---

### Post by Tim Legg on 2008-12-27
Hello,

I like to use flash memory to copy data between my office and my off-the-net home computer.

My trusty old USB card reader had a little LED mounted on the board to indicate when data is transferring.  I noticed long ago that when I copy a file to my USB device, the command line will return once the file is copied.  However, the light will continue flashing for another minute or so.  Once it is done, I can unmount my card and carry it home.

I have a new USB drive that is missing this LED light.  And this poses a problem for me that I can no longer tell if it is still transferring data.  For transferring files, I can umount the device and the umount process will wait until the transactions are complete.  This is not true if I am using dd to place a live distro on my drive since the device isn't mounted to the filesystem.

Where do I find this buffer so I can query it's size of content.  Not that I am impatient at times, but it would also be nice to know how much more it has to copy.

Tim Legg

---

