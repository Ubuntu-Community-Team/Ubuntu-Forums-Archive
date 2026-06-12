---
title: "[SOLVED] failure of ubuntu 8.10 upgrade"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by wclarowe on 2008-12-12
After much tribulation I finally got my system to accept upgrade to 8.10.  After boot I received message that nvidia driver version 173 was not enabled.  i clicked to enable it.  Now system hangs on boot then boots to a white on black screen which gives me access to the command prompt.  I don't have clue what to do.  Any help will be appreciated.  Feel free to comment on my IT deficiencies, I'm already aware of that. I could format and reinstall but don't want to lose data.

---

### Post by toolfan2k4 on 2008-12-12
> **wclarowe said:**
> After much tribulation I finally got my system to accept upgrade to 8.10.  After boot I received message that nvidia driver version 173 was not enabled.  i clicked to enable it.  Now system hangs on boot then boots to a white on black screen which gives me access to the command prompt.  I don't have clue what to do.  Any help will be appreciated.  Feel free to comment on my IT deficiencies, I'm already aware of that. I could format and reinstall but don't want to lose data.


This is not a solution, but it is quite easy to backup ubuntu. Simply use the copy command as either root or with sudo before it. Use the code below just replace source and destination.file with the source and destination on your computer.

```
cp /source directory.file /destination.file or sudo cp /source directory.file /destination.file
```

---

