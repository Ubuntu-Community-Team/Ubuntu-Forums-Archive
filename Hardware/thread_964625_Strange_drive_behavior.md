---
title: "Strange drive behavior"
date: 2008-10-31
forum: Hardware
---

### Post by easoukenka on 2008-10-31
Hello I purchased a wd usb passport hard drive and the dmesg is all filled up with errors bad sectors etc.  I have scanned the drive and everything seems to work fine on it and heck its got a 2 year warranty so I will not stress too much about it here is the log file and I think the drive is fine.

[73707.588238] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[73707.588286] Buffer I/O error on device sdc1, logical block 0
[73707.588289] lost page write due to I/O error on sdc1

I get several errors like that my problem is it likes to unmount itself frequently.  I set a label so it always mounts to bond but when it remounts the old directory still exists and it creates /media/bond_ then it will create /media/bond__ and continue going on.  This messes up all of my symlinks.  

To fix this I have to do a combination of unmount and fuser -mk (which sometimes crashes my desktop) then manually remove the directories.  

If anyone has any ideas like even a script I could run and put in cron im ok with hacks.  I would just put fuser -mk /media/bond_ fuser -mk /media/bond and repeat it but as stated this kills my computer sometimes.  I can't just rm the directory and remount because it states that its already mounted somewhere else?  This isn't an urgent problem or anything just annoying.  

Thanks for any input I am relatively linux savvy so if you can just point me in right direction I should be able to figure this out.

---

### Post by easoukenka on 2008-11-09
Well this was driving me nuts was ruining my movie indexer and symlinks wife did not know how to fix while I was gone so I decided to make a script afterall.  I know it's not pretty at all but in case anyone knows  a little bit and wants to use it shouldn't need too  much changing.  I know it could be more efficient but im not all that good a bash scripter yet so here it is simple but long.  I even threw it in a cron.  NO LAUGHING AT THIS :)

#!/bin/bash
BOND="/media/bond"
BOND_="/media/bond_"
BOND__="/media/bond__"
BOND___="/media/bond___"
CHECKER="/movies"
if [ -d $BOND ]; then
	echo "FOUND BOND"
	if [ -d $BOND$CHECKER ]; then
		echo "BOND IS PROPERLY MOUNTED"
	else 
		echo "BOND IS  MOUNTED BUT DIR NOT FOUND"	
		sudo umount $BOND
		sudo eject $BOND
		sudo rm -rf $BOND
		fixbond
		exit 1
		#sudo mkdir $BOND
		#sudo mount /dev/sde1 $BOND
		#sudo mount /dev/sdf1 $BOND 
		if [ -d $BOND$CHECKER ]; then
			echo "IT WORKED"
		fi
	fi
else 
	echo "BOND IS GONE!"
	if [ -d $BOND_ ]; then
		sudo umount $BOND_
		sudo eject $BOND_
		if [ -d $BOND_$CHECKER ]; then
			echo "MOVIES STILL FOUND /media/bond_"
		else 
			echo "FOUND BOND_ NOT MOUNTED PROPERLY WILL TRY TO FIX NOW"
			sudo rm -rf $BOND_
			sudo mkdir $BOND
			sudo mount /dev/sdd1 $BOND
			sudo mount /dev/sde1 $BOND
			sudo mount /dev/sdf1 $BOND
			if [ -d $BOND$CHECKER ]; then
				echo "IT WORKED"
			fi
		fi
	fi
	if [ -d $BOND__ ]; then
		sudo umount $BOND__
		sudo eject $BOND__
		if [ -d $BOND__$CHECKER ]; then
			echo "MOVIES STILL FOUND /media/bond__"
		else 
			echo "FOUND BOND__ NOT MOUNTED PROPERLY WILL TRY TO FIX NOW"
			sudo rm -rf $BOND__
			sudo mkdir $BOND
			sudo mount /dev/sdd1 $BOND
			sudo mount /dev/sde1 $BOND
			sudo mount /dev/sdf1 $BOND
			if [ -d $BOND$CHECKER ]; then
				echo "IT WORKED"
			fi
		fi
	fi
	if [ -d $BOND___ ]; then
		sudo umount $BOND___
		sudo eject $BOND___
		if [ -d $BOND___$CHECKER ]; then
			echo "MOVIES STILL FOUND /media/bond___"
		else 
			echo "FOUND BOND___ NOT MOUNTED PROPERLY WILL TRY TO FIX NOW"
			sudo rm -rf $BOND___
			sudo mkdir $BOND
			sudo mount /dev/sdd1 $BOND
			sudo mount /dev/sde1 $BOND
			sudo mount /dev/sdf1 $BOND
			if [ -d $BOND$CHECKER ]; then
				echo "IT WORKED"
			fi
		fi
	fi
fi

if [ -d $BOND$CHECKER ]; then
	echo "IT DID WORK ENJOY"
else
	sudo umount $BOND
	sudo eject $BOND
	sudo umount $BOND__
	sudo eject $BOND__
	sudo umount $BOND___
	sudo eject $BOND___
	sudo rm -rf $BOND 
	sudo mkdir /media/bond
	sudo mount /dev/sdd1 $BOND
	sudo mount /dev/sde1 $BOND
	sudo mount /dev/sdf1 $BOND
	if [ -d $BOND$CHECKER ]; then
		echo "LAST SHOT BUT IT WORKED"
		exit 1
	fi

fi

---

### Post by easoukenka on 2008-11-20
Ok after this has been working so nicely for so long I am having a problem.  

the directory /media/bond can't be deleted because the device is busy.  There is nothing there and the drive is mounted now in /media/bond_  I did the usual fuser -mk/umount /media/bond but it still says drive is busy.  

If I do an LS i get input out error and if I try to adda  file it says its a read only filesystem.  If I do eject I get 
eject: tried to use `/dev/sdd1' as device name but it is no block device
eject: unable to find or open device for: `/media/bond'

This problem has been very annoying and now I have to  reboot I hate rebooting linux as it should never need done :) 

Thanks for any input on this

---

