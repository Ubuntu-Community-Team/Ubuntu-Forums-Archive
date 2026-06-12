---
title: "external hdd failure, ddrescue, errors"
date: 2011-07-19
forum: Hardware
---

### Post by Claus7 on 2011-07-19
Hello,

your lights and feedback if you can.

The case: a friend's external hdd sata 1.5TB which produces errors while trying to mount it, ext3 formatted.

The error is:
> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

[The drive is visible via Places though.]

and typing dmesg | tail (or just dmesg) the result is:
> [12191.674587] usb-storage: device scan complete
     54 [12191.716677] scsi 8:0:0:0: Direct-Access     WDC WD15 EARS-00MVWB0          PQ: 0 ANSI: 2 CCS
     55 [12191.725512] sd 8:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
     56 [12191.726878] sd 8:0:0:0: [sdc] Write Protect is off
     57 [12191.726888] sd 8:0:0:0: [sdc] Mode Sense: 34 00 00 00
     58 [12191.726892] sd 8:0:0:0: [sdc] Assuming drive cache: write through
     59 [12191.728497] sd 8:0:0:0: [sdc] 2930277168 512-byte hardware sectors (1500302 MB)
     60 [12191.729364] sd 8:0:0:0: [sdc] Write Protect is off
     61 [12191.729371] sd 8:0:0:0: [sdc] Mode Sense: 34 00 00 00
     62 [12191.729376] sd 8:0:0:0: [sdc] Assuming drive cache: write through
     63 [12191.729386]  sdc: sdc1
     64 [12191.744513] sd 8:0:0:0: [sdc] Attached SCSI disk
     65 [12191.744611] sd 8:0:0:0: Attached scsi generic sg4 type 0

>      80 [12196.339958] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
     81 [12196.339970] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
     82 [12196.339979] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
     83 [12196.339988] end_request: I/O error, dev sdc, sector 2791047231
     84 [12196.339993] printk: 170747 messages suppressed.
     85 [12196.339999] Buffer I/O error on device sdc1, logical block 348880896
     86 [12196.340007] lost page write due to I/O error on sdc1


>  91 [12196.627305] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
     92 [12196.627316] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
     93 [12196.627330] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
     94 [12196.627338] end_request: I/O error, dev sdc, sector 2791309375
     95 [12196.627346] Buffer I/O error on device sdc1, logical block 348913664
     96 [12196.627351] lost page write due to I/O error on sdc1
     97 [12196.914772] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
     98 [12196.914784] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
     99 [12196.914793] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
    100 [12196.914801] end_request: I/O error, dev sdc, sector 2791571519
    101 [12196.914809] Buffer I/O error on device sdc1, logical block 348946432
    102 [12196.914815] lost page write due to I/O error on sdc1
    103 [12197.201993] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
    104 [12197.202005] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
    105 [12197.202013] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
    106 [12197.202021] end_request: I/O error, dev sdc, sector 2791833663
    107 [12197.202029] Buffer I/O error on device sdc1, logical block 348979200
    108 [12197.202037] lost page write due to I/O error on sdc1

>     110 [12197.489462] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
    111 [12197.489472] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
    112 [12197.489480] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
    113 [12197.489488] end_request: I/O error, dev sdc, sector 2792095807
    114 [12197.489496] Buffer I/O error on device sdc1, logical block 349011968
    115 [12197.489503] lost page write due to I/O error on sdc1
    116 [12197.776929] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
    117 [12197.776940] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
    118 [12197.776950] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
    119 [12197.776958] end_request: I/O error, dev sdc, sector 2792357951
    120 [12197.776966] Buffer I/O error on device sdc1, logical block 349044736
    121 [12197.776971] lost page write due to I/O error on sdc1
    122 [12198.064153] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
    123 [12198.064165] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
    124 [12198.064174] sd 8:0:0:0: [sdc] Add. Sense: Peripheral device write fault
    125 [12198.064183] end_request: I/O error, dev sdc, sector 2792620095
    126 [12198.064190] Buffer I/O error on device sdc1, logical block 349077504
    127 [12198.064196] lost page write due to I/O error on sdc1

...............and on................

So, in order to try and save an image of this drive I tried:
```
sudo ddrescue -v -r 1 /dev/sdc /dev/sdb Recovery.log
```

where sdb a sound hdd 1.0TB, ext3 formatted too.

