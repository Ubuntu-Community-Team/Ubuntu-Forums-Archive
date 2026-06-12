---
title: "network interfaces shell script"
date: 2008-10-03
forum: General Help
---

### Post by jp73107 on 2008-10-03
Hello. I've written a shell script to switch between certain network interfaces files so i can be a lazy ******* and not have to manually edit /etc/network/interfaces every time i switch networks. Here is what i have.
[COLOR="Red"]
Edited --- wrong script and wrong result and wrong box! >< ---
[/COLOR]

Script:

```
#!/bin/bash
# belkin.sh
# Script to change the current /etc/network/interfaces file to use Belkin router
clear
echo "Now changing network configuration to Belkin Router."
cp /etc/network/config/coyote/interfaces /etc/network/interfaces
resolvconf -u
/etc/init.d/networking restart
resolvconf -u
/etc/init.d/networking restart
echo "Now using the Belkin router configuration"

```

invoking the belkin.sh script gives me this error:

```
root@vmjeossrv:~/scripts# sh belkin.sh
: not found4: clear
Now changing network configuration to Belkin Router.
cp: cannot stat `/etc/network/config/coyote/interfaces': No such file or directory
resolvconf: Error: Invalid argument
Usage: resolvconf (-u|-d IFACE|-a IFACE)
Usage: /etc/init.d/networking {start|stop|restart|force-reload}
resolvconf: Error: Invalid argument
Usage: resolvconf (-u|-d IFACE|-a IFACE)
Usage: /etc/init.d/networking {start|stop|restart|force-reload}
Now using the Belkin router configuration
```


Can anyone tell me what i did wrong? Thanks in advance!!!

---

### Post by hyper_ch on 2008-10-03
Hmmm, I discovered - because of some other problem - just a little while ago [WICD]("http://wicd.sourceforge.net/"). In order to use it, you'll have to get rid of any network manager - and it lets you easily setup different configs for wireless and wired networks. You might want to try that.

But regarding your shell script:

(1) I'd add the "-f" option to the cp command
(2) Not sure about "resolvconf"... I don't think you need to run that manually...
(3) The "networking restart" error is odd...

Do you run that script as root?

---

### Post by jp73107 on 2008-10-03
i usually run the script as root (sudo su) then go back to normal user. If i don't run resolvconf manually, my network doesn't come back up after i restart it. I'm not sure if this is because i'm using JeOS on this particular virtual machine or what, but resolvconf didn't come preinstalled with JeOS. I might just suck it up, install ubuntu server and try it again after installing the linux-virtual image.

---

### Post by jp73107 on 2008-10-03
Well.. i removed the resolvconf line and added sh to the /etc/init.d/networking restart line, and problem solved.. heh

---

