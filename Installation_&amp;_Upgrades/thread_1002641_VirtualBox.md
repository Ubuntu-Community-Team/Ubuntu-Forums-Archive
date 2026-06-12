---
title: "VirtualBox"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by uttaran on 2008-12-05
How can i mount the existing partitions of hard drives of my pc in the virtual system??????Can i write a cd from that virtual system??

---

### Post by Chainz on 2008-12-05
[LIST=1]
[*]First you need to set up a shared folder from normal VBox interface (it just shows which folder from your normal system you want to share).

[*]Then inside guest system just launch below command from the terminal:
```
sudo mount -t vboxsf NewFolder /home/UserName/Desktop/NewFolder
```
[/LIST]

This will mount NewFolder (from your host machine set up in point 1.) into UserName's Desktop/NewFolder
You can of course make a shortcut for this command or even add it to the fstab so it will mount automatically on system start.

I'm not sure but think that you also need to install guest additions

Hope I was not too confusing ;)

---

### Post by Chainz on 2008-12-06
Did it help?

---

