---
title: "Multiple keyboards with multiple layouts and udev/xinput"
date: 2011-10-20
forum: Hardware
---

### Post by keyboardguy on 2011-10-20
Hi All,

I have two keyboards. My main one, set to the nl layout and my secondary USB keyboard, which I need set to the us layout.

Setting the secondary keyboard to us works fine with this command:
```
/usr/bin/setxkbmap -device $ID us
```Where $ID is the keyboard ID as per xinput list.

I am now trying to get this to run everytime I plug the keyboard in, using udev.

In /etc/udev/rules.d/external.rules I have this:
```

ACTION=="add", SUBSYSTEM=="input", ATTRS{idVendor}=="0112", ATTRS{idProduct}=="0065", RUN+="/usr/local/external.sh"

```external.sh runs fine when I plug the keyboard in. external.sh is:
```

#!/bin/bash
echo "Starting kbmap mod" >> /var/log/external.log;
DISP=":0.0";
XAUTH="/var/run/gdm/auth-for-myuser-4y8yFp/database";


DISPLAY=$DISP XAUTHORITY=$XAUTH /usr/bin/xinput list >> /var/log/external.log;

DISPLAY=$DISP XAUTHORITY=$XAUTH /usr/bin/xinput list | grep "USB Keyboard" | awk -Fid= '{print $2}' | awk -F\\\t '{print $1}' >> /var/log/external.log;
echo "ID="$ID >> /var/log/external.log;

if [ ! -z "$ID" ];
  then
    /usr/bin/setxkbmap -device $ID us;
    echo "Set device kb map" >> /var/log/external.log;
  fi

echo "Done" >> /var/log/external.log;
```This is a debug line:
```
DISPLAY=$DISP XAUTHORITY=$XAUTH /usr/bin/xinput list >> /var/log/external.log;
```The script works fine when run from the command prompt but not when called from udev. The problem is that "xinput list" does not show the plugged in keyboard until after the script is done. If I add a sleep command, running "xinput list" from the command prompt also does not show the external keyboard until the script completes.

The steps seem to be:
- Insert USB keyboard
- udev detects it
- udev runs script during which time "xinput list" does not show inserted USB keyboard.
- script completes
- udev does something else
- USB keyboard appears in "xinput list"

How can I make udev run the script after the "udev does something else" step? If that makes sense!

Thanks!

---

### Post by rizumu on 2011-10-25
I got to the same exact point today in trying to set up two keyboards with udev, setxkbmap, and xinput --list

I found a way to work around this, though its a little hacky. 

I have two files ~/bin/kbd and ~/bin/kbd_udev

All that the `~/bin/kbd_udev` script contains is

```

#!/bin/bash
/home/rizumu/bin/kbd &

```And you'll notice that all it does is call `~/bin/kbd' in the background. First we sleep for a second, so that udev completes (the magic step). Then we have to set some variables and export them so setxkbmap can do its work. I've set DISPLAY, XAUTHORITY, HOME.

```

#!/bin/bash
sleep 1
DISPLAY=":0.0"
HOME=/home/rizumu/
XAUTHORITY=$HOME/.Xauthority
export DISPLAY XAUTHORITY HOME
daskb_id=`xinput -list | grep -i 'daskeyboard' | grep -o id=[0-9]. | grep -o [0-9]. | head -1`

 xset r rate 200 30
setxkbmap -option ctrl:nocaps
if [ "${daskb_id}" ]; then
    setxkbmap -device "${daskb_id}" -option altwin:swap_lalt_lwin
fi

```

---

### Post by keyboardguy on 2011-10-26
Hey rizumu,

Thanks for the message, that is a great idea! I guess you could even replace the sleep command with a loop checking to see if the keyboard has appeared.

Interesting that this is the way udev works, unless I am doing something wrong I would expect the script to be called right at the last moment.

I will give your suggestion a try, thanks again.

---

