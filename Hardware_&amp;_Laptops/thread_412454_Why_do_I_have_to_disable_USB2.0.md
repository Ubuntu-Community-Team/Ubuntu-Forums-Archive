---
title: "Why do I have to disable USB2.0?"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by mushr00m on 2007-04-18
I recently installed Feisty on my parents broken HP; they were happy to get their digital photos off and my Dad still (mostly) has Picasa and Yahoo Games<--- (He's looking forward to a Native version HINT, HINT google and yahoo, I may be poor but my parents have money!).

They've got 4 big icons on the desktop and thats all they needed.  That and my mom needs this mp3 player, a mpio FY500,  to pretty much just work or she won't use it.

OK, we plug it in an instead of plug-and-play we got plug-and-crash. On their computer it crashes the whole USB bus, which just toasts their USB keyboard+mouse, on mine I at least get logs to sift through(thanks ps2!).

**My personal solution**, after reading  a million threads about completely different USB peripherals causing the same sort of problems, was to apply that to a general fix in my case. A quick:
```
sudo modprobe -r ehci_hcd
``` and the fall back modules do the dirty work.

But this terminal stuff ain't gonna fly with ma. Here is the down and dirty script for her:
```

#!/bin/bash
#because we love GUIs
gksudo "modprobe -r ehci_hcd"

if [ -z `lsmod |grep ehci`]
then
# I'm gonna cheat and use dialog. I wonder if she'll need more than 10 seconds... those USB's can be tricky!
dialog --pause "Plug-In Non-Compliant Device" 200 300 10
# what is the benefit of exec vs. calling the program? I can never remember.
exec amarokapp
exit 0
fi
dialog --infobox "failed" 200 300
exit 1

```

the closer:
```

#!/bin/bash
#Amarok calls this script when you Disconnect
if [ -e `lsmod |grep ehci`]  # I want a check for FY500 in fstab too, but I'm lazy and tired.
then
gksudo "umount /media/MPIO-FY500" && gksudo "modprobe -aq ehci_hcd"
exit 0
fi
dialog --infobox "failed" 200 300
exit 1


```

Why is ehci_hcd trying to wrangle what is obviously a lesser beast?

---

### Post by mushr00m on 2007-04-18
Bump, Is there a reason behind the solution ?

---

