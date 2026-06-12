---
title: "HAL - disable auto mount"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by thece on 2006-11-08
How I can disable auto mount for removable media, like USB sticks or CD/DVDs, and the related creation of the icon on the desktop?

I have tried with the tools in KControl but ... nothing!

Ciao

---

### Post by thece on 2006-11-09
How I can disable HAL from upstart?

Please, can someone help me?

Thanks

---

### Post by iskate on 2006-11-10
Actually I am here to learn how to enable auto mounting:KS

---

### Post by thece on 2006-11-10
Why? In Kubuntu every media it's auto mounted from HAL/KDE by default. In Ubuntu it's not the same one (HAL/Gnome)?

Ciao

---

### Post by TDsai on 2007-04-20
my question is similar to the 1st post. However, mine was about mounted swap partitions. My Feisty is automatically mounting both swap (linux, windows) partions and showing it on my desktop.

media/sda4 ntsf swap
media/sda5 linux swap

During the installation process I didn't delete them because i am afraid the partition might be deleted. How can i remove them to automatically mount during startup? 

thanks for anyhelp

---

### Post by TDsai on 2007-04-21
nevermind it was just easy than i thought. i just have to comment those partitions on my etc/fstab

---

### Post by s7ewie on 2007-07-08
Congrats TDsai, but the initial question *still stands*.
Is it possible to select which device is automounted by hal daemon and if so how could you do it? If not, it would be helpful to know at least how to stop automounting all together.

Thanks

---

### Post by hob4bit on 2007-11-09
This will stop HAL starting altogether. I use "autofs" instead:

sudo chmod ugo-rwx /usr/sbin/hald /usr/lib/libhal-storage.so.1

Here are some reasons why "autofs" is better than "hal". Autofs is
the standard UNIX way.
 
   HAL is an extremely annoying program. It can cause non-stop mount/umount
   of floppy disks, something even when no disk exists. When the CD-ROM tray
   is ejected it can sometimes immediately reload and not let you put a CD.
   Also for USB pens it can keep mounting making it unsafe to remove them.
   This is because HAL constantly tries to detect and mount removeable media.

   You are strongly encouraged to disable HAL and use "autofs" instead.
   With "autofs" devices are mounted when they are used and unmounted when
   finished. So you don't need to eject USB memory sticks. Also you don't
   waste CPU cycles trying to detect non-existent devices.

---

### Post by hob4bit on 2007-11-10
HAL is a truly annoying piece of software. Disabling HAL also disables power mangement in Gutsy. This causes <quit> in Gnome to hang for a few minutes. While this bug has a workaround and that is to install the feisty "gnome-power-manager":

wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.18.2-0ubuntu3_amd64.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/gnome-power-manager_2.18.2-0ubuntu3_amd64.deb)
wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck18_2.18.0-0ubuntu1_amd64.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck18_2.18.0-0ubuntu1_amd64.deb)
wget [http://uk.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.18.0-0ubuntu1_all.deb](http://uk.archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.18.0-0ubuntu1_all.deb)
dpkg -i gnome-power-manager_* libwnck18_* libwnck-common_*

I have had CDROMs that eject and immediately close offering just one second to put a
CDROM. That is totally unacceptable. So I had disabled HAL. However, HAL is required for power management and lots of other things.

I have been playing around with the HAL "fdi" trying to stop it dealing with removeable storage. I found a way and that is to remove permissions on the "libhal-storgae.so.1" file instead of the "hald" file. This stops HAL dealing for storage devices altogether.

chmod ugo-rwx /usr/lib/libhal-storage.so.1

While power-management is not disabled. The Gnome "quit" works with suspend option llisted. I think HAL needs to have a master switch to disable storage devcies in one go.

Here are some notes on how I setup "autofs" to deal with CDROMs, ZIPs, USB pens/cameras. I just "cd /media/cdrom" and it mounts and if I cd out it umounts.

   a) Disable HAL daemon (You MUST reboot to get rid of HAL properly):
      chmod ugo-rwx /usr/lib/libhal-storage.so.1
   b) Install Autofs automounter (super_dvd/linux64apps/gutsy-amd64):
      dpkg -i autofs_*
   c) Edit "/etc/fstab":
