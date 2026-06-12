---
title: "Wipe Clean External Hard Drive"
date: 2008-04-22
forum: Hardware
---

### Post by i_like_you on 2008-04-22
I have an old Lacie 250 GB external hard drive that I bought a couple years ago, and I want to give it to my brother. But before I do, I want to wipe it clean, using something like Darin's Nuke and Boot. I tried using Darin's Nuke and Boot, but it didn't recognize the external usb drive. I know I can reformat the external drive with GParted, but I want to completely erase the data on it so that nothing can be recovered (were someone to run one of those undelete programs). I've searched Google for tutorials but, to my surprise, haven't been able to find any instructions on how to perform this task using Linux.

---

### Post by Limpan on 2008-04-22
You could use something like this to write random data to sdXX (you'll have to figure out the device name of the external drive, usually sdd or something.
```
dd if=/dev/random of=/dev/sdXX bs=8M
```
To write with zeroes instead of random you'd have to do
```
dd if=/dev/zero of=/dev/sdXX bs=8M
```
It will take a long time to do this either way.
To be absolutely positively certain that nobody would ever read it you'd have to totally destroy the disk. To be reasonably certain I'd say 3 rewrites of random data would do it.

[http://ubuntuforums.org/showthread.php?t=240257]("http://ubuntuforums.org/showthread.php?t=240257")

---

### Post by i_like_you on 2008-04-23
Thank you! I was looking for a program that might do the trick, but couldn't find one with a gui. So I used your method and it worked! I ran it three times, twice with zeros, and once with random data. It took about three hours for each run-through.

---

### Post by Limpan on 2008-04-23
Just out of curiosity, where the random run any slower than the ones with zeroes?

---

### Post by i_like_you on 2008-04-23
Actually, I spoke too soon regarding the random runthrough. I wiped the disk using zeros, and I did that twice. Each time it took 2 1/2-3 hours to complete. However, I've been running the random wipe for at least 8 hours now and I don't know when it's going to complete. I'm not in a rush to have it done so I'll let it run for another 24 hours if I have to.

---

### Post by johnboiles on 2009-09-12
I don't think random works very well. I hit ctrl-c after running:
```
sudo dd if=/dev/random of=/dev/sdb
```
and it said "183 bytes (183 B) copied, 56.8288 s, 0.0 kB/s" where when I ran
```
sudo dd if=/dev/zero of=/dev/sdb
```
and it said "352321536 bytes (352 MB) copied, 15.856 s, 22.2 MB/s"
My 500gb drive would take forever if I used random! Is this just because my random number generator is slow or something?

---

### Post by ddrichardson on 2009-09-12
Not on an Ubuntu box at the moment, but is the shred command not there?

---

### Post by -::Bas::- on 2010-01-20
> **Limpan said:**
>  To be reasonably certain I'd say 3 rewrites of random data would do it.


I know that that's always the advise given, and I don't want to sound like a smartass, but it's only necessarry to write random data over your old stuff once. 
There is NO physical way you will ever get that data back. There is NO software in the world that can get your data back after One cycle of random data writing.

---

### Post by johngreth on 2010-02-25
> **-::Bas::- said:**
> There is NO physical way you will ever get that data back
Actually, the data could be recovered using "Magnetic force scanning tunneling microscopy", but that's only if you have unlimited money, and a good reason. I have some info about how it works on [my blog]("http://johngreth.com/blog/?p=4")

---

### Post by uopjohnson on 2010-05-04
> **johnboiles said:**
> I don't think random works very well.
/dev/random is very slow because it has to wait for the system to make random data.  /dev/urandom is going to be WAY faster.  There is a difference, but I personally don't think it matters for this case.

---

### Post by antiram on 2010-05-04
most disks have secure erase (or enhanced secure erase) build in. eg. for sda:
hdparm --security-set-pass NULL /dev/sda
hdparm --security-erase NULL /dev/sda

---

### Post by willsomebody on 2011-05-26
I had to do this for a few drives, so I threw together a little script. It uses dd to copy from /dev/urandom, then from /dev/zero if you want. I also used bar to give a progress bar for each dd step.

To use do the following from a terminal:

install bar from repositories 
```
sudo apt-get install bar
```

create the file
```
gedit wipe
```

paste in script from below
save
close

back in terminal, make file executable
```
chmod +x wipe
```

use script
```
sudo ./wipe /dev/whatever
```

```
#! /bin/bash

#
#	Usage: sudo ./wipe device 
#	Ex. sudo ./wipe /dev/sdc
#
#	Use M,G for size of drive
#	Ex. 250G
#

count=0
echo "Are you sure you want to detroy all data on $1? (y/n)"
read sure

if [ $sure = y ]
then

	echo "How many passes would you like to make?"
	read pass
	echo "finish with zeros? (y/n)"
	read zero
	echo "What is the size of the drive?"
	read size
	umount "$1"1
	umount "$1"2
	umount "$1"3
	umount "$1"4

	while [ $count -ne $pass ]
	do
		echo "pass "$(( $count + 1))" of "$pass""
		dd if=/dev/urandom bs=32k | bar -s $size > $1
		count=$(( $count + 1))
		echo "$count""$1""$size" `date` >> $HOME/wipe.log
	
	done

	if [ $zero = y ]
	then
		echo "writing zeros"
		dd if=/dev/zero bs=32k | bar -s $size > $1
		echo "zero""$1""$size" `date` >> $HOME/wipe.log
	fi

fi
exit 0
```

Hope this helps!

---

### Post by heyup on 2012-01-11
> **willsomebody said:**
> I had to do this for a few drives, so I threw together a little script. It uses dd to copy from /dev/urandom, then from /dev/zero if you want. I also used bar to give a progress bar for each dd step.

Thanks for the script. Worked for me. Couldn't find bar in repository (using Lucid) but it is easy to compile and install from:

 [http://clpbar.sourceforge.net/](http://clpbar.sourceforge.net/)

It took about 4.5 hours to zero 500GB disk (no urandom passes).

---