After at least a week of running the aforementioned command the output is:
> About to copy 1500 GBytes from /dev/sdc to /dev/sdb
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512 bytes
Max_retries: 1    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:   1500 GB,  errors: 519356629
Current status
rescued:         0 B,  errsize:   1500 GB,  current rate:        0 B/s
   ipos:   265921 MB,   errors: 519378600,    average rate:        0 B/s
   opos:   265921 MB
Splitting error areas...

My question is:
is there any hope on rescuing anything from this drive? It seems that after all this time, there are no rescued files! Is this drive totally corrupted and we are just loosing our time with it or is there any hope?

The Recovery.log file is looking like this:
>       1 # Rescue Logfile. Created by GNU ddrescue version 1.2
      2 #      pos        size  status
      3 0x00000000  0x3DEAA91A00  -
      4 0x3DEAA91A00  0x11F664D4600  /

Any feedback will be more than welcome,
thank you,
Regards!

---

### Post by Claus7 on 2011-07-23
Hello,

just to add, that after a lot of time, the first attempt was finished with 0 rescued files. I suppose that the hdd is so damaged that there is no hope of rescuing something. Do you thing that a second attempt might give different results? I'm asking cause it takes a lot of time.

Thank you,
Regards!

---

### Post by DunZH on 2011-07-25
I don't have my bookmarks and terminal commands with me, but I just dealt with this kind of issue recently.

First, what problems is the drive having?  Can it mount at all?  Can any data be pulled off of it? also, what are you trying to do?  Get a lot of data off, or just some files?

For your dd commands, they don't look right to me.  Here is a standard command:

```
dd bs=4k if=/dev/hdx of=/dev/hdy conv=noerror,sync
```

Also, make sure the drives are refered to correctly. I had a situation where I tried something like /dev/sdc1 and it didn't work, because that drive was mounted at /media/mountpoint, and that is what I needed to use to tell dd what to do.

If it was me I would probably install testdisk and run photorec first, to see if I can see into that drive at all.  Photorec works pretty good if you only need some of the drive data.

I guess all I am saying is before deciding to copy the drive block for block it might be good to see if you can access it at all...but dd should work, I had a really bad drive that could only mount for a couple minutes before errors started popping up and the drive automatically unmounted, and dd copied it pretty much perfectly.

---

### Post by Claus7 on 2011-07-28
Hello,

thank you for your feedback. Unfortunately, I cannot have a direct access with the hdd, so my responses are not quick.

EDIT: <**What I would like to do**>
I would like to rescue huge binary files, which I cannot access, since the drive cannot be mounted. I cannot use photorec, since the drive is not possible to be mounted even for some seconds and I would like to rescue the files with their names on, otherwise I won't know which one is what.

So, the drive is not possible to be mounted, as it produces errors (1st post, 1st quote).

I 'm trying your command right now typing:
> sudo dd bs=4k if=/dev/sdc of=/dev/sdb1 conv=noerror,sync

*sdc: the faulty hdd
**sdb1: the mounted good hdd

the output so far is like:
> 0+6265 records in
6265+0 records out
25661440 bytes (26 MB) copied, 301.002 s, 85.3 kB/s
dd: reading `/dev/sdc': Input/output error
0+6266 records in
6266+0 records out
25665536 bytes (26 MB) copied, 301.05 s, 85.3 kB/s
dd: reading `/dev/sdc': Input/output error
0+6267 records in
6267+0 records out
25669632 bytes (26 MB) copied, 301.098 s, 85.3 kB/s
dd: reading `/dev/sdc': Input/output error
0+6268 records in
6268+0 records out
25673728 bytes (26 MB) copied, 301.146 s, 85.3 kB/s
dd: reading `/dev/sdc': Input/output error
0+6269 records in
6269+0 records out
25677824 bytes (26 MB) copied, 301.194 s, 85.3 kB/s
dd: reading `/dev/sdc': Input/output error
0+6270 records in
6270+0 records out
25681920 bytes (26 MB) copied, 301.242 s, 85.3 kB/s

yet, the input-output error is something I do not like.

I'll keep it on and see what I'll get.

Thank you,
Regards!

---

### Post by Claus7 on 2011-08-07
Hello,

the last command did end, without producing any results. It seems that in the good drive nothing is written on it. I guess that every effort would be in vain then.

Thank you,
Regards!

---

