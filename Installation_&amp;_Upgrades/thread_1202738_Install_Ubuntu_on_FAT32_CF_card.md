---
title: "Install Ubuntu on FAT32 CF card"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by ralyon on 2009-07-02
Let me first start off by saying that I know you can not install a linux system on FAT32 so if that is your only response, please don't post.

I'll try to describe my situation. I have set up a micro pc which uses a CF card for the drive that my company will use as monitoring. We have it working partitioned as ext3 currently, but my problem is we need to create hundreds of these and repartitioning/reformatting the CF cards to ext3 has not been reliable.

What I am thinking of trying is to create a virtual image similar to the way wubi does in windows which I could format as ext3, but would reside on the fat32 partition so we should be able to simply copy the virtual partition from one card to another to make additional copies and then just install grub to point to the virtual partition on each card.

I'm having a hard time finding info on how to do this though so any hints or links you can provide would be greatly appreciated. I'll continue to research and post updates as I have them.

ralyon

---

### Post by C.S.Cameron on 2009-07-02
Persistent installs using usb-creator or unetbootin work fine with FAT32.
sudo dd if=/dev/sda of=/dev/sdb works great for cloning drives.

---

### Post by ralyon on 2009-07-06
I've used persistent installs on 1 GB thumb drives and I find that if you make to many modifications to the base install it will fill up the persistent space and fail to boot the next time on 8.10 systems. We use them a lot for backup up files and imaging systems here at the office and I keep a backup of the casper file which I replace when I have these problems. I haven't had the problem with 9.04 yet so they might have fixed it, but I'm not comfortable with using this in production yet.

I'll try and run some stress tests with that configuration to see if it is stable enough to use if i can't use a virtual partition. Thanks for the suggestion.

Daniel

---

### Post by ralyon on 2009-07-07
Can you do a livecd boot into a minimal cli system like you get by doing a cli install from the alternate cd and make it persistent? My problem is the computers are 200Mhz with 128MB ram so running gnome is not only useless since they are headless units but also not very practical. They are currently running a stripped down system (less than 350MB total) as well and the systems are more than powerful enough to do the modbus data grab and upload to an external server via a python program with this install.

ralyon

---

