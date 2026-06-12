---
title: "Auto-start MySQL"
date: 2008-11-23
forum: General Help
---

### Post by felldin on 2008-11-23
I have a webserver running ubuntu 8.04. My problem is that I manually have to start MySQL on reboot. Is there any way my server can do this automatically?

---

### Post by Dr Small on 2008-11-23
Did you install MySQL from the repositories?
If so, there should be a startup script in /etc/init.d/

Please tell us how you manually start it.

---

### Post by felldin on 2008-11-23
I start it manually by typing:
sudo /etc/init.d/mysql startsudo /etc/init.d/mysql start

---

### Post by Dr Small on 2008-11-23
Please post the output of this command:
```
ls -l /etc/init.d/mysql
```

---

### Post by felldin on 2008-11-23
Here is the output:

-rwxr-xr-x 1 root root 5755 2008-05-09 17:52 /etc/init.d/mysql

---

### Post by Dr Small on 2008-11-23
Well then, unless something is wrong with your startup script, it should be starting.

---

### Post by felldin on 2008-11-23
It will not start. how do I check if my startup script is ok?

---

### Post by Dr Small on 2008-11-23
Post your startup script here and I will compare it against mine. Then, if it is identical, we'll have you reboot and run a command to see if it is really starting.

```
cat /etc/init.d/mysql
```

---

### Post by felldin on 2008-11-23
Thanks for your help. Here comes my startup script:



#!/bin/bash
#
### BEGIN INIT INFO
# Provides:          mysql
# Required-Start:    $remote_fs $syslog mysql-ndb
# Required-Stop:     $remote_fs $syslog mysql-ndb
# Should-Start:      $network $named $time
# Should-Stop:       $network $named $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start and stop the mysql database server daemon
# Description:       Controls the main MySQL database server daemon "mysqld"
#                    and its wrapper script "mysqld_safe".
### END INIT INFO
#
set -e
set -u
${DEBIAN_SCRIPT_DEBUG:+ set -v -x}

test -x /usr/sbin/mysqld || exit 0

. /lib/lsb/init-functions

SELF=$(cd $(dirname $0); pwd -P)/$(basename $0)
CONF=/etc/mysql/my.cnf
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"

# priority can be overriden and "-s" adds output to stderr
ERR_LOGGER="logger -p daemon.err -t /etc/init.d/mysql -i"

# Safeguard (relative paths, core dumps..)
cd /
umask 077

# mysqladmin likes to read /root/.my.cnf. This is usually not what I want
# as many admins e.g. only store a password without a username there and
# so break my scripts.
export HOME=/etc/mysql/

## Fetch a particular option from mysql's invocation.
#
# Usage: void mysqld_get_param option
mysqld_get_param() {
        /usr/sbin/mysqld --print-defaults \
                | tr " " "\n" \
                | grep -- "--$1" \
                | tail -n 1 \
                | cut -d= -f2
}

## Do some sanity checks before even trying to start mysqld.
sanity_checks() {
  # check for config file
  if [ ! -r /etc/mysql/my.cnf ]; then
    log_warning_msg "$0: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz"
    echo                "WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz" | $ERR_LOGGER
  fi

  # check for diskspace shortage
  datadir=`mysqld_get_param datadir`
  if LC_ALL=C BLOCKSIZE= df --portability $datadir/. | tail -n 1 | awk '{ exit ($4>4096) }'; then
    log_failure_msg "$0: ERROR: The partition with $datadir is too full!"
    echo                "ERROR: The partition with $datadir is too full!" | $ERR_LOGGER
    exit 1
  fi
}

## Checks if there is a server running and if so if it is accessible.
#
# check_alive insists on a pingable server
# check_dead also fails if there is a lost mysqld in the process list
#
# Usage: boolean mysqld_status [check_alive|check_dead] [warn|nowarn]
mysqld_status () {
    ping_output=`$MYADMIN ping 2>&1`; ping_alive=$(( ! $? ))

    ps_alive=0
    pidfile=`mysqld_get_param pid-file`
    if [ -f "$pidfile" ] && ps `cat $pidfile` >/dev/null 2>&1; then ps_alive=1; fi

    if [ "$1" = "check_alive"  -a  $ping_alive = 1 ] ||
       [ "$1" = "check_dead"   -a  $ping_alive = 0  -a  $ps_alive = 0 ]; then
        return 0 # EXIT_SUCCESS
    else
        if [ "$2" = "warn" ]; then
            echo -e "$ps_alive processes alive and '$MYADMIN ping' resulted in\n$ping_output\n" | $ERR_LOGGER -p daemon.debug
        fi
        return 1 # EXIT_FAILURE
    fi
}