#Device    Mount Point      Type   Attributes
proc       /proc            proc   defaults 0 0
/dev/hda1  /c              ntfs-3g umask=022,fmask=133 0 0
/dev/hda2  /e              ntfs-3g umask=022,fmask=133 0 0
/dev/hda3  /f               auto   shortname=mixed,umask=022 0 0
/dev/hda7  /                ext3   defaults,errors=remount-ro,noatime 0 1
/dev/hda9  none             swap   default 0 0
/dev/hda10 /data            ext3   defaults,errors=remount-ro,noatime 0 2
   d) Edit "/etc/auto.disk" for automating disk partitions:
#!/bin/sh
MOUNT="$1"
PID=`ps -o "user ppid args" -e | grep "^root .*X " | head -1 | awk '{print $2}'`
OWNER=`pstree -u $PID | grep "(.*)" | head -1 | sed -e "s/).*//" -e "s/.*(//"`
if [ "$OWNER" ]; then
  GROUP=`id -g -n $OWNER`
else
  OWNER=root; GROUP=root
fi
case $MOUNT in
hda5)
  OPTIONS="uid=$OWNER,gid=$GROUP"; DEVICE="/dev/hda5"
  echo "-fstype=ntfs-3g,user,$OPTIONS,$GROUP,umask=022,fmask=133 :$DEVICE";;
esac
   e) Edit "/etc/auto.floppy" for automounting floppy disk:
#!/bin/sh
MOUNT="$1"
PID=`ps -o "user ppid args" -e | grep "^root .*X " | head -1 | awk '{print $2}'`
OWNER=`pstree -u $PID | grep "(.*)" | head -1 | sed -e "s/).*//" -e "s/.*(//"`
if [ "$OWNER" ]; then
  GROUP=`id -g -n $OWNER`
else
  OWNER=root; GROUP=root
fi
case $MOUNT in
floppy)
  OPTIONS="uid=$OWNER,gid=$GROUP"; DEVICE="/dev/fd0"
  echo "-fstype=auto,user,$OPTIONS,umask=022,fmask=133 :$DEVICE";;
esac
   f) Edit "/etc/auto.media" for automating removeable media (CD-ROM, USB etc)
