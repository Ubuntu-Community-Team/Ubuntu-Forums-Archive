---
title: "Starting rtorrent in a screen session at boot"
date: 2008-07-14
forum: General Help
---

### Post by ranger0293 on 2008-07-14
I'm trying to add an rtorrent script to /etc/init.d, but it's not able to start up an rtorrent instance.

Here is the script in /etc/init.d which I got from the rtorrent site:
```
#!/bin/bash
#############
###<Notes>###
#############
# This script depends on screen.
# For the stop function to work, you must set an
# explicit session directory using absolute paths (no, ~ is not absolute) in your rtorrent.rc.
# If you typically just start rtorrent with just "rtorrent" on the
# command line, all you need to change is the "user" option.
# Attach to the screen session as your user with 
# "screen -dr rtorrent". Change "rtorrent" with srnname option.
# Licensed under the GPLv2 by lostnihilist: lostnihilist _at_ gmail _dot_ com
##############
###</Notes>###
##############

#######################
##Start Configuration##
#######################
# You can specify your configuration in a different file 
# (so that it is saved with upgrades, saved in your home directory,
# or whatever reason you want to)
# by commenting out/deleting the configuration lines and placing them
# in a text file (say /home/user/.rtorrent.init.conf) exactly as you would
# have written them here (you can leave the comments if you desire
# and then uncommenting the following line correcting the path/filename 
# for the one you used. note the space after the ".".
# . /etc/rtorrent.init.conf


#Do not put a space on either side of the equal signs e.g.
# user = user 
# will not work
# system user to run as (can only use one)
user="jeff"

# system user to run as # not implemented, see d_start for beginning implementation
# group=$(id -ng "$user")

# the full path to the filename where you store your rtorrent configuration
# must keep parentheses around the entire statement, quotations around each config file
#config=("$(su -c 'echo $HOME' $user)/.rtorrent.rc")
# Examples:
config=("/home/jeff/.rtorrent.rc")
# config=("/home/user/.rtorrent.rc" "/mnt/some/drive/.rtorrent2.rc")
# config=("/home/user/.rtorrent.rc"
# "/mnt/some/drive/.rtorrent2.rc"
# "/mnt/another/drive/.rtorrent3.rc")

# set of options to run with each instance, separated by a new line
# must keep parentheses around the entire statement
#if no special options, specify with: ""
options=("")
# Examples:
# starts one instance, sourcing both .rtorrent.rc and .rtorrent2.rc
# options=("-o import=~/.rtorrent2.rc")
# starts two instances, ignoring .rtorrent.rc for both, and using
# .rtorrent2.rc for the first, and .rtorrent3.rc for the second
# we do not check for valid options
# options=("-n -o import=~/.rtorrent2.rc" "-n -o import=~/rtorrent3.rc")

# default directory for screen, needs to be an absolute path
base=$(su -c 'echo $HOME' $user)

# name of screen session
srnname="rtorrent"

# file to log to (makes for easier debugging if something goes wrong)
logfile="/var/log/rtorrentInit.log"
#######################
###END CONFIGURATION###
#######################

PATH=/usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
DESC="rtorrent"
NAME=rtorrent
DAEMON=$NAME
SCRIPTNAME=/etc/init.d/$NAME

checkcnfg() {
  exists=0
  for i in `echo "$PATH" | tr ':' '\n'` ; do
    if [ -f $i/$NAME ] ; then
      exists=1
      break
    fi
  done
  if [ $exists -eq 0 ] ; then
    echo "cannot find $NAME binary in PATH: $PATH" | tee -a "$logfile" >&2
    exit 3
  fi
  for (( i=0 ; i < ${#config[@]} ;  i++ )) ; do
    if ! [ -r "${config[i]}" ] ; then
        echo "cannot find readable config ${config[i]}. check that it is there and permissions are appropriate"  | tee -a "$logfile" >&2
        exit 3
    fi
    session=$(getsession "${config[i]}")
    if ! [ -d "${session}" ] ; then
        echo "cannot find readable session directory ${session} from config ${config[i]}. check permissions" | tee -a "$logfile" >&2
        exit 3
    fi
  done
}

d_start() {
  [ -d "${base}" ] && cd "${base}"
  stty stop undef && stty start undef
  #su -c "screen -S "${srnname}" -X screen rtorrent ${options} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
  su -c "screen -S "${srnname}" -X screen rtorrent ${options} " ${user} | tee -a "$logfile" >&2
  # this works for the screen command, but starting rtorrent below adopts screen session gid
  # even if it is not the screen session we started (e.g. running under an undesirable gid
  #su -c "screen -ls | grep -sq "\.${srnname}[[:space:]]" " ${user} || su -c "sg \"$group\" -c \"screen -fn -dm -S ${srnname} 2>&1 1>/dev/null\"" ${user} | tee -a "$logfile" >&2
  for (( i=0 ; i < ${#options[@]} ; i++ )) ;  do
    sleep 3
    #su -c "screen -S "${srnname}" -X screen rtorrent ${options[i]} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
    su -c "screen -S "${srnname}" -X screen rtorrent ${options[i]} " ${user} | tee -a "$logfile" >&2
  done
}

d_stop() {
  for (( i=0 ; i < ${#config[@]} ; i++ )) ; do
    session=$(getsession "${config[i]}")
    if ! [ -s ${session}/rtorrent.lock ] ; then
        return
    fi
    pid=$(cat ${session}/rtorrent.lock | awk -F: '{print($2)}' | sed "s/[^0-9]//g")
    # make sure the pid doesn't belong to another process
    if ps -A | grep -sq ${pid}.*rtorrent ; then
        kill -s INT ${pid}
    fi
  done
}

getsession() { 
    session=$(cat "$1" | grep "^[[:space:]]*session[[:space:]]*=" | sed "s/^[[:space:]]*session[[:space:]]*=[[:space:]]*//" )
    #session=${session/#~/`getent passwd ${user}|cut -d: -f6`}
    echo $session
}

checkcnfg

case "$1" in
  start)
    echo -n "Starting $DESC: $NAME"
    d_start
    echo "."
    ;;
  stop)
    echo -n "Stopping $DESC: $NAME"
    d_stop
    echo "."
    ;;
  restart|force-reload)
    echo -n "Restarting $DESC: $NAME"
    d_stop
    sleep 1
    d_start
    echo "."
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
```

