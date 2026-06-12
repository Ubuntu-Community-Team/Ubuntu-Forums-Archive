---
title: "mounting /dev/disk"
date: 2014-06-11
forum: Hardware
---

### Post by ericmikrut on 2014-06-11
So a while back, I turned on my computer, but instead of loading like it usually does, it just brought up this screen that said:
 mount: mounting /dev/disk/by-uuid/72ff2ac7-7a7f-4286-9f1b-e729ead5e8df on/root
mount: mounting /dev on /root/dev failed: No such file or Directory

Then some more stuff like that. (If it makes a difference, the version is 12.04 LTS) I'm kinda new to ubuntu, and had my friend set up my computer for me, so I have no clue what to do. He told me to re-format it, but I can't for the life of me figure out how to do that from my USB. I've read some forums before, and I wanted to mention that my laptop doesn't have a disk drive. Any help would be much appreciated.

---

### Post by yancek on 2014-06-11
When you say you don't have a disk drive, are you referring to a CD/DVD drive?  If you don't have a hard drive I would wonder where your Ubuntu is?  Do you have the Ubuntu installation medium on a flash drive?  The message you are getting seems to indicate it is trying to mount the root partition at a uuid which it can't find.  Boot the flash drive and open a terminal and run the following and post the output here:

sudo fdisk -l
sudo blkid

---

### Post by ericmikrut on 2014-06-12
Thanks for the tip, I will try that but whenever I plug in my USB, it gives me a message saying BOOTMGR is missing, press any key to continue. When I press a key, the same message just appears under it.

---

