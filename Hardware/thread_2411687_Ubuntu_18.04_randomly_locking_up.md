---
title: "Ubuntu 18.04 randomly locking up"
date: 2019-02-02
forum: Hardware
---

### Post by really-wonderful-really on 2019-02-02
I am posting here first because i am guessing this is some kind of hardware issue. I am using a Toshiba c55  4 gig of ram (will be upgrading to 8) 2.16Ghz quad core CPU 2TB HD.  Ubuntu will lock up randomly. I had issues so i reinstalled Ubuntu because i thought atom and firefox were causing the lockups (have to power off the laptop) so i reinstalled Ubuntu. came home from work (8 hours) Ubuntu was locked up could not use the mouse had to reboot.  since it locked up i let it sit. it will lock up for no reason. so i tried a live cd does the same with Ubuntu 18.04 and Ubuntu-MATE.  I do need to replace the bios/cmos battery but the pc dose not lose power. I have tried to give all information without making this a page long, if you need more information let me know.  I want to change to Linux systems and Ubuntu seems to be what everyone is talking about

---

### Post by TheFu on 2019-02-02
There is a reason and 95% of the time, that reason is spelled out in the log files.  Those are in /var/log/.  Look for errors and warnings in that directory.  Then, copy/paste the exact error message (removing things that are specific to your machine, your network and any timestamps), into google.

If you need more details about log files, google "ubuntu logs" and a help.ubuntu.com page should be near the top.

Checking with a liveboot was smart.  The fact that the issue happens under that version too means it is likely hardware that isn't the HDD causing the issues.  On a laptop, that isn't good, since replacing parts is much harder.  Also, the exact model of toshiba would be helpful - they probably made 20 different variants.

---

### Post by really-wonderful-really on 2019-02-02
I will reinstall it again and check my logs  thanks
Toshiba c55-b5382

---

### Post by really-wonderful-really on 2019-02-02
side question what size should i make my swap, home, and root partitions

---

### Post by really-wonderful-really on 2019-02-05
it locked up again.  I took a screen shot of the var/log as i was asked to 
hope you can see the image
[IMG]/home/trickster/Desktop/Screenshot at 2019-02-05 10-24-57.png[/IMG]

---

### Post by Autodave on 2019-02-05
Nothing showing on your upload.

---

### Post by really-wonderful-really on 2019-02-05
i cant get it to upload. when i copy the image it gives me an error when i post it. i am truing a different way

---

### Post by TheFu on 2019-02-05
> **really-wonderful-really said:**
> side question what size should i make my swap, home, and root partitions

System logs should be available using journalctl, especially errors. You may need to enable persistent storage for those logs.  I don't know how to do it and didn't look it up.

The size for partitions, or LVs, is mostly about making fast, convenient backups and so that restoring is fast and easy.  There is a huge difference in backing up 1 partition with 900GB vs backing up a 25G /, a 200G /var/ and a 25G /home and a /Data with all the other storage (800G?).

**/ **- the root partition should be whatever size you need. This is between 15G and 25G almost always.  Limiting the OS partition size really helps with backups.  

**swap** should be 4.1G on a low-RAM system which I consider any system with 4G or less of RAM.  It would be good to enable zswap, compression.  Not having enough swap can be terrible on a desktop system running a few hog programs like modern browsers.  I had stability issues on my 4G chromebook running a stripped down Ubuntu with only 2G of swap.  It would run out of total RAM, then lock up.  After moving to 4.1G swap, it doesn't lockup, ever without clear warning.  The warning comes by programs feeling sluggish as I alt-tab between them.  It is up to the end-user to recognize that and take corrective action.  I usually close thunderbird to free 1-2G of RAM out of the 4+4=8G total available on the system between real RAM and swap.

I do not use hibernation, so on systems with more than 4G of RAM, my swap is 4.1G too.  If you use hibernation, then swap needs to be at least the same size as RAM.  The purpose of swap has changed over the decades.  The old rules of thumb to use 2-3x the physical RAM for swap stopped being useful once systems had 1GB and more of RAM.  Just to be clear, there are many different opinions on this topic, so do a little reading to see what others say.

/ is the root partition.
/root is the root home directory, which needs to be part of the root/OS partition.

Not everyone uses a separate /var/ or separate /home/ partitions.  I don't always either.  Some really smart folks here keep the /home as part of / (the root partition), but have a separate partition for their personal data and use symbolic links to it out of their HOME for all their old email, and browser data.

You can monitor RAM and swap using the **free -mh** command.  You can see which specific processes are using RAM with **top**. Almost always, it will be the browser at the top of the list. They are all hogs.  If you want a lighter browser and can deal with the limitations, check out **dillo**.  Dillo isn't safe for websites you need secure connections, but when you visit cnn.com or almost any other of the bloated "news" sites, it is nice. Dillo isn't secure.

I hope these ideas can help you solve the issue.  Google found this for settings to control persistent logs across different boots: [https://www.freedesktop.org/software/systemd/man/journald.conf.html](https://www.freedesktop.org/software/systemd/man/journald.conf.html) syslog should be persistent already, so only the boot/HW logging should need changing. If you enable it, be certain to put a limit on the size or timeframe.

---

### Post by TheFu on 2019-02-05
Dude.  You need to look inside the log files. Showing a list of filenames isn't helpful.

---

