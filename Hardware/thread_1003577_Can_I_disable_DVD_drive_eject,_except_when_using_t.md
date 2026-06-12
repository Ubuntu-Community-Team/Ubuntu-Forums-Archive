---
title: "Can I disable DVD drive eject, except when using the button?"
date: 2008-12-06
forum: Hardware
---

### Post by Sirron on 2008-12-06
I have a case with a door covering the DVD drives, and when using windows I had a nasty surprise when it oh-so-helpfully ejected the DVD drive's tray without giving me enough warning to open the door. The drive never worked again. Two broken drives later, I ended up spending £10 on software to inhibit windows from ejecting the tray, because it turns out that windows doesn't actually have a setting for that.

I've never had the problem on ubuntu since I actually very rarely need to use the DVD drive on here, but I don't want to take any chances.

I read this on another site:

```
#sudo echo "dev.cdrom.lock=1" >> /etc/sysctl.conf
```

but I assume it would completely lock the drive. Is there a way for me to stop the drive from being able to eject unless I press the button on it?

If not, would I be able to make a little app to edit that file and lock or unlock the drive when I need to - does it require a system restart to take effect?

Thanks

---

