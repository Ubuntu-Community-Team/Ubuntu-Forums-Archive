---
title: "[SOLVED] BIG BOOT PROBLEM - busybox"
date: 2008-05-10
forum: Hardware
---

### Post by damis648 on 2008-05-10
Ok, i will get straight to the point. I try to boot up ubuntu, and the progress bar bounces for it seems like ages and at some point it throws me into a busybox prompt like shown below.
```
BusyBux 1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I was very frustrated, so i decided to try booting without "quiet splash" and the last couple things that showed up in the output are as followed:
```
usbcore: registered new interface driver usbhid
  /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
done.
check root= bootarg cat /proc/cmdline
  or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/### does not exist. Dropping to a shell!
```
And now gives me the busybox prompt. By the way so you know, the "###" found in the code above is just some letter and number jibber-jabber that i did not think was necessary. If it is, i will fetch it.

I am really confused!:confused: Could someone help me? Now this is a relatively new install because my old install had the same problem and i couldn't find an answer so i reinstalled. I think i know the source of the problem, but maybe you can help. When i installed ubuntu, i installed it while Windows was hibernated. I used windows every once in a while, but every time i am done, i hibernate because stupid windows takes way too long to boot. I was just using it a while ago, and I had to restart Windows. I restarted, and now ubuntu doesn't work anymore. I think this is the cause of the problem, but i am not sure. I tried re-hibernating but still no dice. Any suggestions please???:cry:

---

### Post by damis648 on 2008-05-10
bump? please i really need help.

---

### Post by damis648 on 2008-05-10
Bump Again

---

### Post by kerry_s on 2008-05-10
its saying it can't find the hard drive with that id.

do you know where it was installed? what partion?

i believe you need to mount the drive, then you need to point it back at the drive you installed in /etc/fstab. don't worry about uuid, just use the old method /dev/hda?.

---

### Post by damis648 on 2008-05-10
Ok, it was /dev/sda2 I am pretty sure. How should i edit /etc/fstab?

---

### Post by kerry_s on 2008-05-11
okay your at busybox, type>
cd /
mount -t auto -o rw /dev/sda2 /cdrom

cd /cdrom

cp /etc/fstab /etc/fstab.bak

vi /etc/fstab
or 
nano /etc/fstab

which ever 1 you know how to use.

change the start of the line with that messed up uuid to /dev/sda2


i hope thats right, haven't had to do a rescue in years.

in case your wondering why mounting to cdrom, cause it's already there, saves a step in creating a folder to mount.

---

### Post by kerry_s on 2008-05-11
wait, i just saw another thread with the same problem. it sounds like there's a problem with the kernel update.
try picking a older kernel from your boot list.

---

### Post by damis648 on 2008-05-11
Well i had not done a kernel upgrade, so i will try your rescue method. Wish me luck ;).

---

### Post by damis648 on 2008-05-11
i just tried what you suggested, but mount kept throwing me error messages that there was an invalid argument, no matter what i tried. I finally gave up with that and whipped out my Ubuntu 8.04 liveCD and booted that up. I mounted my drive and edited the fstab this way. I changed the UUID in the fstab to /dev/sda2 and rebooted back into ubuntu without the quiet and splash options and i still get the same error messages. Any suggestions?

---

### Post by damis648 on 2008-05-11
Ah I fixed it!! Thanks to this thread: [http://www.linuxquestions.org/questions/ubuntu-63/dropped-into-busybox-shell-after-modifying-install-597774/](http://www.linuxquestions.org/questions/ubuntu-63/dropped-into-busybox-shell-after-modifying-install-597774/) i figured out all i had to do what change the UUID in the boot parameters into /dev/sda2 adnd its all good now! Thanks for the help though!

---

### Post by kerry_s on 2008-05-11
> **damis648 said:**
> Ah I fixed it!! Thanks to this thread: [http://www.linuxquestions.org/questions/ubuntu-63/dropped-into-busybox-shell-after-modifying-install-597774/](http://www.linuxquestions.org/questions/ubuntu-63/dropped-into-busybox-shell-after-modifying-install-597774/) i figured out all i had to do what change the UUID in the boot parameters into /dev/sda2 adnd its all good now! Thanks for the help though!

golly gee, i forgot all about that. in debian don't get problems like that. still uses the simple method(pic)

---

