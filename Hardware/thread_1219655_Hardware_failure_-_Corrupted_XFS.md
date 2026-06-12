---
title: "Hardware failure - Corrupted XFS??"
date: 2009-07-22
forum: Hardware
---

### Post by nowhere@cox.net on 2009-07-22
Hey all,
At about 8pm today I had to hard reset my 8.10 myth backend server as absolutely nothing was responsive. 

After reboot I checked the logs and around 3pm the messages log had started filling up with
```
ata1: link is slow to respond, please be patient (ready=0)
ata1: device not ready (errno=-16), forcing hardreset
ata1: soft resetting link

```

I sudo reboot'ed to get a fresh boot and it would not respond to ssh remote login so I headed up, connected a monitor and keyboard and was greeted with black screen with one white cursor blinking. Ctrl-Alt-Del rebooted again and as I watched it, I noticed only one of the hard drives was auto detected at post. I removed power from the PSU and powered everything back on and the drive was detected. Since then the same drive detection is very intermittent. Also, while on the mythbuntu desktop with a liveCD just sitting in the drive (not booted from the LiveCD), spontaneously, the CD icon disappeared from the desktop. 

At this point I checked the logs again and now noticed the logs filling up with ```
xfs_log_force: error 5 returned
```

The drive scheme looks like this:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb3             19228308  13258052   4993504  73% /
tmpfs                  1032072         0   1032072   0% /lib/init/rw
varrun                 1032072       360   1031712   1% /var/run
varlock                1032072         0   1032072   0% /var/lock
udev                   1032072      2860   1029212   1% /dev
tmpfs                  1032072         0   1032072   0% /dev/shm
lrm                    1032072      2204   1029868   1% /lib/modules/2.6.27-14-server/volatile
/dev/sdb1               241116     43851    184817  20% /boot
/dev/mapper/MYTHLVM-mythdata
                     1150246912 791021540 359225372  69% /mythdata

``` The LVM spans a 1TB samsung and a 200GB Seagate. The 200GB drive is the one that is intermittently not being detected. 

I unmounted the XFS LVM partition and ran 
```
xfs_check /dev/mapper/MYTHLVM-mythdata

``` on it but was given and I/O error. Then I could not remount the volume. Rebooting, the drive was not detected and removing all power to the PSU reset it so that the drive was detected again.

I see a bug reported (from a mail archive) about 8.10 and the slow ata1 but no other info. I suspect either a hard drive has failed or my ata controller is nuts on the mb. Any ideas or comments?

I'm trying to determine the best way of backing up the data on these drives before I lose it totally and start troubleshooting hardware. Any suggestions here would be appreciated too. Specifically, I am wondering if there is a way to remove the 200GB drive from the LVM thus allowing me to save everything on the 1TB drive. How can I tell which files are saved where?

Help!!?

---

### Post by prshah on 2009-07-22
> **nowhere@cox.net said:**
> I suspect either a hard drive has failed or my ata controller is nuts on the mb. Any ideas or comments?


I'd say that the power is fluctuating and causing a problem. If you have a spare PSU, I'd suggest you test with that, or, at the very least, change the power connecter that is plugged into the 200GB HDD. For example, pull the power connecter on the 1TB and plug it into the CDROM (which is also experiencing intermittent failures) and then test run it for 15~20 mins; if it is stable, then you can probably pinpoint that as the failure.

---

### Post by nowhere@cox.net on 2009-07-22
Well, Thanks for the input, prshah. It's a good idea I hadn't thought of yet. So I opened up the machine (it's been a while) and the 1TB drive is a SATA while the 200GB is a PATA drive and sharing the same power lead as the DVD ROM. So I disconnected the DVD ROM which is quite old and everything has been stable for about an hour now. 

The only other variables are that the case is open now instead of being all closed up and it sat off overnight. I had a power issue on one system I built years ago where it would crash anytime I closed the case. The extra strain on the case fans drew too much current for the fan head on the MB. 

I deleted most of the files from the affected time period and the mysql DB checks out ok with mysqlcheck but I do need to figure out how to run xfs_check on the LVM volume tho. I also need to figure out where to do a back up. I don't have 780GB free anywhere....

---

### Post by prshah on 2009-07-23
> **nowhere@cox.net said:**
> I also need to figure out where to do a back up. I don't have 780GB free anywhere....

Hey you can always use 97 8GB DVDs and one 4GB DVD.

---

### Post by nowhere@cox.net on 2009-07-23
And at 25 minutes per 8GB disk burn time it won't take much longer than a full 40 hour work week to do :-D

---

### Post by nowhere@cox.net on 2009-08-02
OK here's an update and request for more opinions. 

Pulling the power on the DVD Drive only worked for a little while. The errors returned.

I have swapped the power supply now, upgrading from a 300W to a 350W spare supply. It's only a small celeron system with no graphics card so power shouldn't be an issue. Everything seemed great. I did an xfs_check with no errors and checked my mysql database also with no errors.

This morning with the new supply and the DVD Drive hooked up too (everything on seperate leads if that makes a diff), I started getting ivtv errors and this error in messages
```
Aug  2 09:40:03 mythserver kernel: [394704.989715] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
```
And this error in syslog
```
Aug  2 09:40:04 mythserver kernel: [394706.307583] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Aug  2 09:40:04 mythserver kernel: [394706.307594] end_request: I/O error, dev sda, sector 99967902
```

sudo reboot would not actually complete. Got to the acpi shutdown and hung. I hard rebooted at that point and again no errors but at this point we know what's coming. 

SO! Is this a kernel issue, hard drive issue or controller issue?

Thanks!

---