#!/bin/sh
_POSIX2_VERSION=199209; export _POSIX2_VERSION
scanbus() {
  for DEVICE in `ls /proc/ide 2> /dev/null`; do
    if [ "`grep ide-cdrom /proc/ide/$DEVICE/driver 2> /dev/null`" ]; then
      MODEL=`sed -e "s/CDRW/CD-RW/" -e "s@ RW/D@ CD-RW/D@" \
        /proc/ide/$DEVICE/model`
      echo /dev/$DEVICE | awk '{printf(" IDE CD:             %-12s ",$1)}'
      echo "($MODEL)"
    elif [ "`grep ide-disk /proc/ide/$DEVICE/driver 2> /dev/null`" ]; then
      MODEL=`cat /proc/ide/$DEVICE/model`
      case $MODEL in
      *ZIP*) DEVICE="${DEVICE}4";;
      esac
      echo /dev/$DEVICE | awk '{printf(" IDE Disk:           %-12s ",$1)}'
      echo "($MODEL)"
    fi
  done
  SCSI=`tail +2 /proc/scsi/scsi 2> /dev/null | paste - - - | grep "CD-ROM" |
    sed -e "s/^Host: scsi//" -e "s/Vendor://" -e "s/Model://" -e "s/Rev:.*//" \
    -e "s/CDRW/CD-RW/" -e "s@ RW/D@ CD-RW/D@" |\
    awk '{printf(" %d,%d,%d,%d (%s %s %s %s %s\n"\
    ,$1,$3,$5,$7,$8,$9,$10,$11,$12)}' | sed -e "s/ *$/)/"`
  for UNIT in `echo "$SCSI" | awk '{print $1}'`; do
    MODEL=`echo "$SCSI" | grep " $UNIT " | cut -f3- -d" "`
    DEVICE=`ls -ld /sys/block/sr*/device 2> /dev/null | \
      grep "/\`echo $UNIT | sed -e \"s/,/:/g\"\`$" | cut -f4 -d/`
    if [ ! "$DEVICE" ]; then
      DEVICE=sr`expr \`echo "$SCSI" | grep -n $UNIT | cut -f1 -d:\` - 1`
    fi
    if [ -b /dev/`echo $DEVICE | sed -e "s/sr/scd/"` ]; then
      DEVICE=`echo $DEVICE | sed -e "s/sr/scd/"`
    fi
    if [ -f /proc/scsi/usb-storage*/`echo $UNIT | cut -f1 -d","` ]; then
      MODEL="$MODEL [USB]"
    elif [ -f  /proc/scsi/ide-scsi*/`echo $UNIT | cut -f1 -d","` ]; then
      MODEL="$MODEL [IDE]"
    fi
    echo $UNIT: /dev/$DEVICE | awk '{printf(" SCSI CD %-11s %-12s ",$1,$2)}'
    echo "$MODEL"
  done
  SCSI=`tail +2 /proc/scsi/scsi 2> /dev/null | paste - - - | \
    grep "Direct-Access" | sed -e "s/^Host: scsi//" -e "s/Vendor://" -e \
      "s/Model://" -e "s/Rev:.*//" | awk '{printf\
      (" %d,%d,%d,%d (%s %s %s %s %s \n",$1,$3,$5,$7,$8,$9,$10,$11,$12)}'\
      | sed -e "s/ *$/)/"`
  for UNIT in `echo "$SCSI" | awk '{print $1}'`; do
    MODEL=`echo "$SCSI" | grep " $UNIT " | cut -f3- -d" "`
    DEVICE=`ls -ld /sys/block/sd*/device 2> /dev/null | \
      grep "/\`echo $UNIT | sed -e \"s/,/:/g\"\`$" | cut -f4 -d/`
    if [ ! "$DEVICE" ]; then
      DEVICE=sd`echo -e "\14\`echo "$SCSI" | grep -n $UNIT | cut -f1 -d:\`"`
    fi
    if [ -f /proc/scsi/usb-storage*/`echo $UNIT | cut -f1 -d","` ]; then
      if [ "`grep \"Attached: No\" /proc/scsi/usb-storage*/\`echo $UNIT | \
          cut -f1 -d\",\"\``" ]; then
        continue
      fi
      MODEL="$MODEL [USB]"
    fi
    case $MODEL in
    *ZIP*) DEVICE="${DEVICE}4";;
    *USB*) DEVICE="${DEVICE}1";;
    esac
    echo $UNIT: /dev/$DEVICE | awk '{printf(" SCSI Disk %-9s %-12s ",$1,$2)}'
    echo "$MODEL"
  done
}
device() {
  UNIT=`echo "$MOUNT" | sed -e "s/[^0-9]*//" -e "s/^$/1/"`
  scanbus | grep "$1" | tail +$UNIT | head -1 | cut -f2 -d":" | awk '{print $1}'
}
MOUNT="$1"
PID=`ps -o "user ppid args" -e | grep "^root .*X " | head -1 | awk '{print $2}'`
OWNER=`pstree -u $PID | grep "(.*)" | head -1 | sed -e "s/).*//" -e "s/.*(//"`
if [ "$OWNER" ]; then
  GROUP=`id -g -n $OWNER`
else
  OWNER=root; GROUP=root
