---
title: "Can i do this....."
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by davkasayres on 2007-09-13
Hi all,


I need a way of speeding up my data transfer process. I take a customers hard drive, and copy the data from that to a folder on my ubuntu machine. Then i have to turn the machine off, unplug the HDD and install windows on that HDD. Then i have to put it back into the ubuntu machine, turn it back on and replace the files.

Ive written a few short scripts to speed up the process of things before on ubuntu, but im wondering, is there a way i can swap these hard drives without turning the machine off?

Im assuming i can do something with hotplug, but im not sure.

Can someone help me please?

Thanks,

Dan.

---

### Post by davkasayres on 2007-09-13
Perhaps even a small terminal based script would be good. If i could get something looking like this:


*********************
**Transfer Data Wizard**
*********************

Please Select The Drive You Wish To Copy From

(e.g the folder the customers drive is on /media/backup)

Please Select The User Dir You Wish To Copy

(User Folder in c:\documents and settings\ on the customers hard drive)

Please Select Folder To Copy

(My Documents Of The User, My Pictures etc..)

Please Select Location To Copy To

(On this machine that would be /home/data/Customer Backup/)



Any help would be greatly apprciated.

Thanks, 


Dan.

---

### Post by mwolfe on 2007-09-13
I believe there are plugs you can get that convert ide/sata to usb2.0.. I know you could get an enclosure that does it.. You'll have to find one though that assembles quickly as you won't want to screw things in just to install the hard drive (or perhaps you could skip screwing it all together)
Then you can leave the ubuntu box on and it will auto detect the hard drive.. Then just write a script that does the copying over and your good to go. I find that the USB 2.0 interface copies pretty dang fast so that shouldnt be a problem unless you are copying a ton of data. Given that it takes probably at least 3 minutes (i'd say) to restart an ubuntu box you've got a little bit of leeway even if it is a bit slower. You may even want to try timing both to see what is faster if you do this a whole lot.

---

### Post by davkasayres on 2007-09-13
Thanks mate,

Actully, ive just found an enclosure just like you are describing, but im lacking a power supply for it :(

Got any ideas on how to write that script? Im at and end :S


Thanks for the advice,


Dan.

---

### Post by mwolfe on 2007-09-13
welll, here is a script i wrote for syncing an external hard drives music folder with my internal hard drive (so i could play the music elsewhere)

#!/bin/bash
OPTS="-vuza --stats --progress --delete"

SOURCE="/media/sdb2/music/"
DEST="/media/disk-2/music/"
echo "Which drive is the destination:[disk-2] "
read TESTD
if [ -n "$TESTD" ]; then
	echo "testd not null"
	DEST=/media/${TESTD}/music/
fi;

if [ ! -d ${DEST} ]; then
        echo "invalid destination";
        exit;
fi;
echo "rsync ${OPTS} ${SOURCE} ${DEST}"
rsync ${OPTS} ${SOURCE} ${DEST}


you probably won't use rsync though since your not syncing.. Try using the cp command instead..
First you need to figure out what folders you want to copy. I'm guessing you copy stuff from their user directory.
This location will change depending on whether its windows xp or vista..
Also, the user could move his/her my documents anywhere they want.. You'll probably have to make note of where it is before you begin. I dont know if you even have access to that beforehand though.. (i'm guessing the users computer doesnt work)
What you could do is copy everything from documents and settings.. Also, when they turn in the computer ask if they moved there my documents somewhere else (they probably wouldn't know what you were talking about)

Another alternative is copy everything other than windows and program files (unless you copy those anyways). This is probably the safest option. 

I'm not sure what your current strategy is, but if you have a current strategy, let me know and i may be able to help you write the script.. It shouldn't be too tough. You may have to prompt for some info so that you can do customizations.
Also, you can type bash scripting in google and you'll get all kinds of good tutorials and references.

---

### Post by tech9 on 2007-09-13
> **mwolfe said:**
> welll, here is a script i wrote for syncing an external hard drives music folder with my internal hard drive (so i could play the music elsewhere)

#!/bin/bash
OPTS="-vuza --stats --progress --delete"

SOURCE="/media/sdb2/music/"
DEST="/media/disk-2/music/"
echo "Which drive is the destination:[disk-2] "
read TESTD
if [ -n "$TESTD" ]; then
	echo "testd not null"
	DEST=/media/${TESTD}/music/
fi;

if [ ! -d ${DEST} ]; then
        echo "invalid destination";
        exit;
fi;
echo "rsync ${OPTS} ${SOURCE} ${DEST}"
rsync ${OPTS} ${SOURCE} ${DEST}


you probably won't use rsync though since your not syncing.. Try using the cp command instead..
First you need to figure out what folders you want to copy. I'm guessing you copy stuff from their user directory.
This location will change depending on whether its windows xp or vista..
Also, the user could move his/her my documents anywhere they want.. You'll probably have to make note of where it is before you begin. I dont know if you even have access to that beforehand though.. (i'm guessing the users computer doesnt work)
What you could do is copy everything from documents and settings.. Also, when they turn in the computer ask if they moved there my documents somewhere else (they probably wouldn't know what you were talking about)

Another alternative is copy everything other than windows and program files (unless you copy those anyways). This is probably the safest option. 

I'm not sure what your current strategy is, but if you have a current strategy, let me know and i may be able to help you write the script.. It shouldn't be too tough. You may have to prompt for some info so that you can do customizations.
Also, you can type bash scripting in google and you'll get all kinds of good tutorials and references.

Nice script

---

### Post by davkasayres on 2007-09-14
Thanks for the script, im going to try and change it when i get time.

The way im currently doing it is like so:


Got a PCI expansion card in PCI slot 1, and a SATA expansion card in PCI2 (this board doesnt have sata).

Connect the customers hard drive to the machine and boot up ubuntu.

Go in to C:\Documents and Settings\

I Copy the (Username) folder to /home/data/Customer Backup/

Then, take the customers hard drive out and replace it into their own machine and install windows.

Then i replace the customers hard drive back into the ubuntu machine and copy the (Username) folder normally to their desktop. Hotplugging would be nice because then i wouldnt have to keep turning the machine off.

Well, thats the way ive been doing it. Im open to suggestions if anyone has a better idea how to speed things up.


Thanks for all your support,

Dan.

Frustrated I.T Technician      ](*,)

Edit:

Sorry, should have mentioned we havent had a vista machine in yet (Thank God!), so all this applys to XP only.

---

### Post by trippinnik on 2007-09-14
How about a Samba share?  That's basically what we did at my last job (it was all windows) but we backed up the personal data over the network, wiped the drive, imaged it and then copied the personal data back over the network.  The computer you're working on does need to be in some working order (but you could use a live cd too) and in most cases will save you a lot of swapping.  The only cases we had to take out the drive was when there were serious errors on the disk and we were doing recovery.  Any case where the machine won't boot windows is solved by the LiveCD.

---

