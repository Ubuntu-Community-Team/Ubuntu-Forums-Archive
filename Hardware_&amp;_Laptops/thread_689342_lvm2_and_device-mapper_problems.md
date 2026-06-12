---
title: "lvm2 and device-mapper problems"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by xkorakidis on 2008-02-06
Hi guys!
A have a fedora installed on a tower witch crashed and I need to get some files from there..
The problem is that tower's hd is lvm2. 
I used a ubuntu 7.10 cd to boot and get any files from the tower's hd but didn't success..
I downloaded and installed lvm2 but cannot mount logical volumes (LogVol00 and LogVol01) of volume group VolGroup00. Using vghange -a y VolGroup00 I get err msg: 
```

/proc/misc: No entry for device-mapper found 
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/misc: No entry for device-mapper found 
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.20 (2007-06-15) (compat) and kernel driver
0 logical volume(s) in volume group "VolGroup00" now active

```

if i try mounting e.g. sudo mount /dev/VolGroup00/LogVol00 /media/mainhd, I get a message:
```
mount: special device /dev/VolGroup00/LogVol00 does not exist.
```

any Idea?
thanks in advance.

---

### Post by jamessnell on 2008-02-17
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=608369](http://ubuntuforums.org/showthread.php?t=608369) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had this problem. It's due to dm_mod not being loaded. I ran the below lines to load the necessary modules without rebooting. Though once I rebooted the modules loaded on their own - so I think it's a minor bug in the lvm2 deb package not loading those modules after installation - not really a problem though. Either just reboot or read on below.

Run: 
```

modprobe dm_mod
modprobe dm_mirror
modprobe dm_snapshot

```

Some people may also want to load dm_crypt.

You should be good now. Verify the modules are loaded with:
```

lsmod | grep dm_*

```


So you should see something like:
```

james@mailbag:~$ lsmod | grep dm_*
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  5 dm_mirror,dm_snapshot

```


You can also look at the discussion here: [http://ubuntuforums.org/showthread.php?t=608369](http://ubuntuforums.org/showthread.php?t=608369)

---

