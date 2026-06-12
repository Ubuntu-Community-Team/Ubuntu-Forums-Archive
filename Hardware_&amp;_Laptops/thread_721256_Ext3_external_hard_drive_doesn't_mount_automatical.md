---
title: "Ext3 external hard drive doesn't mount automatically at boot"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by allanlewis on 2008-03-11
I know there are similar threads to this elsewhere, but I haven't yet found one that resolves my specific problem, which is as follows:

I have an external USB hard drive, which I have formatted as Ext3 as I now mostly use Kubuntu as opposed to WinXP, which I mostly use for games and a couple of apps I need. I can mount the drive manually with no problems:
```
sudo mount /dev/sdb1 /media/External
```
...but it won't mount automatically on boot. I've fiddled with my */etc/fstab* a bit but I don't want to do any more in case I mess up my drive. Since the drive is plugged in almost constantly, I assume it's just a matter of an extra line in [i[fstab[/i], but I'm not sure what options I need to give it. The last one I tried was:
```
/dev/sdb1 /media/External ext3 nouser,defaults,utf8,umask=007,gid=46,atime,auto,rw,dev,exec,suid 0 0
```
How far off am I? And do I need to do anything other than editing *fstab*?

---

### Post by scragar on 2008-03-11
why not just try:
```
/dev/sdb1 /media/External auto defaults 0 0
```
that should work for almost any device(some exceptions, but for the most part)

---

