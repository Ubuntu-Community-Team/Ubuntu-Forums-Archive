---
title: "[SOLVED] Conky bugs my fullscreen firefox"
date: 2008-09-24
forum: General Help
---

### Post by evergreen_p on 2008-09-24
hi, i just discovered conky, i followed [_this beginners guide_]("http://ubuntuforums.org/showthread.php?t=867076"). everything seemed to be working without any big problems.

 but once i added conky it to startup and rebooted firefox now has no minimize, restore or close buttons in the top left corner. in adition firefox now sits ontop of AWN which it didnt before.

it seems weird to me that conky caused this, but it is the only thing i changed between boots

please help

---

### Post by lian1238 on 2008-09-24
Weird. Conky shouldn't affect firefox. Let's kill conky to see if it's really bugging firefox.
```
killall conky
```
Restart firefox and see if it's good again. If it's still the same, try uninstalling conky.

---

### Post by evergreen_p on 2008-09-24
i think you may be conky in startup.

---

### Post by evergreen_p on 2008-09-24
sorry, stuffed up in my last post, killing conky and rebooting firefox does nothing the problem persists. but if i reboot my system without conky in startup then everything goes back to normal. it has too be something to do with conky in startup, as i can even start conky manually oncer Ubuntu is booted and everything is fine.

this is the code i am using to launch conky at startup

```
#!/bin/bash
sleep 20 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/home/evergreen/.conkyrc &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```

---

### Post by lian1238 on 2008-09-24
Why don't you try with just "conky"? Works for me.

---

### Post by evergreen_p on 2008-09-24
ok that fixes it. wow, i feel stupid, so simple. thanks lian

---