fi
case $MOUNT in
cdrom*)OPTIONS="ro,speed=16"; DEVICE=`device " CD.*:"`;;
usb*)  OPTIONS="uid=$OWNER,gid=$GROUP"; DEVICE=`device " Disk.*[a-z]1 .*USB"`;;
zip*)  OPTIONS="uid=$OWNER,gid=$GROUP"; DEVICE=`device " Disk.*:.*ZIP"`;;
esac
case `whoami`@$DEVICE in
root@/dev/*)
  grep -v "/$MOUNT " /etc/fstab > /etc/.fstab-$$
  echo "$DEVICE /mnt/media/$MOUNT auto" | \
    awk '{printf("%-10s %-16s %-6s users,noauto,umask=022,fmask=133,ro 0 0\n",\
    $1,$2,$3)}' >> /etc/.fstab-$$; mv /etc/.fstab-$$ /etc/fstab;;
esac
case $MOUNT in
cdrom*) echo "-fstype=auto,user,$OPTIONS :$DEVICE";;
*)      echo "-fstype=auto,user,$OPTIONS,umask=022,fmask=133 :$DEVICE";;
esac
   g) Create top level links to mount points:
      chmod ugo+x /etc/auto.disk /etc/auto.floppy /etc/auto.media
      umount /mnt/* /media/* 2> /dev/null
      rmdir /media/* /mnt/* 2> /dev/null
      rm -f /c /d /e /f /cdrom /media/* 2> /dev/null
      mkdir /c /e /f /data 2> /dev/null
      ln -s /mnt/disk/hda5     /d
      ln -s /mnt/floppy/floppy /media/floppy
      ln -s /mnt/media/cdrom   /media/cdrom
      ln -s /mnt/media/cdrom2  /media/cdrom2
      ln -s /mnt/media/cdrom3  /media/cdrom3
      ln -s /mnt/media/usb     /media/usb
      ln -s /mnt/media/usb2    /media/usb2
      ln -s /mnt/media/usb3    /media/usb3
      ln -s /mnt/media/usb4    /media/usb4
      ln -s /mnt/media/usb5    /media/usb5
      ln -s /mnt/media/usb6    /media/usb6
      ln -s /mnt/media/zip     /media/zip
      ln -s /mnt/media/zip2    /media/zip2
   h) Edit "/etc/auto.master":
      /mnt/disk   /etc/auto.disk   --timeout=60
      /mnt/floppy /etc/auto.floppy --timeout=1
      /mnt/media  /etc/auto.media  --timeout=2
   i) Start autofs daemon:
      /etc/init.d/autofs start
   j) Fix eject of zippy:
      chmod ug+s /usr/bin/eject; ls -l /usr/bin/eject
   k) Add "/sbin/eject" wrapper to "/usr/bin/eject" for "autofs" automounting:
      (cd /usr/bin; mv eject /sbin; touch eject; chmod ugo+x eject)
#!/bin/sh
if [ "$1" -a -x "/etc/auto.media" ]; then
  DEVICE=`/etc/auto.media \`basename $1\` | sed -e "s/.*://"`
  if [ "$DEVICE" ]; then
    case $DEVICE in
    sd*) /sbin/eject `echo $DEVICE | sed -e "s/[0-9]*$//"`;;
    *)   /sbin/eject $DEVICE; exit $?;;
    esac
  fi
fi; /sbin/eject $1
   k) Edit "/etc/rc.local" and add (fix missing SCSI devices):
MINOR=0; # Fix missing SCSI disk devices
for DEVICE in a b c d e f g h; do
  for PART in "" `/usr/bin/seq 1 15`; do
    (mknod /dev/sd$DEVICE$PART b 8 $MINOR) 2> /dev/null; MINOR=`expr $MINOR + 1`
  done
done
for DEVICE in `/usr/bin/seq 0 16`; do # Fix missing SCSI cdrom devices
  (mknod /dev/scd$DEVICE b 11 $DEVICE) 2> /dev/null
done

===== END ====

---

### Post by macogw on 2008-02-07
> **hob4bit said:**
> HAL is a truly annoying piece of software. Disabling HAL also disables power mangement in Gutsy. 

Really???  Maybe *that's* why I have no ACPI!

---

### Post by hack6500 on 2008-02-10
> **hob4bit said:**
> HAL is a truly annoying ... 

i have been haunted by the HAL daemon this very night for the first time! it was way scary, cd/rom drives appeared and USB drives disappeared! it made me tremble in my britches!

your directions look excellent, but no workie in kubuntu 7.10 64, there must be a way to excommunicate this daemon... for now it has returned to hiding, usb drive mounting is still flakey.

hack6500

---

### Post by salutis on 2008-07-10
> **hob4bit said:**
> This will stop HAL starting altogether. I use "autofs" instead:

sudo chmod ugo-rwx /usr/sbin/hald /usr/lib/libhal-storage.so.1



Thanks for tip!

---

