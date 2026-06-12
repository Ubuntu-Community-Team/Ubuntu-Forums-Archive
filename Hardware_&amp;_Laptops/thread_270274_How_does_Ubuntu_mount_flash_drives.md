---
title: "How does Ubuntu mount flash drives?"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by zergberg on 2006-10-03
The only way I can seem to mount a flash drive is to click on its icon on the desktop or in the file manager. However, I'd rather be able to do it from the command line, but that requires an entry in /etc/fstab. Sadly, adding one and mounting it that way mounts the drive so only root can write to it, and it also disables the other method of mounting.

How can I mount my flash drive from the console and still have write permissions for it?

On another note, is there any way I can give myself 'mount'-ing power so I don't have to 'sudo mount' every time I mount a drive?

---

### Post by po0f on 2006-10-03
zergberg,

When you mount it via the command line, add this as a parameter to mount:
```
$ sudo mount /dev/sda* -o umask=002 /media/stick
```

* I don't know exactly what this is in your situation, just substitute whatever it shows up as.

You know the permissions that show up in the terminal when you do an "ls -l"?  They have a meaning.  rwxrwxrwx would mean everyone has full permission.  The first set of letters (rwx) refer to the owner, the second set to the group, and the third set to everyone else.  (r)ead = 4, (w)rite = 2, and e(x)ecute = 1.  The umask setting assumes full privileges (rwxrwxrwx, or 777), and subtracts the value given, so whatever drive you mounted this way would have permissions 775, or rwxrwxr-x.  And if you are in the group that owns the device, you now have write permission to it.

Make sure you are in the "plugdev" group by checking the output of:
```
$ groups
```

I think that's the group assigned to hot-pluggable things like that.  Might want to look that up.

---