As you can I see, I removed the redirection of output and errors in the actual 'screen' commands to try and better debug it.  When I run it from the command line I get this:
```
jeff@lamp:/etc/init.d$ sudo /etc/init.d/rtorrent start
Starting rtorrent: rtorrentNo screen session found.
No screen session found.
.
jeff@lamp:/etc/init.d$ 
```

It seems like it's an issue with the screen command more than with rtorrent, but I don't know what "No screen session found" means.

I'd appreciate any help.

---

### Post by ghost_ryder35 on 2008-07-14
it means that screen is not running.  add a script to start screen before rtorrent and u should be fine.

---

### Post by ranger0293 on 2008-07-14
> **ghost_ryder35 said:**
> it means that screen is not running.  add a script to start screen before rtorrent and u should be fine.

Thanks very much for the help.  Once I start a screen session, then run that init.d script, it starts fine.  However, it still isn't starting automatically on reboot.

I added the line
```
screen -m -d -S "${srnname}"
``` to the script like this:

```
d_start() {
  [ -d "${base}" ] && cd "${base}"
  stty stop undef && stty start undef
  screen -m -d -S "${srnname}"
  su -c "screen -S "${srnname}" -X screen rtorrent ${options} 2>&1 1>/dev/null" ${user} | tee -a "$logfile" >&2
``` but no luck.  Is there a better way to start screen on boot?

---

### Post by ranger0293 on 2008-07-14
Ah, I figured it out.  Just needed to execute the screen command as my user isntead of root.  Thanks for the help! :)

---

### Post by u4david on 2008-12-14
Could you please post the complete files and let me know where to change what so it works on my computer?

I'd also would like to start screen and torrent @ boot.

Thank you ,Ubuntu 8.04.

---

### Post by TygerFish on 2009-07-03
> **u4david said:**
> Could you please post the complete files and let me know where to change what so it works on my computer?

I'd also would like to start screen and torrent @ boot.

Thank you ,Ubuntu 8.04.

It took me a couple tries to figure it out too.


Add this:
```
# Start screen first
su -c "screen -m -d -S $srnname" $user
```

Just below the first lines of the actual script... right below this:
```

#######################
###END CONFIGURATION###
#######################

PATH=/usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
DESC="rtorrent"
NAME=rtorrent
DAEMON=$NAME
SCRIPTNAME=/etc/init.d/$NAME
```

It seems to work for me!

---

### Post by TomtheWombat on 2009-08-01
I've been trying to figure this out for 3 weeks!!  THanks a bunch!

---

### Post by megamih on 2009-08-13
This version of script leaves dead screen sessions after stop|restart. So, I've mixed some parts of this script and of others found with Google. This is a draft, but it's working for me.

