---
title: "CDRom help? D:"
date: 2009-10-12
forum: Hardware
---

### Post by aBv on 2009-10-12
Alright, I'm am entirely new  to the whole Linux thing. I am running Xubuntu 9.04 (I think) and I am having problems with my cdrom. I cannot seem to get it to read cds. I have searched a bit and have not found a successful answer. Can anyone help me with this problem?

---

### Post by prshah on 2009-10-13
> **aBv said:**
> Alright, I'm am entirely new  to the whole Linux thing. I am running Xubuntu 9.04 (I think) and I am having problems with my cdrom. I cannot seem to get it to read cds. I have searched a bit and have not found a successful answer. Can anyone help me with this problem?

(X)Ubuntu handles CDs differently from Windows. In Ubuntu (Linux) all CDs/DVDs are mounted to a directory in the filesystem, typically under /media. For example, if your CD is called MYCD, when inserted, it will be available under /media/MYCD.

It will also appear in Thunar (Xubuntu's file manager) which is accessible from Applications-Accessories-Thunar file manager (i think?)

---

### Post by aBv on 2009-10-13
I've gone through Thunar File Manager and looked at the contents of the CD. However, there is nothing in any of the files. I do not believe that my disk drive is reading it. Any suggestions?

---

### Post by nzadLithium on 2009-10-13
In the file manager thunar, when you insert a cd does a cd drive icon appear with the name of your cd in the left hand pane? The one that shows your home directory, the trash can, desktop etc. The cd drive icon is a box with half a cd poking out.

---

### Post by aBv on 2009-10-14
No, it does not.

---

### Post by prshah on 2009-10-14
> **aBv said:**
> I do not believe that my disk drive is reading it. Any suggestions?

Remove the CD. Open a terminal (Applications-Accessories-Terminal). In that give the command```
tail -f /var/log/messages
``` Now pop the CD into the drive. You should have some new output appear in the terminal. Post back this output. You can close the terminal once you have copy/pasted the output. (Copy, Paste, THEN close the terminal; use the mouse, if you want to use keyboard, you need to use Ctrl+SHIFT+c to copy selected text from the terminal).

Also, from a fresh terminal, post the output of the command ```
mount
```

---

### Post by aBv on 2009-10-14
Output for var/log/messages:

monster@monster-laptop:~/Desktop$ tail -f /var/log/messages
Oct 13 23:10:08 monster-laptop -- MARK --
Oct 13 23:30:08 monster-laptop -- MARK --
Oct 13 23:50:08 monster-laptop -- MARK --
Oct 14 00:10:08 monster-laptop -- MARK --
Oct 14 00:30:08 monster-laptop -- MARK --
Oct 14 00:50:08 monster-laptop -- MARK --
Oct 14 01:10:08 monster-laptop -- MARK --
Oct 14 01:30:09 monster-laptop -- MARK --
Oct 14 01:50:09 monster-laptop -- MARK --
Oct 14 02:10:09 monster-laptop -- MARK --
Oct 14 02:11:27 monster-laptop kernel: [528100.917313] __ratelimit: 30 callbacks suppressed



Output for mount:

monster@monster-laptop:~/Desktop$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
tmpfs on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by nzadLithium on 2009-10-14
stick something in the drive then post:

dmesg | tail

---

### Post by aBv on 2009-10-14
monster@monster-laptop:~/Desktop$ dmesg | tail
[570817.405834] wlan0: associate with AP 00:1f:33:d1:f2:1f
[570817.408627] wlan0: RX ReassocResp from 00:1f:33:d1:f2:1f (capab=0x411 status=0 aid=2)
[570817.408634] wlan0: associated
[579190.754512] end_request: I/O error, dev sr0, sector 0
[579190.754525] Buffer I/O error on device sr0, logical block 0
[579190.754536] Buffer I/O error on device sr0, logical block 1
[579190.754543] Buffer I/O error on device sr0, logical block 2
[579190.754550] Buffer I/O error on device sr0, logical block 3
[579190.758364] end_request: I/O error, dev sr0, sector 0
[579190.758372] Buffer I/O error on device sr0, logical block 0

---

### Post by nzadLithium on 2009-10-15
ok so heres your problem:
end_request: I/O error, dev sr0, sector 0

With that error, either your cd is damaged, the kernel driver is malfunctioning or your cd-rom drive is damaged.

First thing is try another cd, if that works its the cd.
Second you can try booting xubuntu with the parameter 'all_generic_ide' which if its a kernel driver issue should hopefully be a temporary solution. To do that when grub comes up hit e on your boot line and then add that text to then end.

Are you dual booting with another operating system? could you confirm that the cd drive works with any other one?

---

### Post by aBv on 2009-10-16
I am not dual booting unfortunately. I installed Linux from a CD if that counts for anything. I'll try your fix though.

---

