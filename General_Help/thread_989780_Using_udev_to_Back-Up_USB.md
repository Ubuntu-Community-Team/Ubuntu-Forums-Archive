---
title: "Using udev to Back-Up USB"
date: 2008-11-22
forum: General Help
---

### Post by Masterofpsi on 2008-11-22
I've been doing a lot on a portable USB flash drive recently. Because this is important work and because horrible things can easily happen to small, easily missed pieces of hardware, I wrote a script to back it up:

```

#!/bin/bash

#A script to sync my computer with my USB drives, backing up files when the
#drive is plugged in. Takes the name of the drive as the command line
#argument.

#Do not consider spaces to be field separators.
IFS=$'\n'

#If the drive is not designed to sync (has no "sync" directory), the program quits.
if [ ! -d /media/$1/"$USERNAME"_sync ]
then
    exit 0
fi

#Create a corresponding sync folder on the main drive if necessary.
mkdir -p /home/sync/$1

#Recursively delete all files on the main drive not on the external drive.
cd; cd sync; cd $1
testFile=/media/$1/"$USERNAME"_sync
function clean_up_wd
{
    for f in `ls`
    do
        testFile=$testFile/$f
        if [ ! -e $testFile ]
        then
            rm -r ./$f
        elif [ -d $f ]
        then
            cd $f
            clean_up_wd
        fi
        testFile=`dirname $testFile`
    done
}
clean_up_wd

#Copy over all files on the external drive.
rsync -r /media/$1/"$USERNAME"_sync/ /home/$USERNAME/sync/$1

```

Invoking this script from the command line makes it do exactly what I want it to. (Knowing that, of course, I could just title it autorun.sh and put it on my flash drive, but I want to hammer this out.)

My current device is named "CHARON." Running

```

$ udevinfo -a -p $(udevinfo -q path -n /dev/disk/by-label/CHARON)

```

yields

```

  looking at device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4/target4:0:0/4:0:0:0/block/sdb/sdb1':
    KERNEL=="sdb1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{start}=="8064"
    ATTR{size}=="3913856"
    ATTR{stat}=="     182     1017     3832      504        4        5        9       28        0      448      532"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4/target4:0:0/4:0:0:0/block/sdb':
    KERNELS=="sdb"
    SUBSYSTEMS=="block"
    DRIVERS==""
    ATTRS{range}=="16"
    ATTRS{removable}=="1"
    ATTRS{ro}=="0"
    ATTRS{size}=="3921920"
    ATTRS{capability}=="13"
    ATTRS{stat}=="     194     1079     4424      584        4        5        9       28        0      512      612"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4/target4:0:0/4:0:0:0/block':
    KERNELS=="block"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4/target4:0:0/4:0:0:0':
    KERNELS=="4:0:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="0"
    ATTRS{vendor}=="        "
    ATTRS{model}=="USB Flash Memory"
    ATTRS{rev}=="PMAP"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x2175"
    ATTRS{iodone_cnt}=="0x2175"
    ATTRS{ioerr_cnt}=="0x2"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"
    ATTRS{max_sectors}=="240"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4/target4:0:0':
    KERNELS=="target4:0:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/host4':
    KERNELS=="host4"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0':
    KERNELS=="3-3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb-storage"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="08"
    ATTRS{bInterfaceSubClass}=="06"
    ATTRS{bInterfaceProtocol}=="50"
    ATTRS{modalias}=="usb:v0930p6545d0110dc00dsc00dp00ic08isc06ip50"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3/3-3':
    KERNELS=="3-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="200mA"
    ATTRS{urbnum}=="17657"
    ATTRS{idVendor}=="0930"
    ATTRS{idProduct}=="6545"
    ATTRS{bcdDevice}=="0110"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="        "
    ATTRS{product}=="USB Flash Memory"
    ATTRS{serial}=="5B8614000401"

  looking at parent device '/devices/pci0000:00/0000:00:13.2/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="63"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="8"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-7-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:13.2"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:13.2':
    KERNELS=="0000:00:13.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x1002"
    ATTRS{device}=="0x4373"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xff00"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00001002d00004373sv00001179sd0000FF00bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

I wrote the following udev rule and put it in 80-programs.rules:

```

ACTION=="add", KERNEL=="sdb*", SUBSYSTEM=="block", SUBSYSTEMS=="usb", DRIVERS=="usb-storage", RUN+="/usr/local/bin/sync.sh $env{ID_FS_LABEL}"

