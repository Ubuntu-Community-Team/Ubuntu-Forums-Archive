---
title: "[SOLVED] Help on starting/killing services using a bash script"
date: 2008-09-24
forum: General Help
---

### Post by RonB123123 on 2008-09-24
Is there a way to write a bash script to check if the following services are running? 

mysql
mysql-ndb
mysql-ndb-mgm
apache2

And if there are not running, can the bash script start those services?

These services always seem to slow down my computer so I only like to use those when I'm doing webpage design. Any help is appreciated. Thank you!

---

### Post by Pelham123 on 2008-09-24
Have a look here...

[http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml](http://www.anyexample.com/linux_bsd/bash/check_if_program_is_running_with_bash_shell_script.xml)


Could add different variables for $SERVICE(s) and I am sure it would be easy to add '/etc/init.d/$SERVICE start|stop' to the script

I've only ever written a few, so hardly an expert and its always such an subjective subject...just thought I'd get the ball rolling ;)

---

### Post by RonB123123 on 2008-09-24
OK cool. This is my code so far, but for some reason it only checks for MySQL. It's as if the loop isn't working properly. Any ideas?

```

#!/bin/sh
## MySQL + Apache Services
## Ronak
## Sept 24, 2008
##
## - Checks if the MySQL + Apache services are running, if they are
## not then start each one.

SERVICES[0]="mysql"
SERVICES[1]="mysql-ndb"
SERVICES[2]="mysql-ndb-mgm"
SERVICES[3]="apache2"

# check if each service is running
for service in $SERVICES
do
  # if current service is running, dont do anything.
  if ps ax | grep -v grep | grep $service > /dev/null
  then
    echo "$service service is running!"
  else # otherwise, turn it on
    echo "$service is not running"
    sudo /etc/init.d/$service start
    if ps ax | grep -v grep | grep $service > /dev/null
    then
      echo "$service is now running."
    else
      echo "Unable to start $service."
    fi
  fi
done

```

---

### Post by Pelham123 on 2008-09-25
Replace...

```
SERVICES[0]="mysql"
SERVICES[1]="mysql-ndb"
SERVICES[2]="mysql-ndb-mgm"
SERVICES[3]="apache2"
```

With

```
SERVICES="mysql mysql-ndb mysql-ndb-mgm apache2"
```

---

### Post by RonB123123 on 2008-09-27
Thanks! It works in the sense that it goes through each array value but for some reason it can't seem to start the middle two services. The mysql and apache2 services can start flawlessly after the correct password has been entered.

Thanks for the help.

---

### Post by Pelham123 on 2008-09-28
Couple of suggestions then.

Try commenting out the two /dev/null with # so you get the results of grep on the screen.

```
# > /dev/null
```

You didnt say what sort of error messages (if any) you get. Maybe as grep is searching for mysql on the first entry...it will find mysql AND mysql-ndb AND mysql-ndm-mgm. If this will *confuse* the script I dont know, but you can add the -m switch to grep which will tell it to stop grepping after a certain amount of lines. Eg..

```
if ps ax | grep -v grep | grep -m 1 $service > /dev/null
```

..will cause grep to stop searching after it has found one (the first) match. So hopefully it will *only* find mysql, then mysql-ndb etc.

*shrugs shoulders*

Worth a go?

---

### Post by RonB123123 on 2009-10-19
Here is my somewhat updated code. It still needs work because it cannot start/stop the mysql-ndb and mysql-ndb-mgm services. 

```

#!/bin/sh
## Author:	RonB123123
## Created:	Sept 24, 2008
## Description: 
## 		Checks if the MySQL + Apache services are running, if not
## 		not then start each service.

echo "Options"
echo "1 - Start"
echo "2 - Stop"
read option

SERVICES="mysql mysql-ndb mysql-ndb-mgm apache2"

# check if each service is running
for service in $SERVICES
do
  if [ "$option" == "2" ]
  then
    echo "Stopping $service..."
    sudo /etc/init.d/$service stop
  elif [ "$option" == "1" ]
  then
    echo "Starting $service..."
    sudo /etc/init.d/$service start
  fi
  if (ps ax | grep -v grep | grep $service > /dev/null)
  then
    echo "$service is running."
  else
    echo "$service is not running."
  fi
done

```

If anyone can work on this code and figure it out, it would be greatly appreciated. Thank you.

---

### Post by Rich_B_uk on 2009-10-20
You can either use Monit for this - [http://mmonit.com/monit/](http://mmonit.com/monit/)

Or this simple shell script should work - [http://www.heritage-tech.net/762/automatically-restart-dead-services-via-bash-scripting/](http://www.heritage-tech.net/762/automatically-restart-dead-services-via-bash-scripting/)

Have fun :P

---

