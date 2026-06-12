---
title: "Migrate Hard Drive"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by Gladier on 2007-08-14
i know this has been asked a thousand times and can be done with copydisk or dd - however i have a twist:popcorn:

a long long time ago in a faraway land gladier was a linux n00b and didnt realise the benefits of having seperate partitions for his ubuntu install.

now comes the sad sad day when his home directory takes up most of the drive and needs to be seperated.

end of story :lol:

basically i have two hard drives a pata 300g and a 15k scsi 36 gig.
scsi drive is empty, pata drive has 2 partitions (one 270gb ext3 and one swap)

my home directory is becoming ... bloated to say the least - and to  save the hassle of reinstalling and getting settings right.

for speed reasons i want to move everything but the home directory to the scsi drive. i do have enough space on the 300 to create a partition large enough to house the home directory.

im my mind what im going to need to do is:
1)create a new partition for home
2)in a livecd move all my data from home to the new home partition
3) edit fstab to mount home at boot
4) check it works
5)create seperate partitions on the scsi drive for usr and var etc etc etc
6) in a livecd move the data across and edit fstab to suit
7) reinstall/edit grub to boot from the scsi drive
8) resize my home partition to fill the drive.

so yes i know what i need to do but im a little unsure of editing the fstab and grub. and moving everything while keeping permissions/ownership

any help would be much appreciated.

edit: and then i want to put in a second ide drive and software raid/lvm a mirror for redundancy - but that can wait

---

### Post by BobE on 2007-12-12
I know U want to leave home & move everything else.  This is the reverse of that but may still have useful info for U. This is a gr8 write up:  [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
Lots of detail & discussions.

Below is just the commands (frm above) I use to move home to another partition.  I did this while booted, I did not use the live cd.   

It worked for me. I made an ext3 partition on sda3 & then followed the writeup. I had to use sudo in 3 more places. Here is my (slightly modified) list of commands:

$sudo mkdir /mnt/newhome
$sudo mount -t ext3 /dev/sda3 /mnt/newhome
$cd /home/
$sudo find . -depth -print0 | sudo cpio -–null -–sparse -pvd /mnt/newhome/
$sudo umount /mnt/newhome
$sudo mv /home /old_home
sudo mkdir /home
$sudo mount /dev/sda3 /home

Cursorily verify that everything works right. (it did)
Now, you have to tell Ubuntu to mount your new home when you boot. Add a line to the “/etc/fstab” file that looks like the following:
/dev/sda3 /home ext3 nodev,nosuid 0 2

Once all this is done, and everything works fine, you can delete the “/old_home” directory by using:
$sudo rm -r /old_home

---

