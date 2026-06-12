---
title: "Uniquely identifying users w/ oidentd"
date: 2005-11-19
forum: General Help
---

### Post by zen_monk on 2005-11-19
Hi.

I'm looking to configure **oident** to report the name of the user currently logged in via a Gnome session i.e. if UserA is actively running their desktop session, all ident queries to the machine should report UserA.  

Also, if I do user switching via Gnome do say UserB, the ident queries should then report UserB.

I've tried setting a per user configuration using the $HOME/.oidentd.conf file yet it doesn't seem to work yet in relation to who is logged in via Gnome.

Any pointers or help would be greatly appreciated.

---

### Post by becatlibra on 2007-01-28
I got this from someone else - it is in regards to dansguardian but check it out anyway

This is how I did it:

1. Download ident2_1.05.orig.tar.gz from Debian website and unpack it to your
home directory.

2. Download tp-ident2.patch from DansGuardian website to your home directory.

3. Open a shell ( xterm, rxvt, konsole, etc.) and as root, cd into the directory
where you unpacked ident2, and run this command: ./configure .

4. When 'configure' has finished...
run this command: patch -p0 machine.c [here, write the location of the patch]
for example: patch -p0 machine.c /home/charlie/tp-ident2.patch

5. When 'patch' has finished running, run this command: make .

6. When 'make' has finished, run: make install . When it is done running you
can use ident2 by typing this at the shell: /usr/local/sbin/ident2. 


for ubuntu save the code below to a file called ident2
> 
#! /bin/sh
#
# ident2   Start/Stop RFC 1413 ident2 server
#
# chkconfig: 345 35 65
# description:   The identd server provides a means to determine the identity
#      of a user of a particular TCP connection.  Given a TCP port
#      number pair, it returns a character string which identifies
#      the owner of that connection on the server's system.
# processname: ident2
# pidfile: /var/run/ident2
# config: /etc/identd.conf

# Source function library.
. /lib/lsb/init-functions

[ -x /usr/local/sbin/ident2 ] || exit 0

RETVAL=0

# See how we were called.
case "$1" in
  start)
   log_begin_msg "Starting ident2: "
   /usr/local/sbin/ident2
   RETVAL=$?
   echo
   [ $RETVAL -eq 0 ] && touch /var/run/identd/ident2.pid
   ;;
  stop)
   log_begin_msg "Stopping ident2 services: "
   killproc ident2
   RETVAL=$?
   echo
   [ $RETVAL -eq 0 ] && rm -f /var/run/identd/ident2.pid
   ;;
  status)
   status ident2
   RETVAL=$?
   ;;
  restart|reload)
   $0 stop
   $0 start
   RETVAL=$?
   ;;
  *)
   log_success_msg "Usage: ident2 {start|stop|status|restart|reload}\n"
   exit 1
esac

exit $RETVAL 


chown root:root ident2
chmod 755
cp ident2 /etc/init.d

sudo update-rc.d ident2 defaults

And that's it!  It works great!


Benjamin

---