```

It's general because I anticipate using more and different devices at later times. [This site]("http://bbs.archlinux.org/viewtopic.php?pid=446719") suggests that $env{ID_FS_LABEL} is the device's label (in this case, "CHARON"), which is what I intend the command line argument to be.

However, with all this, it still doesn't run when I plug my device in. Does anyone know the problem?

---

### Post by joe.six.pack on 2008-11-24
your udev rule is wrong.  you can only select attributes from ONE parent device.

```

ACTION=="add", KERNEL=="sdb*", SUBSYSTEM=="block", SUBSYSTEMS=="usb", DRIVERS=="usb-storage", RUN+="/usr/local/bin/sync.sh $env{ID_FS_LABEL}"

```

becomes

```

ACTION=="add", SUBSYSTEMS=="usb", DRIVERS=="usb-storage", RUN+="/usr/local/bin/sync.sh $env{ID_FS_LABEL}"

```


if you wanted that specific usb drive

```

ACTION=="add", SUBSYSTEMS=="usb", DRIVERS=="usb", ATTRS{idVendor}=="0930", ATTRS{idProduct}=="6545",
ATTRS{product}=="USB Flash Memory", ATTRS{serial}=="5B8614000401", RUN+="/usr/local/bin/sync.sh $env{ID_FS_LABEL}"

```

---

### Post by allspiritseve on 2009-02-02
I'm trying to do this same thing, but for some reason the script is run three times:

```
ACTION=="add", SUBSYSTEM=="block", SUBSYSTEMS=="usb", ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5406", SYMLINK+="cruzer", RUN+="/home/spirit/backup2.sh"
```

Any ideas?

---

### Post by fragos on 2009-02-02
Why not use unison? It performs flawlessy for me used on my LAN or with USB memory stick sneaker net.

---

### Post by drdub on 2009-03-05
> **allspiritseve said:**
> I'm trying to do this same thing, but for some reason the script is run three times

Once for the entire drive, and once for each partition I guess.

Try solving that using a two-step approach:

```
# name devices
ACTION="add", KERNEL=="sd*", SUBSYSTEM=="block", SUBSYSTEMS=="scsi", SUBSYSTEMS=="usb", ATTRS{serial}=="yourserialnumber", SYMLINK+="cruzer%n"

# run scripts
ACTION="add", KERNEL=="sd?1", SUBSYSTEM=="block", SUBSYSTEMS=="scsi", SUBSYSTEMS=="usb", ATTRS{serial}=="yourserialnumber", RUN+="/home/spirit/backup2.sh"
```

This will give you /dev/cruzer (the device itself), as well as /dev/cruser1 and /dev/cruser2 (if you have two partitions).

---

### Post by heindsight on 2009-03-05
> **Masterofpsi said:**
> 
```

#!/bin/bash

#A script to sync my computer with my USB drives, backing up files when the
#drive is plugged in. Takes the name of the drive as the command line
#argument.

#Do not consider spaces to be field separators.
IFS=$'\n'

#If the drive is not designed to sync (has no "sync" directory), the program quits.
if [ ! -d /media/$1/"$USERNAME"_sync ]
then
    exit 0
fi

#Create a corresponding sync folder on the main drive if necessary.
mkdir -p /home/sync/$1

#Recursively delete all files on the main drive not on the external drive.
cd; cd sync; cd $1
testFile=/media/$1/"$USERNAME"_sync
function clean_up_wd
{
    for f in `ls`
    do
        testFile=$testFile/$f
        if [ ! -e $testFile ]
        then
            rm -r ./$f
        elif [ -d $f ]
        then
            cd $f
            clean_up_wd
        fi
        testFile=`dirname $testFile`
    done
}
clean_up_wd

#Copy over all files on the external drive.
rsync -r /media/$1/"$USERNAME"_sync/ /home/$USERNAME/sync/$1

```


Just a couple of comments about your script.

Firstly:
```
#Do not consider spaces to be field separators.
IFS=$'\n'

```
You shouldn't need this if you just quote your variables properly.

Secondly, here you first create /home/sync/$1:
```
#Create a corresponding sync folder on the main drive if necessary.
mkdir -p /home/sync/$1

```
but then you do:
```

cd; cd sync; cd $1

```
which takes you to /home/$USERNAME/sync/$1, which is also what you use later in your rsync command:
```

rsync -r /media/$1/"$USERNAME"_sync/ /home/$USERNAME/sync/$1

```
I suspect that mkdir line should have been:
```
#Create a corresponding sync folder on the main drive if necessary.
mkdir -p /home/$USERNAME/sync/$1

