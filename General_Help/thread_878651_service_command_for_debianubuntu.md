---
title: "service command for debian/ubuntu"
date: 2008-08-03
forum: General Help
---

### Post by suyashjain on 2008-08-03
service command for debian/ubuntu

I almost worked 7years on redhat platform linux , but we i started exploring ubuntu i was surprised that their was no command like "service" to check the services.

So i immediately write one very simple bash script "service" command.

This command with do most of the operations as redhat service command do.

#######################################################################
#!/bin/bash

if [ "$2" == "status" ]; then

PID=`pidof $1`
if [ "$PID" == "" ]; then
echo "Service $1 is not running......."
else
echo "Serivce $1 is running with $PID pid...."
fi

else

sh /etc/init.d/$1 $2

fi
##############################################################

Contribution is very much welcome. Kindly reply the blog for your contribution.
[http://suyashjain.blogspot.com/2008/08/service-command-for-debianubuntu.html](http://suyashjain.blogspot.com/2008/08/service-command-for-debianubuntu.html)

---

### Post by sayakb on 2008-08-03
I think you need to install debian-helper-scripts. At a terminal:
```
sudo apt-get install debian-helper-scripts
```

---

