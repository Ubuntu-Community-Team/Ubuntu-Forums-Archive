---
title: "Harddrive Read/Write issue"
date: 2016-01-11
forum: Hardware
---

### Post by gandhi2 on 2016-01-11
Hi all!!

how are you?

I'm having continual issues with my external harddrive...

500GB
FAT32

basically once connected, I will be able to read AND write for a very short while before the harddrive declares that is now READ ONLY!??

what gives? why is this happening? i have the same issue on and off with my usb keys too.....

its a pain is the ass as everytime i wanna copy a large amount of files (tv series etc) part way though it will stop and say the harddrive is ready only...

PLEASE HELP

thank you

---

### Post by matt_symes on 2016-01-12
Hi

> basically once connected, I will be able to read AND write for a very short while before the harddrive declares that is now READ ONLY!??

This is not uncommon and expected behaviour if the kernel encounters certain types of serious drive errors.

Firtsly, backup any inportant files you have on that hard drive.

I would suspect failing hard drive but look in /var/log/syslog at the time the drive is remounted read only only. That should give some clue as to what is going on.

Also run a SMART test on the external hard drive.

Kind regards

---

### Post by gandhi2 on 2016-01-13
hi there thank you for your help..........

I did a SMART check on my harddrive...it fine.... and to be honest its the newest harddrive i have at about 1.5 years old....

i looked at the syslog file and i can not understand it....

can you assist me further please?

thanks again

---

### Post by matt_symes on 2016-01-13
Hi

You'll have to post the contents of syslog into your next post.

Post a section around the time that the drive is mounted read only.

That may give some clues.

Kind regards

---

### Post by weatherman2 on 2016-01-13
> **gandhi2 said:**
> I did a SMART check on my harddrive...it fine.... and to be honest its the newest harddrive i have at about 1.5 years old....


What does that mean?  Did you run the Short S.M.A.R.T. test?  The Extended Test?  What?

What is the current state of the S.M.A.R.T. Attributes?  You might want to install GSmartControl to get better access/control of S.M.A.R.T. tests, etc.

Any hard drive could fail, certainly a drive that is over a year old.  Even new drives sometimes fail.

You might also have some issue with the controller in the external casing or even the power supply (is it USB powered or is there an external power supply to the drive?).  If it is not say providing reliable power, it might not be able to stay active all the time and may lose communication with the computer or something.  It could even be something weord with the USB connector or the cable.  

As Matt says, it's likely that the drive's partition is being un-mounted and re-mounted read-only automatically due to some sort of errors.  But that could be caused by numerous things, some of them hardware-related.

---

### Post by oldfred on 2016-01-13
Also FAT32 is not recommended for larger drives. It does not have a journal nor can store a file over 4GB. It is ok for small partitions or small flash drives, etc.

Did you try to write a large file which then may corrupt the partition? And without journal chkdsk from Windows can take forever.

---

### Post by weatherman2 on 2016-01-13
I seriously doubt writing a file larger than 4.1GB would corrupt the partition.  I think I've done that more than once by accident and simply had a truncated, corrupted file.  Nor do I see how that would cause the partition to be unmounted.

I'd be careful running chkdsk on a drive with important data on it where there might be some hardware issue (e.g. power supply) causing the disk not to be mounted reliably.  THAT could corrupt something.  (In other words, this might not be a "Linux" issue at all.)

---

### Post by gandhi2 on 2016-01-14
Hi Matt,

i really dont't know whats happening..... this time i tried to copy a folder and it came up with some error to do with "splicing".... then it unmounted.... then i reconected the drive and all the folders, BUT the one i was copying to, have a padlocks on them... when i right click to look at the properties it says that i have read and write access

the harddrive has no issue with my windows partition..... 

here is the syslog file.... sorry its not more specific... i really don't know what i'm looking for....

