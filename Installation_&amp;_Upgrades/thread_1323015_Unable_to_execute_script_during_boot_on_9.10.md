---
title: "Unable to execute script during boot on 9.10"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by jmz2 on 2009-11-11
Hello,

My /home partition is fully encrypted with Truecrypt. In order to be able to log in this partition has to be mounted during boot time.

In Ubuntu 9.04 Remix I had an scrpit placed on /etc/init.d/ that stopped the boot process and asked for the password of the encrypted partition in order to mount it. Once you provided the password the booting process keept going on.

I have upgraded to Ubuntu 9.10 Remix and use the same script in the same /etc/init.d/ in order to achieve the same as with 9.04 regarding mounting /home. However, the boot process is not considering my script as the booting is not stopping in order to mount the partition.

I now is not a problem with the code of the script as it is the same script as used in version 9.04 and moreover it runs well if I call it manually one my Ubuntu sesion is started.

I have made the symbliks to the script correcly:

> @akoya1210:~$ sudo find /etc/ -name *mounttrue*
/etc/rc2.d/S20mounttruecrypt
/etc/rc5.d/S20mounttruecrypt
/etc/rc0.d/K20mounttruecrypt
/etc/rc6.d/K20mounttruecrypt
/etc/rc4.d/S20mounttruecrypt
/etc/init.d/mounttruecrypt.old
/etc/init.d/mounttruecrypt~
/etc/init.d/mounttruecrypt
/etc/rc1.d/K20mounttruecrypt
/etc/rc3.d/S20mounttruecrypt


Is there any change in the boot sequence on Ubuntu 9.10 than in 9.04? What has changed in version 9.10 that my script is not launched during boot?

Thanks for your help.

---

### Post by jmz2 on 2009-11-15
This is the script that I am trying to run:

> #!/bin/bash
#
#   /etc/rc.d/init.d/truecrypt
#
# Mounts the /home partition with truecrypt.
#
# chkconfig: 2345 90 10
# description: Truecrypt

# processname: truecrypt

#source /etc/init.d/functions

[ -x /usr/bin/truecrypt ] || exit 1

RETVAL=0
prog="truecrypt" 
desc="Truecrypt" 

start() {
    truecrypt --mount /dev/sda7 /home_test
   RETVAL=$?
   [ $RETVAL -eq 0 ] && touch /var/lock/subsys/$prog
   echo
}

stop() {
   echo "Unmounting encrypted disks." 
   truecrypt -d  /home_test
   RETVAL=$?
   [ $RETVAL -eq 0 ] && success || failure
   echo
   [ $RETVAL -eq 0 ] && rm -f /var/lock/subsys/$prog
   return $RETVAL
}

case "$1" in
  start)
   start
   ;;
  stop)
   stop
   ;;
  restart)
   stop
   start
   RETVAL=$?
   ;;
  condrestart)
        [ -e /var/lock/subsys/$prog ] && restart
   RETVAL=$?
   ;;
  *)
   echo $"Usage: $0 {start|stop|restart|condrestart}" 
   RETVAL=1
esac

exit $RETVAL 


---

### Post by jmz2 on 2009-11-21
What that script does is to stop the boot process and truecrypt comes up for the password question. Once you introduce the correct password the encrypted partition is mounted and the boot process continue.

But since installation of Ubuntu 9.10 the boot process is not stopping. Something has changed in the boot process on the last version of Ubuntu 9.10 from the 9.04 version as in 9.04 it worked perfectly.

I know is  not a scripting mistake as I can manually run the script doing:
/etc/init.d/mounttruecript start

Anybody can help me? THANKS!!

---

