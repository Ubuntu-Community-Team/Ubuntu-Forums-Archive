---
title: "Brasero ISO Burn Scripting"
date: 2008-11-24
forum: General Help
---

### Post by bkuhns on 2008-11-24
I have a long process of creating an ISO file (takes about 3 hours to create the ISO). I then need to burn it at a slow speed, which takes another 30-45 minutes. I decided it would save me some time if I wrote a simple shell script to burn the ISO as soon as it's ready. I would like to use Brasero because the Nautilus ISO burner refuses to burn the ISO. I can get the ISO burning dialog in Brasero to come up easily enough: "brasero -i /path/to/file.iso", but it only brings up the dialog... it doesn't automatically start burning.

Is this possible with Brasero? Or maybe with another burning app (other than Nautilus') that might bode well with these ISO files? I'd like to just put a DVD-R in the drive, and start the shell script, come back in 3-4 hours and have the copy burned and ready to go.

Thanks in advance! :)

---

### Post by geirha on 2008-11-24
There's growisofs from the [apt://dvd+rw-tools](apt://dvd+rw-tools) package. You can do something like:

```
growisofs -Z /dev/dvd=/path/to/file.iso -speed=1
```
with /dev/dvd being the device node of the cd/dvd recorder. If it's a dvd-video, add -dvd-compat as well. Make sure to read the man-page ```
man growisofs
```

---

