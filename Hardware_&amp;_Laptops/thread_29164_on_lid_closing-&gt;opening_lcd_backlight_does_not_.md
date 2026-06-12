---
title: "on lid closing-&gt;opening lcd backlight does not turn on again, acer tm225x"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by marty on 2005-04-23
hi,
i have laptop acer travelmate 225X
I'm using Kubuntu (the KDE version..:) for a month. everything works well, i have only one strange problem:
when i close (going out of computer...)  and then open back the LCD lid, the backlight remains in off state. However, if enough of light, i  can see the screen that system is running ok and i could continue my work... ;)
but, you know, the backlight is good on laptop sometimes... :)
there is no way how to force the backlight turn on... Must restart system...
I have similar problem at my WinXP, but to hit a key starts the lcd backlight on... not at Kubuntu...
Hibernation works perfect, sleeping (ACPI S3?) not, but it's known problem on those Acer models running linux's i have read at disscusions...

please, any note from anybody would be great for me... ;)
marty

---

### Post by localzuk on 2005-04-23
I have a similar issue, but to do with it changing terminal as well as turning off the backlight. I type 'ctrl alt f7' to get back to right terminal and it all works ok. Does this work?

---

### Post by vimpagliazzo on 2005-06-13
[QUOTE=localzuk]I have a similar issue, but to do with it changing terminal as well as turning off the backlight. I type 'ctrl alt f7' to get back to right terminal and it all works ok. Does this work?[/QUOTE]
 I'm experiencing the same on a Dell Latitude X1, but switching to terminal (Ctrl+alt+f1) and back to X again (Alt-f7) does not work for me... any idea?

---

### Post by jerome bettis on 2005-06-13
[QUOTE=marty]there is no way how to force the backlight turn on... Must restart system...[/QUOTE]

restarting is a windows thing.  you really shouldn't have to restart linux ever except for a change to the kernel.

you can turn the backlight on with the command vbetool dpms on .

```
#!/bin/bash
#/etc/acpi/lid.sh

. /usr/share/acpi-support/power-funcs
getXuser;

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ] #lid is closed
then
        . /usr/share/acpi-support/screenblank
        echo `fgconsole` > $LIDSTATE
        chvt 12
else  # lid is open
        vbetool dpms on #turn the backlight on
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
                su - $user -c "xscreensaver-command -unthrottle"
        fi
        chvt `cat $LIDSTATE`
        su - $user -c "xscreensaver-command -deactivate"
fi

[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

that's worked for me a while back when i had the same issue.  i've blanked the script because i don't want anything to happen when i close the lid (i close it and use my big monitor a lot)

not sure if that will work for you, give it a try and let us know how it goes.

---

### Post by Franko30 on 2005-07-28
For me this only happens (on a Dell Latitude X1) when resuming from Standby.

Changing the brightness with Fn+arrow-up (or down) turns the backlight on.

None of the other tips here worked, neither did editing the /etc/default/acpi-support (VBE-State, POST_VIDEO or USE_DPMS).

Cheers

Franko30

---

### Post by az_human on 2006-12-29
Holy poo-poo head!  I was SO frustrated with my laptop.... I had been playing a game (using kxmame) and was accidentally hitting the FN + left/right arrow keys and dimmed my backlight considerably.  I was SO PISSED because last night I was also using kxmame, but on my desktop, and my monitor went kaput altogether.  I figured kxmame was doing something to destroy my lcd screens... but whew!  My laptop screen is back!  Yay!

Yes I know this is in response to an old post but hey, it solved my problem and I am now expressing my glee  :)

Thanks guys.

---

### Post by starlily on 2007-02-15
I had this problem too, I tried a lot of things, but the fix was really simple.

/etc/acpi/lid.sh is *BROKEN*

I replaced it with a much shorter version I found here on the forums, and all is well.

There are MANY posts about lid.sh being broken in a lot of ways in Edgy. Will someone who knows how please put a fixed version in the release updates? This was one of the very few things that made my install less than perfect.

Lily

---

