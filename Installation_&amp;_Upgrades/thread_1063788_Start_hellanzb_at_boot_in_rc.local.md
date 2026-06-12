---
title: "Start hellanzb at boot in rc.local"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by itsmeok on 2009-02-08
Hi, I hope some of you can help me a bit on getting Hellanzb started at startup. I am running Kubuntu 7.10 with Linuxmce installed. I have seen some post on this topic but it did fix my problem. This is my rc.local:

 #!/bin/sh -e
 #
 # rc.local
 #
 # This script is executed at the end of each multiuser runlevel.
 # Make sure that the script will "exit 0" on success or any other
 # value on error.
 #
 # In order to enable or disable this script just change the execution
 # bits.
 #
 # By default this script does nothing.
 
 su -c 'hellanzb -D' - linuxmce

 exit 0

If I run the rc.local file from a command prompt it runs fine. 

What is the execution bit and how would i change that ?

---

### Post by lemming465 on 2009-02-09
Traditionally linux files have choices of read, write, and execute permissions for the file user owner, the file group owner, and the general public.  E.g. ```

$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 306 2008-10-29 16:05 /etc/rc.local

```
On this system (ubuntu 8.10) /etc/rc.local is owned by user root with permissions "rwx" (read+write+execute), group root with permissions read+execute; and everyone else also gets read+execute.  To add execute permissions to a file use "chmod", e.g. *sudo chmod +x ...*. 

However, lack of execute permissions may not be your issue.  Also check that /etc/init.d/rc.local exists and has execute permissions, and that /etc/rc2.d has a symbolic link (made by "ln -s") S99rc.local pointing at it.

---

### Post by lemming465 on 2009-02-09
Traditionally linux files have choices of read, write, and execute permissions for the file user owner, the file group owner, and the general public.  E.g. ```

$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 306 2008-10-29 16:05 /etc/rc.local

```
On this system (ubuntu 8.10) /etc/rc.local is owned by user root with permissions "rwx" (read+write+execute), group root with permissions read+execute; and everyone else also gets read+execute.  To add execute permissions to a file use "chmod", e.g. *sudo chmod +x ...*. 

However, lack of execute permissions may not be your issue.  Also check that /etc/init.d/rc.local exists and has execute permissions, and that /etc/rc2.d has a symbolic link (made by "ln -s") S99rc.local pointing at it.

---

### Post by itsmeok on 2009-02-14
Hope I understood you correctly:

My execution looks fine I guess:

 -rwxr-xr-x 1 root root 338 2009-02-08 15:26 /etc/rc.local
 
 -rwxr-xr-x 1 root root 522 2007-10-04 13:17 /etc/init.d/rc.local

I checked /etc/rc2.d/S99rc.local with vi and it looks like this:

 #! /bin/sh
 
 PATH=/sbin:/bin:/usr/sbin:/usr/bin
 [ -f /etc/default/rcS ] && . /etc/default/rcS
 . /lib/lsb/init-functions

 do_start() {
        if [ -x /etc/rc.local ]; then
                log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                log_end_msg $?
        fi
 }

 case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)

Anu more thoughts?

Maybe how could I check if it even get run at boot. Could I check that during boot or in a log file ?

---

### Post by lemming465 on 2009-02-14
See if /var/log/messages or /var/log/boot has the line about *Running local boot scripts*.  Other things that could help increase the noise level: take "quiet" out of the kernel arguments in /boot/grub/menu.lst, and add "set -x" to /etc/rc.local.

I'm wondering if this is a path issue.  If rc.local works when you run it, but not when /etc/init.d/rc runs it, where is linuxmce?  If it's not in one of /bin /sbin /usr/bin /usr/sbin try providing the absolute path to it.

---

