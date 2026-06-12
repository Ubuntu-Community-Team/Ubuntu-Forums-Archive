---
title: "something about &quot;failed to initialize hal&quot;"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by pupilla on 2006-04-23
i write here my experience because for three days i've search for something into all the forums i could without find anything right.

i'm one of the millions of people who received a day the famous message FAILED TO INITIALIZE HAL"

For a long time i ignored it but three days ago i start to try to solve this problem and all that i could find in internet was a solucion in my case.

at the end i noticed that the file "hal.conf" was missing in the directory /etc/dbus/system.d and that not even reinstalling the package hal it came, although is in the list of the ones that are going to be installed. Luckly i fuond a cat of the file in a forum and i write it my self.

i don't now if this is a bug of the package and not even if this is the solution for all that have this problem but maybe this could be useful for someone.

here the file:

<!DOCTYPE busconfig PUBLIC
"-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

<!-- This configuration file specifies the required security policies
for the HAL to work. -->

<!-- Only root or user hal can own the HAL service -->
<policy user="hal">
<allow own="org.freedesktop.Hal"/>
</policy>
<policy user="root">
<allow own="org.freedesktop.Hal"/>
</policy>
<policy user="YOUR_USERNAME_HERE">
<allow own="org.freedesktop.Hal"/>
</policy>

<!-- Allow anyone to invoke methods on the Manager and Device interfaces -->
<policy context="default">
<allow send_interface="org.freedesktop.Hal.Manager"/>
<allow send_interface="org.freedesktop.Hal.Device"/>

<allow receive_interface="org.freedesktop.Hal.Manager"
receive_sender="org.freedesktop.Hal"/>
<allow receive_interface="org.freedesktop.Hal.Device"
receive_sender="org.freedesktop.Hal"/>
</policy>

<limit name="max_match_rules_per_connection">512</limit>

</busconfig>

---

