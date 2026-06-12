---
title: "How to Make Driver Module Parameters Default?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by snowman4839 on 2009-09-22
I just installed kernel 2.6.31 and Madwifi trunk v409x and I FINALLY got my wifi working correctly.

Madwifi uses the Sample algorithm for setting the data rate and, in short, it's an awful algorithm in the current time. That is why the Minstrel algorithm is used now because it works a lot better.

I finally got the Minstrel algorithm to work correctly by shutting down networking and removing the ath_pci module and starting it back up with the ratectl parameter equal to minstrel
"sudo modprobe -r ath_pci"
"sudo modprobe ath_pci ratectl=minstrel"

I'm VERY happy to finally get it working but I need a way to make this the default. I've looked around to try to find the config file that starts the ath_pci module with no luck. I really want to edit the config file that initilizes the ath_pci module so I can add the parameter. Any ideas on how to do that guys? Thanks

---

### Post by sisco311 on 2009-09-22
The config file should be in the /etc/modprobe.d directory.

run
```
grep ath_pci /etc/modprobe.d/*
```
to find the file.

the command should produces an output similar to:
```
/etc/modprobe.d/file-name.conf: options ath_pci
```

edit the file and replace **options ath_pci** with **options ath_pci ratectl=minstrel**.

reboot.

---

### Post by snowman4839 on 2009-09-22
I didn't get a chance to you read your post but I figured it out about 5 minutes after I posted this thread.

Since modprobe will read any file in /etc/modprobe.d that ends in .conf, I made a file called ath_rate.conf and put 1 line in it, "options ath_pci ratectl=minstrel"

If I remember right, modprobe reads through the .conf in /etc/modprobe.d to check and see if any driver have options or blacklists or whatnot. So I just stopped the ath_pci module, "sudo modprobe -r ath_pci", and I started it back up, "sudo modprobe ath_pci", but since it reads though the .conf files in /etc/modprobe.d, it read my options in the /etc/modprobe.d/ath_rate.conf file I made which then started the ath_pci with the Minstrel algorithm.

I tried to spell it out so that everyone would understand what was going on. I hope that this may help someone.

---

