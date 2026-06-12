---
title: "How to start-up service at boot time with non-root user?"
date: 2008-10-29
forum: General Help
---

### Post by abcuser on 2008-10-29
Hi,
I have created service script in /etc/init.d/ and if I execute it by user that installed Ubuntu by command:
```
cd /etc/init.d/
./myscrip start

```
Script starts up successfully.

But when I reboot this service doesn't start. If I start it manually by:
```
cd /etc/init.d/
sudo ./myscript start

```
it reports that there is no xxxxx library found.

Is there any way I could start service at boot time with non-root user? So to start it by user that installed Ubuntu?
Thanks,
Abcuser

---

### Post by jigsaws on 2008-10-29
Tell us more about this service. Maybe it is good idea to start this service from user because of security reasons. You can do it by modyfing your start scripts and using su with -c parameter.

The problem with libary can be related to paths and environment variables.

---

### Post by abcuser on 2008-10-29
Hi,
I have installed "Oracle Essbase server 9.3.1.2" on Ubuntu 8.04. Essbase is working fine on Ubuntu - no problems at all. I have also installed [sysvconfig package](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html) to have service comand (like in Red Hat).

I have written boot up script: /etc/init.d/essbase
```

#!/bin/bash
set -e
. /lib/lsb/init-functions
case "$1" in
start)
/home/<userid>/Hyperion/AnalyticServices/bin/ESSBASE/ password -b &
;;
esac

```

If I execute above script with command "service essbase start" (it starts /etc/init.d/essbase script) with user that installed Essbase (non-root user!) Essbase server starts up successfully!!!

But if I execute the same script with root user (just like on boot up process) "**sudo** service essbase start" error appears:
"/home/<userid>/Hyperion/AnalyticServices/bin/ESSBASE: error while loading shared libraries: libessapinu.so: cannot open shared object file: No such file or directory."

I see this library is in path /home/<userid>/Hyperion/AnalyticServices/bin. And it looks like root user is unable to know where it is located.

It should be envirnonment variables problem, because myuserid can access Essabase server, but root can't.

I have copied all environment variables from my home directory's file .bashrc  to /etc/bash.bashrc and still doesn't help.

So now there can be two ways that I can see to solve a problem:
1. start script with non-root user (that is myuserid which starts script successfully)
2. set environment variables in that way that root could start up a script.

add 1) can you please write full sintax of "su -c" command?
add 2) is bash.bahrc started before services (daemons) are started?

Thanks,
Abcuser

---

### Post by jigsaws on 2008-10-29
Better idea is start service from its user. Try 

su - <userid> -c "/home/<userid>/Hyperion/AnalyticServices/bin/ESSBASE/ password -b &"

from root user.

---

### Post by bodhi.zazen on 2008-10-29
Well, ubuntu uses sudo (although I am sure su works as well) :)

sudo -u <user> command

will run the command as the user specified by -u <user>

---

### Post by abcuser on 2008-10-30
@bodhi.zazen, I have tried:
```
sudo -u hyperion /home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE password -b
```
or
```
sudo -u hyperion service essbase start
```
Both commands returned the same error:
"/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE: error while loading shared libraries: libessapinu.so: cannot open shared object file: No such file or directory."

But executing command with hyperion user:
```
/home/<user>/Hyperion/AnalyticServices/bin/ESSBASE password -b
```
or
```
service essbase start
```
essbase starts successfully.

Any idea how to fix the problem?
Regards,
Abcuser

---

### Post by jigsaws on 2008-10-30
And what about:
su - <userid> -c "/home/<userid>/Hyperion/AnalyticServices/bin/ESSBASE/ password -b &"
?

---

### Post by abcuser on 2008-10-30
@jigsaws,
su - hyperion -c "/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE/ password -b &"

returns the same error:
"/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE: error while loading shared libraries: libessapinu.so: cannot open shared object file: No such file or directory."

Any idea why?

---

### Post by bodhi.zazen on 2008-10-30
My guess is that ESSBASE uses a relative path. When you log in as a you are, by default, in your home directory.

You may need to 

cd /home/<user> && sudo -u <user> bash -c "/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE/ password -b" &

---

### Post by abcuser on 2008-11-04
> **bodhi.zazen said:**
> My guess is that ESSBASE uses a relative path. When you log in as a you are, by default, in your home directory.

You may need to 

cd /home/<user> && sudo -u <user> bash -c "/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE/ password -b" &

Hi I have tried above command but still getting the same error:
"/home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE: error while loading shared libraries: libessapinu.so: cannot open shared object file: No such file or directory."

Any idea?

---

### Post by bodhi.zazen on 2008-11-04
is libessapinu.so in /home/hyperion/Hyperion/AnalyticServices/bin/ESSBASE ?

If so, what are the permissions ?

---

### Post by abcuser on 2008-11-05
Hi,
in directory/home/hyperion/Hyperion/AnalyticServices/bin are both files:
ESSBASE - executible file
libessapinu.so - library

Both files have the same file permissions (click on attachment bellow).
Regards,
Abcuser

---

### Post by bodhi.zazen on 2008-11-05
Try changing the permissions on libessapinu.so to 777

chmod 777 .../libessapinu.so

---

### Post by abcuser on 2008-11-06
Hi,
I have set permissions to this library file and tried to execute "sudo -u hyperion ..." and still got error: "No such file or directory".

It looks like if sudo command is involved it just doesn't set environment variables... because library file can't be found.

I look into "man sudo" and tried several options but getting the same error.
Regards

---