```
Jan 13 08:23:38 gandhi-winbuntu anacron[13036]: Job `cron.daily' terminatedJan 13 08:23:38 gandhi-winbuntu anacron[13036]: Normal exit (1 job run)
Jan 13 08:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 08:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 08:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 08:33:25 gandhi-winbuntu acpid: client 13180[0:0] has disconnected
Jan 13 08:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 08:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 08:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 08:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 08:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 08:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 08:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 08:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 08:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:17:01 gandhi-winbuntu CRON[17232]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 09:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 09:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 09:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 09:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:17:01 gandhi-winbuntu CRON[19757]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 10:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 10:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 10:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 10:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:17:01 gandhi-winbuntu CRON[22367]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 11:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 11:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 11:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 11:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:17:01 gandhi-winbuntu CRON[25578]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 12:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 12:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 12:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 12:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:17:01 gandhi-winbuntu CRON[28428]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 13:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 13:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 13:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 13:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:17:01 gandhi-winbuntu CRON[31541]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 14:15:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:17:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:17:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:17:16 gandhi-winbuntu wpa_supplicant[988]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jan 13 14:19:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:25:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:27:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:27:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:35:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:37:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:37:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:45:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:47:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:47:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 14:52:37 gandhi-winbuntu dbus[616]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan 13 14:52:40 gandhi-winbuntu AptDaemon: INFO: Initializing daemon
Jan 13 14:52:40 gandhi-winbuntu dbus[616]: [system] Successfully activated service 'org.debian.apt'
Jan 13 14:52:41 gandhi-winbuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jan 13 14:55:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 14:57:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 14:57:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 15:02:41 gandhi-winbuntu AptDaemon: INFO: Quitting due to inactivity
Jan 13 15:02:41 gandhi-winbuntu AptDaemon: INFO: Quitting was requested
Jan 13 15:02:41 gandhi-winbuntu dbus[616]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan 13 15:02:41 gandhi-winbuntu AptDaemon: INFO: Initializing daemon
Jan 13 15:02:41 gandhi-winbuntu dbus[616]: [system] Successfully activated service 'org.debian.apt'
Jan 13 15:02:41 gandhi-winbuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jan 13 15:05:14 gandhi-winbuntu wpa_supplicant[988]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 15:07:11 gandhi-winbuntu wpa_supplicant[988]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 15:07:14 gandhi-winbuntu wpa_supplicant[988]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 15:12:42 gandhi-winbuntu AptDaemon: INFO: Quitting due to inactivity
Jan 13 15:12:42 gandhi-winbuntu AptDaemon: INFO: Quitting was requested
Jan 13 15:12:42 gandhi-winbuntu dbus[616]: [system] Activating service name='org.debian.apt' (using servicehelper)
Jan 13 15:12:42 gandhi-winbuntu AptDaemon: INFO: Initializing daemon
Jan 13 15:12:42 gandhi-winbuntu dbus[616]: [system] Successfully activated service 'org.debian.apt'
Jan 13 15:12:42 gandhi-winbuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jan 13 15:13:29 gandhi-winbuntu kernel: [33996.696040] usb 6-1: new low-speed USB device number 2 using uhci_hcd
Jan 13 15:13:29 gandhi-winbuntu kernel: [33996.878095] usb 6-1: New USB device found, idVendor=045e, idProduct=0029
Jan 13 15:13:29 gandhi-winbuntu kernel: [33996.878100] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan 13 15:13:29 gandhi-winbuntu kernel: [33996.878103] usb 6-1: Product: Microsoft IntelliMouse® Optical
Jan 13 15:13:29 gandhi-winbuntu kernel: [33996.878106] usb 6-1: Manufacturer: Microsoft
Jan 13 15:13:29 gandhi-winbuntu mtp-probe: checking bus 6, device 2: "/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1"
Jan 13 15:13:29 gandhi-winbuntu mtp-probe: bus: 6, device: 2 was not an MTP device
Jan 13 15:13:29 gandhi-winbuntu kernel: [33997.562019] hidraw: raw HID events driver (C) Jiri Kosina
Jan 13 15:13:29 gandhi-winbuntu kernel: [33997.632797] usbcore: registered new interface driver usbhid
Jan 13 15:13:29 gandhi-winbuntu kernel: [33997.632801] usbhid: USB HID core driver
Jan 13 15:13:30 gandhi-winbuntu kernel: [33997.754742] input: Microsoft Microsoft IntelliMouse® Optical as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/0003:045E:0029.0001/input/input24
Jan 13 15:13:30 gandhi-winbuntu kernel: [33997.755114] hid-generic 0003:045E:0029.0001: input,hidraw0: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Optical] on usb-0000:00:1d.1-1/input0
Jan 13 15:13:56 gandhi-winbuntu dbus[616]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jan 13 15:13:56 gandhi-winbuntu dbus[616]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jan 13 15:13:58 gandhi-winbuntu rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="718" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jan 13 17:02:26 gandhi-winbuntu rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="762" x-info="http://www.rsyslog.com"] start
Jan 13 17:02:26 gandhi-winbuntu rsyslogd: rsyslogd's groupid changed to 104
Jan 13 17:02:26 gandhi-winbuntu rsyslogd: rsyslogd's userid changed to 101
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Linux version 3.16.0-57-generic (buildd@lcy01-20) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #77~14.04.1-Ubuntu SMP Thu Dec 17 23:20:32 UTC 2015 (Ubuntu 3.16.0-57.77~14.04.1-generic 3.16.7-ckt20)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] KERNEL supported cpus:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Intel GenuineIntel
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   AMD AuthenticAMD
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   NSC Geode by NSC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Cyrix CyrixInstead
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Centaur CentaurHauls
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   UMC UMC UMC UMC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d3ff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d400-0x000000000009ffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d7fff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bb6a0fff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb6a1000-0x00000000bb6a6fff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb6a7000-0x00000000bb7b8fff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb7b9000-0x00000000bb80efff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb80f000-0x00000000bb907fff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bb908000-0x00000000bbb0efff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbb0f000-0x00000000bbb17fff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbb18000-0x00000000bbb1efff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbb1f000-0x00000000bbb5efff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbb5f000-0x00000000bbb9efff] ACPI NVS
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbb9f000-0x00000000bbbe1fff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbbe2000-0x00000000bbbfefff] ACPI data
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbbff000-0x00000000bbbfffff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bbc00000-0x00000000bbdfffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000bc000000-0x00000000bfffffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] SMBIOS 2.5 present.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] DMI: Acer            Aspire 5338                    /JV50                           , BIOS V1.06           04/14/2009
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] e820: last_pfn = 0xbbc00 max_arch_pfn = 0x1000000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] MTRR default type: uncachable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   00000-9FFFF write-back
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   C0000-FFFFF write-protect
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   0 base 0BC000000 mask FFC000000 uncachable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   3 base 0BBE00000 mask FFFE00000 uncachable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   4 disabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   5 disabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   6 disabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] original variable MTRRs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 0, base: 3008MB, range: 64MB, type UC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 1, base: 0GB, range: 2GB, type WB
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 2, base: 2GB, range: 1GB, type WB
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 3, base: 3006MB, range: 2MB, type UC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] total RAM covered: 3006M
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 4  	lose cover RAM: 0G
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] New variable MTRRs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 2, base: 3006MB, range: 2MB, type UC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] reg 3, base: 3008MB, range: 64MB, type UC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] found SMP MP-table at [mem 0x000f6d80-0x000f6d8f] mapped at [c00f6d80]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] init_memory_mapping: [mem 0x37400000-0x375fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x37400000-0x375fffff] page 2M
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] init_memory_mapping: [mem 0x34000000-0x373fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x34000000-0x373fffff] page 2M
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] init_memory_mapping: [mem 0x37600000-0x377fdfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]  [mem 0x37600000-0x377fdfff] page 4k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BRK [0x01bd5000, 0x01bd5fff] PGTABLE
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BRK [0x01bd6000, 0x01bd6fff] PGTABLE
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] RAMDISK: [mem 0x35b98000-0x36dc3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: RSDP 0x00000000000F6C00 000024 (v02 PTLTD )
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: XSDT 0x00000000BBBF45B1 000064 (v01 ACRSYS ACRPRDCT 06040000 INNA 00000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: FACP 0x00000000BBBE4000 0000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: DSDT 0x00000000BBBE5000 00A434 (v02 Intel  CANTIGA  06040000 MSFT 03000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: FACS 0x00000000BBB9DFC0 000040
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: FACS 0x00000000BBB9DFC0 000040
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: HPET 0x00000000BBBFED86 000038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: MCFG 0x00000000BBBFEDBE 00003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: SLIC 0x00000000BBBFEDFA 000176 (v01 ACRSYS ACRPRDCT 06040000 ANNI 00000001)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: APIC 0x00000000BBBFEF70 000068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: BOOT 0x00000000BBBFEFD8 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: SSDT 0x00000000BBBF464D 00019D (v01 BrtRef DD01BRT  00001000 INTL 20050624)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: SSDT 0x00000000BBBE3000 000655 (v01 PmRef  CpuPm    00003000 INTL 20050624)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] 2116MB HIGHMEM available.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] 887MB LOWMEM available.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] BRK [0x01bd7000, 0x01bd7fff] PGTABLE
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Zone ranges:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Normal   [mem 0x01000000-0x377fdfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   HighMem  [mem 0x377fe000-0xbbbfffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Movable zone start for each node
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Early memory node ranges
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0x00100000-0xbb6a0fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbb6a7000-0xbb7b8fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbb80f000-0xbb907fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbbb0f000-0xbbb17fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbbb1f000-0xbbb5efff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbbb9f000-0xbbbe1fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   node   0: [mem 0xbbbff000-0xbbbfffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] On node 0 totalpages: 768213
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   Normal zone: 223230 pages, LIFO batch:31
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   HighMem zone: 4233 pages used for memmap
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]   HighMem zone: 540987 pages, LIFO batch:31
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Using APIC driver default
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Reserving Intel graphics stolen memory at 0xbc000000-0xbfffffff
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] nr_irqs_gsi: 40
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000d1fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000d2000-0x000d7fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000d8000-0x000e3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e4000-0x000fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f6fbb000 s35008 r0 d22336 u57344
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 766437
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-57-generic root=UUID=d16104d1-89d7-4a45-9173-625690b88e7b ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing CPU#0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] xsave: enabled xstate_bv 0x3, cntxt size 0x240
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000bbc00)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Initializing Movable for node 0 (00000000:00000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Memory: 3016400K/3072852K available (6757K kernel code, 642K rwdata, 2916K rodata, 896K init, 788K bss, 56452K reserved, 2163948K highmem)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] virtual kernel memory layout:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]       .init : 0xc1a16000 - 0xc1af6000   ( 896 kB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]       .data : 0xc16998a8 - 0xc1a14980   (3564 kB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc16998a8   (6758 kB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] Console: colour dummy device 80x25
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] console [tty0] enabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] allocated 6291456 bytes of page_cgroup
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] hpet clockevent registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.000000] tsc: Detected 1795.486 MHz processor
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.004016] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.97 BogoMIPS (lpj=7181944)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.004021] pid_max: default: 32768 minimum: 301
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.004035] ACPI: Core revision 20140424
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015326] ACPI: All ACPI Tables successfully acquired
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015353] Security Framework initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015374] AppArmor: AppArmor initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015376] Yama: becoming mindful.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015435] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015438] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015760] Initializing cgroup subsys memory
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015797] Initializing cgroup subsys devices
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015808] Initializing cgroup subsys freezer
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015812] Initializing cgroup subsys net_cls
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015819] Initializing cgroup subsys blkio
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015826] Initializing cgroup subsys perf_event
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015829] Initializing cgroup subsys net_prio
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015839] Initializing cgroup subsys hugetlb
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015868] CPU: Physical Processor ID: 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015870] CPU: Processor Core ID: 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015876] mce: CPU supports 6 MCE banks
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015885] CPU0: Thermal monitoring enabled (TM1)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015888] process: using mwait in idle threads
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015897] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015897] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.015897] tlb_flushall_shift: -1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.016487] Freeing SMP alternatives memory: 32K (c1af6000 - c1afe000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.020009] ftrace: allocating 28621 entries in 56 pages
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.032106] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.032487] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.073658] smpboot: CPU0: Intel Celeron(R) Dual-Core CPU       T3000  @ 1.80GHz (fam: 06, model: 17, stepping: 0a)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... version:                2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... bit width:              40
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... generic registers:      2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... value mask:             000000ffffffffff
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... max period:             000000007fffffff
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... fixed-purpose events:   3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] ... event mask:             0000000700000003
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] CPU 1 irqstacks, hard=f44f2000 soft=f44f4000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] x86: Booting SMP configuration:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.076000] .... node  #0, CPUs:      #1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.008000] Initializing CPU#1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.087872] x86: Booted up 1 node, 2 CPUs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.087876] smpboot: Total of 2 processors activated (7181.94 BogoMIPS)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.087965] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088155] devtmpfs: initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088570] evm: security.selinux
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088572] evm: security.SMACK64
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088574] evm: security.SMACK64EXEC
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088575] evm: security.SMACK64TRANSMUTE
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088577] evm: security.SMACK64MMAP
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088578] evm: security.ima
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088580] evm: security.capability
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.088748] PM: Registering ACPI NVS region [mem 0xbbb5f000-0xbbb9efff] (262144 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090309] pinctrl core: initialized pinctrl subsystem
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090440] regulator-dummy: no parameters
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090482] RTC time: 17:02:07, date: 01/13/16
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] NET: Registered protocol family 16
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] EISA bus registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] cpuidle: using governor ladder
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] cpuidle: using governor menu
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] ACPI: bus type PCI registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] PCI: Using MMCONFIG for extended config space
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.090558] PCI: Using configuration type 1 for base access
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.104166] ACPI: Added _OSI(Module Device)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.104170] ACPI: Added _OSI(Processor Device)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.104172] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.104174] ACPI: Added _OSI(Processor Aggregator Device)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.104177] ACPI: Added _OSI(Linux)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.110456] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.111368] ACPI: Dynamic OEM Table Load:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.111379] ACPI: SSDT 0x00000000F4453000 000549 (v01 PmRef  Cpu0Cst  00003001 INTL 20050624)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.124338] ACPI: Dynamic OEM Table Load:
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.124346] ACPI: SSDT 0x00000000F3FBD780 00008D (v01 PmRef  ApCst    00003000 INTL 20050624)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148092] ACPI: Interpreter enabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148113] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148118] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148139] ACPI: (supports S0 S3 S4 S5)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148141] ACPI: Using IOAPIC for interrupt routing
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.148188] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.160964] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.160974] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.160982] acpi PNP0A08:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162063] PCI host bridge to bus 0000:00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162068] pci_bus 0000:00: root bus resource [bus 00-ff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162072] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162075] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162078] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162080] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162083] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162087] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162090] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162093] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162107] pci 0000:00:00.0: [8086:2a40] type 00 class 0x060000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162136] DMAR: Forcing write-buffer flush capability
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162138] DMAR: Disabling IOMMU for graphics on this chipset
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162267] pci 0000:00:02.0: [8086:2a42] type 00 class 0x030000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162285] pci 0000:00:02.0: reg 0x10: [mem 0xf4000000-0xf43fffff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162296] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162304] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x1807]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162446] pci 0000:00:02.1: [8086:2a43] type 00 class 0x038000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162461] pci 0000:00:02.1: reg 0x10: [mem 0xf4400000-0xf44fffff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162640] pci 0000:00:1a.0: [8086:2937] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162690] pci 0000:00:1a.0: reg 0x20: [io  0x1820-0x183f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162812] pci 0000:00:1a.0: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162886] pci 0000:00:1a.1: [8086:2938] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.1: reg 0x20: [io  0x1840-0x185f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.1: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.7: [8086:293c] type 00 class 0x0c0320
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.7: reg 0x10: [mem 0xf4904800-0xf4904bff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1a.7: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1b.0: [8086:293e] type 00 class 0x040300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1b.0: reg 0x10: [mem 0xf4700000-0xf4703fff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1b.0: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.0: [8086:2940] type 01 class 0x060400
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.1: [8086:2942] type 01 class 0x060400
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.2: [8086:2944] type 01 class 0x060400
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.4: [8086:2948] type 01 class 0x060400
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.0: [8086:2934] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.0: reg 0x20: [io  0x1860-0x187f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.0: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.1: [8086:2935] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.1: reg 0x20: [io  0x1880-0x189f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.1: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.2: [8086:2936] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.2: reg 0x20: [io  0x18a0-0x18bf]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.2: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.3: [8086:2939] type 00 class 0x0c0300
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.3: reg 0x20: [io  0x18c0-0x18df]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.3: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.7: [8086:293a] type 00 class 0x0c0320
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.7: reg 0x10: [mem 0xf4904c00-0xf4904fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1d.7: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162936] pci 0000:00:1e.0: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.162984] pci 0000:00:1f.0: [8086:2919] type 00 class 0x060100
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163215] pci 0000:00:1f.2: [8086:2929] type 00 class 0x010601
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163239] pci 0000:00:1f.2: reg 0x10: [io  0x1818-0x181f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163249] pci 0000:00:1f.2: reg 0x14: [io  0x180c-0x180f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163259] pci 0000:00:1f.2: reg 0x18: [io  0x1810-0x1817]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163269] pci 0000:00:1f.2: reg 0x1c: [io  0x1808-0x180b]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163279] pci 0000:00:1f.2: reg 0x20: [io  0x18e0-0x18ff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163289] pci 0000:00:1f.2: reg 0x24: [mem 0xf4904000-0xf49047ff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163346] pci 0000:00:1f.2: PME# supported from D3hot
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163472] pci 0000:00:1f.3: [8086:2930] type 00 class 0x0c0500
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163492] pci 0000:00:1f.3: reg 0x10: [mem 0x00000000-0x000000ff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163517] pci 0000:00:1f.3: reg 0x20: [io  0x1c00-0x1c1f]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163916] pci 0000:02:00.0: [14e4:1698] type 00 class 0x020000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.163948] pci 0000:02:00.0: reg 0x10: [mem 0xf4500000-0xf450ffff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.164125] pci 0000:02:00.0: PME# supported from D3hot D3cold
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.164161] pci 0000:02:00.0: System wakeup disabled by ACPI
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176173] pci 0000:00:1c.0: PCI bridge to [bus 02]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176181] pci 0000:00:1c.0:   bridge window [mem 0xf4500000-0xf45fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176276] pci 0000:00:1c.1: PCI bridge to [bus 03]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176393] pci 0000:04:00.0: [168c:002a] type 00 class 0x028000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176424] pci 0000:04:00.0: reg 0x10: [mem 0xf4600000-0xf460ffff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176568] pci 0000:04:00.0: supports D1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176570] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176670] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176681] pci 0000:00:1c.2: PCI bridge to [bus 04]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176689] pci 0000:00:1c.2:   bridge window [mem 0xf4600000-0xf46fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176801] acpiphp: Slot [1] registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176808] pci 0000:00:1c.4: PCI bridge to [bus 05-07]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176814] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176819] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf3ffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176826] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176924] pci 0000:00:1e.0: PCI bridge to [bus 0d] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176936] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176939] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176942] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176945] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176948] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176951] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176954] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176957] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.176989] pci_bus 0000:00: on NUMA node 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177566] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177642] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177714] ACPI: PCI Interrupt Link [LNKC] (IRQs *10 11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177787] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177860] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.177935] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.178009] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.178085] ACPI: PCI Interrupt Link [LNKH] (IRQs *10 11)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.178319] ACPI: Enabled 4 GPEs in block 00 to 3F
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180061] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180224] vgaarb: setting as boot device: PCI:0000:00:02.0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180224] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180224] vgaarb: loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180224] vgaarb: bridge control possible 0000:00:02.0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180480] SCSI subsystem initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180535] libata version 3.00 loaded.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180583] ACPI: bus type USB registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180619] usbcore: registered new interface driver usbfs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180636] usbcore: registered new interface driver hub
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180643] usbcore: registered new device driver usb
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.180643] PCI: Using ACPI for IRQ routing
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190445] PCI: pci_cache_line_size set to 64 bytes
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190671] e820: reserve RAM buffer [mem 0x0009d400-0x0009ffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190674] e820: reserve RAM buffer [mem 0xbb6a1000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190679] e820: reserve RAM buffer [mem 0xbb7b9000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190682] e820: reserve RAM buffer [mem 0xbb908000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190686] e820: reserve RAM buffer [mem 0xbbb18000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190690] e820: reserve RAM buffer [mem 0xbbb5f000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190693] e820: reserve RAM buffer [mem 0xbbbe2000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190696] e820: reserve RAM buffer [mem 0xbbc00000-0xbbffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190886] NetLabel: Initializing
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190888] NetLabel:  domain hash size = 128
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190890] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190906] NetLabel:  unlabeled traffic allowed by default
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190927] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190927] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.190927] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.193015] Switched to clocksource hpet
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.204648] AppArmor: AppArmor Filesystem Enabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.204703] pnp: PnP ACPI init
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.204732] ACPI: bus type PNP registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.204932] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.204987] pnp 00:01: Plug and Play ACPI device, IDs SYN1b22 SYN1b00 SYN0002 PNP0f13 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205161] system 00:02: [mem 0xfed00000-0xfed003ff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205167] system 00:02: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205261] system 00:03: [io  0x0480-0x048f] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205265] system 00:03: [io  0xffff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205269] system 00:03: [io  0xffff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205275] system 00:03: [io  0x0400-0x047f] could not be reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205279] system 00:03: [io  0x1180-0x11ff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205282] system 00:03: [io  0xfe00] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205286] system 00:03: [mem 0xff800000-0xff800fff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205290] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205346] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205578] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205582] system 00:05: [mem 0xfed10000-0xfed13fff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205586] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205590] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205593] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205597] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205601] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205767] pnp: PnP ACPI: found 6 devices
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205769] ACPI: bus type PNP unregistered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.205777] PnPBIOS: Disabled by ACPI PNP
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243668] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243674] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243685] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243689] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243692] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243702] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243706] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243731] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243734] pci 0000:00:1c.1: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243737] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243741] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243744] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243747] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243751] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243766] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243772] pci 0000:00:1c.1: BAR 14: assigned [mem 0xc0200000-0xc03fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243782] pci 0000:00:1c.1: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243792] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0600000-0xc07fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243797] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243802] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243806] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243816] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0800000-0xc08000ff 64bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243828] pci 0000:00:1c.0: PCI bridge to [bus 02]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243832] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243839] pci 0000:00:1c.0:   bridge window [mem 0xf4500000-0xf45fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243844] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243851] pci 0000:00:1c.1: PCI bridge to [bus 03]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243855] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243861] pci 0000:00:1c.1:   bridge window [mem 0xc0200000-0xc03fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243866] pci 0000:00:1c.1:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243873] pci 0000:00:1c.2: PCI bridge to [bus 04]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243877] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243883] pci 0000:00:1c.2:   bridge window [mem 0xf4600000-0xf46fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243888] pci 0000:00:1c.2:   bridge window [mem 0xc0600000-0xc07fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243895] pci 0000:00:1c.4: PCI bridge to [bus 05-07]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243898] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243904] pci 0000:00:1c.4:   bridge window [mem 0xf2000000-0xf3ffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243909] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243916] pci 0000:00:1e.0: PCI bridge to [bus 0d]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243929] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243932] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243935] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243938] pci_bus 0000:00: resource 7 [mem 0x000d8000-0x000dbfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243941] pci_bus 0000:00: resource 8 [mem 0x000dc000-0x000dffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243944] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243947] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xdfffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243950] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243953] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243956] pci_bus 0000:02: resource 1 [mem 0xf4500000-0xf45fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243959] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243962] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243965] pci_bus 0000:03: resource 1 [mem 0xc0200000-0xc03fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243967] pci_bus 0000:03: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243970] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243973] pci_bus 0000:04: resource 1 [mem 0xf4600000-0xf46fffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243976] pci_bus 0000:04: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243979] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243982] pci_bus 0000:05: resource 1 [mem 0xf2000000-0xf3ffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243985] pci_bus 0000:05: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243988] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243991] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243994] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.243997] pci_bus 0000:0d: resource 7 [mem 0x000d8000-0x000dbfff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244008] pci_bus 0000:0d: resource 8 [mem 0x000dc000-0x000dffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244011] pci_bus 0000:0d: resource 9 [mem 0x000e0000-0x000e3fff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244014] pci_bus 0000:0d: resource 10 [mem 0xc0000000-0xdfffffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244017] pci_bus 0000:0d: resource 11 [mem 0xf0000000-0xfebfffff]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244059] NET: Registered protocol family 2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244356] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244374] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244400] TCP: Hash tables configured (established 8192 bind 8192)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244427] TCP: reno registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244431] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244438] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244495] NET: Registered protocol family 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.244518] pci 0000:00:02.0: Video device with shadowed ROM
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.246135] PCI: CLS 64 bytes, default 64
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.246213] Trying to unpack rootfs image as initramfs...
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731310] Freeing initrd memory: 18608K (f5b98000 - f6dc4000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731530] Simple Boot Flag at 0x57 set to 0x1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731755] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731768] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731869] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.731916] Scanning for low memory corruption every 60 seconds
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.732347] futex hash table entries: 512 (order: 3, 32768 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.732374] Initialise system trusted keyring
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.732409] audit: initializing netlink subsys (disabled)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.732432] audit: type=2000 audit(1452704527.732:1): initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.732851] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.735984] zpool: loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.735987] zbud: loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.736124] VFS: Disk quotas dquot_6.5.2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.736192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.736969] fuse init (API version 7.23)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737130] msgmni has been set to 1701
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737232] Key type big_key registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737672] Key type asymmetric registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737677] Asymmetric key parser 'x509' registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737702] bounce: pool size: 64 pages
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737716] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737774] io scheduler noop registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737778] io scheduler deadline registered (default)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.737872] io scheduler cfq registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738177] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738373] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738559] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738744] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738877] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.738905] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739002] vesafb: mode is 1024x768x32, linelength=4096, pages=0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739004] vesafb: scrolling: redraw
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739007] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739781] vesafb: framebuffer at 0xd0000000, mapped to 0xf8080000, using 3072k, total 3072k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739955] Console: switching to colour frame buffer device 128x48
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.739985] fb0: VESA VGA frame buffer device
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.740055] intel_idle: does not run on family 6 model 23
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.742528] ACPI: AC Adapter [ADP1] (on-line)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.742688] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.744930] ACPI: Lid Switch [LID0]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.745009] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.745014] ACPI: Sleep Button [SLPB]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.745083] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.745087] ACPI: Power Button [PWRF]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.746476] Monitor-Mwait will be used to enter C-1 state
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.746483] Monitor-Mwait will be used to enter C-2 state
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.746489] tsc: Marking TSC unstable due to TSC halts in idle
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.746494] ACPI: acpi_idle registered with cpuidle
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.769675] thermal LNXTHERM:00: registered as thermal_zone0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.769679] ACPI: Thermal Zone [TZS0] (76 C)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.779849] thermal LNXTHERM:01: registered as thermal_zone1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.779852] ACPI: Thermal Zone [TZS1] (75 C)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.779908] GHES: HEST is not enabled!
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.780029] isapnp: Scanning for PnP cards...
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.784206] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.796826] Linux agpgart interface v0.103
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.796975] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.797005] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.797345] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.797488] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.799913] brd: module loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801259] loop: module loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801650] libphy: Fixed MDIO Bus: probed
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801656] tun: Universal TUN/TAP device driver, 1.6
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801657] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801725] PPP generic driver version 2.4.2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801815] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801823] ehci-pci: EHCI PCI platform driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.801995] ehci-pci 0000:00:1a.7: EHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.802004] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.802019] ehci-pci 0000:00:1a.7: debug port 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.805929] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.805966] ehci-pci 0000:00:1a.7: irq 20, io mem 0xf4904800
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816035] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816094] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816098] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816101] usb usb1: Product: EHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816104] usb usb1: Manufacturer: Linux 3.16.0-57-generic ehci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816106] usb usb1: SerialNumber: 0000:00:1a.7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816285] hub 1-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816298] hub 1-0:1.0: 4 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816665] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816676] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.816691] ehci-pci 0000:00:1d.7: debug port 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.820610] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.820642] ehci-pci 0000:00:1d.7: irq 23, io mem 0xf4904c00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832039] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832093] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832096] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832099] usb usb2: Product: EHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832102] usb usb2: Manufacturer: Linux 3.16.0-57-generic ehci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832104] usb usb2: SerialNumber: 0000:00:1d.7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832276] hub 2-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832285] hub 2-0:1.0: 8 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832627] ehci-platform: EHCI generic platform driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832648] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832656] ohci-pci: OHCI PCI platform driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832678] ohci-platform: OHCI generic platform driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832694] uhci_hcd: USB Universal Host Controller Interface driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832834] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832845] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832852] uhci_hcd 0000:00:1a.0: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832875] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001820
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832938] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832941] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832944] usb usb3: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832947] usb usb3: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.832950] usb usb3: SerialNumber: 0000:00:1a.0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833181] hub 3-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833191] hub 3-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833449] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833457] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833464] uhci_hcd 0000:00:1a.1: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833485] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001840
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833546] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833549] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833552] usb usb4: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833555] usb usb4: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833557] usb usb4: SerialNumber: 0000:00:1a.1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833722] hub 4-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833732] hub 4-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.833996] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834004] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834011] uhci_hcd 0000:00:1d.0: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834031] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834094] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834097] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834100] usb usb5: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834103] usb usb5: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834105] usb usb5: SerialNumber: 0000:00:1d.0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834296] hub 5-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834310] hub 5-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834570] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834578] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834585] uhci_hcd 0000:00:1d.1: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834620] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001880
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834681] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834684] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834687] usb usb6: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834690] usb usb6: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834693] usb usb6: SerialNumber: 0000:00:1d.1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834857] hub 6-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.834867] hub 6-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835117] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835125] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835132] uhci_hcd 0000:00:1d.2: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835163] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835227] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835231] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835234] usb usb7: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835236] usb usb7: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835239] usb usb7: SerialNumber: 0000:00:1d.2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835452] hub 7-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835462] hub 7-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835719] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835727] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835734] uhci_hcd 0000:00:1d.3: detected 2 ports
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835755] uhci_hcd 0000:00:1d.3: irq 18, io base 0x000018c0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835816] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835819] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835822] usb usb8: Product: UHCI Host Controller
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835825] usb usb8: Manufacturer: Linux 3.16.0-57-generic uhci_hcd
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835828] usb usb8: SerialNumber: 0000:00:1d.3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.835996] hub 8-0:1.0: USB hub found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.836036] hub 8-0:1.0: 2 ports detected
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.836330] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.857314] i8042: Detected active multiplexing controller, rev 1.1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.869976] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.869982] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.870032] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.870074] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.870118] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.870303] mousedev: PS/2 mouse device common for all mice
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871345] rtc_cmos 00:04: RTC can wake from S4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871488] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871516] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871595] device-mapper: uevent: version 1.0.3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871709] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871748] platform eisa.0: Probing EISA bus 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871752] platform eisa.0: EISA: Cannot allocate resource for mainboard
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871755] platform eisa.0: Cannot allocate resource for EISA slot 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871758] platform eisa.0: Cannot allocate resource for EISA slot 2
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871761] platform eisa.0: Cannot allocate resource for EISA slot 3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871764] platform eisa.0: Cannot allocate resource for EISA slot 4
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871766] platform eisa.0: Cannot allocate resource for EISA slot 5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871769] platform eisa.0: Cannot allocate resource for EISA slot 6
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871772] platform eisa.0: Cannot allocate resource for EISA slot 7
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871775] platform eisa.0: Cannot allocate resource for EISA slot 8
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871778] platform eisa.0: EISA: Detected 0 cards
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871798] cpufreq-nforce2: No nForce2 chipset.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871809] ledtrig-cpu: registered to indicate activity on CPUs
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.871976] TCP: cubic registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.872199] NET: Registered protocol family 10
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.872488] NET: Registered protocol family 17
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.872508] Key type dns_resolver registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.872832] Using IPI No-Shortcut mode
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.872982] Loading compiled-in X.509 certificates
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.877903] Loaded X.509 cert 'Magrathea: Glacier signing key: 16d7bd9a3dd39a4e65d6d769c5f9f5ddc18b81cb'
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.877925] registered taskstats version 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.880969] Key type trusted registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886423] Key type encrypted registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886435] AppArmor: AppArmor sha1 policy hashing enabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886440] ima: No TPM chip found, activating TPM-bypass!
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886465] evm: HMAC attrs: 0x1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886940]   Magic number: 0:709:36
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886961] bdi 7:1: hash matches
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.886965] misc loop-control: hash matches
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.887049] rtc_cmos 00:04: setting system clock to 2016-01-13 17:02:08 UTC (1452704528)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.887146] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.887148] EDD information not available.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.887354] PM: Hibernation image not present or could not be loaded.
Jan 13 17:02:26 gandhi-winbuntu kernel: [    0.901678] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.089981] isapnp: No Plug & Play device found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.335779] ACPI: Battery Slot [BAT0] (battery present)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.336240] Freeing unused kernel memory: 896K (c1a16000 - c1af6000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.336327] Write protecting the kernel text: 6760k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.336475] Write protecting the kernel read-only data: 2920k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.336476] NX-protecting the kernel data: 5528k
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.354955] systemd-udevd[98]: starting version 204
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.403285] pps_core: LinuxPPS API ver. 1 registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.403289] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.409146] PTP clock support registered
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.417834] ahci 0000:00:1f.2: version 3.0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.418024] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.418070] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.418104] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.418109] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.422738] tg3.c:v3.137 (May 11, 2014)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.448428] scsi0 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.456315] scsi1 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.465683] scsi2 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.472041] scsi3 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479470] scsi4 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479671] scsi5 : ahci
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479781] ata1: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904100 irq 44
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479792] ata2: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904180 irq 44
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479794] ata3: DUMMY
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479796] ata4: DUMMY
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479799] ata5: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904300 irq 44
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.479803] ata6: SATA max UDMA/133 abar m2048@0xf4904000 port 0xf4904380 irq 44
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.480616] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:1d:72:fe:9c:f3
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.480621] tg3 0000:02:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.480625] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.480628] tg3 0000:02:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.796062] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.859339] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.859343] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.860721] ata1.00: configured for UDMA/133
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.860894] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 1A11 PQ: 0 ANSI: 5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.861300] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.861325] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.861376] sd 0:0:0:0: [sda] Write Protect is off
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.861380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.861422] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.909353]  sda: sda1 sda2 sda3 < sda5 sda6 >
Jan 13 17:02:26 gandhi-winbuntu kernel: [    1.910055] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.180058] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.196775] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633B, AC01, max UDMA/100
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.196779] ata2.00: applying bridge limits
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.210144] ata2.00: configured for UDMA/100
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.212832] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633B  AC01 PQ: 0 ANSI: 5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.231952] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.231956] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.232286] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.232412] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.446523] psmouse serio2: synaptics: queried max coordinates: x [..5720], y [..4780]
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.550775] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa44000/0xa0000, board id: 0, fw id: 529512
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.552055] ata5: SATA link down (SStatus 0 SControl 300)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.618349] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9
Jan 13 17:02:26 gandhi-winbuntu kernel: [    2.872054] ata6: SATA link down (SStatus 0 SControl 300)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    3.341654] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.081421] random: nonblocking pool is initialized
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.984146] init: plymouth-upstart-bridge main process (166) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.984166] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.987331] init: plymouth-upstart-bridge main process (175) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.987349] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.990517] init: plymouth-upstart-bridge main process (176) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.990536] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.993664] init: plymouth-upstart-bridge main process (177) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.993682] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.996847] init: plymouth-upstart-bridge main process (178) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.996866] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    4.999989] init: plymouth-upstart-bridge main process (179) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.000037] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.003153] init: plymouth-upstart-bridge main process (180) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.003172] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.006319] init: plymouth-upstart-bridge main process (181) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.006338] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.009462] init: plymouth-upstart-bridge main process (182) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.009481] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.012899] init: plymouth-upstart-bridge main process (183) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.012918] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.016147] init: plymouth-upstart-bridge main process (184) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.016168] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.019272] init: plymouth-upstart-bridge main process (185) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.019291] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.022446] init: plymouth-upstart-bridge main process (186) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.022466] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.025656] init: plymouth-upstart-bridge main process (187) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.025675] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.028870] init: plymouth-upstart-bridge main process (188) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.028891] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.032045] init: plymouth-upstart-bridge main process (189) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.032065] init: plymouth-upstart-bridge main process ended, respawning
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.035250] init: plymouth-upstart-bridge main process (190) terminated with status 1
Jan 13 17:02:26 gandhi-winbuntu kernel: [    5.035269] init: plymouth-upstart-bridge respawning too fast, stopped
Jan 13 17:02:26 gandhi-winbuntu kernel: [    6.311241] Adding 3070972k swap on /dev/sda6.  Priority:-1 extents:1 across:3070972k FS
Jan 13 17:02:26 gandhi-winbuntu kernel: [    7.531516] systemd-udevd[295]: starting version 204
Jan 13 17:02:26 gandhi-winbuntu kernel: [    8.813206] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Jan 13 17:02:26 gandhi-winbuntu kernel: [    9.048683] lp: driver loaded but no devices found
Jan 13 17:02:26 gandhi-winbuntu kernel: [    9.171926] media: Linux media interface: v0.10
Jan 13 17:02:26 gandhi-winbuntu kernel: [    9.236612] Linux video capture interface: v2.00
Jan 13 17:02:26 gandhi-winbuntu kernel: [    9.391609] ppdev: user-space parallel port driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.327771] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.369180] [drm] Initialized drm 1.1.0 20060810
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.396905] wmi: Mapper loaded
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469931] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20140424/utaddress-254)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469943] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469947] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20140424/utaddress-254)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469953] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469955] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20140424/utaddress-254)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469961] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.469963] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.850737] cfg80211: Calling CRDA to update world regulatory domain
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.935683] [drm] Memory usable by graphics device = 2048M
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.935689] checking generic (d0000000 300000) vs hw (d0000000 10000000)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.935692] fb: switching to inteldrmfb from VESA VGA
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.935736] Console: switching to colour dummy device 80x25
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.936245] [drm] Replacing VGA console driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.984094] i915 0000:00:02.0: irq 45 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.984107] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.984109] [drm] Driver supports precise vblank timestamp query.
Jan 13 17:02:26 gandhi-winbuntu kernel: [   10.984190] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.133534] fbcon: inteldrmfb (fb0) is primary device
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.133623] Console: switching to colour frame buffer device 170x48
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.133666] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.133669] i915 0000:00:02.0: registered panic notifier
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.184720] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.184935] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input12
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.185174] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.377210] acer_wmi: Acer Laptop ACPI-WMI Extras
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.386077] acer_wmi: Function bitmap for Communication Device: 0x83
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.386587] acer_wmi: Disabling ACPI video driver
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.387009] input: Acer BMA150 accelerometer as /devices/virtual/input/input13
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.523877] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624160] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624166] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624169] sound hdaudioC0D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624172] sound hdaudioC0D0:    mono: mono_out=0x0
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624175] sound hdaudioC0D0:    dig-out=0x1e/0x0
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624177] sound hdaudioC0D0:    inputs:
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624180] sound hdaudioC0D0:      Internal Mic=0x19
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624183] sound hdaudioC0D0:      Mic=0x18
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.624186] sound hdaudioC0D0:      Line=0x1a
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.714329] ath: EEPROM regdomain: 0x65
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.714333] ath: EEPROM indicates we should expect a direct regpair map
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.714336] ath: Country alpha2 being used: 00
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.714338] ath: Regpair used: 0x65
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.738844] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.738983] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.739111] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.739229] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.764995] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan 13 17:02:26 gandhi-winbuntu kernel: [   11.765597] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xf8180000, irq=18
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272466] cfg80211: World regulatory domain updated:
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272473] cfg80211:  DFS Master region: unset
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272475] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272479] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272482] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272485] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272488] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.272491] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.887545] audit: type=1400 audit(1452704541.494:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=472 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.887556] audit: type=1400 audit(1452704541.494:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=472 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.887563] audit: type=1400 audit(1452704541.494:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=472 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.888646] audit: type=1400 audit(1452704541.498:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.888656] audit: type=1400 audit(1452704541.498:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.888663] audit: type=1400 audit(1452704541.498:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.889352] audit: type=1400 audit(1452704541.498:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.889359] audit: type=1400 audit(1452704541.498:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.889721] audit: type=1400 audit(1452704541.498:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   13.891129] audit: type=1400 audit(1452704541.498:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   17.364712] init: failsafe main process (622) killed by TERM signal
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299109] audit_printk_skb: 24 callbacks suppressed
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299114] audit: type=1400 audit(1452704546.906:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299125] audit: type=1400 audit(1452704546.906:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299132] audit: type=1400 audit(1452704546.906:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299823] audit: type=1400 audit(1452704546.906:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.299830] audit: type=1400 audit(1452704546.906:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu kernel: [   19.300249] audit: type=1400 audit(1452704546.910:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=777 comm="apparmor_parser"
Jan 13 17:02:26 gandhi-winbuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan 13 17:02:27 gandhi-winbuntu ntpdate[724]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jan 13 17:02:27 gandhi-winbuntu ntpdate[724]: no servers can be used, exiting
Jan 13 17:02:27 gandhi-winbuntu kernel: [   20.320326] audit: type=1400 audit(1452704547.930:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=776 comm="apparmor_parser"
Jan 13 17:02:27 gandhi-winbuntu kernel: [   20.320339] audit: type=1400 audit(1452704547.930:27): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=776 comm="apparmor_parser"
Jan 13 17:02:27 gandhi-winbuntu kernel: [   20.320765] audit: type=1400 audit(1452704547.930:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=776 comm="apparmor_parser"
Jan 13 17:02:28 gandhi-winbuntu kernel: [   20.464857] audit: type=1400 audit(1452704548.074:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=784 comm="apparmor_parser"
Jan 13 17:02:29 gandhi-winbuntu dbus[814]: [system] AppArmor D-Bus mediation is enabled
Jan 13 17:02:29 gandhi-winbuntu anacron[871]: Anacron 2.3 started on 2016-01-13
Jan 13 17:02:30 gandhi-winbuntu anacron[871]: Normal exit (0 jobs run)
Jan 13 17:02:30 gandhi-winbuntu cron[846]: (CRON) INFO (pidfile fd = 3)
Jan 13 17:02:30 gandhi-winbuntu cron[926]: (CRON) STARTUP (fork ok)
Jan 13 17:02:30 gandhi-winbuntu acpid: starting up with netlink and the input layer
Jan 13 17:02:31 gandhi-winbuntu bluetoothd[949]: Bluetooth daemon 4.101
Jan 13 17:02:31 gandhi-winbuntu bluetoothd[949]: Starting SDP server
Jan 13 17:02:31 gandhi-winbuntu cron[926]: (CRON) INFO (Running @reboot jobs)
Jan 13 17:02:31 gandhi-winbuntu pommed[964]: pommed v1.39 Apple laptops hotkeys handler
Jan 13 17:02:31 gandhi-winbuntu pommed[964]: Copyright (C) 2006-2011 Julien BLACHE <jb@jblache.org>
Jan 13 17:02:31 gandhi-winbuntu pommed[964]: Unknown non-Apple machine
Jan 13 17:02:31 gandhi-winbuntu acpid: 9 rules loaded
Jan 13 17:02:31 gandhi-winbuntu acpid: waiting for events: event logging is off
Jan 13 17:02:32 gandhi-winbuntu ModemManager[941]: <info>  ModemManager (version 1.0.0) starting...
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594175] Bluetooth: Core ver 2.19
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594204] NET: Registered protocol family 31
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594206] Bluetooth: HCI device and connection manager initialized
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594215] Bluetooth: HCI socket layer initialized
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594218] Bluetooth: L2CAP socket layer initialized
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.594235] Bluetooth: SCO socket layer initialized
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: DIS cannot start: GATT is disabled
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init deviceinfo plugin
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init proximity plugin
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init time plugin
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init alert plugin
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init thermometer plugin
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.901311] Bluetooth: RFCOMM TTY layer initialized
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.901324] Bluetooth: RFCOMM socket layer initialized
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.901336] Bluetooth: RFCOMM ver 1.11
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.977053] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.977058] Bluetooth: BNEP filters: protocol multicast
Jan 13 17:02:32 gandhi-winbuntu kernel: [   24.977068] Bluetooth: BNEP socket layer initialized
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Successfully dropped root privileges.
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: avahi-daemon 0.6.31 starting up.
Jan 13 17:02:32 gandhi-winbuntu kernel: [   25.005413] init: cups main process (974) killed by HUP signal
Jan 13 17:02:32 gandhi-winbuntu kernel: [   25.005434] init: cups main process ended, respawning
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Successfully called chroot().
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Successfully dropped remaining capabilities.
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: No service file found in /etc/avahi/services.
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Failed to init gatt_example plugin
Jan 13 17:02:32 gandhi-winbuntu bluetoothd[949]: Bluetooth Management interface initialized
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Network interface enumeration completed.
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 13 17:02:32 gandhi-winbuntu avahi-daemon[1007]: Server startup complete. Host name is gandhi-winbuntu.local. Local service cookie is 1457510724.
Jan 13 17:02:35 gandhi-winbuntu whoopsie[925]: whoopsie 0.2.24.6ubuntu2 starting up.
Jan 13 17:02:35 gandhi-winbuntu whoopsie[925]: Using lock path: /var/lock/whoopsie/lock
Jan 13 17:02:36 gandhi-winbuntu whoopsie[1053]: Could not get the Network Manager state:
Jan 13 17:02:36 gandhi-winbuntu whoopsie[1053]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Jan 13 17:02:37 gandhi-winbuntu NetworkManager[1080]: <info> NetworkManager (version 0.9.8.8) is starting...
Jan 13 17:02:37 gandhi-winbuntu NetworkManager[1080]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jan 13 17:02:37 gandhi-winbuntu NetworkManager[1080]: <info> WEXT support is enabled
Jan 13 17:02:37 gandhi-winbuntu NetworkManager[1080]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan 13 17:02:37 gandhi-winbuntu NetworkManager[1080]: <info> DNS: loaded plugin dnsmasq
Jan 13 17:02:37 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan 13 17:02:37 gandhi-winbuntu ModemManager[941]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0': not supported by any plugin
Jan 13 17:02:37 gandhi-winbuntu ModemManager[941]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0': not supported by any plugin
Jan 13 17:02:38 gandhi-winbuntu polkitd[1086]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jan 13 17:02:38 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: init!
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: update_system_hostname
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:       interface-parser: parsing file /etc/network/interfaces
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:       interface-parser: finished parsing file /etc/network/interfaces
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPluginIfupdown: management mode: unmanaged
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/wlan0, iface: wlan0)
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: end _init.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ofono: init!
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ofono: end _init.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]: <info> Loaded plugin (null): (null)
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    Ifupdown: get unmanaged devices count: 0
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: (138803088) ... get_connections.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ifupdown: (138803088) ... get_connections (managed=false): return empty list.
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing 7monkeyslairthesequel ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection '7monkeyslairthesequel'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing 7monkeyslairthesequal ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection '7monkeyslairthesequal'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing Doktor Mohlberg's Evil Lair ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'Doktor Mohlberg's Evil Lair'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing BTHub5-NQ2N ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'BTHub5-NQ2N'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing BTHub5-8KQ7 ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'BTHub5-8KQ7'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing VM111970-2G ... 
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'VM111970-2G'
Jan 13 17:02:38 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing asis1646 ... 
Jan 13 17:02:39 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'asis1646'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing HOTELSARINENA ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'HOTELSARINENA'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing TALKTALK-C8F428 ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'TALKTALK-C8F428'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing BTHub5-FKPR ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'BTHub5-FKPR'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing 7monkeyslair ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection '7monkeyslair'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing BTHub5-3J2Q ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'BTHub5-3J2Q'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing Wired connection 1 ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'Wired connection 1'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile: parsing EE-BrightBox-q42t93 ... 
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    keyfile:     read connection 'EE-BrightBox-q42t93'
Jan 13 17:02:39 gandhi-winbuntu accounts-daemon[1118]: started daemon version 0.6.35
Jan 13 17:02:39 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ofono: (138842176) ... get_connections.
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    SCPlugin-Ofono: (138842176) connections count: 0
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]:    Ifupdown: get unmanaged devices count: 0
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/ieee80211/phy0/rfkill1) (driver ath9k)
Jan 13 17:02:39 gandhi-winbuntu NetworkManager[1080]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/platform/acer-wmi/rfkill/rfkill0) (platform driver acer-wmi)
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> Networking is enabled by state file
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <warn> failed to allocate link cache: (-12) Object not found
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): carrier is OFF
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): new Ethernet device (driver: 'tg3' ifindex: 2)
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 13 17:02:40 gandhi-winbuntu kernel: [   32.689662] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): bringing up device.
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): preparing device.
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): using nl80211 for WiFi device control
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): driver supports Access Point (AP) mode
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): bringing up device.
Jan 13 17:02:40 gandhi-winbuntu kernel: [   32.796632] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): preparing device.
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 13 17:02:40 gandhi-winbuntu kernel: [   32.813655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 13 17:02:40 gandhi-winbuntu dbus[814]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> urfkill disappeared from the bus
Jan 13 17:02:40 gandhi-winbuntu NetworkManager[1080]: <info> ModemManager available in the bus
Jan 13 17:02:41 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> wpa_supplicant started
Jan 13 17:02:41 gandhi-winbuntu wpa_supplicant[1136]: Successfully initialized wpa_supplicant
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0) supports 4 scan SSIDs
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <warn> Trying to remove a non-existant call id.
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jan 13 17:02:41 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0) supports 4 scan SSIDs
Jan 13 17:02:41 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:02:41 gandhi-winbuntu acpid: client connected from 1115[0:0]
Jan 13 17:02:41 gandhi-winbuntu acpid: 1 client rule loaded
Jan 13 17:02:42 gandhi-winbuntu wpa_supplicant[1140]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jan 13 17:02:42 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Auto-activating connection 'VM111970-2G'.
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) starting connection 'VM111970-2G'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> NetworkManager state is now CONNECTING
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 13 17:02:42 gandhi-winbuntu whoopsie[1053]: offline
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0/wireless): connection 'VM111970-2G' has security, and secrets exist.  No new secrets needed.
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: added 'ssid' value 'VM111970-2G'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: added 'scan_ssid' value '1'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: added 'auth_alg' value 'OPEN'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: added 'psk' value '<omitted>'
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 13 17:02:42 gandhi-winbuntu NetworkManager[1080]: <info> Config: set interface ap_scan to 1
Jan 13 17:02:42 gandhi-winbuntu wpa_supplicant[1140]: wlan0: SME: Trying to authenticate with 50:6a:03:23:d9:80 (SSID='VM111970-2G' freq=2462 MHz)
Jan 13 17:02:42 gandhi-winbuntu kernel: [   35.377087] wlan0: authenticate with 50:6a:03:23:d9:80
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.389971] wlan0: send auth to 50:6a:03:23:d9:80 (try 1/3)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: Trying to associate with 50:6a:03:23:d9:80 (SSID='VM111970-2G' freq=2462 MHz)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.394511] wlan0: authenticated
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.396085] wlan0: associate with 50:6a:03:23:d9:80 (try 1/3)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: Associated with 50:6a:03:23:d9:80
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.402158] wlan0: RX AssocResp from 50:6a:03:23:d9:80 (capab=0x411 status=0 aid=3)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.402216] wlan0: associated
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.402250] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.402320] cfg80211: Calling CRDA for country: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406881] ath: EEPROM regdomain: 0x833a
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406885] ath: EEPROM indicates we should expect a country code
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406888] ath: doing EEPROM country->regdmn map search
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406890] ath: country maps to regdmn code: 0x37
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406892] ath: Country alpha2 being used: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406893] ath: Regpair used: 0x37
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406896] ath: regdomain 0x833a dynamically updated by country IE
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406927] cfg80211: Regulatory domain changed to country: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406929] cfg80211:  DFS Master region: unset
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406931] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406935] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406938] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406940] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406943] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.406946] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Key negotiation completed with 50:6a:03:23:d9:80 [PTK=CCMP GTK=TKIP]
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-CONNECTED - Connection to 50:6a:03:23:d9:80 completed [id=0 id_str=]
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: SME: Trying to authenticate with 50:6a:03:23:d9:80 (SSID='VM111970-2G' freq=2462 MHz)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.526525] wlan0: deauthenticating from 50:6a:03:23:d9:80 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.534546] cfg80211: Calling CRDA to update world regulatory domain
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.534616] wlan0: authenticate with 50:6a:03:23:d9:80
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: 4-way handshake -> authenticating
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-DISCONNECTED bssid=50:6a:03:23:d9:80 reason=2 locally_generated=1
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.541710] wlan0: send auth to 50:6a:03:23:d9:80 (try 1/3)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542247] cfg80211: World regulatory domain updated:
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542253] cfg80211:  DFS Master region: unset
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542255] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542259] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542262] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542265] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542268] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.542270] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <warn> Connection disconnected (reason -2)
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: Trying to associate with 50:6a:03:23:d9:80 (SSID='VM111970-2G' freq=2462 MHz)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.545073] wlan0: authenticated
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.548060] wlan0: associate with 50:6a:03:23:d9:80 (try 1/3)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: Associated with 50:6a:03:23:d9:80
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.554125] wlan0: RX AssocResp from 50:6a:03:23:d9:80 (capab=0x411 status=0 aid=3)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.554177] wlan0: associated
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.554220] cfg80211: Calling CRDA for country: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558686] ath: EEPROM regdomain: 0x833a
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558690] ath: EEPROM indicates we should expect a country code
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558694] ath: doing EEPROM country->regdmn map search
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558696] ath: country maps to regdmn code: 0x37
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558699] ath: Country alpha2 being used: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558701] ath: Regpair used: 0x37
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558703] ath: regdomain 0x833a dynamically updated by country IE
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558734] cfg80211: Regulatory domain changed to country: GB
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558736] cfg80211:  DFS Master region: unset
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558739] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558742] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558745] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558748] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558750] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jan 13 17:02:43 gandhi-winbuntu kernel: [   35.558753] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Key negotiation completed with 50:6a:03:23:d9:80 [PTK=CCMP GTK=TKIP]
Jan 13 17:02:43 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-CONNECTED - Connection to 50:6a:03:23:d9:80 completed [id=0 id_str=]
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'VM111970-2G'.
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> dhclient started with pid 1199
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 13 17:02:43 gandhi-winbuntu dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jan 13 17:02:43 gandhi-winbuntu dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jan 13 17:02:43 gandhi-winbuntu dhclient: All rights reserved.
Jan 13 17:02:43 gandhi-winbuntu dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan 13 17:02:43 gandhi-winbuntu dhclient: 
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 13 17:02:43 gandhi-winbuntu dhclient: Listening on LPF/wlan0/00:26:5e:17:cc:41
Jan 13 17:02:43 gandhi-winbuntu dhclient: Sending on   LPF/wlan0/00:26:5e:17:cc:41
Jan 13 17:02:43 gandhi-winbuntu dhclient: Sending on   Socket/fallback
Jan 13 17:02:43 gandhi-winbuntu dhclient: DHCPREQUEST of 192.168.0.5 on wlan0 to 255.255.255.255 port 67 (xid=0x1c20038e)
Jan 13 17:02:43 gandhi-winbuntu dhclient: DHCPACK of 192.168.0.5 from 192.168.0.1
Jan 13 17:02:43 gandhi-winbuntu dhclient: bound to 192.168.0.5 -- renewal in 35452 seconds.
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info>   address 192.168.0.5
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info>   prefix 24 (255.255.255.0)
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info>   gateway 192.168.0.1
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info>   hostname 'gandhi-winbuntu'
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info>   nameserver '192.168.0.1'
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan 13 17:02:43 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jan 13 17:02:43 gandhi-winbuntu avahi-daemon[1007]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.5.
Jan 13 17:02:43 gandhi-winbuntu avahi-daemon[1007]: New relevant interface wlan0.IPv4 for mDNS.
Jan 13 17:02:43 gandhi-winbuntu avahi-daemon[1007]: Registering new address record for 192.168.0.5 on wlan0.IPv4.
Jan 13 17:02:44 gandhi-winbuntu avahi-daemon[1007]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::226:5eff:fe17:cc41.
Jan 13 17:02:44 gandhi-winbuntu avahi-daemon[1007]: New relevant interface wlan0.IPv6 for mDNS.
Jan 13 17:02:44 gandhi-winbuntu avahi-daemon[1007]: Registering new address record for fe80::226:5eff:fe17:cc41 on wlan0.*.
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> Policy set 'VM111970-2G' (wlan0) as default for IPv4 routing and DNS.
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> DNS: starting dnsmasq...
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <warn> dnsmasq not available on the bus, can't update servers.
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <error> [1452704564.772088] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <warn> DNS: plugin dnsmasq update failed
Jan 13 17:02:44 gandhi-winbuntu NetworkManager[1080]: <info> Writing DNS information to /sbin/resolvconf
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: started, version 2.68 cache disabled
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: DBus support enabled: connected to system bus
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: warning: no upstream servers configured
Jan 13 17:02:45 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) successful, device activated.
Jan 13 17:02:45 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan 13 17:02:45 gandhi-winbuntu NetworkManager[1080]: <warn> dnsmasq appeared on DBus: :1.17
Jan 13 17:02:45 gandhi-winbuntu NetworkManager[1080]: <info> Writing DNS information to /sbin/resolvconf
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: setting upstream servers from DBus
Jan 13 17:02:45 gandhi-winbuntu dnsmasq[1219]: using nameserver 192.168.0.1#53
Jan 13 17:02:45 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan 13 17:02:45 gandhi-winbuntu whoopsie[1053]: online
Jan 13 17:02:47 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan 13 17:02:48 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan 13 17:02:49 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan 13 17:02:49 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Successfully called chroot.
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Successfully dropped privileges.
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Successfully limited resources.
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Running.
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Canary thread running.
Jan 13 17:02:49 gandhi-winbuntu rtkit-daemon[1431]: Watchdog thread running.
Jan 13 17:02:50 gandhi-winbuntu anacron[1513]: Anacron 2.3 started on 2016-01-13
Jan 13 17:02:50 gandhi-winbuntu anacron[1513]: Normal exit (0 jobs run)
Jan 13 17:02:50 gandhi-winbuntu NetworkManager[1080]: <info> WiFi hardware radio set enabled
Jan 13 17:02:50 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1429 of process 1429 (n/a) owned by '112' high priority at nice level -11.
Jan 13 17:02:50 gandhi-winbuntu rtkit-daemon[1431]: Supervising 1 threads of 1 processes of 1 users.
Jan 13 17:02:51 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1602 of process 1429 (n/a) owned by '112' RT at priority 5.
Jan 13 17:02:51 gandhi-winbuntu rtkit-daemon[1431]: Supervising 2 threads of 1 processes of 1 users.
Jan 13 17:02:51 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1603 of process 1429 (n/a) owned by '112' RT at priority 5.
Jan 13 17:02:51 gandhi-winbuntu rtkit-daemon[1431]: Supervising 3 threads of 1 processes of 1 users.
Jan 13 17:02:52 gandhi-winbuntu ntpdate[1343]: step time server 91.189.94.4 offset 0.652391 sec
Jan 13 17:03:02 gandhi-winbuntu kernel: [   54.050245] audit_printk_skb: 96 callbacks suppressed
Jan 13 17:03:02 gandhi-winbuntu kernel: [   54.050249] audit: type=1400 audit(1452704582.312:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1635 comm="apparmor_parser"
Jan 13 17:03:02 gandhi-winbuntu kernel: [   54.050261] audit: type=1400 audit(1452704582.312:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1635 comm="apparmor_parser"
Jan 13 17:03:02 gandhi-winbuntu kernel: [   54.050947] audit: type=1400 audit(1452704582.312:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1635 comm="apparmor_parser"
Jan 13 17:03:02 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jan 13 17:03:02 gandhi-winbuntu colord: Using config file /etc/colord.conf
Jan 13 17:03:02 gandhi-winbuntu colord: Using mapping database file /var/lib/colord/mapping.db
Jan 13 17:03:02 gandhi-winbuntu colord: Using device database file /var/lib/colord/storage.db
Jan 13 17:03:03 gandhi-winbuntu colord: loaded plugin libcd_plugin_scanner.so
Jan 13 17:03:03 gandhi-winbuntu colord: loaded plugin libcd_plugin_camera.so
Jan 13 17:03:03 gandhi-winbuntu colord: plugin /usr/lib/i386-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jan 13 17:03:03 gandhi-winbuntu colord: Daemon ready for requests
Jan 13 17:03:03 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-288a6f2c3bb54a1d2a29221c9caf5011
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-3c54e22f77a8f6175941c3f39f1029f9
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-50e7bd95c5a7d850b2051ad93a63906d
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-fd79463e1808f0d8ea7a8f7eefd3256b
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-fb41735d46e9e2c5b7dfa641160c3393
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-94ec9a8cbcf45963ef9bfbe80b33e02f
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-2ee6b6114ddeed0d4f61e0211c23427b
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-ccebee4c2d6eddc597c1425ac2f128b1
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-b2016991d9b9c2cf940a251d1441c7fc
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-82f5d16fcef1fbd987b6a82c94104464
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-8b73141bce6d164037dd46000bafb2a2
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-56cc29b73a685afb027a630b6d5057dc
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: MP210-series-Gray..
Jan 13 17:03:03 gandhi-winbuntu colord: Profile added: MP210-series-RGB..
Jan 13 17:03:03 gandhi-winbuntu colord: Device added: cups-MP210-series
Jan 13 17:03:04 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): IP6 addrconf timed out or failed.
Jan 13 17:03:04 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 13 17:03:04 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 13 17:03:04 gandhi-winbuntu NetworkManager[1080]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 13 17:03:05 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1972 of process 1972 (n/a) owned by '1000' high priority at nice level -11.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Supervising 4 threads of 2 processes of 2 users.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1986 of process 1972 (n/a) owned by '1000' RT at priority 5.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Supervising 5 threads of 2 processes of 2 users.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1988 of process 1972 (n/a) owned by '1000' RT at priority 5.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Supervising 6 threads of 2 processes of 2 users.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Successfully made thread 1995 of process 1995 (n/a) owned by '1000' high priority at nice level -11.
Jan 13 17:03:10 gandhi-winbuntu rtkit-daemon[1431]: Supervising 7 threads of 3 processes of 2 users.
Jan 13 17:03:10 gandhi-winbuntu pulseaudio[1995]: [pulseaudio] pid.c: Daemon already running.
Jan 13 17:03:15 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jan 13 17:03:15 gandhi-winbuntu udisksd[2184]: udisks daemon version 2.1.3 starting
Jan 13 17:03:16 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jan 13 17:03:16 gandhi-winbuntu udisksd[2184]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jan 13 17:04:20 gandhi-winbuntu avahi-daemon[1007]: Invalid response packet from host 192.168.0.8.
Jan 13 17:06:14 gandhi-winbuntu wpa_supplicant[1140]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:07:12 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:11:00 gandhi-winbuntu kernel: [  532.354735] perf interrupt took too long (2527 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Jan 13 17:17:01 gandhi-winbuntu CRON[2708]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 17:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:17:59 gandhi-winbuntu NetworkManager[1080]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jan 13 17:23:43 gandhi-winbuntu acpid: client connected from 2714[0:0]
Jan 13 17:23:43 gandhi-winbuntu acpid: 1 client rule loaded
Jan 13 17:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:37:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:45:15 gandhi-winbuntu acpid: client 2714[0:0] has disconnected
Jan 13 17:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:47:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 17:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 17:57:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 17:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:07:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:17:01 gandhi-winbuntu CRON[3366]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 18:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:22:11 gandhi-winbuntu acpid: client connected from 3369[0:0]
Jan 13 18:22:11 gandhi-winbuntu acpid: 1 client rule loaded
Jan 13 18:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:37:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:47:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 18:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 18:57:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 18:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:07:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:17:01 gandhi-winbuntu CRON[3517]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 19:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:23:55 gandhi-winbuntu anacron[3560]: Anacron 2.3 started on 2016-01-13
Jan 13 19:23:55 gandhi-winbuntu anacron[3560]: Normal exit (0 jobs run)
Jan 13 19:26:30 gandhi-winbuntu acpid: client 3369[0:0] has disconnected
Jan 13 19:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:28:10 gandhi-winbuntu dbus[814]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jan 13 19:28:11 gandhi-winbuntu kernel: [ 8762.745900] systemd-hostnamed[3848]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Jan 13 19:28:11 gandhi-winbuntu dbus[814]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.356047] usb 2-3: new high-speed USB device number 2 using ehci-pci
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.488912] usb 2-3: New USB device found, idVendor=22b8, idProduct=2e76
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.488918] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.488921] usb 2-3: Product: MotoG3
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.488924] usb 2-3: Manufacturer: motorola
Jan 13 19:31:50 gandhi-winbuntu kernel: [ 8982.488927] usb 2-3: SerialNumber: ZY222X8BJ5
Jan 13 19:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:37:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:47:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 19:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 19:57:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 19:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:07:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:13:15 gandhi-winbuntu kernel: [11466.767560] usb 2-3: usbfs: process 3911 (events) did not claim interface 0 before use
Jan 13 20:13:16 gandhi-winbuntu kernel: [11468.354886] usb 2-3: USB disconnect, device number 2
Jan 13 20:17:01 gandhi-winbuntu CRON[6616]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 20:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:17:29 gandhi-winbuntu anacron[6674]: Anacron 2.3 started on 2016-01-13
Jan 13 20:17:29 gandhi-winbuntu anacron[6674]: Normal exit (0 jobs run)
Jan 13 20:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:37:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:47:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 20:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 20:57:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 20:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:07:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:17:01 gandhi-winbuntu CRON[8837]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 21:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:37:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:47:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 21:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 21:57:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 21:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:07:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:17:02 gandhi-winbuntu CRON[10941]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 22:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:17:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:25:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:27:13 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:27:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:35:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:37:09 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:37:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:45:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:47:09 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:47:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 22:55:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 22:57:09 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 22:57:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 23:05:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 23:07:09 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 23:07:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 23:17:01 gandhi-winbuntu CRON[13057]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 23:15:57 gandhi-winbuntu wpa_supplicant[1140]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jan 13 23:17:09 gandhi-winbuntu wpa_supplicant[1140]: wlan0: WPA: Group rekeying completed with 50:6a:03:23:d9:80 [GTK=TKIP]
Jan 13 23:17:57 gandhi-winbuntu wpa_supplicant[1140]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.744065] usb 1-4: new high-speed USB device number 2 using ehci-pci
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.877371] usb 1-4: New USB device found, idVendor=04e8, idProduct=6860
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.877376] usb 1-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.877379] usb 1-4: Product: SAMSUNG_Android
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.877383] usb 1-4: Manufacturer: SAMSUNG
Jan 13 23:18:25 gandhi-winbuntu kernel: [22576.877386] usb 1-4: SerialNumber: 00199aa736d01f
Jan 13 23:18:26 gandhi-winbuntu colord: Device added: sysfs-SAMSUNG-SAMSUNG_Android
Jan 13 23:18:26 gandhi-winbuntu colord: Device added: sysfs-(null)
Jan 13 23:20:00 gandhi-winbuntu NetworkManager[1080]: message repeated 51 times: [ <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted]
Jan 13 23:24:25 gandhi-winbuntu NetworkManager[1080]: <info> sleep requested (sleeping: no  enabled: yes)
Jan 13 23:24:25 gandhi-winbuntu NetworkManager[1080]: <info> sleeping or disabling...
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): cleaning up...
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (eth0): taking down device.
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> NetworkManager state is now ASLEEP
Jan 13 23:24:26 gandhi-winbuntu whoopsie[1053]: offline
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): deactivating device (reason 'sleeping') [37]
Jan 13 23:24:26 gandhi-winbuntu NetworkManager[1080]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1199
Jan 13 22:27:57 gandhi-winbuntu avahi-daemon[1007]: message repeated 164 times: 
```

---

### Post by matt_symes on 2016-01-15
Hi

There's nothing in your logs to suggest a problem.

> **weatherman2 said:**
> You might also have some issue with the controller in the external casing or even the power supply (is it USB powered or is there an external power supply to the drive?).  If it is not say providing reliable power, it might not be able to stay active all the time and may lose communication with the computer or something.  It could even be something weord with the USB connector or the cable.  

I like this suggestion. I've come across power issues before myself.

How are you powering the external hard drive ?

Is it powered with its own power supply or powered from the USB bus ? Are you using a powered external USB hub and is it connected to that ?

Have you tried another cable ?

Kind regards

---