```
#!/bin/bash
#############
###<Notes>###
#############
# This script depends on screen.
# For the stop function to work, you must set an
# explicit session directory using absolute paths (no, ~ is not absolute) in your rtorrent.rc.
# If you typically just start rtorrent with just "rtorrent" on the
# command line, all you need to change is the "user" option.
# Attach to the screen session as your user with 
# "screen -dr rtorrent". Change "rtorrent" with srnname option.
# Licensed under the GPLv2 by lostnihilist: lostnihilist _at_ gmail _dot_ com
##############
###</Notes>###
##############

#######################
##Start Configuration##
#######################
# You can specify your configuration in a different file 
# (so that it is saved with upgrades, saved in your home directory,
# or whatever reason you want to)
# by commenting out/deleting the configuration lines and placing them
# in a text file (say /home/user/.rtorrent.init.conf) exactly as you would
# have written them here (you can leave the comments if you desire
# and then uncommenting the following line correcting the path/filename 
# for the one you used. note the space after the ".".
# . /etc/rtorrent.init.conf


#Do not put a space on either side of the equal signs e.g.
# user = user 
# will not work
# system user to run as (can only use one)
user="megamih"

# system user to run as # not implemented, see d_start for beginning implementation
group=$(id -ng "$user")

# the full path to the filename where you store your rtorrent configuration
# must keep parentheses around the entire statement, quotations around each config file
config=("$(su -c 'echo $HOME' $user)/.rtorrent.rc")
# Examples:
#config=("/home/jeff/.rtorrent.rc")
# config=("/home/user/.rtorrent.rc" "/mnt/some/drive/.rtorrent2.rc")
# config=("/home/user/.rtorrent.rc"
# "/mnt/some/drive/.rtorrent2.rc"
# "/mnt/another/drive/.rtorrent3.rc")

# set of options to run with each instance, separated by a new line
# must keep parentheses around the entire statement
#if no special options, specify with: ""
options=("")
# Examples:
# starts one instance, sourcing both .rtorrent.rc and .rtorrent2.rc
# options=("-o import=~/.rtorrent2.rc")
# starts two instances, ignoring .rtorrent.rc for both, and using
# .rtorrent2.rc for the first, and .rtorrent3.rc for the second
# we do not check for valid options
# options=("-n -o import=~/.rtorrent2.rc" "-n -o import=~/rtorrent3.rc")

# default directory for screen, needs to be an absolute path
base=$(su -c 'echo $HOME' $user)

# name of screen session
srnname="rtorrent"

# file to log to (makes for easier debugging if something goes wrong)
logfile="/var/log/rtorrentInit.log"
#######################
###END CONFIGURATION###
#######################

PATH=/usr/bin:/usr/local/bin:/usr/local/sbin:/sbin:/bin:/usr/sbin
DESC="rtorrent"
NAME=rtorrent
DAEMON=$NAME
SCRIPTNAME=/etc/init.d/$NAME

case "$1" in
  start)
    echo "Starting $DESC: $NAME"
    [ -d "${base}" ] && cd "${base}"
    stty stop undef && stty start undef
    su $user -c 'screen -d -m rtorrent' &> /dev/null
    if [ $? -gt 0 ]; then
      echo "Failed to start $DESC: $NAME"
    else
      echo "Started $DESC: $NAME"
    fi
    ;;
  stop)
    echo "Stopping $DESC: $NAME"
    killall -w -s 2 rtorrent &> /dev/null
    screen -wipe
    if [ $? -gt 0 ]; then
      echo "Failed to stop $DESC: $NAME"
    else
      echo -n "Stopped $DESC: $NAME"
    fi
    ;;
  restart|force-reload)
    $0 stop
    sleep 1
    $0 start
    ;;
  *)
    echo "usage: $0 {start|stop|restart|force-reload}"
esac
exit 0
```

---

### Post by iamed18 on 2009-08-15
Hello All...I seem to be having a problem that I'm unsure about how to solve...

```
root@edserver:~# /etc/init.d/rtorrentInit.sh start
cannot find readable session directory  from config /home/iamed18/.rtorrent.rc. check permissions
root@edserver:~#

```Any response to this would be appreciated.

Oh, also, my .rtorrent.rc file is simply the following:
```
scgi_port = 127.0.0.1:5000
```

Also, here's the permissions for .rtorrent.rc
```
root@edserver:~# ls -l .rtorrent.rc
-rwxrwx--- 1 iamed18 root 27 2009-08-06 03:24 .rtorrent.rc

```

---

### Post by gogobambi on 2009-08-28
I couldn't get megamih's script to work, but got the 'less features, more compatible' one working from the [rtorrent wiki]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#StartingrTorrentonSystemStartup").

iamed18: sounds like you don't have the full rtorrent.rc config file. Get the [example file]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc#latest") from the rtorent wiki and then add the scgi port line.

---

