---
title: "Cloning a hard drive."
date: 2008-07-21
forum: General Help
---

### Post by Roasted on 2008-07-21
Is there any software out there that does an exact clone of your hard drive, similar to ghost?

---

### Post by logos34 on 2008-07-21
Partimage, Clonezilla, Ghost4Linux.  Or just use the **dd** command

---

### Post by eximius1 on 2008-07-21
Cloneit is another one.

---

### Post by Roasted on 2008-07-21
Is there any how-to guides with partimage you'd recommend?

---

### Post by logos34 on 2008-07-21
The partimage guides leave something to be desired.  But try these two:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by DGortze380 on 2008-07-21
> **Roasted said:**
> Is there any how-to guides with partimage you'd recommend?

the simplest way to get an iso of a drive is to use dd. But then, I'm a command line junky. man dd for more info or post here and we'll help you nail down the exact command you need.

---

### Post by logos34 on 2008-07-21
> **DGortze380 said:**
> the simplest way to get an iso of a drive is to use dd. 

Yeah, I love dd.  Have you noticed how everyone else is prejudiced against it? (no gui) True, it does copy everything, used and UNUSED disk space, but the command is so simple and elegant.

---

### Post by Radioman991 on 2008-07-21
I used this.....

[http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php](http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php)

...to create an image of my Windows drive on my dual boot Dell desktop.  Worked like a charm.  Hope it is helpful.

---

### Post by cprofitt on 2008-07-21
dd is an excellent tool; and there are times you want everything.

---

### Post by Spaceman9 on 2008-07-22
If I use dd will it break up an image of the drive in case the image won't fit on one cd-rw?

---

### Post by Roasted on 2008-07-22
So, I'm trying to understand this.

I have a 15 gb partition for Ubuntu's OS, and my home dir on another partition to itself.

Can I DD my freshly installed/fully configured setup to an image, burn it, and if I ever mess up Ubuntu, just pop the CD in, reboot, and install?

---

### Post by logos34 on 2008-07-22
I do the same thing with my / partition (which is a manageable size because I have a separate /home partition), but use Partimage because it only copies used sectors, and so I end up with a gzipped image ~2 GB--which easily fits on a DVD.  DD is better suited IMO for transferring a partition or copying a whole disk to another disk.  Partimage will by default split the images into 2 gb slices.  So that's what I'd use.

But if you want to use dd, here's the command to make an image of partition sda1, and pipe it through gzip, and save as file 'sda1backup.img.gz' to partition sda5:

**sudo dd if=/dev/sda1 | gzip > /media/sda5/sda1backup.img.gz**

to restore:

sudo gzip -dc /media/sda5/sda1backup.img.gz | dd of=/dev/sda1

If the file ends up too large to burn to dvd, you could run the split command:
[B]
split -d -b 4480m - /media/sda5/sda1backup.img.gz[/B]

this will make dvd5-size (single layer) slices

---

### Post by Roasted on 2008-07-22
How exactly would I restore this if I were to do a fresh install of Ubuntu? Would I have to reinstall, then pop the imaged disc in and have my way with it? Or what?

---

### Post by Krupski on 2008-07-22
> **Roasted said:**
> Is there any software out there that does an exact clone of your hard drive, similar to ghost?

The 'dd" command works very well. It works like this:

dd if=input-file of=output-file bs=block-size count=how-many-blocks

Here are some command line examples. [COLOR="Red"]**DO NOT RUN THEM - THEY ARE JUST EXAMPLES!**[/COLOR]

```

[COLOR="Red"]**# WARNING! EXAMPLES ONLY - DO NOT EXECUTE**[/COLOR]
# copy /dev/sda to /dev/sdb, both of which are 100 gigabyte drives:
dd if=/dev/sda of=/dev/sdb bs=1G count=100

# copy /dev/sda to a file for later use:
dd if=/dev/sda of=/tmp/disk.img bs=1G count=100

# copy an image file to a drive called /dev/sda:
dd if=/tmp/disk.img of=/dev/sda bs=1G count=100
[COLOR="Red"]**# WARNING! EXAMPLES ONLY - DO NOT EXECUTE**[/COLOR]

```

Of course, you need to be root or prefix the commands with 'sudo'.

And, at a speed of 40 some megabytes per second, the 'dd' command will take quite a while to copy multi-gigabyte sized drives, so be patient.

Another thing... obviously you cannot store the image of a drive on the same drive. You wouldn't want to try making an image of, say, /dev/sda to /tmp/disk.img which resides on /dev/sda... you would be trying to put 10 gallons of data into a 9 gallon bucket! :)

Lastly... see 'man dd' for more info.

-- Roger

---

### Post by logos34 on 2008-07-22
> **Roasted said:**
> How exactly would I restore this if I were to do a fresh install of Ubuntu? Would I have to reinstall, then pop the imaged disc in and have my way with it? Or what?

