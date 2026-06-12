---
title: "Laptop loses wireless on re-awakening from standby"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by busgeek on 2007-04-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125](https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm trying to fix the standby & re-awaken on my Dell Latitude D600.  The network manager seems to lose the wireless network on re-awakening.   I have tried adding scripts to the /etc/acpi directories as suggested in [https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125](https://bugs.launchpad.net/ubuntu/+s...ger/+bug/40125)

However, the bug seems a bit more profound than that listed here.  (I think I need to do a new iwlist scan as well as re-starting the network manager.)

Currently my scripts are as follows:
In **/etc/acpi/suspend/06-networkmanager.sh**:

[INDENT]#!/bin/sh
# HD> Ensure suspend keeps wireless networking settings.

/usr/bin/dbus-send --system \
--dest=org.freedesktop.NetworkManager \
--type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.sleep

[/INDENT] 

and in **/etc/acpi/resume.d/#!/bin/sh**

[INDENT]
# HD> Added wireless restart code
/usr/bin/dbus-send --system \
--dest=org.freedesktop.NetworkManager \
--type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.wake
# HD> End of change.

if [ -x /etc/init.d/wifi-radar ]; then
        /etc/init.d/wifi-radar start
fi
[/INDENT]

Also, on startup I need to load ndiswrapper and run iwconfig and iwlist scan (I do this in a script) 
Then I need to start the network manager...
The question is...  Is there a correct way to do this on startup?

Of course all this worked perfectly for me on Dapper Drake, but I recently updated to Feisty and it no longer works...

Thanks in anticipation.

---

### Post by H.E. Pennypacker on 2007-05-06
Same problem here.  Uhm, it appears that there is something going on at the point of resume.  For some odd reason, Feisty does not do what it should be doing.  In another post, one person explained that doing "sudo modprobe [driver]" worked for him.

Since this reliably worked for him, he could add it to some resume script, and this may work for you and I as well.  How to create a resume script, and where to place it are beyond me.

By the way, the launchpad links in your post are dead.

---

### Post by aot2002 on 2007-05-06
yes same here 

looks like a ubuntu bug ...this sux i didnt expect such a popular distro to have issues like this...
anyone know a better fix

---

### Post by Ubuntiac on 2007-05-15
The solution in this post fixed it for me:
[http://ubuntuforums.org/showpost.php?p=2654502&postcount=18](http://ubuntuforums.org/showpost.php?p=2654502&postcount=18)

BTW You'll find bugs in even the biggest distro's (win...ahem...dows..ahem). The question is what kind of support do you get at what price afterwards. Hope this (free) suggestion helps. :)

---

### Post by mfichifichi on 2007-05-18
I had the problem on a latitude c400 but not because the module was unloading. To fix it I changed the /etc/acpi/resume.d/62-ifup.sh from

for x in $INTERFACES; do
    ifup $x &
done


to:

ifdown -a;ifup -a

---

### Post by veebis on 2007-06-05
> I had the problem on a latitude c400 but not because the module was unloading. To fix it I changed the /etc/acpi/resume.d/62-ifup.sh from

for x in $INTERFACES; do
ifup $x &
done

to:
ifdown -a;ifup -a

Thank you! This worked for me. 
Waking up is s-l-o-w-e-r now, but that's okay since it's now restoring the network during the delay (approx. 10-15 seconds).

BTW, this is with a Thinkpad T22, Linksys WPC11 v4 PCMCIA. 
That's right... 8 MB of SCREAMING video muscle.
-Vb

---

