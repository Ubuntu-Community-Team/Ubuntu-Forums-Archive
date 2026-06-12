---
title: "USB automount NOT WORKING"
date: 2008-12-06
forum: Hardware
---

### Post by iosifidis on 2008-12-06
Hello,

I have Ubuntu 8.04 installed.
The last few days when I plug my USB drive, the system doesn't mount it automatically. I have to click on it when I have the nautilus opened or go to PLACES>Usb_disk.

I found on line a post that I must delete an fdi file but I didn't find it in the directory that I had to find.

The lsusb command gives me that it's pluged.

Then I found a post:

Alt+F2 > gksu nautilus 

Found the directory /media/ and I deleted 2 files: 
    .hal-mtab
    .hal-mtab-lock

Then restart but it didn't help.

Can anyone help?

---

### Post by iosifidis on 2009-03-25
Hello,

Well, here's the thing.

I made a fresh installation. I have 3 partitions:

1st is the root /
2nd is the home /home
3rd is the swap

So when I make an installation, I don't have to keep backup. Now I made a fresh install but I created another user, I copied all files there and erased the old user. There were files kept there that when I did fresh install, using the same user, there were some files kept in there, preventing the automount fucntion.

---

