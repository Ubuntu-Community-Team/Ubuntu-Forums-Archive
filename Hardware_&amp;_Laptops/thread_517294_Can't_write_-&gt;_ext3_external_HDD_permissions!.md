---
title: "Can't write -&gt; ext3 external HDD permissions!"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by teHIngo on 2007-08-04
I'm having some serious problems concerning my new external HDD. I have already googled for a solution and tried out several commands, however none worked so far. I hope very much that you can help me, you are my last chance :)!

**Summary of the problem: **I have an external hard drive formatted to ext3 and can read write to it via "sudo nautilus", however I can't when logging in just normally. "sudo nautilus" is no solution, however. Now I want to make it possible to write to the drive using a normal user.

I have made screenshots of the relevant Terminal outputs or menus for you. I hope that helps. Firstly of course my fstab file with which I have already tried out some crazy stuff!

[IMG]http://o-r-c.org/Bilder/Errors/fstab.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/properties.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/volume.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/permissions.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/gparted.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/theerror.png[/IMG]


Thank you very much! You rock! :guitar:

---

### Post by teHIngo on 2007-08-04
Pics part 2:

[IMG]http://o-r-c.org/Bilder/Errors/ls_command.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/mount_output.png[/IMG]
[IMG]http://o-r-c.org/Bilder/Errors/fdisk_command.png[/IMG]

---

### Post by taurus on 2007-08-04
Try

```
sudo chown -R ingo:ingo /media/sda1
ls -la /media/sda1
```

---

### Post by teHIngo on 2007-08-04
NO WAY!! It worked! Thank you so much :)!!!

---

### Post by taurus on 2007-08-04
> **teHIngo said:**
> NO WAY!! It worked! Thank you so much :)!!!

Yeah, way.  :)

---

