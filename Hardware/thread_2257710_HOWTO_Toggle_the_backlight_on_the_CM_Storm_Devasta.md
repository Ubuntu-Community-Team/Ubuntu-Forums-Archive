---
title: "HOWTO: Toggle the backlight on the CM Storm Devastator keyboard"
date: 2014-12-21
forum: Hardware
---

### Post by Emblem Parade on 2014-12-21
The CM Storm Devastator is a cheap and very, very good keyboard/mouse combo that works fine with Linux. Operating the backlight does require some extra work, though. (As of Ubuntu 14.04.)

This guide might actually work for other keyboards, too, because it uses general X11 tools. Please respond if it does, so that other people can search-find it!

First, create a script that does the toggling. I called mine "keyboard-toggle-backlight.sh":
```
#!/bin/bash
FLAGS=$(xset -q | awk 'NR==2' | awk '{ print $10 }')
if [ "$FLAGS" = 00000000 ]; then
	xset led on
else
	xset led off
fi

```
To make the script executable:
```
chmod +X keyboard-toggle-backlight.sh
```
Run it to make sure it actually toggles the backlight:
```
./keyboard-toggle-backlight.sh
```
Does it work? Yay! Now, I use Xfce (Xubuntu), so I just assigned the script to the SCROLL LOCK key (to match what the Windows driver does) by using "Settings -> Keyboard -> Application Shortcuts", and using the full path to the script. I'm sure you favorite desktop shell can do somethig similar.

If you want to the backlight on by default when you logon, add this as a session startup command:
```
/usr/bin/xset led on
```

**ALTERNATIVE METHOD**

Now, you have another option: use xmodmap. For me, this did not work well, because it confliced with Xfce and broke my other application shortcuts. But I'm including it here. To test if it works:
```
xmodmap -e 'add mod3 = Scroll_Lock'
```
Did it work? No conflicts with other applications keys? Awesome. You can make this set automatically for your user when you login by creating the file ".Xmodmap" in your home directory, with this content:
```
add mod3 = Scroll_Lock
```

---

### Post by pqwoerituytrueiwoq on 2014-12-22
what keyboard shortcuts did it break
BTW does the backlight work in the bios/grub menu?
i ordered this keyboard/mouse for my dad, hopefully it arrives by tomorrow
it has a 2 year warranty so i figure it can't be that bad as far as the durability goes
*suddenly recalls dad has a hibit of poring coffie in his keyboard, doubt that is covered*

---

### Post by schragge on 2014-12-22
Just some random thoughts on your code.
[LIST]
[*]Your code doesn't use any bash-specific features. Just *#!/bin/sh* would be enough.
[*]You can easily combine a test expression and an action into one awk call like this
```
awk 'NR==2 { print $10 }'
```
[/LIST]
It also could be simplified a bit further
```

#!/bin/sh
xset led $(xset -q | awk '/LED mask:/{print ($NF?"off":"on")}')

```
But I wouldn't recommend doing it like this. It toggles not only backlight, but all LED indicators like NumLock, CapsLock, and ScrollLock as well. Is that really what you want?

I know next to nothing about CM Storm Devastator. Does it repurpose ScrollLock to switch backlight on/off? Then you probably could achieve the same effect just changing that LED's state with
```

xset led named "Scroll Lock"
xset -led named "Scroll Lock"

```

Also, the problem with applying your code to different keyboard models is best described in [xset(1)]("http://manpages.ubuntu.com/manpages/trusty/en/man1/xset.1.html") manpage:> The particular LED values may refer to different LEDs on different hardware.

---

### Post by pqwoerituytrueiwoq on 2014-12-24
i can confirm the backlight IS the scroll Lock LED (good news: standard drivres can toggle the back-light; bad news: it is not a mechanical switch)

i noticed when the scroll lock key is enabled $([FONT=Courier New]xmodmap -e 'add mod3 = Scroll_Lock'[/FONT]) that if you run $([FONT=Courier New]xset led named "Scroll Lock"[/FONT]) the scroll lock can't be turned on/off via the keyboard until you run $([FONT=Courier New]xset -led named "Scroll Lock"[/FONT])

i would say you are probably best off adding [FONT=Courier New]xset led named "Scroll Lock"[/FONT] to [FONT=Courier New]/etc/rc.local[/FONT] and making a keyboard shortcut linked to the scroll lock key to run a toggle script
i assume someone may want to back-light off during media playback
Here is a compete script for replacing the scroll lock feature, set the scroll lock key to call the script, thus giving you a on/off button as well a scripted control of the backlight
```
#!/bin/sh
if [ -z "$1" ];then
    if [ "$(xset -q | sed 's/[0-9][0-9]: /\n/g' | grep 'Scroll Lock' | awk '{print $3}')" = "off" ];then
        xset led named "Scroll Lock"
    else
        xset -led named "Scroll Lock"
    fi
elif [ "$1" = "on" ];then
    xset led named "Scroll Lock"
elif [ "$1" = "off" ];then
    xset -led named "Scroll Lock"
elif [ "$1" = "-q" ];then
    xset -q | sed 's/[0-9][0-9]: /\n/g' | grep 'Scroll Lock' | awk '{print $3}'
else
    me="$(basename $0)"
    echo "Usage:\n\t$me on \t Turn Scroll Lock on"
    echo "\t$me off\t Turn Scroll Lock off"
    echo "\t$me    \t Toggle Scroll Lock"
    echo "\t$me -q \t Print Scroll Lock LED status (on/off)"
fi
```
if you replace the name [FONT=courier new]Scroll Lock[/FONT] with [FONT=courier new]Caps Lock[/FONT] it will toggle caps lock instead, this should work with any XKB indicator (run [FONT=Courier New]xset -q[/FONT] for a list)
* If you indicator name is not 2 words you will need to change the 3 in [FONT=courier new]$3[/FONT] to the number of words +1
* does not seem to be able to set numlock/caps lock
now you can enjoy making the scroll lock led play Morse Code whit your custom script that calls this toggle script

---

### Post by rayfenwindspear on 2015-02-02
Just my 2 cents here, but it didn't work for me exactly the way you described it. On mine, for whatever reason, line 3 of the script needed to look for [COLOR=#000000][FONT=Ubuntu Mono]00000002[/FONT][/COLOR] instead of [COLOR=#000000][FONT=Ubuntu Mono]00000000. I ran this line here to determine what I needed to replace there.
[/FONT][/COLOR]```
xset -q | awk 'NR==2' | awk '{ print $10 }'
```

EDIT
So after reading further down, it seems this was taken care of by other people. They also fixed the issue I had where the original method would set the 10-key to mouse keys mode.
I.E ignore me entirely :)

---

