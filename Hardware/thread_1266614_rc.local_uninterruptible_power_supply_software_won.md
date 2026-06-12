---
title: "rc.local uninterruptible power supply software wont start at boot"
date: 2009-09-14
forum: Hardware
---

### Post by cebif on 2009-09-14
[SIZE="3"]I have a KI1000LCD UPS with monitoring software from richcomm.com.
Up to ubuntu 8.10 it would start automatically when I edited the /etc/rc.local file. In ubuntu 9.04 jaunty it doesn't work.
This is my rc.local file:
```
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
# BEGIN: Startup for UPS Manager
cd /etc/ups_manager
./ups_manager start &
# END: Startup for UPS Manager

exit 0
```
I can start the monitoring software with the command lines:
```
$ cd /etc/ups_manager
$ sudo ./ups_manager start
[sudo] password for greg:                                   
Starting UPS_Manager...:
                 
greg@greg-desktop:/etc/ups_manager$ =========================UPS Power Manager start...============================
================Initialize is OK!  start read the data from com================

```
What is different about ubuntu 9.04, that the software won't start? How can I make it start at boot?[/SIZE]

---

### Post by lswb on 2009-09-14
/etc/rc.local should work the same in 9.04 as in earlier versions. Have you by any chance chmod /etc/rc.local or perhaps used a program like update-rc.d or startup manager to modify any start-up services?

---

### Post by cebif on 2009-09-15
> **lswb said:**
> /etc/rc.local should work the same in 9.04 as in earlier versions. Have you by any chance chmod /etc/rc.local or perhaps used a program like update-rc.d or startup manager to modify any start-up services?
This is the permissions of rc.local:
[http://pics.livejournal.com/cebif/pic/00004pyk/](http://pics.livejournal.com/cebif/pic/00004pyk/)
The original installation of KI1000LCD monitoring software tried to change the rc.local file automatically but was looking in /etc/rc.d for it. rc.d doesn't exist in ubuntu, so I created the folder rc.d and a blank rc.local file in it. I then copied what it wrote in the created rc.local to the rc.local in /etc and deleted the created rc.d/rc.local. This worked up to ubuntu 8.10.
So the installation software is the only software that has altered rc.local in a roundabout way.
I have altered what services start in the control center and made some alterations in autostart but autostart only affects the window manager after login.
What services need to start for rc.local to work?

---

### Post by lswb on 2009-09-15
The screenshot you posted shows that the rc.local file does not have execute permissions.

Open a terminal and execute this command

sudo chmod +x /etc/rc.local

and it should start working.

---

### Post by cebif on 2009-09-15
> **lswb said:**
> The screenshot you posted shows that the rc.local file does not have execute permissions.

Open a terminal and execute this command

sudo chmod +x /etc/rc.local

and it should start working.

No it still wont start. I definitely confirmed that the command did change it to executable. 
Thanks for your help.

---

### Post by lswb on 2009-09-15
> **cebif said:**
> 
What services need to start for rc.local to work?

Assuming runlevel 2 is your default then in your /etc/rc2.d directory, there should be a symlink named S99rc.local that points to /etc/init.d/rc.local.

FYI, do not confuse /etc/init.d/rc.local with /etc/rc.local, they are 2 different files. /etc/init.d/rc.local is an an initscript that is part of the normal boot sequence and it should not be modified. It is one of the last initscripts to run and it *calls* /etc/rc.local.

---

### Post by cebif on 2009-09-16
> **lswb said:**
> Assuming runlevel 2 is your default then in your /etc/rc2.d directory, there should be a symlink named S99rc.local that points to /etc/init.d/rc.local.

FYI, do not confuse /etc/init.d/rc.local with /etc/rc.local, they are 2 different files. /etc/init.d/rc.local is an an initscript that is part of the normal boot sequence and it should not be modified. It is one of the last initscripts to run and it *calls* /etc/rc.local.
There is a file named /etc/rc2.d/S99rc.local and it is symlinked to /etc/init.d/rc.local
The S99rc.local has this in it:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
	        [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		ES=$?
		[ "$VERBOSE" != no ] && log_end_msg $ES
		return $ES
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
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```
The file /etc/init.d/rc.local has this:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
	        [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		ES=$?
		[ "$VERBOSE" != no ] && log_end_msg $ES
		return $ES
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
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```
Both these files are marked as executable.

---

### Post by lswb on 2009-09-16
I'm out of any more ideas at the moment. Does the ups software start up if you run /etc/rc.local from the command line, i.e.

sudo /etc/rc.local 

and how about if you manually run the initscript,

sudo /etc/init.d/rc.local


Just to confirm that /etc/rc.local is NOT running at boot, could you add this or a similar line (before the exit line) to /etc/rc.local

touch /Running-rc.local

then reboot and see if /Running-rc.local was created?

---

### Post by cebif on 2009-09-16
> **lswb said:**
> I'm out of any more ideas at the moment. Does the ups software start up if you run /etc/rc.local from the command line, i.e.

sudo /etc/rc.local
Yes it starts. 

> **lswb said:**
> and how about if you manually run the initscript,

sudo /etc/init.d/rc.local
That works aswell.

> **lswb said:**
> Just to confirm that /etc/rc.local is NOT running at boot, could you add this or a similar line (before the exit line) to /etc/rc.local

touch /Running-rc.local

then reboot and see if /Running-rc.local was created?
Yes it was created after a reboot.
I did a bit of redundant file uploading in the last post because both S99rc.local and /etc/init.d/rc.local are exactly the same content. I should have checked first.
I also compared all the involved files in ubuntu 9.04, with 8.10 on my other hd, and they are exactly the same.
The UPS software is still starting at boot in 8.10.

---

### Post by lswb on 2009-09-16
I still don't know why your rc.local is not running at boot, but just wanted to clear something up. /etc/rc2.d/S99rc.local and /etc/init.d/rc.local *both refer to same file*, they are not 2 different files with the same contents. The S99rc.local file is a symbolic link to /etc/init.d/rc.local. There are some README files in /usr/share/doc/sysv-rc that help explain how runlevels and the init scripts work if you are interested.

---

### Post by cebif on 2009-09-20
It is strange but after some days rc.local now seems to start the UPS monitoring software. It seems to have corrected itself without me doing anything more.

---

### Post by cebif on 2009-09-21
I found out what enables the rc.local to work and what stops it. If I stop the ubuntu graphic and progress bar during boot with alt + f1, the rc.local will start the uninterruptible power supply software but if the graphic boot is allowed it wont start. The only problem is I cannot find how to stop the graphical boot permanently. I looked in control center startup manager and cannot see anything to disable this. There is something in the men.lst file:
```
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=915a4563-e2ee-4842-999f-f4c55be09bf8 ro quiet splash
```
Do I have to edit the splash reference or remove it?

---

### Post by cebif on 2009-09-25
> **cebif said:**
> I found out what enables the rc.local to work and what stops it. If I stop the ubuntu graphic and progress bar during boot with alt + f1, the rc.local will start the uninterruptible power supply software but if the graphic boot is allowed it wont start. The only problem is I cannot find how to stop the graphical boot permanently. I looked in control center startup manager and cannot see anything to disable this. There is something in the men.lst file:
```
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=915a4563-e2ee-4842-999f-f4c55be09bf8 ro quiet splash
```
Do I have to edit the splash reference or remove it?

've found how to stop the graphical boot.
I edited menu.lst

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=915a4563-e2ee-4842-999f-f4c55be09bf8 ro [COLOR="Blue"]quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.28-15-generic
quiet
```

The colored text is deleted.
After a reboot I found the application was started by rc.local.

---

