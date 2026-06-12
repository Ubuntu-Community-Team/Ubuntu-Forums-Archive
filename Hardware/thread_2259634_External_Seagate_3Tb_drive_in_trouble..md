---
title: "External Seagate 3Tb drive in trouble."
date: 2015-01-05
forum: Hardware
---

### Post by BCRailrodder on 2015-01-05
Hi all,

While backing up my home directory to my External Seagate drive, I noticed that the system had hung up on me and it sounded like the head was continually searching.  As nothing that I could do seemed to get the machine back under control, I ended up doing a hard reboot hoping that I wouldn't corrupt any files.

Of course, I wasn't that lucky.

Now, when I boot up, the external drive sounds like it's searching for a couple of seconds and then stops.  As well, it is not VISABLE to either of my desktops or my Window 7 machine (first time I booted that in 2 years <G>).

And of course, I have a bunch of video that I hadn't gotten off that drive yet :(.

Any suggestions on how to recover it?

Kent

---

### Post by weatherman2 on 2015-01-05
The drive could be failing or have failed.  You can install GSmartControl to check the drive's S.M.A.R.T. status, check its Attributes, and run tests.  That's the first thing I would do.  If the drive is failing, it will be much more difficult to recover files from it.

If the drive shows no failing S.M.A.R.T. Attributes (e.g. pending sectors > 0) and passes the extended S.M.A.R.T. test (which would take hours on a 3TB drive but might fail quickly if the test will fail), then likely there is just a corruption of the filesystem or the partition.  You could then try a file system recovery tool like Testdisk to recover files.  But if the drive is experiencing real S.M.A.R.T. issues, though, Testdisk may take a long time to run.

---

### Post by BCRailrodder on 2015-01-06
Thanks for the suggestion but GSmartControl can't see the drive to check it.  At this point, I don't believe that the OS is seeing the drive dispite hearing the head moving when it's powered up. Any other suggestions?

Kent

---

### Post by weatherman2 on 2015-01-06
You may need to coax GSmartControl to see the drive with extra options for the smartctl command (which it is using to gather the S.M.A.R.T. information).

In GSmartControl, under the Options menu and then Preferences find the field for 

Smartctl parameters:

and if there is nothing there, add these:

```
-T permissive -d sat
```

Then Ctrl-R to re-scan the device list.

If still nothing, open a terminal and type 

```
dmesg
```

Anything related to the drive appear there?  (That's like a summary of recent events.)

Turn the drive off, wait about 10 seconds, then turn it on again.  Try dmesg again - any new events related to the drive?  If not...then you're right, maybe the OS isn't seeing it.

If you can't get any OS to detect the drive, the next step might be to crack open that Seagate case and see if you can attach the drive to another adapter or to a desktop computer motherboard.  Kind of a last resort.  As it sounds like the drive itself is powering up, the enclosure/interface might have failed but I doubt it.  More likely the drive inside has failed anyway.

---

### Post by weatherman2 on 2015-01-06
[duplicate]

---

### Post by BCRailrodder on 2015-01-08
Thanks Weatherman2,

I tried both suggestions and the result was the same, no indication that the drive was being seen at all.  It may take me a couple of days but I try to find another controlller and see if that will work.

Again, thanks for the help,

Kent

---

