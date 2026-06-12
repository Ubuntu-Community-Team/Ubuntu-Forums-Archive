---
title: "[SOLVED] Converting server to desktop"
date: 2008-10-10
forum: General Help
---

### Post by hivoltage on 2008-10-10
I'm trying to convert an Ultra 10 running Ubuntu Server 7.04 to a desktop environment.  I tried "apt-get install ubuntu-desktop", but no luck.  Could my site config file be out of whack, or is there no way to get to 'desktop' from 'server'?  TIA.

---

### Post by Sef on 2008-10-11
> "apt-get install ubuntu-desktop"

1) Did you put sudo in front of apt-get?

2) What happens when you try and upgrade?

3) Update the repositories before upgrading - ```
sudo apt-get update
```

---

### Post by hivoltage on 2008-10-14
Thanks for the advice.  The problem turned out to be a "can't get there from here" type.  I couldn't do your recommended 'update' until I brought the system up to 7.10. Thennnnnn the 'ubuntu-desktop' command worked.  Once again, thank you for your time.

---

