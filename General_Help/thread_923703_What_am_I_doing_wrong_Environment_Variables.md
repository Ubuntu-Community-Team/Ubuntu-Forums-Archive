---
title: "What am I doing wrong? Environment Variables"
date: 2008-09-18
forum: General Help
---

### Post by sdlyr8 on 2008-09-18
I wrote a simple little script that gets my home pc's ip address and updates my webserver. Then from my laptop I am now writing a script that grabs that address from my webserver and then saves the ip as an environment variable. But for some reason it wont save the environment variable like I would expect.. anyone see what I'm doing wrong? I'm guessing it's something stupid... it IS getting the IP address correctly so i'm not sure...

```
#!/bin/bash

wget -q http://*webserver*/ssh_ip_current.txt

FILE="ssh_ip_current.txt"
   if [ ! -f $FILE ]; then
        echo "$FILE : does not exists"
        exit 1
   elif [ ! -r $FILE ]; then
        echo "$FILE: can not read"
        exit 2
   fi

exec 3<&0
exec 0<$FILE

read ip
echo $ip

exec 0<&3

export HOMEIP=$ip

rm ssh_ip_current.txt

```

---

### Post by Pro-reason on 2008-09-18
I'm not sure what all that exec and read stuff is for.  If you just want to put the contents of the file into a variable, wouldn't this suffice?

```
#!/bin/bash
wget -q http://*webserver*/ssh_ip_current.txt
HOMEIP="$(cat ssh_ip_current.txt)"

```

---

### Post by lswb on 2008-09-18
Once that script exits, the variable is gone. The "export" line will only pass the variable to child scripts. I agree with Pro also, if you don't need that exec for some other reason.

---

