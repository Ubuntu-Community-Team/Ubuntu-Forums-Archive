---
title: "force disk spin down (LUCID)"
date: 2010-05-05
forum: Hardware
---

### Post by jm.mico on 2010-05-05
Hello community!

I moved my whole / to a usb flash drive (one of those nano drives, which do not pop out of the laptop) so that I can run linux from it and only mount the internal hard disk drive on-demand (because I am a noiseless freak.)

Now, I can not get to spin down the laptop's hard drive automatically! Maybe some guru knows ?

What I do:

1. In my fstab there is no entry for the /dev/sda, because I want to mount it only on demand.

2. Added to /etc/local.rc the line "hdparm -Y /dev/sda" which actually, during boot, spins down the drive.

3. HOWEVER, when X-session starts, I can hear the hard drive spinning up back. why??

I have tried adding the same command "hdparm -Y..." to the "startup applications" from gnome panel, but does not work since the line needs sudo and for whatever reason that doesn not allow it.

On my energy preferences is also ticked "spin down hard disks when possible". But this looks like makes absolutely nothing.


Any ideas ?

Cheers.

Lucid :guitar:ROCKS!!! my laptop is back booting fast!

---

### Post by jm.mico on 2010-05-10
Nobody???

Ok, let's put the question in another way:

Is there a way to execute a command which requires "sudo" without being asked for the passwd, after starting X?

Thnks!

Jm

---

### Post by jm.mico on 2010-05-28
Found a way by myself. 

Execute:
```
sudo visudo
```

And just add at the end of the file:
```
username ALL = NOPASSWD: /sbin/hdparm
```

where 'username' is your linux username. Now it can be run
```
sudo hdparm -Y /dev/sda
```

And you are not required to enter the password. So, you can add it to the "Preferences">"Startup Applications" and it will be run without problems.

Maybe somebody else find it useful.

Cheers.

JM

---

