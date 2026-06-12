---
title: "screen brightness ajustment issue"
date: 2013-07-03
forum: Hardware
---

### Post by n3wbvip3r on 2013-07-03
okay, i have a toshiba satilite c675-s7200. my volume 'fn' works, up and down properly. however, my brightness does not, it will go close to all the way high, or low when hitting (fn)+volume keys.. am i missing a setting somewhere? or missing something? this may be the wrong section, i imagined this issue would be a video issue. i'm stumped, its a bit annoying. thanks.

---

### Post by Toz on 2013-07-03
*Moving thread to the **Hardware** section.*

Which version of ubuntu are you using?

What video card(s) do you have? This should help identify them:
```
sudo lspci -vnn | grep -A12 VGA
```

> my volume 'fn' works, up and down properly
.........
my brightness does not, it will go close to all the way high, or low when hitting (fn)+volume keys
^^^Are you saying that the brightness changes when you press the volume keys or did you mean the brightness keys?

I wouldn't mind having a look at your dmesg log file. Post it like this:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

