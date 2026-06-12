---
title: "ipod mounts read only"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by crmccreary on 2006-06-05
I've upgraded from Breezy to Dapper. Extremely pleased. Just this one problem so far. Plugging in my 3rd gen ipod yields the expected icon. It mounts but it is mounted read only! How to I change the automount to mount it rw?

---

### Post by aysiu on 2006-06-05
Can you plug your iPod in and then post the output of these terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by darteaga on 2006-06-06
[QUOTE=crmccreary]I've upgraded from Breezy to Dapper. Extremely pleased. Just this one problem so far. Plugging in my 3rd gen ipod yields the expected icon. It mounts but it is mounted read only! How to I change the automount to mount it rw?[/QUOTE]

I have exactly the same problem. See my post in another forum: [http://www.ubuntuforums.org/showthread.php?t=186878]("http://www.ubuntuforums.org/showthread.php?t=186878")

---

### Post by crmccreary on 2006-06-06
I will do so as soon as my family returns from the UK with the laptop.

---

### Post by crmccreary on 2006-06-06
[QUOTE=darteaga]I have exactly the same problem. See my post in another forum: [http://www.ubuntuforums.org/showthread.php?t=186878]("http://www.ubuntuforums.org/showthread.php?t=186878")[/QUOTE]
Yes, I read your post but unfortunately there were no replies. When the laptop returns, I will be educating myself on automount, udevs ([http://ubuntuforums.org/showthread.php?t=168221&highlight=automount+read](http://ubuntuforums.org/showthread.php?t=168221&highlight=automount+read)) , etc. to try and resolve this problem. This could be a showstopper for my girls. They do not have the patience nor the skills just yet to  solve it themselves.

---

### Post by martin_xxxz on 2006-06-21
I have this problem with read only ipod too. It happened when i upgraded to Ubuntu 6.06. It is really strange because when i plug my ipod in it's not write protected. But after a short while it suddenly changes to read only. Any idea ? :confused:

---

### Post by martin_xxxz on 2006-06-23
So I figured out that my problem was not in upgrading to 6.06. I did chkdsk /f (in windows) to check errors on my ipod. It did some repairs and now ipod in ubuntu is fine again (i can mount it read/write). In my opinion what happened in my case was this: as soon as ubuntu detected inconsistency on my ipod read only access was forced.

---

### Post by corefile on 2006-07-02
[QUOTE=martin_xxxz]So I figured out that my problem was not in upgrading to 6.06. I did chkdsk /f (in windows) to check errors on my ipod. It did some repairs and now ipod in ubuntu is fine again (i can mount it read/write). In my opinion what happened in my case was this: as soon as ubuntu detected inconsistency on my ipod read only access was forced.[/QUOTE]


So for those of us without PC's running windows what is the solution? I've seen this answer a couple times now, connect to PC and restore or do this or that. I don't run windows. How do I get my Ipod so I can write to it?

---

### Post by MarcMaserati on 2006-07-18
First

```
cat /etc/mtab
```

to find out where the ipod is mounted (it'll be the line with /media/ipod, cat that when the iPod is plugged in and automounted, obviously).  Once you have the /dev, alls you do is

```
dosfsck /dev/sdb2 -a
```

Where /dev/sdb2 is your ipod's device.

---

### Post by st14n on 2006-07-23
> **MarcMaserati said:**
> First

```
cat /etc/mtab
```

to find out where the ipod is mounted (it'll be the line with /media/ipod, cat that when the iPod is plugged in and automounted, obviously).  Once you have the /dev, alls you do is

```
dosfsck /dev/sdb2 -a
```

Where /dev/sdb2 is your ipod's device.

Thanks, that did the trick!

---

### Post by quickblaine on 2006-08-15
> **MarcMaserati said:**
> First

```
cat /etc/mtab
```

to find out where the ipod is mounted (it'll be the line with /media/ipod, cat that when the iPod is plugged in and automounted, obviously).  Once you have the /dev, alls you do is

```
dosfsck /dev/sdb2 -a
```

Where /dev/sdb2 is your ipod's device.

So i did that, and now my ipod shows the folder icon and "www.apple.com/support/ipod"!!! what now?

---

### Post by hanzomon4 on 2006-08-16
If you have windows or a mac update the ipod firmware

---

### Post by quickblaine on 2006-08-16
> **hanzomon4 said:**
> If you have windows or a mac update the ipod firmware

yeah, just done that. amaroK still not able to succesfully copy songs though

---

### Post by hanzomon4 on 2006-08-16
I have never used amork, but prehaps amrok my be looking at the wrong drive.
See if you can set what partition/mount-point amrok looks to for the ipod

---

