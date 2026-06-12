---
title: "Linux Mint 64 doesn't boot: what's BusyBox?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by jorx on 2009-08-05
In the middle of boot it says 

"mount: mounting /dev to /root/dev failed: No such file or directory
mount: mounting /sys to /root/sys failed: No such file or directory
mount: mounting /proc to /root/proc failed: No such file or directory"

And something about Init missing- and sends me to the 
"BusyBox" which has no shutdown or reboot command- and I'm helpless!

This is pretty strange!

---

### Post by SoftwareExplorer on 2009-08-05
Well, I can answer the busybox part: It's a very minimalist system that is very small. All the Linux routers I've messed with use busybox.

---

### Post by louieb on 2009-08-05
You go to busybox when the kernel can't find the partition holding the root file system (other reasons too) as SoftwareExplorer says it a light shell. 

Anyway looks like your getting busybox because the  kernel can't find the partition holding the root file system.

Grub passes that information to the kernel when it loads.

example
```
kernel    /vmlinuz [COLOR=Red]root=/dev/hda2[/COLOR] ro
``` 
follow [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt file in your next post. (wrap it in code tags)

---

### Post by jorx on 2009-08-08
*SOLVED*.

But barely.
So because I'm running off a USB hard-drive- the hard drive number tends to change from computer to computer. So what I have to do is edit the GRUB flags and instead of hda1/root or something like that- 
I have to replace hda1 with hdb1.

But if I hadn't wrestled with mounting drives earlier- I would have been hopelessly lost!
Fortunately the problem was that simple ;)

I really don't understand the busy box- you can't navigate, (cd, ls, etc.) shutdown, or do anything. I'm clueless as how to troubleshoot within the busy box.

---

### Post by SoftwareExplorer on 2009-08-08
Just a thought:would it not change sda/sdb stuff if you used uuids?

---

