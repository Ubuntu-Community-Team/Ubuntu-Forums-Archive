---
title: "problem with using dd to move ubuntu installation to another hd"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by fleaaccela on 2009-07-07
I used the following commands to copy my Ubuntu installation to my main hard drive:

df -h

which told me:

/dev/sbd1 (my Ubuntu drive that I wanted to copy, ata 80gb)
/dev/sdc1 (the new hard drive to have Ubuntu copied to, sata 500gb)

then i did:

sudo dd if=/dev/sbd1 of=/dev/sdc1

I unplugged my ata drive, kept the sata plugged in, then i ran Ubuntu from a LiveCD. I pulled up a terminal and typed this in:

sudo grub 
[grub prompt came up]

find /boot/grub/stage1
[it said (hd0,0)]

root (hd0,0)
setup (hd0)
quit

I restarted the computer and my installation of Ubuntu with all my programs and data files are here on the new drive. Everything is normal except for one thing:

I opened up GParted and it tells me this:

/dev/sda1
File System: ext3
Mount Point: /
Size: 460.01 gb
Used: 437.79 gb
Unused: 22.22 gb

I have 2 other partitons: 
/dev/sda2 - extended - 5.75 gb
/dev/sda5 - linux-swap - 5.75 gb

Why does my new drive only have 22 gigs of free space? My original drive was a 80gb, and I was only using about 30 gigs or so of space. What is wrong and how can i fix it?

---

