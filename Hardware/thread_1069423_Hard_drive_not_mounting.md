---
title: "Hard drive not mounting"
date: 2009-02-14
forum: Hardware
---

### Post by nkhlgeorge on 2009-02-14
Hey i recently tried to install XP SP3 on my computer, but since it failed half way through i decided to install Ubuntu 8.10 on my PC, now the problem is that none of my other hard drives are opening up. ist gives an error saying cannot mount volume. 
I get the followwing errors-


1.   DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.



2.  $log file indicates unclean shutdown9o,0) failed to mount '/ dev/sda7':operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have windows then disconnect the external devices by clicking safely remove Hardware icon in the windows taskbar then shutdown windows cleanly. choice 2: if you dont have windows then you can use the force option for your won responsibility For example type on the command line: mount-t-ntfs-3g/dev/sda7/media/docs and program files-o force   or add the option to the relavent row in the etc/fstab file:    /dev/sda7/media/docs and program files ntfs-3g force 0 0



plzz help out because all my files are in this drive. 

thnxx in advance

---

### Post by lykwydchykyn on 2009-02-14
If the windows partition is /dev/sda7 (looks like it is from the error message), try this command:

```

ntfsfix /dev/sda7

```

Then try to mount it.

If that fails, you may have a bad spot on the drive.  Try scanning sda with badblocks:
```

badblocks -v /dev/sda

```

---

### Post by nkhlgeorge on 2009-02-14
> **lykwydchykyn said:**
> If the windows partition is /dev/sda7 (looks like it is from the error message), try this command:

```

ntfsfix /dev/sda7

```

Then try to mount it.

If that fails, you may have a bad spot on the drive.  Try scanning sda with badblocks:
```

badblocks -v /dev/sda

```

ok thnxx for ur help but im a total novice at this where am i to write these commands??? and how??? i know its a rilly dumb question.

---

### Post by lykwydchykyn on 2009-02-14
> **nkhlgeorge said:**
> ok thnxx for ur help but im a total novice at this where am i to write these commands??? and how??? i know its a rilly dumb question.

Open up a terminal.  I don't know the GNOME menu structure, so if you can't find it just hit alt-f2 and type "gnome-terminal".  

I forgot to mention you need to put "sudo" on the front of those commands, so it would be:
```

sudo ntfsfix /dev/sda7
sudo badblocks -v /dev/sda

```

---

### Post by nkhlgeorge on 2009-02-14
nope didnt work it says command not found.

---

### Post by trikster_x on 2009-02-14
```
sudo mount -o force /dev/sda7 /mnt
```
This will force mount the drive so you can at least get what you want off of it.  Type this into the terminal like the rest of the commands.

---

### Post by nkhlgeorge on 2009-02-15
hey thnxx for all ur help guyz, but i re installed ubuntu as well as xp it works fine now, but im having another problem, my internet connection has stopped working on xp, but continues to work on ubuntu, even though bith the OS's show as connected

---

