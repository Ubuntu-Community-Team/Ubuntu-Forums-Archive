---
title: "Unable to unmount external hard drive"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by ingvald on 2007-05-30
Hey,
i am totally new to Linux and discovered my first problem. When I try to eject or unmount my Maxtor external hard drive from the GUI I get the error message "cannot remove directory"... It does actually sounds like it is unmounted a small second before it is automounted. 

Sofar I have unplugged the cable with the risk of damage to my ext. hard drive. 
I have no idea how to unmount it. Anyone that can help me? I was reading in the bugs reported, and to my understanding it seemed to be a ubuntu bug on unmounting......Is there a fix for this, another way to unmount maybe using the command line?

Appreciate some help on this

---

### Post by taurus on 2007-05-30
See if you can unmount it from a terminal like

```
sudo umount /dev/sdb1
```
_assuming_ /dev/sdb1 is the device of that harddrive.

---

### Post by Tilo on 2007-05-31
if the above unmount command still doesn't work...

sometimes a process or shell is still using the mounted directory, and you can't un-mount it.
e.g. somebody did a "cd /mnt/your-mounted-drive/" ... and the shell-session is still in that directory.

you can run this command, giving it the device name of the mounted partition

# sudo lsof /dev/sda1

COMMAND  PID     USER   FD   TYPE DEVICE SIZE NODE NAME
bash    5050 ubuntu  cwd    DIR   8,33 4096 5183 /mnt/tmp/cdrom

to see whcih processes are currently accessing the mounted partition
If it's a shell like in the example above, you can find the window where that session is
and do a 'cd /'  or 'cd'  - to change directories out of the mounted drive.
If it's another program accessing the mounted drive, you may have to kill that program/process:

you can kill the process which uses your mounted directory with "kill -TERM PID" where PID is the process number.. 
e.g. 

sudo kill -TERM 5050

and then:

sudo umount /dev/sda1
  
 T.

---

### Post by jarocooke on 2007-06-03
I am having the same problem.

What I think is happening is that the drive is unmounting successfully and then remounting automatically, which isn't very helpful.

If you yank the cable a the moment just after you've tried to eject the drive, it doesn't give you the error.

This has got to be some sort of automount bug surely?

---

### Post by jarocooke on 2007-06-03
Further update, if you untick the option to auto mount external drivers (found under preferences / removable drives and media), it works a bit better.

You'll have to manually mount everything by right clicking on it in the computer view in nautilus and it will still give the error, but it will unmount the drive anyway.

No idea what is going on here, but this should be a safe way to unmount you external media (I think).

---

### Post by vanadium on 2007-06-03
Ingval, you have observed it correctly. Indeed, the drive is unmounted, but is mounted again immediately thereafter. This is a bug in Feisty (one of the few very visible ones that should never have been there in a stable release). There is a workaround. Open a command prompt and run

```

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

```

and restart the system (sounds like Windows, doesn it ;)

After that, the right-click menu item will read Unmount rather than Eject. You now can unmount and safely remove the device.

---

### Post by jarocooke on 2007-06-03
I see I have been beaten to it!!!

I was going to suggest installing the upgrades that are in Feisty Backports, this has the same effect as the fix above, though it might be better to follow the advice above as the backports aren't supported.  That said it seems to be working fine here at the moment.

---

### Post by Zeenomorph on 2007-08-18
That's a great fix.  I've had the same problem for a long time now.  I was restarting my computer just to remove my portable HD.  That code fixed everything wonderfully.  Thanx!

Zeenomorph

---

