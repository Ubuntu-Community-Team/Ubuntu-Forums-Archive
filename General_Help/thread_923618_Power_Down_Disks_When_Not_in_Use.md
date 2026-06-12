---
title: "Power Down Disks When Not in Use?"
date: 2008-09-18
forum: General Help
---

### Post by Kissell on 2008-09-18
Maybe this is a newbie question, but I can't find it anywhere.

In windows power management there is an option to turn off hard disks when not in use.  This takes a few extra seconds when you go to use them, but it should significantly increase the life of the drive.  

I have some internal large hard disks I use for backup/storage but I don't access them very often.  I want them available for use when someone goes to use them without having the user do anything, but I'd like them to power down and stop spinning until the user attempts to use them.

Anyone know how to do this?  I'm not finding the option anywhere in the Ubuntu menus.

---

### Post by bingoUV on 2008-09-18
I don't know about menus, but this is how you can accomplish this.

Assuming your hard disk device name is /dev/sda, the following will power it down after 2 hours of inactivity. Whenever you access it again, it will come back to life but it will take time.
```

sudo hdparm -S 244 /dev/sda

```


The number 244 comes from this formula (copied from man page of hdparm):
```

The encoding of the timeout value is somewhat peculiar.  A value of zero means "timeouts are disabled":  the  device
              will  not automatically enter standby mode.  Values from 1 to 240 specify multiples of 5 seconds, yielding time-
              outs from 5 seconds to 20 minutes.  Values from 241 to 251 specify from 1 to 11 units of  30  minutes,  yielding
              timeouts  from 30 minutes to 5.5 hours.

```

Once you are sure about this number, run this and test whether it is powering down as expected. Once you have made sure of this, put this command without the leading sudo in /etc/rc.local so that next boot also maintains this behaviour. /etc/rc.local anyway runs with root privileges, so you do not need sudo there.

---

### Post by Kissell on 2008-09-18
Great, that's exactly what I was looking for...  I am loving linux but it's been less than a year since I switched to using it exclusively in my environment, and there are still things like hdparm I'm unfamiliar with.

You answered my question about 244, very good...  but I have two others.

1) Can I list the current value?  If I set this command or change the value I'll know what it is, but is there a way to see what it is already set to without changing it?

2) Is this okay to run on md?  For instance, I'm going to be gone for a few months, and will have a laptop and remote connection ability, I'd like to be able to access data on a software RAID, but very infrequently...  so I'd like to be able to put the RAID into standby...  I assume I can run this on the /dev/md0 device, and it will work, and I don't need to run it on each individual hard disk in the array...  but I'm not sure.

---

### Post by bingoUV on 2008-09-18
Read man page of hdparm for more details. I can't find a way to show the current setting for standby timeout, but I didn't look in detail.
```

man hdparm

```

No, you cannot directly run it on /dev/md0. It only works on hard disks. Now that you mention md, I don't know how well md behaves when disks are powered down and md needs to access them. You will need to confirm this.

---

### Post by Kissell on 2008-09-18
yeah, i tried to run it on a non-critical md and it told me "no".

I was worried that if I ran it on individual disks in the raid array that md would think a disk failed if one went into standby.  So I did some more searching (now that I have the hdparm and standby keywords) and found other forum posts saying it's okay to put individual disks in an array into standby mode.  Linux is smart enough to figure out they're in standby.  Testing it now, if it turns out this is wrong, i'll let you know.  ;)

Thanks!

hdparm is pretty cool, "hdparm -tT /dev/md0" is awesome, shows me the speed the array is performing at...  I just upgraded the controller card in a software raid the other day because it was having I/O problems and the controller was a likely candidate... The problem ended up being the port-multiplier, so now i have an extra controller, but the old one was slow anyway, now I can play and get a real equal comparison between them, show me some real numbers on how much faster the new card is in the real-world, not what it says in the marketing literature.

---

### Post by bingoUV on 2008-09-19
I was sure that you cannot hdparm on /dev/md0. I asked you to confirm about how md raid will behave when some of its constituent disks are sleeping. Turns out you are researching that before setting standby for the drives, like a good user.

hdparm -tT is great. It is even greater when you run it in single user mode (the recovery mode). There is no other process to disturb the test so the test is more accurate.

---

