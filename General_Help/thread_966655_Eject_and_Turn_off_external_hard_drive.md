---
title: "Eject and Turn off external hard drive"
date: 2008-11-01
forum: General Help
---

### Post by FLCL on 2008-11-01
Well i've been having a problem with my external hard drive, that while i can unmount it, i cannot eject it and have it turn off without physically pulling the plug on it. So i've looked around, and came across a script here on the forums, but am having a bit of trouble. 
> 1. Create a file named eject.sh with the following contents:

#!/bin/bash
exec 2>&1
pumount $1 || umount $1
sdparm --command=sync $1
sdparm --command=stop $1

2. copy it into root folder

cd Desktop
sudo cp ~/Desktop/eject.sh /eject.sh

3. Create a launcher, which you can either dump on you desktop or have as an option in your main menu. When clicked, your drive will eject and turn off:

Option: run in terminal
command: sudo /./eject.sh /dev/sd* (mountpoint of your drive) 

I've changed the location for the script to /home/username/scripts instead of "/". But when i try to execute the script in terminal, this is what it returns:
> Eject.sh: 3: pumount: not found
Usage: umount [-hV]
       umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-f] [-r] [-n] [-v] special | node...
Eject.sh: 4: sdparm: not found
Eject.sh: 5: sdparm: not found

I have the command set to: sudo /./eject.sh /dev/sd* /media/drivename
Thats the correct format right?
Can anyone please help get this script to work? I would really be grateful.

---

### Post by geirha on 2008-11-01
That doesn't make sense. Running the script with **./eject.sh /dev/sd*** will give it all drives and partitions, but the script clearly only uses one argument. 

I'm unfamiliar with sdparm, but assuming those command are supposed to run on the drive (and not each partition), then I'd try changing the script to

```

#!/bin/sh
# Script should only be run with one argument, so exit if it isn't.
if [ $# -ne 1 ]; then   
   echo "Usage: $0 device"
   exit 1
fi

# unmount all partitions on the drive
for partition in ${1}?; do
  umount "$partition"
done

sdparm --command=sync $1
sdparm --command=stop $1

```

Then, if your  external drive is /dev/sdb for example, run ```
sudo ./eject.sh /dev/sdb
```

---

### Post by FLCL on 2008-11-01
Now this ones will eject and turn off the external hard drive correct?

---