#
# main()
#

case "${1:-''}" in
  'start')
        sanity_checks;
        # Start daemon
        log_daemon_msg "Starting MySQL database server" "mysqld"
        if mysqld_status check_alive nowarn; then
           log_progress_msg "already running"
           log_end_msg 0
        else
            /usr/bin/mysqld_safe > /dev/null 2>&1 &
            # 6s was reported in #352070 to be too few when using ndbcluster
            for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14; do
                sleep 1
                if mysqld_status check_alive nowarn ; then break; fi
                log_progress_msg "."
            done
            if mysqld_status check_alive warn; then
                log_end_msg 0
                # Now start mysqlcheck or whatever the admin wants.
                output=$(/etc/mysql/debian-start)
                [ -n "$output" ] && log_action_msg "$output"
            else
                log_end_msg 1
                log_failure_msg "Please take a look at the syslog"
            fi
        fi

        # Some warnings
        if $MYADMIN variables | egrep -q have_bdb.*YES; then
            echo "BerkeleyDB is obsolete, see /usr/share/doc/mysql-server-5.0/README.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        if [ -f /etc/mysql/debian-log-rotate.conf ]; then
            echo "/etc/mysql/debian-log-rotate.conf is obsolete, see /usr/share/doc/mysql-server-5.0/NEWS.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        ;;

  'stop')
        # * As a passwordless mysqladmin (e.g. via ~/.my.cnf) must be possible
        # at least for cron, we can rely on it here, too. (although we have
        # to specify it explicit as e.g. sudo environments points to the normal
        # users home and not /root)
        log_daemon_msg "Stopping MySQL database server" "mysqld"
        if ! mysqld_status check_dead nowarn; then
          set +e
          shutdown_out=`$MYADMIN shutdown 2>&1`; r=$?
          set -e
          if [ "$r" -ne 0 ]; then
            log_end_msg 1
            [ "$VERBOSE" != "no" ] && log_failure_msg "Error: $shutdown_out"
            log_daemon_msg "Killing MySQL database server by signal" "mysqld"
            killall -15 mysqld
            server_down=
            for i in 1 2 3 4 5 6 7 8 9 10; do
              sleep 1
              if mysqld_status check_dead nowarn; then server_down=1; break; fi
            done
          if test -z "$server_down"; then killall -9 mysqld; fi
          fi
        fi

        if ! mysqld_status check_dead warn; then
          log_end_msg 1
          log_failure_msg "Please stop MySQL manually and read /usr/share/doc/mysql-server-5.0/README.Debian.gz!"
          exit -1
        else
          log_end_msg 0
        fi
        ;;

  'restart')
        set +e; $SELF stop; set -e
        $SELF start
        ;;

  'reload'|'force-reload')
        log_daemon_msg "Reloading MySQL database server" "mysqld"
        $MYADMIN reload
        log_end_msg 0
        ;;

  'status')
        if mysqld_status check_alive nowarn; then
          log_action_msg "$($MYADMIN version)"
        else
          log_action_msg "MySQL is stopped."
          exit 3
        fi
        ;;

  *)
        echo "Usage: $SELF start|stop|restart|reload|force-reload|status"
        exit 1
        ;;
esac

---

### Post by Dr Small on 2008-11-23
Your file is definitely bigger and looks newer that mine. I don't see why it wouldn't be starting. So anyhow, try rebooting, don't start MySQL, then try running this commands:

Check and see if there was any errors, first:
```
cat /var/log/mysql.err
```

And then see if MySQL is actually running:
```
netstat -tl | grep mysql
```

You can also check by using:
```
ps aux | grep mysql
```

---

