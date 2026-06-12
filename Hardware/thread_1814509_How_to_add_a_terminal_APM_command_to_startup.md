---
title: "How to add a terminal APM command to startup?"
date: 2011-07-29
forum: Hardware
---

### Post by jamesensor on 2011-07-29
How do I add a terminal command to  ubuntu startup?

I'd like to put this:

sudo hdparm -B 255 /dev/sda

I added to rc.local

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

hdparm -B 255 /dev/sda

exit 0

but when I reboot I use TLP tools to check its status and the APM is on set to 244. I'd like it permanently off.

How do I do this? Thank you.

---

