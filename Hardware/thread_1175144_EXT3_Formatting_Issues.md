---
title: "EXT3 Formatting Issues"
date: 2009-05-31
forum: Hardware
---

### Post by X96 Design on 2009-05-31
I just finished reformatting my External Hard Drive as EXT3. I went to do a backup of my home folder, and I got an "Input/Output" error. (See attached screenshot)

This is the first time I've ever formatted something other than installing Ubuntu over Windows.

I used GParted. It's an EXT3 Partition with a capacity of 596.17 Gigs.

Thanks,
X96 WD

---

### Post by expelledboy on 2009-06-01
I am going to take the guess that it has been mounted incorrectly..

Go to a terminal, type in *mount* and check with what options it has been mounted.

---

### Post by X96 Design on 2009-06-01
Here's what it says for that drive:
> /dev/sdb1 on /media/Lafawnduh type ext3 (rw,nosuid,nodev,uhelper=hal)

Yes, the drive's name is "*Lafawnduh*" :p

// X \\

---

### Post by expelledboy on 2009-06-02
Ok well I dont see a problem there..

I actually dont use ext3 for external hd larger than 200gb. Instead I use xfs. But that is just my personal preference.

You could try format from the command line..

I am guessing that your hd is located at /dev/sdb.. you could double check
```
sudo fdisk /dev/sdb
```
[LIST]
[*]type `d` to delete the current partition
[*]then `n` to start a new one
[*]`p` for primary partition
[*]`1` to select what partition number it should be (I dont know why this isnt automatic?)
[*]hit enter twice to select the default choices for start and end sectors
[*]`w` to write and save the partition table
[/LIST]

Now we format the thing
```
sudo mkfs.ext3 -L LabelAbitMoreIformative /dev/sdb1
```

and you are a4away! :popcorn:

---

### Post by X96 Design on 2009-06-02
The option to format as XFS is disabled in GParted, can you think of a reason why?

Thanks,
X96

---

### Post by expelledboy on 2009-06-02
ah.. let me remember..ya
```
sudo apt-get install xfsprogs
```
that should do it :)

You could also format xfs via the command line.. just use this line instead of the one I gave in my previous post
```
sudo mkfs.xfs -L Label /dev/sdb1
```

---

### Post by X96 Design on 2009-06-06
Fixed! Formatting as XFS seemed to work... I haven't got one I/O error yet, and hopefully won't ever!

Thanks
X96

---

### Post by X96 Design on 2009-08-21
Ya, I gave up. Turns out the hardware was faulty. I learned my lesson about buying the cheapest brand! :p

Got a Maxtor, works like a charm. :)

Thanks for your help!

// X96 \\

---

