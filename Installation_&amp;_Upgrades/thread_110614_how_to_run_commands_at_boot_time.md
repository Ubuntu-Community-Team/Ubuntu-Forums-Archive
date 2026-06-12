---
title: "how to run commands at boot time ?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by surfer63 on 2005-12-31
Hi all,

I searched the forums but I could not find an answer there.
I want to run commands at boot time. I recently switched from slackware to kubuntu.  In slackware there was the directory /etc/rc.d. which contained among many others also a rc.local file in which you could place your own commands.
I have been reading the debian guide on how to do this for debian.
I now have a z-commands file in /etc/init.d having my commands in there. In the rcS.d and all /etc/rcx.d sub directories I created a soft link S65z-commands to the z-commands file in /etc/init.d. The z-commands file is (off course) executable.
It looks like this:
======================
#! /bin/sh
#
# Author:   Harry van der wolf
# Version:   1.0  29-Dec-2005 

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="My own settings"
SCRIPTNAME="z-commands"

case "$1" in
  start)
   echo -n "Starting $DESC"
   # As the smb mounts doesn't get mounted (??) from fstab, I do it here
#   log_begin_msg "Mounting webshots"
   /bin/mount -t smbfs -o username=guest,password= //192.168.144.125/webshots /media/webshots
#   log_end_msg "Mounted webshots ??"
   echo "."
   ;;
  stop)
   echo -n "Stopping $DESC: $NAME"
   /bin/umount /media/webshots
   echo "."
   ;;
  *)
   # echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
   echo "Usage: $SCRIPTNAME {start|stop}" >&2
   exit 1
   ;;
esac

exit 0
=================

When running it by hand it works, why not from the boot scripts ?
What am I doing wrong ?

Harry

---

### Post by surfer63 on 2005-12-31
Solved !!

I changed the S65z-commands shortlink to S95z-commands and now it works. I thought that after level S40 networking was working (as does the policy guide tells), but samba was not running yet.

Bye

---

