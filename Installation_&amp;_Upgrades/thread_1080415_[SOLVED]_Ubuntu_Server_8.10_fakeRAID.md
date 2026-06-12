---
title: "[SOLVED] Ubuntu Server 8.10 fakeRAID"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by bancek on 2009-02-25
This solution works for my HP Proliant ML110 G5 E2160.

If you already tried this [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto") try my solution.

When you finish normal Ubuntu Server 8.10 installation, when it asks you to remove CD, switch to console (alt + f2).

You must chroot into your new installation.
```
chroot /target /bin/bash
mount -t proc proc /proc
mount -t sysfs sysfs /sys
```
Than go to directory /usr/share/initramfs-tools/scripts
```
cd /usr/share/initramfs-tools/scripts
```
Edit file local with your favourite file editor (nano in my case)
```
nano local
```
Find function root_missing() and insert this line into it
```
dmraid -ay > /dev/null
```
So it looks like this
```

root_missing()
{
      dmraid -ay > /dev/null
      ROOT="${1}"
      [ ! -e "{ROOT}" ] || ! $(get_fstype "{ROOT}" >/dev/null) || ! /sbin/udevadm settle
}

```
Save and exit your editor. Then you must update initramfs
```
update-initramfs -u
```

Now you can reboot.

I hope this helped you.

---

### Post by touficjohn on 2009-05-25
Thank you! :P :P
I've been trying to fix this for nearly 8hours!

Edit:
This works perfectly until you do apt-get upgrade...
Its broken again... *sigh*

Edit2:
Re-editing the local file and re-updating initramfs fixes it.

---

