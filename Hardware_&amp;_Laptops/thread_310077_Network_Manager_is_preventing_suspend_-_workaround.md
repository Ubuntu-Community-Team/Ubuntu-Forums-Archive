---
title: "Network Manager is preventing suspend - workaround"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by Leppiz on 2006-11-30
I'd been really frustrated because my HP/Compaq nx6110 laptop didn't suspend or hibernate any more. Today I started to really dig deeper.

I found out in the logs, that some processes didn't want to die when going to suspend. Quite luckily I guessed first, that Network Manager might be causing problems. I killed it, and whoa, my laptop finally agreed to suspend and hibernate. After resuming I started Network Manager again and my wireless was quickly fully functional.

After digging the issue deeper, I found out that **Network Manager has to be killed** with a -KILL switch (in Finnish: "tappaa talossa ja puutarhassa"), when doing it from a script.

I wrote 2 scripts to automate this workaround:

/etc/acpi/suspend.d/01-fix-stop-NetworkManager.sh
```
#!/bin/sh

# force Network Manager to shutdown, seems to be a tough guy
killall -KILL NetworkManager

```

/etc/acpi/resume.d/99-fix-resume-NetworkManager.sh
```

#!/bin/sh

# bring Network Manager up again
NetworkManager

```

You have to give the scripts execute permissions with running chmod +x on both of them.

---

