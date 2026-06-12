---
title: "[SOLVED] install partition"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by hydraulicjj on 2009-01-03
hi
I was wondering if anyone knew how i could make a partition that i could install ubuntu off. pretty much the same way as what computer manufacturers do so you can re-install windows if it goes wrong. thanks.

---

### Post by dragos_iliescu_2005 on 2009-01-03
Use live cd and select manual install. From that point on, you will be guide how to make a new partition for ubuntu installation.

---

### Post by hydraulicjj on 2009-01-03
> **dragos_iliescu_2005 said:**
> Use live cd and select manual install. From that point on, you will be guide how to make a new partition for ubuntu installation.

i know that but i want to know how to make a partition where i can install ubuntu from so i dont have to use a cd

---

### Post by DeMus on 2009-01-03
> **hydraulicjj said:**
> i know that but i want to know how to make a partition where i can install ubuntu from so i dont have to use a cd

I don't know if this works but you could give it a try:
Copy the whole CD, inclusive hidden files of course, to your harddrive.
Make an extra line in Grub to that partition so it should be possible to start-up the installation as if you would do it from a real CD.
Once more, I have no idea if it works, never tried it myself.
Also it is an absolute must that your MBR, including Grub, is still operational.

Demus

---

### Post by hydraulicjj on 2009-01-03
> **DeMus said:**
> I don't know if this works but you could give it a try:
Copy the whole CD, inclusive hidden files of course, to your harddrive.
Make an extra line in Grub to that partition so it should be possible to start-up the installation as if you would do it from a real CD.
Once more, I have no idea if it works, never tried it myself.
Also it is an absolute must that your MBR, including Grub, is still operational.

Demus

do you know what i would have to put in my grub list?

---

### Post by DeMus on 2009-01-03
> **hydraulicjj said:**
> do you know what i would have to put in my grub list?

I just looked in my own Grub list and I have to admit I really have no idea what you should put into the Grub list. Sorry, can't help you there.
If you do find out please let us know here, so others can benefit from it.

Success.

DeMus

---

### Post by jerrylamos on 2009-01-03
This assumes you have a running linux on the hard drive and want to install another, or else just want to run another linux Live - without making a CD.  You have to download desired the linux .iso image onto the hard drive.

Then make a 1 gb partition. You might be able to squeak by with 750 mb.  If gparted isn't installed, then Synaptic or sudo apt-get install gparted. Achtung! Use test system and backup anything you want, futzing around with gparted can trash a hard drive instantly!

Use gparted to create a 1 gb partition from resizing or whatever:

sudo gparted
select 1 gb partition
# Achtung! Note what partition it is, in this case sda10
format ext3
apply
quit

In my case I'm downloading the latest Daily Build fairly frequently, for example make an executable file:

#filename rsyn or whatever you use
rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/jaunty-desktop-i386.iso .
rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS .
md5sum jaunty-desktop-i386.iso >> MD5SUMS
less MD5SUMS
#

then sudo chmod 777 rsyn 
run the file: ./rsyn

Create CD image on the 1 gb partition, I use an executable file in the same directory as the .iso is in.  Change the line with sudo mount to match the name of your .iso.

# filename LivePartition10 hda(0,9) note these must match gparted
mkdir /tmp/install_cd
sudo mount jaunty-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
#Achtung! Dangerous - which sda?
sudo mount /dev/sda10 /mnt/installer
sudo cp -r /tmp/install_cd/* /mnt/installer
sudo cp -r /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd
#

of course sudo chmod 777 LivePartition10 or whatever filename you used.
Run the file: ./LiveAPartition10

Now update menu.lst to enable booting the CD image:
sudo gedit /boot/grub/menu.lst. I copy the following file into menu.lst just after the "...Automagic..." line.

#name Livesda10 or whatever you choose, (hd0,9) to match sda10
title jaunty Live
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw quiet splash
initrd /casper/initrd.gz

title jaunty Live recovery
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw single
initrd /casper/initrd.gz
#

If you don't have a large memory, for example if you have 512 mb, then use ramdisk_size 384000. It could be smaller I think if you want to play around. I don't know much about root=/dev/ram.

Enjoy....I've found it pretty quick to do rsyn most days to get the latest daily build, then LivePartition10 to copy it to the CD image on the 1 gb partition. The exec complains it can't create the directories since they exist already, then goes right on to finish the copy. Reboot  choosing the Live partition and find out that my launchpad bugs still aren't fixed: 310982 312332

Jerry

---

### Post by hydraulicjj on 2009-01-03
> **jerrylamos said:**
> This assumes you have a running linux on the hard drive and want to install another, or else just want to run another linux Live - without making a CD. ...

Jerry

cool thanks for your help

---

