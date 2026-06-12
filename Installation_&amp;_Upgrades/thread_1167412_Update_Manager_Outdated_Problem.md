---
title: "Update Manager Outdated Problem"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by X96 Design on 2009-05-22
Hi all,
> 
I noticed a "warning" icon in my status bar, saying that the update manager was outdated, so I tried to update it by clicking "Check", but I got this:
[quote]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Some index files failed to download, they have been ignored, or old ones used instead.Is this something on my side, or are other people experiencing this?
[/quote]

**I just figured it out, the url says edgy, and when changed to INTREPID, it works... How do I change this in Update Manager?**

Thanks
X96

---

### Post by cariboo on 2009-05-22
Edgy eol'd in April, it may be worth your while to press Alt-F2 and type:

```
sudo update-manager -d
```

This will allow you to update to the next version.

---

### Post by X96 Design on 2009-05-23
I run it, and it just opens update manager, no upgrading or anything happening... :confused:

What's supposed to happen?

Screenshot: [http://x96webdesign.uuuq.com/xtra/update-manager.png](http://x96webdesign.uuuq.com/xtra/update-manager.png)

Thanks
X

---

### Post by mcduck on 2009-05-23
> **X96 Design said:**
> I run it, and it just opens update manager, no upgrading or anything happening... :confused:

What's supposed to happen?

Screenshot: [http://x96webdesign.uuuq.com/xtra/update-manager.png](http://x96webdesign.uuuq.com/xtra/update-manager.png)

Thanks
X
Notice the part on the top with text "New distribution release "9.04" is available" and "Upgrade"-button.. ;)

---

### Post by X96 Design on 2009-05-23
Thanks, but no thanks :)

I still want to keep 8.10, I already tried 9.04, and a bunch of stuff didn't work, so I reinstalled 8.10. Is there a way I can manually edit a config file or something? I'm comfortable editing sys files and using terminal...

Thanks,
X96

---

### Post by X96 Design on 2009-05-24
I fixed the issue- All O had to do was right click on the icon, click properties, and switch the distro from "edgy" to "intrepid", and it worked!

// X \\

---

