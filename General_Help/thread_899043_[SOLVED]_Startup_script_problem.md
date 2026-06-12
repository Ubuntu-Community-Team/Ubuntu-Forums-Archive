---
title: "[SOLVED] Startup script problem"
date: 2008-08-23
forum: General Help
---

### Post by TrueLens on 2008-08-23
I am having problems with this bash script that I use to start up my headless Azureus client.  This previously worked on a Fedora based machine but after installing a fresh copy of Ubuntu 8.04 it no longer works on startup.  I can run the script successfully when logged in with my normal user, however if I try to run the script with the sudo command I get the an error.  

```
sudo ./azureus_script status
./azureus_script: 64: [[: not found
Azureus is DOWN
```

I can successfully run the code from a root command line after using the command sudo -s.  I have tried changing the #!/bin/bash line to be #!/bin/sh without any success.

Can someone point me in the right direction?

Thanks!


```
 #!/bin/bash

 #The user that will run Azureus
 AZ_USER=az_user

 #Name of the screen-session
 NAME=az

 #executable files in the following paths that are perhaps needed by the script
 PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/azureus/bin

 #your path to the azureus directory, where Azureus2.jar is located
 DIR=/home/az_user/azureus

 #Description
 DESC="Azureus screen daemon"

 case "$1" in
 start)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo "Azureus is already running!"
    else
       echo "Starting $DESC: $NAME"
       su $AZ_USER -c "cd $DIR; screen -dmS $NAME /usr/bin/java -jar ./Azureus2.jar --ui=console"
    fi
    ;;
 stop)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
       then
       echo -n "Stopping $DESC: $NAME"
       su $AZ_USER -c "screen -S $NAME -X quit"
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
    ;;
 restart)
    if [[ `su $AZ_USER -c "screen -ls |grep $NAME"` ]]
        then
       echo -n "Stopping $DESC: $NAME"
       su $AZ_USER -c "screen -S $NAME -X quit"
       echo " ... done."
    else
       echo "Coulnd't find a running $DESC"
    fi
    echo "Starting $DESC: $NAME"
       su $AZ_USER -c "cd $DIR; screen -dmS $NAME /usr/bin/java/java -jar ./Azureus2.jar --ui=console"
    echo " ... done."
    ;;
 status)
     if  [[ -n  $(su $AZ_USER -c "screen -ls |grep $NAME") ]]
       then
       echo "Azureus is RUNNING"
    else
       echo "Azureus is DOWN"
    fi
    ;;
 *)
    echo "Usage: $0 {start|stop|status|restart}"
    exit 1
    ;;
 esac

 exit 0
```

---

### Post by Mister.Vash on 2008-08-24
You could modify the script to set it so that is shows what it is doing with the set command

```
 #!/bin/bash

set -x
 #The user that will run Azureus
.
.
.
 esac

set +x
exit 0

```

---

### Post by TrueLens on 2008-08-24
Thanks for the reply.  After enabling the +x I get the following output:

```
sudo ./azureus_script status
+ AZ_USER=az_user
+ NAME=az
+ PATH=/bin:/usr/bin:/sbin:/usr/sbin:/home/azureus/bin
+ DIR=/home/az_user/azureus
+ DESC=Azureus screen daemon
+ su az_user -c screen -ls |grep az
+ [[ 7612.az (Detached) ]]
./azureus_script: 1: [[: not found
+ echo Azureus is DOWN
Azureus is DOWN
+ set +x

```

The script executes perfectly when I run it with my normal user account, this is still just a problem when running with sudo or with running during boot.  It is weird it seems to indicate line 1 if that is what that number means.

---

### Post by mssever on 2008-08-24
I think that init scripts are required to be sh scripts, not bash. [[ is a bashism. Try changing [[ .... ]] to [ ... ]. You might have to sort out a few other issues.

The reason for this is that Ubuntu now uses dash for /bin/sh, not bash like many other distros use. Bash doesn't work completely like sh should, so sometimes people using systems which use bash for their /bin/sh use bashisms by mistake and don't catch them.

---

### Post by TrueLens on 2008-08-24
You were exactly right about the brackets.  I changed the double ones to single and enclosed the command in double quotes.  Everything then worked properly.  Thanks for your help!

---

