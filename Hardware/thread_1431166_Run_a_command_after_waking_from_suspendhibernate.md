---
title: "Run a command after waking from suspend/hibernate?"
date: 2010-03-16
forum: Hardware
---

### Post by King of Dreams on 2010-03-16
I am running 9.10 on an old Dell laptop.  Suspend and resume is working fine, except I lose my wireless after resuming.  If I run a "rmmod ndiswrapper; modprobe ndiswrapper" manually after resuming, then all is well again.

What I am wondering is if there's a file that gets executed automatically upon resume where I can place these commands to automate it?

I am also open to suggestions for a less bass-ackwards approach if anyone has a suggestion.  My first attempt to get this to work was to edit /etc/default/acpi-support and add ndiswrapper to the MODULES entry, but this did not fix the problem.

Thanks in advance for any info!

---

### Post by King of Dreams on 2010-03-16
Did some more reading, and I was able to get it to work as follows (perhaps a kludgy solution, but I don't know a more elegant one, and it worked for me!):

Created a new file named 0000wireless in /usr/lib/pm-utils/sleep.d, and made it executable:

chmod a+x /usr/lib/pm-utils/sleep.d/0000wireless

The file has the following contents:

#!/bin/sh

# reload ndiswrapper to get wireless to recover properly

case "$1" in
        resume|thaw)
                rmmod ndiswrapper
                modprobe ndiswrapper
                ;;
esac

---

### Post by tgalati4 on 2010-03-16
There is also /etc/default/acpi-support.  You can add a list of modules to be unloaded before sleep, then reloaded after wake.  This file may be deprecated in 9.10, I'm not sure.  I'm running Jaunty at the moment.

---

### Post by King of Dreams on 2010-03-16
That was the first thing I tried, but it seemed to have no effect.

---

