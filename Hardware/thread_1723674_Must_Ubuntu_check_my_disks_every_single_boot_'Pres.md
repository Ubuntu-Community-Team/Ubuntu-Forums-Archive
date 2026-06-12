---
title: "Must Ubuntu check my disks every single boot? 'Press c to cancel all checks...'"
date: 2011-04-07
forum: Hardware
---

### Post by Dáire Fagan on 2011-04-07
It seems every time I see the purple Ubuntu 10.10 boot screen after BIOS I am being told:

> Your disks are being being checked for errors, this may take some time.

Press C to cancel all checks currently in progress.

And because it happens apparently all the time I have been skipping it.

Why does it keep doing this, and is there anyway I can have it do this when I shutdown the computer at night instead?

---

### Post by trundlenut on 2011-04-07
What happens if you let it do the check does it ask again at the next boot or not?

---

### Post by Rubi1200 on 2011-04-07
Are you sure you are seeing this every time you boot?

The default is to check the filesystem every 30 mounts.

You can use this command to list the current and maximim mount count and the next check date:
```
sudo tune2fs -l /dev/sd**XY** | grep -i -e "mount count" -e "check"
```change to reflect your partition obviously.

---

### Post by Dáire Fagan on 2011-04-07
> **trundlenut said:**
> What happens if you let it do the check does it ask again at the next boot or not?
 
 > **Rubi1200 said:**
> Are you sure you are seeing this every time you boot?

Apologies, I let it run through and and rebooted again and it did not check...

The default is to check the filesystem every 30 mounts.

> **trundlenut said:**
> You can use this command to list the current and maximim mount count and the next check date:
```
sudo tune2fs -l /dev/sd**XY** | grep -i -e "mount count" -e "check"
```change to reflect your partition obviously.

From the output it appears it is tune2fs I need to change, how can I find the names of the partition I need to change it to?

---

### Post by Rubi1200 on 2011-04-07
There is an error in your last post; I posted the command and not trundlenut.

Never mind, to find your partitions use fdisk:

```
sudo fdisk -lu
```

(lowercase L not 1)

---

### Post by Dáire Fagan on 2011-04-07
> **Rubi1200 said:**
> There is an error in your last post; I posted the command and not trundlenut.

Never mind, to find your partitions use fdisk:

```
sudo fdisk -lu
```(lowercase L not 1)

My bad.

> dusf@skyrocket:~$ sudo sda1 -l /dev/sdXY | grep -i -e "mount count" -e "check"
[sudo] password for dusf: 
sudo: sda1: command not found


---

### Post by Rubi1200 on 2011-04-07
Is sda1 your Ubuntu install?

The command would look like this then:

```
sudo tune2fs -l /dev/sda1 | grep -i -e "mount count" -e "check"
```

---

### Post by Dáire Fagan on 2011-04-07
> Mount count:              2
Maximum mount count:      27
Last checked:             Thu Apr  7 15:35:15 2011
Check interval:           15552000 (6 months)
Next check after:         Tue Oct  4 15:35:15 2011


Thanks, I am noting the commands down for future use if required.

Do you know a way to make it do these checks when shutting down rather than starting up? Means that if I'm turning on the computer to do something I don't have to wait on the checks, and instead they check when it's clear I'm done with the computer on shutting down. Just a restart and not a shutdown? Press C to cancel checks :)

---

### Post by Rubi1200 on 2011-04-07
You can take a look at the man page for tune2fs:
[http://www.linuxmanpages.com/man8/tune2fs.8.php](http://www.linuxmanpages.com/man8/tune2fs.8.php)

I know you can force a check either on the next boot or force a check and then reboot.

I suppose you could do this:

REMOVED: in hindsight this probably is not a good idea because the touch /forcefsck command necessitates a reboot I believe.

The only other thing I can suggest is to increase the interval between checks. In other words, instead of the default 30, make it a higher number e.g. 50:

```
 sudo tune2fs -C 50 /dev/sda1
```

---

### Post by Sidewinder1 on 2011-04-12
Thank you very much, Rubi; I was searching for that exact syntax to accomplish that exact goal; changing the default setting on boot to a higher number.
Gotta' love Ubuntu, these forums, and, most importantly the tireless volunteers who commit their time and resources to this most humble endeavor.

Side

---

### Post by Dáire Fagan on 2011-04-12
Mine just tried to check my disks again 5 minutes ago, what's a suitable number to increase it to, and what are the risks?

---

