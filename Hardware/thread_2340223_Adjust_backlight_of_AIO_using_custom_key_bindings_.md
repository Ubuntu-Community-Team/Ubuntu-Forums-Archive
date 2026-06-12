---
title: "Adjust backlight of AIO using custom key bindings in openbox &amp; xmonad"
date: 2016-10-16
forum: Hardware
---

### Post by ckrzen on 2016-10-16
For those of us with video hardware _NOT_ supported by ' xbacklight '(Radeon, etc.) or other such tools, I have found the following solution when using any window manager(Unity included) on an AIO(All-In-One) type computer which usually lack dedicated backlight controls:


Reference system:  Lenovo ideacentre AIO 300-22ACL

OS:  Ubuntu 16.10(4.8.0-22-generic #24-Ubuntu SMP Sat Oct 8 09:15:00 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux)

WM:  Openbox(3.6.1-1ubuntu2)


**1. Create control script:**

```
[INDENT]$ sudo vi /usr/local/bin/sysbacklight[/INDENT]

```

**with**

```
[INDENT]#!/bin/bash

# backlight brightness controls. use freely
# and adjust sysfs directory to your backlight type. 
# $author Brice Burgess @iceburg

# modified by Chris Rainey for a Lenovo ideacentre AIO 300-22ACL
# running openbox on Ubuntu


sysfs="/sys/class/backlight/radeon_bl0"
max=`cat ${sysfs}/max_brightness`
level=`cat ${sysfs}/brightness`


usage()
{
script=${0##*/}
echo
echo "Invalid usage of ${script}!"
echo "  $1"
echo "----------------"
echo "$script up     : increases brightness"
echo "$script down   : decreases brightness"
echo "$script set #  : sets brightness to # (integer)"
echo "----------------"
echo


exit 1
}

set_brightness()
{

level=$1

if [ $level -lt 1 ] ; then
 level=1
elif [ $level -gt $max ] ; then
 level=$max
fi
 
echo $level > $sysfs/brightness 
}

case "$1" in
  up)
    let "level+=26"
    set_brightness $level 
    ;;
  down)
    let "level-=26"
    set_brightness $level 
    ;;
  set)
    if [[ ! $2 =~ ^[[:digit:]]+$ ]]; then
     usage "second argument must be an integer"
    fi

    set_brightness $2
    ;;
  *)
    usage "invalid argument"
esac[/INDENT]

```


[B]2. Set permissions on script:
[/B]
```
[INDENT]$ sudo chmod 755 /usr/local/bin/sysbacklight[/INDENT]

```


[B]3. Create sudo override for NOPASSWD on script, above:
[/B]
```
[INDENT]$ sudo visudo -f /etc/sudoers.d/myOverrides[/INDENT]

```

**with**

```
[INDENT]%sudo    ALL=NOPASSWD:/usr/local/bin/sysbacklight[/INDENT]

```


[B]4. Edit your window manager key bindings file to call your new script:
[/B]
```
[INDENT]$ vi .config/openbox/rc.xml[/INDENT]

```

**with**

```
... <snip>

    <keybind key="W-Up">
      <action name="Execute">
        <command>sudo sysbacklight up</command>
      </action>
    </keybind>
    <keybind key="W-Down">
      <action name="Execute">
        <command>sudo sysbacklight down</command>
      </action>
    </keybind>

<snip> ...

```


[B]5. Reload your window manager config file and enjoy!
[/B]


SOURCES:

a. [https://gist.github.com/briceburg/81d2c8d95a7cf4f61c0a](https://gist.github.com/briceburg/81d2c8d95a7cf4f61c0a)

b. [http://askubuntu.com/a/504666/443610](http://askubuntu.com/a/504666/443610)

---