```

Also, regarding your clean up script:
```
#Recursively delete all files on the main drive not on the external drive.
cd; cd sync; cd $1
testFile=/media/$1/"$USERNAME"_sync
function clean_up_wd
{
    for f in `ls`
    do
        testFile=$testFile/$f
        if [ ! -e $testFile ]
        then
            rm -r ./$f
        elif [ -d $f ]
        then
            cd $f
            clean_up_wd
        fi
        testFile=`dirname $testFile`
    done
}
clean_up_wd
```
You'd be better off passing the two directories as arguments to the function, it makes for much cleaner code. Also, you don't need a recursive function, just use the find command, it's much simpler.

Perhaps something like the following. This is longer than it needs to be because I tried to make it as generally applicable as I could (always a good idea, makes the code more reusable) and I commented it quite a lot...
```

cleanup() {
  local NAME SOURCE TARGET
  SOURCE=${1:-.} # Set SOURCE to $1 or . if $1 is empty
  TARGET=${2:-.} # Set TARGET to $2 or . if $2 is empty
  if [ "$SOURCE" = "$TARGET" ]; then
    # Nothing to do if $SOURCE and $TARGET are the same
    return 0;
  fi
  find "$TARGET" -ignore_readdir_race -printf "%P\n" | while read NAME; do
    # Check whether each file/directory in $TARGET exists in $SOURCE
    # Delete file from $TARGET if it's not in $SOURCE
    # otherwise continue to next file
    if [ -e "$SOURCE/$NAME" ]; then
      continue
    fi
    rm -rf "$TARGET/$NAME"
  done
}

# Call the cleanup function to delete files from /home/$USERNAME/sync/$1
# that don't exist in /media/$1/"$USERNAME"_sync/
cleanup "/media/$1/${USERNAME}_sync/" "/home/${USERNAME}/sync/$1"

```
Have a look at the manual for find for details on how that works and what the options do:
```
man find
```

Having said all that, you don't need a function to delete files from the "target" directory if they don't exist in the "source" directory. rsync has that ability built in via the --delete option.
Again see the manual:
```
man rsync
```

Finally, I tend to think it's better to use sh than bash for scripts like this, which means that some syntax is slightly different, and some environment variables you take for granted might not exist.

So your script could be reduced to the following:

```

#!/bin/sh

#A script to sync my computer with my USB drives, backing up files when the
#drive is plugged in. Takes the name of the drive as the command line
#argument.

# Get username
# USERNAME probably isn't necessarily defined already...
USERNAME=$(id -nu) 

#If the drive is not designed to sync (has no "sync" directory), the program quits.
if [ ! -d "/media/$1/${USERNAME}_sync" ]
then
    exit 0
fi

# Create a corresponding sync folder on the main drive if necessary.
# Actually you don't even need this because rsync will create the
# target directory if it doesn't exist...
#if [ ! -d "/home/$USERNAME/sync/$1" ]; then
#  mkdir -p "/home/$USERNAME/sync/$1"
#fi

#Copy over all files on the external drive.
rsync -r --delete "/media/$1/${USERNAME}_sync/" "/home/$USERNAME/sync/$1"

```

---

### Post by bonjour on 2009-05-15
I'm trying to do the same thing, but unfortunately it has stopped working since an upgrade to Jaunty.

My udev:

```
KERNEL=="sd*", SUBSYSTEMS=="usb", SUBSYSTEMS=="scsi", ACTION=="add", RUN+="/usr/local/bin/usb-backup %k"
```My Script (simplified, as I actually run it for 45 different usb devices):

```
#!/bin/bash

# $1 is devicename from udev

# Config
VOLUME_ID="3087-14DA"
VOLUME_SRC_DIR="/home/Backups/SDBackups/"

# Programs used
GOODBEEP="/usr/bin/beep -r 2 -d 100 -f 700 &"
BADBEEP="/usr/bin/beep -r 10 -d 100 -f 50 &"
FDISK="/sbin/fdisk"
AWK="/usr/bin/awk"
GREP="/bin/grep"
ECHO="/bin/echo"
LS="/bin/ls"
VOL_ID="/sbin/vol_id"
RSYNC="/usr/bin/rsync"
MOUNT="/bin/mount"
UMOUNT="/bin/umount"
EGREP="/bin/egrep"

${ECHO} $1 | ${EGREP} "^sd[a-z][0-9]" || {
        echo "- Usage: usb-backup <partition>"
        echo "- Example: usb-backup sdd1"
        exit
}

