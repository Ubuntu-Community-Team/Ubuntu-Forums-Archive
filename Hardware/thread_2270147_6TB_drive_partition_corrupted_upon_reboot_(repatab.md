---
title: "6TB drive partition corrupted upon reboot (repatable)"
date: 2015-03-20
forum: Hardware
---

### Post by scott93 on 2015-03-20
Hi guys.
I recently bought and installed a 6 TB drive into my Ubuntu media box.
I used the built in Disks utility to partition it as a single 6 TB NTFS partition.
All seemed well and I copied 4 TB of videos on to it over the next 24 hours.
I watched a few shows and then restarted the computer.
The partition had become corrupted.It appeared as two unmountable partitions of the same label as the original.
I spent days using testdisk attempting to recover the partition and data to no avail before I repartitioned it.
However, upn reboot the EXACT SAME scenario occured.
Please see this screenshot for the reslting partitions...
[ATTACH=CONFIG]260777[/ATTACH]
I am really curious why???? I can get the data back (slowly from a mates NAS)
Thanks,
Scott C

---

### Post by weatherman2 on 2015-03-20
Did you use a GPT partition table (and not MSDOS)?  That will allow you to use a partition size larger than 2TB.  You can make one huge partition that way if you want.  I would use GPT for sure unless you will use this drive with an older Windows OS (like XP?  not sure) that can't understand GPT.

You might also install GSmartControl and check out the S.M.A.R.T. status of the drive - look for any Attributes highlighted in red/pink.  You can run S.M.A.R.T. tests too.  The Extended Test on this huge drive will surely need to run overnight, at least, though.  The short test will run in just a few minutes.  Even a new drive could fail, though unlikely.

Finally, although I've not had any issues with NTFS for years in Ubuntu, if this is not going to be connected directly to a Windows machine, I'd use ext4 not NTFS as the partition type.  You can still share data on ext4 partitions over a network using Samba.  Windows machines on the network won't know what format you used internally, they'll see it as a Windows share.  NTFS has some performance issues with large files in Linux, though otherwise it's been extremely reliable for me - but in the last few years, I've mostly used ext4 to get better performance in my Linux servers.

---

### Post by scott93 on 2015-03-20
'Thanks for the reply weatherman.
The Disks utility does not offer any other options other than the drive label when NTFS is selected so I couldn't tell you what it does. I chose NTFS so that in the future the drive may be removed and put into a windows machine without complications.
I have installed GSmartControl as you suggested. I enabled SMART and ran the Short Self-Test. Test completed without Error. All SMART Attributes have a failed status of "Never" and nonne are coloured. 

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   209   209   021    Pre-fail  Always       -       8550
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       37
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       139
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       37
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       19
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2281
194 Temperature_Celsius     0x0022   121   110   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

---

### Post by weatherman2 on 2015-03-20
OK, all of those Attributes look fine.  I wouldn't worry about the drive failing.

Install gparted for a much better partitioning tool.

Start it up, and under the device menu choose "Create Partition Table" and try a GPT partition table (this will completely erase the disk again, though).  Then make your partition(s) again.

---

### Post by scott93 on 2015-03-20
Will do Weatherman. It is still a curious.. and odd.. thing to happen huh. ALso a difficult thing to do a google search for I found. Plenty of people have problems losing a partition.. but not in a repeatable and specific way..

I won't get around to partitioning and rebooting today as I am in the middle of another file transfer process (using a different drive!). I will report back with the results. Thanks for all your help so far.

---

### Post by weatherman2 on 2015-03-20
As it seems repeatable for you, you should know whether using GPT as the type of partition table (instead of MSDOS) will make any difference pretty quickly, right?

If you are already using a GPT partition scheme, then I guess you don't need to try again.  Could be something else going on.  You could survey the logfiles like /var/log/syslog .

Which version of Ubuntu is this?

---

### Post by scott93 on 2015-03-23
I partitioned the drive with the GParted Partition Editor using GPT and NTFS and it seems to be working fine now.
Ubuntu 14.10
I will declare this as solved (Although WHY the built in "Disks" utility seemed to not work is not confirmed).
Thanks for your help Weatherman2

---

### Post by weatherman2 on 2015-03-23
Good to hear.  I think it's unfortunate that Disk Utility is pushed as the default for managing disks and partitions in Ubuntu - I always use Gparted but must install it I believe before first use.  I Gparted a ubiquitous tool in Ubuntu.

---

