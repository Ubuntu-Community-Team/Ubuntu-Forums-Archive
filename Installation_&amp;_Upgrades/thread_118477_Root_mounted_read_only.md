---
title: "Root mounted read only"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by Navyblue on 2006-01-17
Hello,

I am trying to move my existing Ubuntu installation to another harddisk. However, after I tar it over the taget partition and boot it. The root partition is mounted read only.

Not sure if it would help, the source partition is EXT3 format on a parallel ATA harddisk, mount option is default. The target partition is REISERFS format on a SATA harddisk, mount option is notail noatime.

Please advice what aother information you would need.

---

### Post by Navyblue on 2006-01-25
Anyone? :)

---

### Post by dcstar on 2006-01-25
[QUOTE=Navyblue]Anyone? :)[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

---

### Post by aysiu on 2006-01-25
Root *should* be read-only.

The only thing that matters is getting your /home directory writable.

```
sudo chown -R navyblue:navyblue /home/navyblue
sudo chmod -R 755 /home/navyblue
```

---

### Post by Navyblue on 2006-01-26
dcstar,

I did according to the link you've provided and the outcome is still the same.

aysiu,

I apologise for not being more clear (no wonder I didn't get any answer). I do not mean write permision for the user. I meant root filesystem is mounted read only, and when it does that the system can't boot itself to a useful state. Many boot processes such as the system log daemon would not be able to start.



So here is my case with a better description:
- I want to move my root partition from hda1 to sda1.
- When I try to boot from sda1, I can't.
- Halfway through the boot process it complaint that the root filesystem is read only, and many boot process failed.
- In my fstab line (as with Ubuntu's default) the root partition comes with the errors=remount-ro. So aparently there is an error in the mounting and thus causing it to mount as read only.

---

### Post by aysiu on 2006-01-26
[QUOTE=Navyblue]In my fstab line (as with Ubuntu's default) the root partition comes with the errors=remount-ro. So aparently there is an error in the mounting and thus causing it to mount as read only.[/QUOTE] I don't know if this helps, but my /etc/fstab line looks like this: ```
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
``` Since you quoted the last part, yours is probably similar, but I just wanted to double-check.

---

### Post by Navyblue on 2006-01-28
Yup... It's exactly thesame except that it was for reiserfs.

---

### Post by GTvulse on 2006-01-28
Navyblue, reiserfs is different to ext3. Remove the errors=remount-ro else, fsck will fail.

---

### Post by Navyblue on 2006-01-28
Dradul,

Thanks so much, you saved me. :)

---

