---
title: "INTREPID - How to make work ATI catalyst driver"
date: 2008-11-30
forum: Hardware
---

### Post by Pépou on 2008-11-30
This post is for people who can't enable fglrx driver since ubuntu intrepid.


Start by removing fglrx and its dependences :

```
sudo apt-get remove fglrx*
```

Then :

```
sudo apt-get install linux-restricted-modules-generic restricted-manager
```

Reinstall fglrx :

```
sudo apt-get install xorg-driver-fglrx
```
```
sudo apt-get install fglrx-modaliases
```

Then :

```
cd /lib/modules/2.6.27-10-generic/kernel/drivers/video
```
(adapt this command on your kernel version. To know it do : "uname -a")

Then :

```
sudo ln -s ../../../updates/dkms/fglrx.ko .
```

Then :

```
sudo modprobe fglrx
```
If no error message, everything is OK.

If "/sbin/lrm-video" is missing :

Create it : 

```
sudo gedit /sbin/lrm-video
```

Past in this file :

```
#!/bin/sh

PATH=/sbin:/bin

MODULE="$1"
shift

if [ "$MODULE" = "nvidia" ]; then
        if [ -e /lib/linux-restricted-modules/.nvidia_legacy_installed ]; then
                MODULE="nvidia_legacy"
        fi
        if [ -e /lib/linux-restricted-modules/.nvidia_new_installed ]; then
                MODULE="nvidia_new"
        fi
        XORG="nvidia";
elif [ "$MODULE" = "nvidia_legacy" -o "$MODULE" = "nvidia_new" ]; then
        XORG="nvidia";
elif [ "$MODULE" = "fglrx" ]; then
        XORG="fglrx";
fi

if cat /etc/X11/xorg.conf 2>/dev/null | \
  sed -n -e '/^[ \t]*section[ \\t]*"device"/I,/^[ \t]*endsection/I{/^[ \t]*driver[ \t]*/I{s/^[ \t]*driver[ \t]*"*//I;s/"*[ \t]*$//
;p}}' | \
  grep -q -w $XORG; then
        modprobe --ignore-install -Qb $@ $MODULE
else
        echo "Not loading $MODULE module; not used in /etc/X11/xorg.conf" 1>&2
fi
```

Make this file executable :

```
sudo chmod u+x /sbin/lrm-video
```

Check is everything works :

```
sudo modprobe fglrx
```

And then a little :

```
sudo reboot
```

I hope this will work for you !

---