Get **Parted Magic** rescue cd (see my sig)--it runs entirely from ram, freeing up the cd/dvd drive. Pop in the dvd/imaged disc and mount it, start up partimage from the command line, tell it what partition to restore to, put in the path to the backup image on the dvd, and select 'restore' option.  For dd, just run the restore command with the path to the image on the dvd.  

If you have a separate /home you could also just store the image there, and use dd or  partimage from the ubuntu live cd.

---

### Post by Roasted on 2008-07-23
Hm, so with it running entirely from RAM, is that what gives it the capability to function and leave the hard drive open for restoration?

---

### Post by logos34 on 2008-07-23
Yes.  Whatever partition you're cloning or restoring to cannot be mounted.  So in the case of / (and /home if on separate partition) that means you have to work from a live cd (whether Ubuntu or a rescue/utility cd).

---

### Post by Krupski on 2008-07-23
> **logos34 said:**
> Yes.  Whatever partition you're cloning or restoring to cannot be mounted.  So in the case of / (and /home if on separate partition) that means you have to work from a live cd (whether Ubuntu or a rescue/utility cd).

That's not *precisely* true...

An active, mounted partition may be read using 'dd' and written to a file on a DIFFERENT partition.

For example, here's a little script that I use to backup my 4 GB compact flash card (which is the active root and swap for an Ubuntu Server box):

```

[COLOR="Red"]**# WARNING - EXAMPLE ONLY - DO NOT EXECUTE #**[/COLOR]
###########################
# /usr/local/sbin/savecf
###########################
# mini-man for dd
#
# /bin/dd if=input-file of=output-file
# -bs=block-size -count=how-many-blocks
#
# BLOCKS and BYTES may be followed by the following
# multiplicative suffixes: xM M, c 1, w 2, b 512,
# kB 1000, K 1024, MB 1000*1000, M 1024*1024,
# GB 1000*1000*1000, G 1024*1024*1024
###########################
echo Saving OS image, please wait...
/bin/dd if=/dev/disk/by-id/edd-int13_dev80 of=/home/shared/ftp/linux/ubuntu/ubuntu-server-snapshot-$(date +%d-%b-%Y-%H%M).vhd bs=32K count=128K
# set permissions so Windows people can't delete these
/bin/chown root /home/shared/ftp/linux/ubuntu/ubuntu-server-snapshot-*.vhd
/bin/chgrp root /home/shared/ftp/linux/ubuntu/ubuntu-server-snapshot-*.vhd
/bin/chmod 0444 /home/shared/ftp/linux/ubuntu/ubuntu-server-snapshot-*.vhd
echo Done!
[COLOR="Red"]**# WARNING - EXAMPLE ONLY - DO NOT EXECUTE #**[/COLOR]

```

The destination file resides on a RAID array and Linux has no problem at all reading the entire ACTIVE and MOUNTED device and writing it to another file.

Actually, 'dd' will even write to an active, mounted drive or partition... but it will only go so far and then crash as the data overwrites a running system! :eek:

---

### Post by logos34 on 2008-07-23
> **Krupski said:**
> That's not *precisely* true...

I was thinking of Partimage, which is what I recommended he use.

But you're right--dd can copy from mounted filesystem (never tried to *write* to a mounted--let alone active--system partition though!).  But it will be even slower..you'll get better I/O performance if you run dd command on an unmounted filesystem--this prevents concurrent random access to the mounted file system.

---

### Post by Krupski on 2008-07-23
> **logos34 said:**
> I was thinking of Partimage, which is what I recommended he use.

But you're right--dd can copy from mounted filesystem (never tried to *write* to a mounted--let alone active--system partition though!).  But it will be even slower..you'll get better I/O performance if you run dd command on an unmounted filesystem--this prevents concurrent random access to the mounted file system.

Well, I use dd to read an active running OS for backup purposes. It works fine.

I even made an image of a "virgin" Ubuntu server install so that if I *really* screwed up, I could just re-copy the image back to the compact flash card and start fresh.

I know that dd can also write to a running system... I found out the hard way, by accident, while "perfecting" my dd backup script.

Luckily, I had a good image saved on another computer so that the fix was only 5 minutes away.

I'm on the (very steep) Linux learning curve... and I still make more mistakes than I make headway. I'm getting there, slowly but surely.

---

### Post by sofasurfer on 2008-08-03
With the 'dd' command being so simple to use and so good at clonoing a drive, and with so many people going crazy trying to find the perfect, easy to use backup software, why isn't cloneing a hard drive to a second hard drive more popular? I used to do this with windows and it worked like a charm. If I screwed up my system I just cloned it back to my main drive. The reason I can't use 'dd' to clone now is that I do not have 2 drives of the same size. From what I understand I must have 2 identicle drives.

---

### Post by linuxd00 on 2008-08-03
hi.
I just foung this fine thread. It seems its just what i was looking for:

I'd like to backup a HD. but the HD is encrypted. So will dd copy everything? i mean also MasterBoot Record and really really everything? that'd be so great!

thanks for answers!

---

