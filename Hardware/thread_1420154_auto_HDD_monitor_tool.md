---
title: "auto HDD monitor tool?"
date: 2010-03-02
forum: Hardware
---

### Post by ARhere on 2010-03-02
I am looking for a Linux app that constantly looks at the hard disks and makes lots of noise, emails, whatever, when one of them gets full or has an issue.  I am surprised that I have been having trouble finding this in Google, so I am asking here.  ;-)

I use Ubuntu 8.04 for my home server.  It has two 500GB HDD, one is mounted and shared out in pieces, the other mirrors the first using rsync every night.  A few weeks ago, one of the drives suddenly lost it's table and would not mount, and I did not notice until I glanced at the rsync logs a week later!!! :shock:   I had to reformat and re-sync to get it going again.  I am worried now because a problem can happen like this and it is possible that I would not notice until something happens to the other drive as well!

-AR

---

### Post by tgalati4 on 2010-03-02
sudo apt-get install smartmontools

sudo smartctl /dev/sda

That will cover the SMART monitoring for physical problems.

For filling up, most applications will throw up errors when they can't write to the disk.  The kernel reserves 5% of drive space to allow for continued operations when a drive fills.

There are gnome-applets that you can set alarms when conditions are met, like temperature exceeds 60C, etc.  You will have to search the gnome-applets for a hard disk space monitor.

---

### Post by ARhere on 2010-03-02
Thank you tgalati4.  I will try out the monitoring tools.

As far as running out of space, oddly what you said did not happen last time.  I just suddenly noticed my server was unresponsive through ssh, and when I checked it, I got nothing but a black screen.  CTRL+ALT+F1 did not even give me a terminal.  When I rebooted, gnome & X did not want to load and when I checked "df -h", my root drive was full.  After freeing some space I was able to restart X.

-AR

---

### Post by delectate on 2010-03-02
smart tools maybe helpful

and this can monitor r/w :

sudo apt-get install iotop

---

### Post by ARhere on 2010-03-02
> **tgalati4 said:**
> sudo apt-get install smartmontools

sudo smartctl /dev/sda

That will cover the SMART monitoring for physical problems.

I forgot to comment to this.  My BIOS has the SMART covered, what I want is something that will try to read and write, and report if there is a problem.  So far I have had two cases where the file table (*sorry, cannot remember the correct term*) mysteriously was lost.  I do not believe SMART can detect this problem.  Am I wrong?

-AR

---

### Post by ARhere on 2010-03-02
> **delectate said:**
> smart tools maybe helpful

and this can monitor r/w :

sudo apt-get install iotop

Is that a typo?  no iotop found.

-AR

---

### Post by tgalati4 on 2010-03-03
SMART will periodically perform short and long tests on the drive.  The results are stored on the drive and can be retrieved:

smartctl -all /dev/sda

When you run out of space on a drive, you should be able to log in using rescue mode (root console only).  So, you are correct, X would not load because it writes a lot of log files, but you can still use the command line:

df -h

and start doing emergency housecleaning.

If this is a server, there are server monitoring tools such as phpadmin and other scripts such as this one:

Administration Page for Galati Consulting

AUTHORIZED ACCESS ONLY. SERVER LOGS ARE MONITORED

washme UPS status

Uptime: 
 21:24:18 up 57 days, 11:48,  0 users,  load average: 0.04, 0.01, 0.00

Kernel Information:
Linux washme 2.6.24-23-server #1 SMP Wed Apr 1 22:22:14 UTC 2009 i686 GNU/Linux

System Information:
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.3 LTS
Release:	8.04
Codename:	hardy

Memory Usage (MB): 
             total       used       free     shared    buffers     cached
Mem:           502        427         74          0        146         91
-/+ buffers/cache:        189        312
Swap:          551          0        551
Total:        1054        428        625

Disk Usage: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/washme-root
                       19G  2.6G   15G  15% /
varrun                252M   88K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   52K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/sda1             236M   25M  199M  12% /boot

Mounted Filesystems:
Filesystem         Mount               Megs     Used    Avail %Used fs Type
/dev/mapper/washme /                18516.7   2634.7  14948.8  19%  ext3   
/dev/sda1          /boot              235.5     24.9    198.5  16%  ext3   
udev               /dev               251.2      0.1    251.1   0%  tmpfs  
devshm             /dev/shm           251.2      0.0    251.2   0%  tmpfs  
varlock            /var/lock          251.2      0.0    251.2   0%  tmpfs  
varrun             /var/run           251.2      0.1    251.1   0%  tmpfs  

CPU Information: 
vendor_id	: GenuineIntel
model name	: Celeron (Coppermine)
cpu MHz		: 598.199
bogomips	: 1197.52

--------------------

It's created with some simple php commands (server_status.php):

```

<?php
// ==================================================================
// Script written by quietas (http://ubuntuforums.org/member.php?u=300503)
// Script Modified 24 Feb 2009 by ussr - CHANGE THIS WHEN YOU MOD THIS
// Make sure this is all good for running over SSL.
// ==================================================================
?>

<html>
<head>
<BODY BGCOLOR="#000000" TEXT="#00CC00">
<title>Ubuntu Hardy 8.04 Server Status</title>

<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0$
</STYLE>
</head>

<center><h1>Administration Page for Galati Consulting</h1></center><br>
<center>AUTHORIZED ACCESS ONLY. SERVER LOGS ARE MONITORED</center<br>

<h1>
<center><a href=http://washme/cgi-bin/apcupsd/multimon.cgi>washme UPS status </a></br></center>
</h1>


<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h "); ?>

<b>Mounted Filesystems:</b>
<?php system("di"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

<center><h3>Report bugs <a href="mailto:ussr@(omit).dyndns.org"> here </a></h3></center>

<meta http-equiv="refresh" content="30">
</body>
</html>


```

---

