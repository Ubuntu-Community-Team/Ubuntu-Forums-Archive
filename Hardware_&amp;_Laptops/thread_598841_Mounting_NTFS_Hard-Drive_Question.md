---
title: "Mounting NTFS Hard-Drive Question"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Karant on 2007-10-31
Hi there! I have a very simple question to ask, however I have been confused over how my Ubuntu has been operating.

I first installed Ubuntu 7.10 on my Dell 1501on a third partition, coupling up with my 2 other NTFS hard-drives (1 x Windows [labelled SDA1], 1 x Media [labelled SDA5]). On my first boot using Ubuntu the NTFS hard-drives were automatically mounted on my desktop with all priveleges. Now hard-drives are no longer mounted, so I'm wondering how I canmanualy  permanently mount both of them? Thanks!

---

### Post by taurus on 2007-10-31
Let's run this command from a terminal to see if there is a problem with your ntfs partition.

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```
Chances are that it will print out a warning about how you didn't shutdown your windows cleanly and you need to boot your windows up again but this time, shut it down instead of putting it into hibernation.

---

