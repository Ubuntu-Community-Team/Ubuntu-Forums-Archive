---
title: "Unmounting a drive"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by NemoPaice on 2005-10-12
I installed Ubutu on one of my pc's.... I love it. 
MY primary pc  has Two Hard-Drives on it. I have 60GB with WindowsXP, and a 10GB secondary HD that I used to put Ubutu on to test it out and see if I liked it. Well I love it. 

While In Ubutu, I mounted my XP HD using what I guess is a bash script, anyway it worked but when I rebooted now it cannot detect it. It basically says its mounted wrong.

What I need is to un-mount it and remount it so I can save all my important files _( i cant even boot into Windows to do this, BTW)_ Then once all saved, I am going to install Ubutu on My 60GB HD and reformat the smaller HD to use as extra storage. 

PLEASE HELP.

---

### Post by aysiu on 2005-10-12
You used a bash script to mount Windows?
That's odd.
Follow these directions instead: [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by NemoPaice on 2005-10-12
Well I'm new at theis. I think thats what it was..... Here is the whole script. Maybe someone will know if I just hace to change something in it to unmount? I just dont know?


f [[ $UID != 0 ]]; then
    echo 'You should run this program as root or using sudo'
    exit 1
fi

# Get label for disk, consisting of size and name (fs labels proves too hard)
getlabel() {
    MAJ=`file /dev/$drive | sed -e 's/.*(\(.\).*/\1/'`
    MIN=`file /dev/$drive | sed -e 's/.*(..\(.\).*/\1/'`
    UDI="/org/freedesktop/Hal/devices/block_${MAJ}_${MIN}"
    SIZE=`hal-get-property --udi $UDI --key volume.size`
    GB=`python -c "print int(round($SIZE.0 / (1024**3)))"`
    label="$GB\\040GB\\040Disk\\040($drive)"
    label2="$GB GB Disk ($drive)"
}

# Simple command line argument for installers
# -w: mount them with user,umask=0111
# -r: mount them with user,umask=0133,uid=1000,gid=1000
RWALL=-1;
if [[ $1 == '-w' ]]; then RWALL=1; fi
if [[ $1 == '-r' ]]; then RWALL=0; fi

if [[ $RWALL == -1 ]]; then
    echo 'By default the disks will be writable only by root and'
    cat /etc/passwd | awk -F ':|,' '/:1000:/ {print $5 " (" $1 ")"}'
    echo 'Do you want to make the disk writable by all users instead? (y/n)'
    read RESP
    if [[ $RESP == 'y' || $RESP == 'Y' ]]; then
        RWALL=1
    else
        RWALL=0
    fi
fi

if [[ $RWALL == 1 ]]; then
    OPTIONS='user,fmask=0111,dmask=0000'
    MACOPTIONS='user,file_umask=0111,dir_umask=0000'
else
    OPTIONS='user,fmask=0133,dmask=0022,uid=1000,gid=1000'
    MACOPTIONS='user,file_umask=0133,dir_umask=0022,uid=1000,gid=1000'
fi

# Now for the real work
drivesntfs=`fdisk -l | grep -i 'ntfs' | awk -F '/| ' '{print $3}'`
drivesfat=`fdisk -l | grep -i 'fat32' | awk -F '/| ' '{print $3}'`
driveshfs=`fdisk -l | grep -i 'Apple_HFS' | awk -F '/| ' '{print $3}'`

donesomething='n'
for drive in $drivesntfs
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label ntfs ro,$OPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done
if [[ $donesomething == 'y' ]]
then
    echo "NTFS drives will be mounted read-only!"
fi
for drive in $drivesfat
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        ln -s "/media/$label2" /media/$drive # yay, spaceless link for b0rken programs
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label vfat rw,$OPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done
for drive in $driveshfs
do
    getlabel $drive
    if [[ ! `grep $drive /etc/fstab` ]]
    then
        mkdir "/media/$label2"
        echo "#Added by winmac_fstab utility" >> /etc/fstab
        echo "/dev/$drive /media/$label hfsplus rw,$MACOPTIONS 0 0" >> /etc/fstab
        echo "Added /dev/$drive as '/media/$label2'"
        donesomething='y'
    else
        echo "Ignoring /dev/$drive - already in /etc/fstab"
    fi
done

if [[ $donesomething == 'y' ]]
then
    # And mount them
    mount -a
    echo "All windows and mac partitions will now be mounted every time you boot"
    echo "You do not need to reboot, the partitions are mounted now too"
else
    echo "No usable windows/mac partitions found"
fi

---

### Post by NemoPaice on 2005-10-12
I just noticed the link you posted..... thanks I am trying it now

---

### Post by NemoPaice on 2005-10-12
this is the error message I just got. It's the same as the error messege at boot up too.

wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by aysiu on 2005-10-12
Can you post the output of these two commands? ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by wylfing on 2005-10-12
Yikes! Where in the world did you get that script? That's awful.

Anyway, what it's doing is editing the file /etc/fstab for you by trying to detect all the Windows disks on your system. Since you've already run this beast, it might be possible to remedy the situation if you post the contents of /etc/fstab for us to inspect.

Edit: Erk, wasn't fast enough. aysiu already asked :)

---

### Post by aysiu on 2005-10-12
[QUOTE=wylfing]Yikes! Where in the world did you get that script? That's awful.[/quote] I feel the same way. It's far easier to edit the /etc/fstab manually. I don't know where that script came from.

> 
Edit: Erk, wasn't fast enough. aysiu already asked :) It happens. The Ubuntu forums are a jumping place--hurry up and give help before someon else does!

---

