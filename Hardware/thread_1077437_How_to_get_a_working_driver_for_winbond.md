---
title: "How to get a working driver for winbond"
date: 2009-02-22
forum: Hardware
---

### Post by mohr tutchy on 2009-02-22
These steps had successful results under intrepid, both 32 and 64 bit, I didn't tried with hardy.

1 ~ Type 
```
hal-device|grep -i wec
```
output should be 
```
57: udi = '/org/freedesktop/Hal/devices/pnp_WEC1020'
  info.product = 'PnP Device (WEC1020)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WEC1020'  (string)
  pnp.id = 'WEC1020'  (string)

```

2 ~ Download the latest version from CVS (which includes the WPC876L module)
```

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc

```

3 ~ cd to the sourcecode directory and update
```

cd lirc
cvs update

```

4 ~ Install dialog and build-essential
```
sudo apt-get install dialog build-essential
```

5 ~ Configure:
```
bash configure
```
Then select: Driver configuration > IRDA/CIR hardware > WINBOND 8769L > Save configuration and run configure

6 ~ Make:
```
make
```

7 ~ Install:
```
sudo make install
```

8 ~ Copy the needed drivers in the right directory:
```
sudo mkdir /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_wpc8769l
sudo cp drivers/lirc_wpc8769l/lirc_wpc8769l.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_wpc8769l/
sudo cp drivers/lirc_dev/lirc_dev.ko /lib/modules/`uname -r`/kernel/ubuntu/lirc/lirc_dev/
```

9 ~ Add the following line to /etc/modules
```

lirc_wpc8769l

```

10 ~ Because there isn't any lirc script in /etc/init.d/ I wrote a very simple one. So create a file in /etc/init.d/ named lirc and copy the following:
```
#!/bin/bash

case "$1" in
  start)
    echo -n "Starting lirc daemon..."
    ARGS=' --permission=666 --device=/dev/lirc0 /etc/lircd.conf'
    start-stop-daemon --start --exec /usr/local/sbin/lircd -- $ARGS
    echo "."
    ;;
  stop)
    echo -n "Stopping lirc daemon..."
    start-stop-daemon --stop --exec /usr/local/sbin/lircd
    echo "."
    ;;
  *)
    echo "Usage: /etc/init.d/lircd {start|stop}"
    exit 1
esac

exit 0
```

11 ~ Give the right permissions to the file:
```
sudo chmod 775 /etc/init.d/lirc
```

12 ~ Update system's scripts:
```
sudo update-rc.d lirc multiuser
```

13 ~ Reboot

14 ~ Test:
```
mode2
```

if everything went fine if you press some buttons of (almost) any remote some output appear.

For the lircd.conf and the .lircrc you can find a lot of howtos in the web ;)

One love

PS: Sorry for bad english :s

Edit: thanks to sokairyk that improved this howto, see [this]("http://ubuntuforums.org/showpost.php?p=6907459&postcount=9")

---