### Post by felldin on 2008-11-23
The first two commands didn't give any output. The last command gave me:
```
113       6022  0.2  0.8  96808 17756 ?        Sl   17:56   0:00 /usr/sbin/mysqld --defaults-file=/var/lib/squeezecenter/cache/my.cnf
felldin   6193  0.0  0.0   3008   776 pts/0    S+   17:59   0:00 grep mysql
```

---

### Post by spiderbatdad on 2008-11-23
would probably help to see /usr/sbin/mysqld
thinking user is not properly defined.

lol meant your .cnf file

---

### Post by felldin on 2008-11-23
> **spiderbatdad said:**
> would probably help to see /usr/sbin/mysqld
thinking user is not properly defined.

And how do I "see /usr/sbin/mysqld"? I'm new to linux so I need more instructions...

---

### Post by spiderbatdad on 2008-11-23
meant your conf file...maybe /etc/mysql/debian.cnf

---

### Post by felldin on 2008-11-23
It looks like this:
```
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = XXXXXX
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = XXXXXX
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

```

Can it give you any hint?

---

### Post by unutbu on 2008-11-23
I don't know if this will solve the problem, but it is something to check:

If you run this:
```
ls -l /etc/rc$(runlevel | cut -d' ' -f2).d | grep mysql
```

you should get this:
```
lrwxrwxrwx 1 root root  23 2008-01-19 14:08 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2008-01-19 14:08 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2008-01-19 14:08 S19mysql -> ../init.d/mysql
```

It is not enough to have the mysql script in /etc/init.d/mysql. It only gets run at boot time if there is a symlink to it in /etc/rc2.d. The above command checks that such symlinks exist.

---

### Post by felldin on 2008-11-23
> **unutbu said:**
> I don't know if this will solve the problem, but it is something to check:

If you run this:
```
ls -l /etc/rc$(runlevel | cut -d' ' -f2).d | grep mysql
```

you should get this:
```
lrwxrwxrwx 1 root root  23 2008-01-19 14:08 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  19 2008-01-19 14:08 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  15 2008-01-19 14:08 S19mysql -> ../init.d/mysql
```

It is not enough to have the mysql script in /etc/init.d/mysql. It only gets run at boot time if there is a symlink to it in /etc/rc2.d. The above command checks that such symlinks exist.

I get the same result as you get. So that don't seem to be the problem.

---

### Post by spiderbatdad on 2008-11-23
and do you have the file ~/.mycnf?

---

### Post by felldin on 2008-11-23
> **spiderbatdad said:**
> and do you have the file ~/.mycnf?

No, I don't have that file. What to do?

---

### Post by spiderbatdad on 2008-11-23
maybe start by reinstalling mysql php5, getting properly configured and passworded: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
Read as much as you can on the conf file, and how mysql starts.
[http://ariejan.net/2007/12/12/how-to-install-mysql-on-ubuntudebian/](http://ariejan.net/2007/12/12/how-to-install-mysql-on-ubuntudebian/)

---

### Post by felldin on 2008-11-29
Solved!

I changed my wired connection from roaming to straight dhcp and MYSql worked on reboot. This is because it changed my /etc/network/interfaces to the following:

auto lo
iface lo inet loopback
iface eth0 inet dhcp

---

### Post by Stoneface on 2010-07-08
I have a problem with MySQL not starting up automatically in Ubuntu Maverick as well. When I check the dmesg log for mysql errors I only get:
```
$ dmesg | grep mysql
[   13.001084] type=1400 audit(1278579546.767:16):  operation="profile_load" pid=833 name="/usr/sbin/mysqld" pid=833 comm="apparmor_parser"
jasper@ubuntu:~$ dmesg | grep mysql
[   13.001084] type=1400 audit(1278579546.767:16):  operation="profile_load" pid=833 name="/usr/sbin/mysqld" pid=833 comm="apparmor_parser"
```
MySQL does have a startup job:
```
$ ls -l /etc/init.d/mysql
lrwxrwxrwx 1 root root 21 2010-06-24 21:51 /etc/init.d/mysql -> /lib/init/upstart-job
``` I have added the init script. I use a bridged auth eth0 connection (Ubuntu in VmWare fusion Virtual Box) When I try to enter mysql from the terminal I get a missing socket error:
```
$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```which is odd as I manually added the socket the last time..
Any ideas why MySQL does not startup on system startup?

---

