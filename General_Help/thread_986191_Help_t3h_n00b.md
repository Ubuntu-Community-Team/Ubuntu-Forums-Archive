---
title: "Help t3h n00b"
date: 2008-11-18
forum: General Help
---

### Post by KarateCowboy on 2008-11-18
Hi all you helpful Ubuntu pros!

There is a jboss application that I am using that is causing me a strange problem.  It works incorrectly when started at boot.  However if the application is terminated via 

```
/etc/init.d/myapp stop
```

Then restarted via 

```
/etc/init.d/myapp start
```

It works correctly. I suspect there is a difference between the environment variables.  So, how do I determine the environment variables for when daemons are launched at boot?  I am not very knowledgable in this process, so any knowledge on the matter and how this process works would be helpful.

---

### Post by geirha on 2008-11-18
the env command should output the environment, so put something like this in /etc/init.d/myapp somewhere, have it run on boot and then manually, then compare the environments in /var/log/myapp_*

```
/usr/bin/env &> /var/log/myapp_$(/bin/date "+%Y-%m-%d_%H:%M:%S")
```

---

### Post by KarateCowboy on 2008-11-18
Hey that was great and showed big differences in the environments.  The only question is: how do I change the environment variables at boot?

---

### Post by prshah on 2008-11-18
> **KarateCowboy said:**
> how do I change the environment variables at boot?

Place them in the /etc/environment file; create it if it does not exist. You'll need to use "sudo" to create such a file; post back for more detailed instructions if you need it.

---

### Post by KarateCowboy on 2008-11-18
OK.
I tried posting a modified PATH in the /etc/environment file.  So it looked like this:
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en"
```

However the command
```
/usr/bin/env &> /var/log/myapp_$(/bin/date "+%Y-%m-%d_%H:%M:%S")
```
From before gave me this:
```

CONSOLE=/dev/console
break=
TERM=linux
rootmnt=/root
INIT_VERSION=sysvinit-2.86
init=/sbin/init
PATH=/sbin:/bin:/usr/sbin:/usr/bin
vga=788
_=/usr/bin/env
RUNLEVEL=2
runlevel=2
resume=/dev/sda2
PWD=/
VERBOSE=no
PREVLEVEL=N
previous=N
quiet=y
ROOT=/dev/sda1
HOME=/
SHLVL=2
PROGRESS_STATE=2
DPKG_ARCH=i386
readonly=y

```

For some reason the paths are different. So, above it has INIT_VERSION, which I suspect is because init is calling this program.  My guess is this program inherits its environment from sysvinit and that is why it is not running correctly on boot.  So if I can determine where the environment variables for sysvinit are stored that is a possible solution

---

### Post by geirha on 2008-11-18
Try adding those variables to the start of the init script then
```

export PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
export LANG="en_US.UTF-8"
export LANGUAGE="en"

```

---

