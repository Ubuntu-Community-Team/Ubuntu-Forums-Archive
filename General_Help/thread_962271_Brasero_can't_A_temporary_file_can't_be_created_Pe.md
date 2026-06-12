---
title: "Brasero can't: A temporary file can't be created: Permission denied"
date: 2008-10-29
forum: General Help
---

### Post by alicetiner on 2008-10-29
Hello people,

I am getting this message with Brasero while trying to create CD/DVDs. I tried Gnomebaker and it also could not burn CDs.

Brasero's error log is as below:

Can anyone help me please? Thanks a tonne!

Retro Gaffar


Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
Session error : a temporary file can't be created: Permission denied (brasero_burn_record burn.c:2524)

---

### Post by ad_267 on 2008-10-29
What's the output from the terminal (applications - accessories - terminal) of 
```
ls -ld /tmp
```

---

### Post by alicetiner on 2008-11-01
The output of ls -ld /tmp is:

drwxrwxrwt 16 root root 4096 2008-11-01 13:06 /tmp


?

---

### Post by ad_267 on 2008-11-01
That's weird. I assume Brasero would write the temporary file in /tmp and it has write permissions.

After a bit of googling, the 5th post here might help:
[http://ubuntuforums.org/showthread.php?t=769584](http://ubuntuforums.org/showthread.php?t=769584)
And this one:
[http://ubuntuforums.org/showthread.php?t=839514](http://ubuntuforums.org/showthread.php?t=839514)

It seems like the temporary directory Brasero uses can be changed, so set it to /tmp or to your home directory.

---

### Post by alicetiner on 2008-11-03
The thread

[http://ubuntuforums.org/showthread.php?t=769584](http://ubuntuforums.org/showthread.php?t=769584)

helped partially. I found out that my brasero's temp folder also somehow points to the "File System" so I corrected it as "/tmp".

However, this time a different error came up. I am sending the log attached herewith.

Thanks for all the help!

---

### Post by ad_267 on 2008-11-03
Someone else had the exact same problem here: [http://ubuntuforums.org/showthread.php?t=785381](http://ubuntuforums.org/showthread.php?t=785381)
and here: [http://ubuntuforums.org/showthread.php?t=921982](http://ubuntuforums.org/showthread.php?t=921982)

Here's the section from your log:
```
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    6.305s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 15 12 73 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 6.279s timeout 60s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
```

The suggestion from that thread was to try a different type of rewritable disc, and that it's probably an incompatibility between your hardware and the disc. It might be worth giving it a go with a different application like k3b which people seem to recommend a lot.

---

### Post by Francewhoa on 2009-07-23
Same here. **The following worked for me.**
-With Ubuntu 8.04 desktop edition click on PLACES menu.
-Select COMPUTER.
-A new window will open.
-Double click on FILESYSTEM folder.
-Double click on TEMP folder.
-Right click on KDE-YOURUSERNAMEHERE folder.
-Click on PERMISSION tab.
-Set appropriate permissions. Find attached screenshot to clarify.
-Click on APPLY PERMISSIONS TO ENCLOSED FILES button.
-That's it. You are now able to burn a disc.

---