ii=`${VOL_ID} -u /dev/${1}`
if [ $ii == ${VOLUME_ID} ]
    then
    if [ ! -d /mnt/${1} ] 
    then
        mkdir -p /mnt/${1}
    fi
    ${MOUNT} /dev/${1} /mnt/${1}
    if [ ! -d /mnt/${1}/usb-backup ]
    then
        mkdir -p /mnt/${1}/usb-backup
    fi
    ${RSYNC} -rlt $SRC_DIR /mnt/${1}/usb-backup
    R_CODE=$?
    ${UMOUNT} -l /mnt/${1}
    if [ $R_CODE == "0" ]
    then
        ${GOODBEEP}
    else
        ${BADBEEP}
    fi
fi
```

---

### Post by unutbu on 2009-05-15
bonjour, try removing "SUBSYSTEMS=="scsi" from the udev rule:
```

KERNEL=="sd*", SUBSYSTEMS=="usb", ACTION=="add", RUN+="/usr/local/bin/usb-backup %k"
```

Also, you could do the following: Run
```

lsusb
```

Look for you USB backup drive in the output. You should see something like this:
```

Bus 004 Device 004: ID **0bc2:3001** Seagate RSS LLC 
```

Look for the id code. Above the id code is "0bc2:3001".
Given the id code, you can add this to the udev rule:
    ```

KERNEL=="sd*", SUBSYSTEMS=="usb", **ATTRS{idVendor}=="0bc2", ATTRS{idProduct}=="3001"**, ACTION=="add", RUN+="/usr/local/bin/usb-backup %k"
```

This way, the udev rule will not launch usb-backup unless your make/model of USB backup drive is connected.

---

### Post by CrusaderAD on 2009-05-15
If you're backing up a usb, why not just use Keep?

```
sudo apt-get install keep
```

You can backup your usb from the mnt directory. Great program.

---

### Post by tahoe on 2009-07-22
Here is my solution.  This is setup for one user, but the solution gets around a nuance I ran into.  The catch 22 was that the rule would fire off, but the backup script needs the file system to be mounted so that it could be backed up, but it would not mount till the backup script exited.  I tried to run the script with "nohup" and "&" with no success, so I wrapped the python code in a little shell script that fires the backup script off as an "at" job.  This all seems to be working.

The script is setup to copy data to a particular user account, so change USERNAME_HERE to your username.

/etc/udev/rules.d/80-program.rules                         
```

KERNEL=="sd?1", SUBSYSTEMS=="usb", ACTION=="add", DRIVERS=="usb-storage", RUN+="/home/USERNAME_HERE/bin/cp_usb_wrapper.sh %k"

```

/home/USERNAME_HERE/bin/cp_usb_wrapper.sh                     
```

#!/bin/bash
echo "/home/USERNAME_HERE/bin/cp_usb.py $@" | at now

```

/home/USERNAME_HERE/bin/cp_usb.py                     
```

#!/usr/bin/python

import sys, os, commands, time, datetime

backup_dir = "/home/USERNAME_HERE/.backup/"
# Do not backup the drive if it is over 16GB
backup_limit = 1024 * 1024 * 16

ofile = open("/tmp/cp_usb.log","a")

partition = sys.argv[1]

# Normally mounting the file system takes less than a second.
time.sleep(1)

dfResults = commands.getoutput("/bin/df -P | grep " + partition)

# If all goes well you should not enter this loop
while len(dfResults) == 0:
    time.sleep(1)
    print >>ofile, "Sleeping"
    ofile.flush()
    dfResults = commands.getoutput("/bin/df -P | grep " + partition)

mounted_on = dfResults.strip().split()[-1]

partition_full_path = dfResults.strip().split()[0]

used_size = int(dfResults.strip().split()[2])

if used_size < backup_limit:
    # vol_id need root permission
    # This is ok since the udev trigger runs as root.
    UUID = commands.getoutput("/sbin/vol_id -u " + partition_full_path)

    # blkid does not need root, but it does not show usb devices.
    # UUID = commands.getoutput("/sbin/blkid -ovalue -sUUID " + partition_full_path)

    backup_cmd = "/usr/bin/rsync -au " + mounted_on + "/ " + backup_dir + UUID

    os.system(backup_cmd)

    print >>ofile, datetime.datetime.now(), "|", backup_cmd

else:
    print >>ofile, datetime.datetime.now(), "| Used Size > ", backup_limit

```

/tmp/cp_usb.log                         
```

2009-07-22 11:23:09.519715 | /usr/bin/rsync -au /media/disk-1/ /home/USERNAME_HERE/.backup/C824-D5F9

```

Hope this helps.

---

