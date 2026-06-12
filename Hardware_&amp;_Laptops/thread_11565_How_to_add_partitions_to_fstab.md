---
title: "How to add partitions to fstab?"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by coolbreeze on 2005-01-17
When i installed Ubuntu I moved to quickly and didn't tell installation to mount my WindowsXP and Debian partitions.  I know because the XP partition is ntfs it would be read-only.  But the Debain is ext3 so I should be read/write.  Now how do I add lines to fstab using the terminal?  If I could log in as root I could use a text editor to add the lines directly.  I have no ideaa how to add lines using the terminal. Please tell me how and while you at it do you know the specifics of the lines I should add? 

coolbreeze

---

### Post by 3spades on 2005-01-17
I use pico/nano, i guess if ya want a graphical interface do a sudo gedit /etc/fstab

/dev/hdb1       /files          ext3    defaults        0       0
/dev/hda1       /C              ntfs    ro,user,auto,uid=lenny  0       0

is how i have mine, if ya dont know the partition fdisk the drive and p to print the partition table, m for help

---

### Post by Buffalo Soldier on 2005-01-17
How to mount Windows partition (NTFS) on boot-up, and allow all users to read only?
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

For beginner users Unofficial Ubuntu 4.10 Starter Guide is a good place for you to start looking at besides this user forum.

---

### Post by coolbreeze on 2005-01-17
thanks to you both. i got the lines added to fstab using pico as you suggested. i have never heard of pico.  i like it!  the Ubuntu guide is full of information and it helped me write the lines. thx again.

---

### Post by coolbreeze on 2005-01-17
woohoo!! I just rebooted and my new fstab worked!  all my partitions are mounted!!! and read/write is the way it's supposed to be!  beginning to get hooked on Ubuntu!

---

