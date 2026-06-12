---
title: "battery issues"
date: 2011-01-24
forum: Hardware
---

### Post by CNUanMAn on 2011-01-24
I just installed Ubuntu Netbook Remix 10.10 on my netbook. It's an Acer Aspire One if that's important. It works like a dream when it's plugged in. When I unplug it though, it lasts for about 10 minutes before it says that the battery is at a critical level and goes into hibernate. When I plug it in before it gets a chance to hibernate, the battery says that it's at about 60%.

Now, I'm a complete Linux newbie and I'm not that well versed in computers in general, but does this sound like an issue with my battery, or something else?

---

### Post by mikewhatever on 2011-01-24
Try the workaround:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
> Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.

Current workaround is to open gconf-editor and browse to:

```
/apps/gnome-power-manager/general
```

And de-select the option use_time_for_policy


---

### Post by Fizzasist on 2011-03-25
I tried the work-around but the option was already de-selected for me....didn't help :(

---

