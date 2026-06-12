---
title: "DVD drive randomly unmounts itself, causes Handbrake to segfault"
date: 2008-08-10
forum: General Help
---

### Post by SkyFire360 on 2008-08-10
Heya!  It seems like my DVD drive randomly unmounts itself...

I'm trying to use Handbrake (latest SVN) to try and rip a DVD.  Upon my initial overnight rip - it's an older computer - I wake up the next morning to a tiny MKV file and a terminal window that says "Segmentation Fault" from Handbrake.  Odd.  So I do a 'ls /media/dvd' and it comes up empty.  Huh?  I try to play the DVD with mplayer: 

```

sky@Mako:~$ mplayer dvd://1
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
Couldn't open DVD device: /dev/dvd

```

What the heck?  Same thing if I do a 'sudo mount -a'.  I eject the DVD, stick it back in and try to 'mplayer dvd://1'.  To my bewilderment, it works perfectly.  So I set up Handbrake to encode and go to sleep.  I wake up to the same result: a slightly larger .mkv file and a segmentation fault from Handbrake.  Ugh, so I try to play it with mplayer and get the above message again.  I eject, re-insert, mplayer it and it works.  

Now here's a strange part: I waited for an hour and tried mplayer again (without running Handbrake) and got the error message again.  'ls'-ing /media/dvd resulted in all the video files! (VIDEO_TS, etc)  So weird...

In short, I can access the DVD immediately after inserting it via /dev/dvd and /dev/cdrom (both symlinks to /dev/cdrom0).  I can also access it through /media/dvd.  After a while, mplayer can't access the device via /dev/dvd anymore, but I can 'ls' the contents of /media/dvd, which means it's still mounted.

The only interesting part of dmesg:
```

[37986.327793] cdrom: This disc doesn't have any tracks I recognize!
[37987.194074] UDF-fs: Partition marked readonly; forcing readonly mount
[37987.276887] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'FINAL_FANTASY_VII', timestamp 2006/03/10 15:09 (1e5c)

```

my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=b1c31059-1865-478f-8453-d41de49d993a /               ext3    defaults,errors=remount-ro 0       0
# /dev/sda1
/dev/sda1 /warehouse     ext3    defaults,errors=remount-ro 0       0
# /dev/sdb6
UUID=2220656f-8822-4044-8a60-2b21fba478ae none            swap    sw              0       0
/dev/sde1       /home/sky/hd   vfat noauto,o=sky,g=sky,rw,umask=000 0       0
/dev/dvd       /media/dvd   udf,iso9660 user,noauto,exec 0       0

```

Thoughts?

---

### Post by SkyFire360 on 2008-08-10
Just a quick bump, since this fell off the front page in a hurry.  I also ran another test, remounting the drive manually using 'mount -t iso9660 -o user,noauto,exec /dev/scd0 /media/dvd' and after running the program for a while, the drive is no longer accessible via /dev/dvd (symlink from /dev/dvd -> scd0), making 'mplayer dvd://1' fail.

Interesting update: /media/dvd is still available and readable, but when you 'ls -la /media/dvd' the first time after it's unmounted, it takes a while - like it's mounting again - and then lists the contents.  Now, re-running 'mplayer dvd://1' works again.  What gives?

---

