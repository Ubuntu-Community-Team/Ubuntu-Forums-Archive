---
title: "Activate laptop-mode to fix Load_Cycle_Count?"
date: 2008-11-01
forum: General Help
---

### Post by SpinningAround on 2008-11-01
I got this problem on my laptop [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) I tried to use the fix for Hardy but that didn't work since I did get this error

```

$sudo install 99-hdd-ugly-fix.sh /etc/acpi/resume.d/
install: cannot create regular file `/etc/acpi/resume.d/99-hdd-ugly-fix.sh': Permission denied 

```

While reading the bug report did I find these posts that was saying that you have to start laptop-mode and change one thing in laptop-mode.conf to fix the problem.


> 


Milan wrote:
> Igor: AFAIK, laptop-mode is not enabled by default. You need to tweak
> /etc/laptop-mode/laptop-mode.conf and switch the
> ENABLE_LAPTOP_MODE_ON_BATTERY option so that CONTROL_HD_POWERMGMT=1
> really takes effect. So the bug does not come from here.

The problem is that the acpi-support code does not check if laptop mode
is enabled or not. It ALWAYS disables the check if
CONTROL_HD_POWERMGMT=1, even if ENABLE_LAPTOP_MODE=false in
/etc/default/acpi-support. The reason for this is that in Debian (from
which this fix was ported), the ENABLE_LAPTOP_MODE setting does not
exist. The check in acpi-support should be adapted to also take
ENABLE_LAPTOP_MODE into account.

Cheers,
Bart



I also found this post, would someone more experiensed explain what it say, please
> 


How come in the file

DO_HDPARM=y
if [ -e /usr/sbin/laptop_mode ] ; then

it checks if the file /usr/sbin/laptop_mode exists rather than laptop mode is enabled? the file /usr/sbin/laptop_mode is always there even if laptop mode tool is not enabled. There is supposed to be other way to heck if laptop mode is enabled instead.

Anyways why does ubuntu still use ENABLE_LAPTOP_MODE to control laptop mode, debian has removed it long time before already and they never had any problem with it. I'm also confused about the lines before ENABLE_LAPTOP_MODE in acpi_support:
# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines. (Note: This is reported to cause breakage in
# Debian - see deb bug #425800. Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)



Note: Both these post are in the end of the bug report comments.

---

### Post by sdennie on 2008-11-01
I think /etc/acpi/resume.d stopped working after Ubuntu 7.10.  You could accomplish what you want with laptop-mode but, really, it's overkill if that is all you need it for.  I recommend creating a script like the following that will make Load_Cycle_Count increase on battery power but not on AC power.  As long as you aren't already at a very high Load_Cycle_Count, it's probably impossible to kill your disk via Load_Cycle_Count with this method:

```

#!/bin/bash

if on_ac_power ; then
    hdparm -B 255 /dev/sda
else
    hdparm -B 1 /dev/sda
fi

```

Name the script something like 99-lcc-fix and install it with:

```

sudo install 99-lcc-fix /etc/pm/sleep.d/
sudo install 99-lcc-fix /etc/pm/power.d/

```

This is a hack to be sure but, it should do what you want.

---

### Post by SpinningAround on 2008-11-01
Thanks, I will try the easy solution.

OT: is there any good guides around for laptop-mode

---

### Post by sdennie on 2008-11-01
The file /etc/laptop-mode/laptop-mode.conf is fairly well documented.  You can also check the man page:

```

man laptop-mode.conf

```

For other power savings information check the links in my signature.

---

