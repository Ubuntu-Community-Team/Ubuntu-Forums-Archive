---
title: "Reinstall Ubuntu"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by Gujs on 2006-01-05
Hello,

I have ubuntu server installed for internet routing purposes. Today when i came home from work my server didn't work. It had a lot of corupted sectors. I run fsck and fix this, but now it has a lot of corrupted files.

Can i reinstall these file whithout reformating and lossing all of my scripts.

Thanks

---

### Post by az on 2006-01-05
If you can find what files are corrupted, you can reinstall those packages.


sudo apt-get install --reinstall ssh

You can find what packages a file belongs to by using the
packages.ubuntu.com page.

---

