---
title: "Installing Breezy over Gentoo w/ existing LVM volume"
date: 2005-12-25
forum: Installation &amp; Upgrades
---

### Post by mike_d on 2005-12-25
I have been slowly switching the computers in my house over to Ubuntu from gentoo.  Because Ubuntu's installation is so easy I have sucessfully set up all of the terminals and laptops in the house with no problems.  Now since I have some free time over the holidays I'd like to move my data server over to Ubuntu.  The data server has a large number of cheap IDE discs all put together in one large LVM2 volume.  It's the only LVM setup that I've ever done, so I just followed the instructions and forgot about it.  My main question is, how do i install Ubuntu and still keep the LVM info so that I don't lose any data.  I wasn't too stupid when i originally set it up, root is on it's own disc, so I don't need LVM to get it booted, i just need it to access the data.  If it helps, here's the output from df, just to show you how my partitions are set up.

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              17G  2.1G   15G  13% /
udev                  125M  232K  125M   1% /dev
/dev/sda1              71M   48M   24M  67% /boot
/dev/mapper/vg-main   457G  187G  271G  41% /boron1
/dev/sdb1              18G  2.8G   15G  17% /boron2
none                  125M     0  125M   0% /dev/shm


```

---

### Post by ed_d on 2005-12-26
What I would do is seeing that the contents of your "server" seem to be snall, copy them to one of your other PCs in the house and re-install. Or if feeling adventurous, when you get to the disk partitioning of Ubuntu, do it in manual mode, and with the output from your current "df" you should be able to leave the data portion alone and install over gentoo.

I re-installed Ubuntu, but I had a second drive in its own filesystem that I keep my data on, so I just cleard out the first os drive and re-installed.

I would, as a learning experiment to you, back up the data on one of the PCs on the network, then do the re-install, without touching the other drives. Once done, just remount those other filesystems, using the System>admin>disks, give those drives a mount point, "enable" then edit /etc/fstab to set the changes for the next reboot, and you should be all good...

---

### Post by mike_d on 2005-12-27
thanks for the reply, ed.  unforutnately i don't have space to backup the data (i know, i know, i should have backups for everything), it's also not a catastrophe if i lose the data, it's mostly music and dvd rips of stuff i already own and could easily replace, it would just be a huge pain to do that.  the discs on my server are small compared to real live servers, but compared to my other networked comptuers, it's huge.  most of my computers are left over from when i was in college (5+ years ago).  i haven't been keeping up with buying new hardware.  i just get a new laptop for presentaions and stuff every couple of years and that's usually my main computer.  the others are either just dumb x-terminals or data storage now.

i was hoping to see if there was a way to carry the lvm configuation info over to the new system.   i did find this in the lvm howto: 

[http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://www.tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

does it make sence that i could "export" my volume, install ubuntu.  and then do the pvscan and vgimport steps in ubuntu?

sorry if these seem like simple questions, but this is something i don't have much experience with.  most of the time i just screw around until i learn how to do something, but here, i don't really want to lose the data on the volume group.

thanks!
mike

---

