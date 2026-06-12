---
title: "Resizing after some time"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by swmcl on 2009-04-14
Hi,

I have an Ubuntu system that has been running on and off for a while now (maybe a year).

I found that the home partition was full and I couldn't run programs anymore.  So ... I tried to resize.  I am using a USB Ubuntu external drive.

I had 4 primary partitions and a swap.  I copied all from /home (on sda4) to /usr/home (on sda3).

Using gparted as root I downsized sda3.  I then deleted the 4th primary and swap and went to an extended which is now a larger partition called /sda5 and a swap.

I then copied all of /usr/home to the new sda5.

When I try to start the computer, fsck reports sda1, sda2 and sda3 OK but fails with sda5.

I am left with a command line logon.

I've not done this before so I'd appreciate help.  There is no 'format' command at the command line either!

Rgds,

Steve

---

### Post by unutbu on 2009-04-14
What is the desired mount point for each of your partitions? For example:
```

sda1   /boot?
sda2   /?
sda3   /usr?
sda5   /home
swap?
```

Please post the output of 
```

cat /etc/fstab
blkid -c /dev/null
sudo fdisk -l
```

If you would like directions on how to post the output using the command-line,
please tell us if you have a network connection or some kind of removable media like a USB flash key.

---

### Post by swmcl on 2009-04-15
Thanks unutbu,

It's pretty dead I think.  I've just read a post here:

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

and it doesn't look good.  I had ext3 partitions.  I was using gparted all the way.  Aparently one must convert to ext2 before resizing?!

I can find a USB key (I could use the Ubuntu on USB disk) but I'm not sure how to get any networking running.

Can I make a summary of the requested info here?

sda1 was /
sda2 ? (possibly /var)
sda3 was /usr
sda4 was /home

fdisk reports the following:

/dev/sda1 * 1     1459  83  Linux
/dev/sda2   1460  3891  83  Linux
/dev/sda3   3892  5185  83  Linux
/dev/sda4   5186  9729      Extended
/dev/sda5   5186  9020  83  Linux
/dev/sda6   9021  9729      Linux Swap

blkid has this:

/dev/sda1: UUID="blk info here--lots of numbers" Type= ext3
/dev/sda2:  --same as above-- SEC_Type="ext2" Type="ext3"
/dev/sda3: --same as above--
/dev/sda5: LABEL="/home" UUID="--same sort of info here--" same type as others
/dev/sda6 TYPE="swap"

/etc/fstab looks OK too in that I can't see anything too bad or out of place.

Could you let me know what I should find?  Do I need to run a fsck somehow?

My USB keys are all FAT drives I'm afraid.

I'm on the verge of going and buying another hard drive and starting again.  All my critical data is on a separate hard drive in the machine.  This drive was running an updated stable Ubuntu.

Thanks so far.

---

### Post by unutbu on 2009-04-15
swmcl, I believe your problem is fixable without buying additional hardware, but it might take a while because we do not seem to be on the forum at the same time, which makes communication slow.

You mentioned that all your critical data is on a separate drive. What a relief that is!
Given the delays in our communication, the quickest way to solve your problem may be to reinstall Ubuntu.

However, if you'd like to try to fix the problem without reinstalling, here are some thoughts and suggestions:

First, be assured: it is entirely possible to resize an ext3 partition using GParted. You've done nothing wrong by using GParted. 

From your description, I believe that the boot process is failing because /etc/fstab references partitions that no longer exist. 

If your /etc/fstab contains a line like this:
```

# /dev/sda4
UUID=9fbf869d-738c-436e-baf4-3e40db8d2c84 /home ext3 relatime 0 2  

```
then this line would cause problems because there is no longer a partition with UUID
9fbf869d-738c-436e-baf4-3e40db8d2c84. (Each partition has a universally unique identifier, called a UUID). 

The blkid command shows the UUIDs of the partitions as they currently exist.

You could try looking through the output of "blkid -c /dev/null" and "cat /etc/fstab" and matching up the UUIDs and making sure the UUIDs are mounted at the right places. Make sure that no UUID referenced in fstab is not also mentioned in the output of blkid.

If you'd like some help doing this, we'll need to see the complete output of 
```

cat /etc/fstab
blkid -c /dev/null
```

It would also help to see the exact wording of the error message that mentions fsck, and at least a few of the lines that preceed the error message.

If you are getting all the way to a command-line login prompt, and if you usually have a network connection, then you probably have one at the command-line too.

To test if that is true, type

```

sudo apt-get install pastebinit

```
If you have a network connection, this will install the pastebinit package, which uses about 50 KB of space. If that works, then type

```

blkid -c /dev/null > /tmp/blkid.out
pastebinit -i /etc/fstab -b http://paste.ubuntu.com 
pastebinit -i /tmp/blkid.out -b http://paste.ubuntu.com 

```
The pastebinit commands will post the /etc/fstab and /tmp/blkid.out files to paste.ubuntu.com. It will output the url where the files can be found. Post back here with the urls.

If you don't have a network connection, try sticking in a USB flash key. It should get mounted at /media/disk automatically. Then you could save the output onto the flash key by typing the command
```

blkid -c /dev/null > /media/disk/blkid.out
cat /etc/fstab > /media/disk/fstab
sudo umount /media/disk     # Be sure to unmount the flash key before removing it.
```

Then remove the flash key, tote it to a computer with an internet connection, and post the contents.

PS. I don't want to tell you to run fsck yet, because fsck is a little bit dangerous -- it can delete inodes which means losing data. If we can fix this be editing /etc/fstab, that would be the much preferred solution.

---

