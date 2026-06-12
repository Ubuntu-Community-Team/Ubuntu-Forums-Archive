---
title: "Tweak write behind for SSD"
date: 2009-09-15
forum: Hardware
---

### Post by V-600 on 2009-09-15
Reading an article on macs I found something interesting. It stated that osx uses aggressive read ahead/write behind to keep a snappy desktop.

I also know that ubuntu uses readahead to speed up booting and that sreadahead is supposed to provide extra benefits for SSD machines.

What I would like to know is if there is anyway to tweak write behind settings as writing small amounts of data to the SSD in my aspire one seems to be slowing things down noticeably. 

As a layman I understand that write behind means that files that are changed or saved aren't written to the disk at the same time you tell the computer to hence providing a more snappy feel.

Basic question is would mounting my ssd "/" with the async option speed things up, and is there anything else I could do to make it faster.

Thanks

---

### Post by V-600 on 2009-09-17
I've been doing some research and have found this website [http://www.thewolfweb.com/message_topic.aspx?topic=566938](http://www.thewolfweb.com/message_topic.aspx?topic=566938) suggesting the following code which may speed up firefox on an SSD. However I am dubious about running random code I find online. Most of it makes sense but I still thought i'd post it here for to see if people with more experience think it'd do what it claims to do.

# Initialize disk image
dd if=/dev/zero of=/home/.mozilla-cache.img bs=1024 count=131072

# Setup a loopback device (assuming the secondary 16GB SDHC is mounted on /home)
losetup /dev/loop0 /home/.mozilla-cache.img

# Create a mirror
mdadm --create /dev/md0 --level=1 --write-behind=1024 --num-devices=2 /dev/loop0 --write-mostly /dev/ram0

# Create the filesystem
mke2fs -j /dev/md0



Copy the template bootscript in /etc/init.d and in the "start" section add:

losetup /dev/loop0 /home/.mozilla-cache.img
mdadm --assemble --scan
mdadm --add /dev/md0 /dev/ram0

---

