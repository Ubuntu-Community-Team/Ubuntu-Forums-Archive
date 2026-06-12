---
title: "VLC Media Player fails to play DVD but can play CD"
date: 2020-03-27
forum: Hardware
---

### Post by satimis on 2020-03-27
Ubuntu 18.04

VLC Media Player fails to play DVD but can play CD

With DVD on CD/DVD writer tray
Warning```

....
Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

```

$ sudo ln -s /dev/sr0 /dev/dvd```

ln: failed to create symbolic link '/dev/dvd': File exists

```

$ ls -al /dev/sr0 ```

brw-rw----+ 1 root cdrom 11, 0 Mar 27 13:34 /dev/sr0

```

$ ls -al /dev/dvd```

lrwxrwxrwx 1 root root 3 Mar 27 13:34 /dev/dvd -> sr0

```

$ ls -al /dev/dvdrw```

lrwxrwxrwx 1 root root 3 Mar 27 13:34 /dev/dvdrw -> sr0

```

$ cat /dev/dvd```

cat: /dev/dvd: No medium found

```

$ sudo lshw -c disk
```

.....
....
  *-cdrom
       description: DVD-RAM writer
       product: DVD RW AW-G170S
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.72
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

Please help.  Thanks

Regards
satimis

---

### Post by mc4man on 2020-03-27
Your lshw shows  "status=nodisc" 
Either there is no DVD in the drive or if there is your drive isn't detecting it.
If the later try cleaning drive/laser lens, a different DVD or a different DVD drive

---

### Post by satimis on 2020-03-27
> **mc4man said:**
> Your lshw shows  "status=nodisc" 
Either there is no DVD in the drive or if there is your drive isn't detecting it.
If the later try cleaning drive/laser lens, a different DVD or a different DVD drive
Hi,

Thanks for your advice.

Have tried other discs;
-some work
-others fail
-some discs have to be tried several times, inserting the tray twice/triple times

This DVD writer is an old device and also hasn't used for prolonged time.  I fail to see whether I can find the cleaning set to clean the len,

I'm considering buying a new USB DVD-Writer to be used on other PCs as well.  I still have a good stocks of movies on VCD and DVD and also music CDs.  I'll convert all of them to mp4 and mp3 files, keeping them on WD HD which are rather cheap in price today.  VLC has this conversion feature,

One additional question.  Can movie VCDs, DVDs and music CDs all work in DVD writer without problem?

Thanks

satims

---

### Post by mc4man on 2020-03-27
The new (external) drive shouldn't have any issue with various optical media.
Some apps may need you to change their settings to /dev/sr1

---

### Post by ipv on 2020-03-27
> **satimis said:**
> I fail to see whether I can find the cleaning set to clean the len

do not waste your money & time with the cleaning kits, get a new dvd rom.

> **satimis said:**
> Can movie VCDs, DVDs and music CDs all work in DVD writer without problem?

yes.

---

### Post by satimis on 2020-03-27
> **ipv said:**
> do not waste your money & time with the cleaning kits, get a new dvd rom.


Hi,

Thanks for your advice.

Just started a new posting on this forum - Seeking advice for purchasing external DVD writer

Regards
satimis

---

### Post by satimis on 2020-03-27
> **mc4man said:**
> The new (external) drive shouldn't have any issue with various optical media.
Some apps may need you to change their settings to /dev/sr1
Thanks

Regards
satimis

---

