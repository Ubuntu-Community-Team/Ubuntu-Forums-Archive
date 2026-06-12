---
title: "Laptop Unplugged"
date: 2010-08-30
forum: Hardware
---

### Post by diablo69er on 2010-08-30
I had my laptop plugged in to the adapter, however one of the children decide to unplug this cord without the battery in the laptop.  So needless to say the laptop powered off.  When I went to start ubuntu 10.04 again, it basically said this.

Enter your encryption passphrase: I did so.and then it drops me to the following.

no init found.  try passing init=bootarg.  Busybox v1.13.3 Ubnuntu 1:1:13.3-1ubuntu11 built in shell ash.

Now here's what i've done so far.

I have messed around with gparted, checked the file systems, everything seems good to go.  I know my root partition is on /dev/sda1.

Here is my fsck output while running a live cd.

ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# fsck -f /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 211/124496 files (2.4% non-contiguous), 57042/248832 blocks

I have also tried to edit the grub menu to see if that was the problem, however I can't even access that because of the ^ error.

I have read every post in these forums that relates to this..and so far i've seen a ton of suggestions, all of which I have tried and failed.  Does anyone know of anyway to get this up and running?

---

### Post by diablo69er on 2010-08-30
Ended up solving this one on my own.

Install required packages using the following command

sudo apt-get install lvm2 cryptsetup

probe required module using the following command

sudo modprobe dm-crypt

setup the crypto module to recognise the partition

sudo cryptsetup luksOpen /dev/hda5 crypt1

Enter your passphrase. You should get the following message:

key slot 0 unlocked.
Command successful.
If not, something has gone wrong.

Scan for volume groups

sudo vgscan --mknodes
sudo vgchange -ay

From there I created my mount point 

mkdir /media/root

In my case I did mount /dev/Wizardsfire/root /media/root
When that was finished I ran 
fsck -c /dev/Wizardsfire/root
I pressed y when needed, when all was said and done..booted up into my operating system just fine.

---

