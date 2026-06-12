---
title: "No more swap !!!"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by ploum on 2005-04-10
I've found that I've no more SWAP !!!  (and it's really necessary because I only have 96Mo of Ram on this computer)

fdisk -l give /dev/hda3 as a Linux Swap (82) starting at 6047, ending at 6304.

But swapon told me :

/dev/hda3: Invalid argument


What can I do and why do I have this problem ?

Thx in advance

---

### Post by heimo on 2005-04-10
Hmm... no idea what has happened to your swap. But you could try to disable all swap, recreate swap partition, and try to enable it again.
```

swapoff -a
/sbin/mkswap /dev/hda3
swapon -a

``` 

You should have something like this in /etc/fstab:
```

/dev/hda3       none            swap    sw              0       0

```

---

### Post by ploum on 2005-04-10
Solved ! 

1) cfdisk : erase the old Swap partition and recreate a new one
2) reboot (mandatory)
3) mkswap /dev/hda3
4) swapon -a

it works !

No idea what happens...

---

### Post by amerigo5 on 2005-04-10
You're not alone. This also happened to me. 

Here's my post: [http://www.ubuntuforums.org/showthread.php?t=24421](http://www.ubuntuforums.org/showthread.php?t=24421)

---

### Post by ploum on 2005-04-11
So there must be a bug...  I don't understand.

---

### Post by ploum on 2005-04-16
Oh no ! 

It happens again !!!!!  I really don't understand what can cause this bug :-(

Hmmm.. The only thing strange is that, liste time, I've tried "hibernate" instead of shutdown.

It may be highly related.

Will try if this is reproductible.

---

### Post by heimo on 2005-04-16
Hmm... You could install smartmontools and check if there's any alarming information (smartctl -a /dev/hda) available in smart values. :-/ Hopefully not.

---

### Post by ploum on 2005-04-17
I don't really understand what it means but here's the output :

```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection:                 ( 185) seconds.
Offline data collection
capabilities:                    (0x05) SMART execute Offline immediate.
                                        No Auto Offline data collection support.
                                        Abort Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        No Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x00) Error logging NOT supported.
                                        No General Purpose Logging support.

SMART Attributes Data Structure revision number: 5
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   197   100   050    Pre-fail  Always       -
       0
  2 Throughput_Performance  0x0004   100   100   050    Old_age   Offline      -
       0
  3 Spin_Up_Time            0x0026   100   100   001    Old_age   Always       -
       1829
  4 Start_Stop_Count        0x0032   098   098   060    Old_age   Always       -
       2817
  5 Reallocated_Sector_Ct   0x0033   100   100   001    Pre-fail  Always       -
       0
  8 Seek_Time_Performance   0x0004   100   100   050    Old_age   Offline      -
       0
  9 Power_On_Hours          0x0032   095   095   050    Old_age   Always       -
       4112
 10 Spin_Retry_Count        0x0033   154   100   030    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -
       1249

Warning: device does not support Error Logging
Error SMART Error Log Read failed: Input/output error
Smartctl: SMART Error Log Read Failed
Warning: device does not support Self Test Logging
Error SMART Error Self-Test Log Read failed: Input/output error
Smartctl: SMART Self Test Log Read Failed
Device does not support Selective Self Tests/Logging

```

---

### Post by heimo on 2005-04-17
Well, there wasn't much to look, and nothing suggests that it'd be failing (values should go under threshold value to be "failed"). Anyway, it'd be quite improbable that failing disk would cause such recuring symptoms (swap disappearing twice).

No idea what it is. Keep eye on it.

Hmm.. this sounds plausible:
[http://www.ubuntuforums.org/showthread.php?t=5897](http://www.ubuntuforums.org/showthread.php?t=5897)

---

### Post by ploum on 2005-04-17
Thank you for your time.

It seems indeed plausible. But if it is, the hibernate button is then very dangerous !!!!

---

### Post by suziequzie on 2005-11-07
[QUOTE=heimo]Hmm... no idea what has happened to your swap. But you could try to disable all swap, recreate swap partition, and try to enable it again.
```

swapoff -a
/sbin/mkswap /dev/hda3
swapon -a

``` 

You should have something like this in /etc/fstab:
```

/dev/hda3       none            swap    sw              0       0

```[/QUOTE]


Thank you, that was a lifesaver! 
And it worked. I used the top command to see, and it went from swap being 0k 0k used,  to the actual numbers showing its usage.  Thanks again.

suziequzie:)

---

### Post by BLTicklemonster on 2008-01-07
My swapfile never works either, so I did the above, and now I have this after a reboot:

ticklemonster@ticklemonster-desktop:~$ sudo swapon -a
[sudo] password for ticklemonster:
swapon: cannot canonicalize /dev/disk/by-uuid/d2184c69-6ec7-4727-97bf-f768d97cc12f: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/d2184c69-6ec7-4727-97bf-f768d97cc12f: No such file or directory
ticklemonster@ticklemonster-desktop:~$ 


so I don't have a swapfile at all.

Should I create a new swapfile as in use hda"number not used presently" ?

what do I do with the swapfile that exists already?

---

### Post by zxcvbnm on 2008-01-07
Post the contents of your fdisk config. Make sure you have allocated a swap partition. I would try defining your partition separately instead of  the -a argument.

Use: to disable current swap partition.
```
swapoff /dev/<swap partition>
```

Then use: to initialize swap partition
```
mkswap /dev/<swap partition>
```

Use: to activate swap partition.
```
swapon /dev/<swap partition>
```

---

### Post by BLTicklemonster on 2008-01-07
How do I list my fdisk? If it's fdisk -l then I get nothing.

ticklemonster@ticklemonster-desktop:~$ fdisk -l
ticklemonster@ticklemonster-desktop:~$

and


ticklemonster@ticklemonster-desktop:~$ sudo swapoff /dev/hda3
[sudo] password for ticklemonster:
ticklemonster@ticklemonster-desktop:~$ sudo mkswap /dev/hda3
Setting up swapspace version 1, size = 3002220 kB
no label, UUID=b791cdda-83d1-4ac4-9056-e8c7b8f371bc
ticklemonster@ticklemonster-desktop:~$ sudo swapon /dev/hda3
ticklemonster@ticklemonster-desktop:~$ 


according to fstab, UUID=b791cdda-83d1-4ac4-9056-e8c7b8f371bc is the identifier for hda6,wiich is not used.

---

### Post by zxcvbnm on 2008-01-07
Just out of curiosity can you post the output of:

```
swapon -s
``` 

If there is an output then that partition is running your swap.
Also make sure you are running fdisk as superuser. You are using the correct argument so you should be able to see the contents of fdisk.




Please post the contents of your fstab. 

```
cat /etc/fstab
```

---

