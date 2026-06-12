---
title: "How to delete Spring(Lobby)?"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by Garofoli on 2009-04-10
Hey guys,
For some reason I am quickly losing HD space like no other and I am wondering how to delete spring. I can't find the files if I search for it but it appears in my applications bar. I try to add/remove but it doesn't show up there either. Any ideas? Thanks.:D

---

### Post by cariboo on 2009-04-10
If you installed it using the ppa, you should be able to find it using Synaptic Package Manager. If you installed from source, use:

```
make uninstall
```

in the source directory

Jim

---

### Post by Garofoli on 2009-04-10
I used Synaptic Package Manager. Thank you, I learn something new about Ubuntu every day.

---

### Post by rajder on 2009-05-22
As a complete ubuntu noob, I can add some more details that I found along the way:

First find the History:
System --> Administration --> Synaptic Packet Manager

and then in the File menu you should find "History" (here you should find what packages were installed)

To remove this horrible game ;) use these commands:

sudo apt-get remove springlobby
sudo apt-get autoremove


and don't forget to remove the entry that the installation instructions told you to add in System --> Administration --> Software Sources

---

