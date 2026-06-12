---
title: "Optical Drive slow reading CDs - Dell XPS17 Xubuntu 18.04.2"
date: 2019-05-07
forum: Hardware
---

### Post by jg1 on 2019-05-07
My Dell XPS17 has been running OK with 16.04 and has recently done the upgrade to 18.04.2. The CD/DVD drive worked fine on 16.04 to the extent that this was the device of choice for recording and copying CDs and DVDs. But on 18.04 It records OK and reads DVDs but is glacially slow at reading CDs.

I've now just got to cutting a heap of CDs and DVDs using the new Xubuntu 18.04.2 AMD64 which seems absolutely OK.  CD-Rs and DVD-Rs record at around 2-3MB/s and 3-4MB/s respectively but I noticed that Brasero was taking a longer to compute the checksum for CDs than for DVDs.  Doing a test, I found reading back a CD-R takes about 19 minutes for 710MB at 600KB/s, while the same CD took less than 5 mins to record. Using an external Dell USB2 CD/DVD reader the same disc reads in 4 mins at 1.5MB/s.  On the other hand Recording and reading back DVDs seems to be OK with a read speed of around 4.7MB/s.

There's a Win10 system on the same box and I found that the DVD performance was much the same as with Linux while the CD read speed began at 600KB/s quickly building to 2.5MB/s and completing the operation in around 4 mins for 710MB.

I've tried to look at the settings and as far as I can tell DMA is enabled so I'm a bit foxed.
The optical drive is a Toshiba Samsung 12.7T SATA DVD+/-RW 8X and the CPU is a series 2 core-i7 with 4GB memory and 2 x 500GB HDDs with plenty of space.

I'd appreciate any help or pointers as to how I might solve this issue.  My next move is to revert to 16.04.4 AMD64 which seemed to work fine.
Tks in anticipation
jg

---

### Post by Autodave on 2019-05-07
The first thing that I would do is to try *xfburn.  *Brasero was always my first choice, but for the last few years I have been using xfburn since I had started having many problems with Brasero.

---

### Post by jg1 on 2019-05-08
It appears to be a CD read problem.  It doesn't matter where or how the CD was cut, Windows, MAC, Ubuntu, or commercial ROM.
Doing some more tests I have isolated the problem to the Xubuntu 16.04 -> 18.04.2 upgrade process.  I did an out of the box 16.04 LTS install and tested it.  Then updated it and tested again with both Nemo and Thunar - all OK.  Now just upgraded this out-of-the-box installation (ie no customisation beyong displaying seconds in the panel clock) and Thunar is taking 20 mins to read the test CD - still going as I type this !!
Next I will try a clean/fresh install of 18.04.2 to see if that cures the problem.
Happy days
jg

---

### Post by jg1 on 2019-05-08
I have now done an out-of-the-box fresh install of 18.04.2 selecting 3rd party s/w (as normal for display drivers etc), with no updates and the CD problem is now back, reading at 614.9-615.0 KB/s. 19mins 22 secs for 710MB.  This is beginning to look more and more like a software bug in Xubuntu 1804.  I have not tried any other flavours but I imagine that they are the same.  It's not life threatening but it would be a deal breaker if I played a lot of CDs, eg for music etc.

Is this something I should report?  Not sure of the best way as I'm not particularly technical.

Anyone know how I might rectify the problem?

jg

---

### Post by scdbackup on 2019-05-09
Hi,

you could try whether it works better if a userland program is
in control of the SCSI transactions, rather than the cdrom driver
of Linux:
```

  xorriso -read_speed max -outdev /dev/sr0 -check_media use=outdev --

```
The medium must be a data CD, DVD, or BD. Not an audio CD.

I get report lines like
```

  xorriso : NOTE : Disc status unsuitable for writing
  Drive current: -outdev '/dev/sr0'
  Media current: CD-RW
  Media status : is written , is closed
  Media summary: 1 session, 157156 data blocks,  307m data,     0 free
  xorriso : UPDATE :      32 blocks read in 3 seconds , 0.2xC
  xorriso : UPDATE :     992 blocks read in 4 seconds , 12.6xC
  xorriso : UPDATE :    2240 blocks read in 5 seconds , 16.5xC
  ...
  xorriso : UPDATE :  101984 blocks read in 64 seconds , 26.6xC
  ...
  xorriso : UPDATE :  155776 blocks read in 89 seconds , 30.2xC
  xorriso : UPDATE :  157156 blocks read in 90 seconds = 23.2xC
  Media checks :        lba ,       size , quality
  Media region :          0 ,     157154 , + good
  Media region :     157154 ,          2 , 0 tao_end

```

The texts "NN.NxC" give the measured speed in CD units of 150 KB/s.

Have a nice day :)

Thomas

---

### Post by jg1 on 2019-05-09
Thomas, tks for your reply.  It looks like it's the Lx driver that's adrift in 18.04.  After installing xorriso I get much the same output as you:

jg@jg-XPS17:~$ xorriso -read_speed max -outdev /dev/sr0 -check_media use=outdev --
xorriso 1.4.8 : RockRidge filesystem manipulator, libburnia project.

xorriso : NOTE : Disc status unsuitable for writing
Drive current: -outdev '/dev/sr0'
Media current: CD-R
Media status : is written , is closed
Media summary: 1 session, 347033 data blocks,  678m data,     0 free
xorriso : UPDATE : 32 blocks read in 3 seconds , 0.2xC
xorriso : UPDATE : 160 blocks read in 4 seconds , 1.7xC
xorriso : UPDATE : 512 blocks read in 5 seconds , 4.6xC
xorriso : UPDATE : 736 blocks read in 6 seconds , 1.8xC
xorriso : UPDATE : 768 blocks read in 8 seconds , 0.2xC
xorriso : UPDATE : 928 blocks read in 9 seconds , 2.1xC
xorriso : UPDATE : 1760 blocks read in 10 seconds , 11.1xC
xorriso : UPDATE : 2592 blocks read in 11 seconds , 11.1xC
xorriso : UPDATE : 3456 blocks read in 13 seconds , 11.1xC
xorriso : UPDATE : 4320 blocks read in 14 seconds , 11.2xC
...
...
xorriso : UPDATE : 32800 blocks read in 45 seconds , 12.9xC
xorriso : UPDATE : 33792 blocks read in 46 seconds , 12.9xC
xorriso : UPDATE : 34784 blocks read in 47 seconds , 13.0xC
xorriso : UPDATE : 35776 blocks read in 48 seconds , 13.0xC
xorriso : UPDATE : 36768 blocks read in 49 seconds , 13.1xC
xorriso : UPDATE : 37760 blocks read in 50 seconds , 13.1xC
xorriso : UPDATE : 38752 blocks read in 51 seconds , 13.2xC
^C
UNIX-SIGNAL:  SIGINT  errno= 2
xorriso : ABORT : Trying to shut down drive and library
xorriso : ABORT : Wait the normal burning time before any kill -9

xorriso : ABORT : Program done. Even if you do not see a shell prompt.

jg@jg-XPS17:~$ 

I suppose the next question is where should I look for a suitable driver and how to install?  I can cope with .dev files and ready made install scripts but *make* and *make-install* are a step too far for a septagenarian!  As far as I can see there's nothing helpful on the Dell website and my searches all bring up Windows stuff.

---

### Post by scdbackup on 2019-05-09
Hi,

> UNIX-SIGNAL: SIGINT errno= 2

I assume this was caused by you by e.g. pressing Ctrl+C.
(If not, then this was not the expected end of the run. We should
 investigate.)


> I suppose the next question is where should I look for a suitable
> driver and how to install? 

If the problem is about a driver, then you will need a fix in the Linux
kernel.

But for now we only know that the drive is ok with the low level drivers
of Linux, which transport xorriso's SCSI commands to the drive and then
brings back the drive's reply.

The read speed of a drive is a quite persistent setting. It might be that
some application (maybe even Brasero) did set that speed to 4x.
If so, then xorriso should now have set the speed to a higher value.
Then the following dd run would be fast after the xorriso speed test:
```

  dd if=/dev/sr0 bs=2048 count=25000 of=/dev/null

```
With my drive it reports
```

  25000+0 records in
  25000+0 records out
  51200000 bytes (51 MB) copied, 17.6107 s, 2.9 MB/s

```
2.9 MB/s is about 20x CD speed.
At 600KB/s = 4x CD speed it would need about 90 seconds.

---------------------------------------------------------------------

If dd is still slow after a xorriso speed test, then something in the
kernel is wrong. You'd need to tell its exact revision. Like:
```

$ uname -a
Linux ts6-sid 4.12.0-1-amd64 #1 SMP Debian 4.12.6-1 (2017-08-12) x86_64 GNU/Linux

```

---------------------------------------------------------------------

If it appears only after Brasero was run with low burn speed, then i
have a more convenient suspect. It is the backside of

"Brasero always burns CD/DVD at max speed (speed option is ignored)"

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/656297)

Brasero swaps the values for read speed and write speed in libburn call
burn_drive_set_speed(). If you ask it to burn at 4x speed, then it tells
libburn to burn at maximum speed and to set read speed to 4x.

(The problem is not new:
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569244](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569244)
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=635179](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=635179)
  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=715405](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=715405)
)

I just made a test with the speed setting of xorriso. "min" rather than
"max". The -check_media parameter max_lba=1024 lets xorriso end after
only 2 MB of reading:
```

$ xorriso -outdev /dev/sr0 -read_speed min -check_media use=outdev min_lba=0 max_lba=1024
...
xorriso : UPDATE : 32 of 1025 blocks read in 2 s , 0.3xC
xorriso : UPDATE : 384 of 1025 blocks read in 3 s , 4.5xC
xorriso : UPDATE : 736 of 1025 blocks read in 4 s , 4.5xC
xorriso : UPDATE : 1025 of 1025 blocks read in 5 s = 2.9xC
Media checks :        lba ,       size , quality
Media region :          0 ,       1025 , + good
Media region :       1025 ,     156131 , 0 untested

```
And now dd is slow:
```

$ dd if=/dev/sr0 bs=2048 count=25000 of=/dev/null
25000+0 records in
25000+0 records out
51200000 bytes (51 MB) copied, 74.9567 s, 683 kB/s

```
Striking ressemblence, isn't it ?
(One can tell by the drive's noise which speed is set.)

---------------------------------------------------------------------
  
Have a nice day :)

Thomas

---

### Post by jg1 on 2019-05-09
Wow ! There's a fair bit to digest here and it's a bit late this evening.
But what you say seems to make sense on a quick first reading although it doesn't matter where the CD was cut, or if it was a commercial disk. However if Brasero has upset the drive perhaps I'll give xfburn a try and see if that has the same effect.  If xorriso has cleared the jam that'd be great.  It would mean that I could do more tests and perhaps isolate the problem definitively
I'll also look at the bug reports.
Yes the ^C was me stopping the thing as the result was clear and it would save me wading through 710MB worth of terminal output to post my reply.
I really appreciate the effort you've put in on this.
At the moment I'm in the middle of synchronising data across 5 machines so I'll pick it up again in the morning.
Tks again
jg

---

### Post by scdbackup on 2019-05-09
Hi,

> Wow ! There's a fair bit to digest here and it's a bit late this evening.

You have reached the cellar level of support: libburn.


> However if Brasero has upset the drive perhaps I'll give xfburn a try

Well, all burn programs which set CD speed have to leave the drive
with some setting when they end their job. Brasero is special because
it leaves the read speed at what it intended to use as write speed.

A search in the Debian source of Xfburn reveils three occassions of the 
libburn call. All three set read speed to 0 (= maximum).
  [https://codesearch.debian.net/search?q=package%3Axfburn+burn_drive_set_speed](https://codesearch.debian.net/search?q=package%3Axfburn+burn_drive_set_speed)
Note the change of position of the 0 in Brasero
  [https://codesearch.debian.net/search?q=package%3Abrasero+burn_drive_set_speed](https://codesearch.debian.net/search?q=package%3Abrasero+burn_drive_set_speed)

So a CD burn run with Xfburn will probably set read speed to maximum,
as did the xorriso -check_media run. (xorriso is actually a burn program,
too.)


Have a nice day :)

Thomas

---

### Post by jg1 on 2019-05-10
I've now done a heap more tests and my summarised findings are as follows.  I have the terminal outputs but there is far too much to post here.

It appears that there are 3 problems at work here.
1)  The CD drive on the XPS17 is a fairly old (7yrs) laptop drive (and therefore flimsy) which occasionally gets read errors (about 1 in 50 CDs inserted) at start-up and initial registration and in responding to the eject command.
2)  Irrespective of the CD/DVD drive being used, Brasero when recording CDs on recent ubuntu distros (1804 and 1604 tested) writes a bad block at the end of the data. This doesn't happen with DVDs or CDs recorded on very old systems (0710 and 1004 were tested).  I haven't tested anything in between.  This doesn't happen with xorriso which writes clean in every test I've done and reads back marginally quicker than any recorded with Brasero. (Same stock, same hardware recorder, 2-5% quicker)
3)  Xubuntu 18.04 recognises the bad block at the end of a CD read (irrespective of application used) and sets the maximum speed to 4x (600KB/s) so that the next program reads slowly.  That can be fixed by using xorriso and cancelling it before the end of the disk.  If it runs to the end, the system still sets the drive speed to 4x.  Earlier distros don't care so read speeds are max on anything up to 16.04.4 irrespective of what happened on the last run.

So I think that we have it.
The problem lies with Brasero and the fact that the new distro recognises and (in my view) overreacts to the error.
 
It's a great pity that xorriso is such a fantastic piece of software that it is too complex for routine daily use by a numpty such as myself.

Question: are there any burners out there that have a simple GUI for handling CDs and DVDs (similar functionality to Brasero) but which have xorriso (or similar engine) as the back end?

Thomas, this has been a really helpful exercise and my understanding of CDs has increased immeasurably.
Thank you
jg

---

### Post by scdbackup on 2019-05-10
Hi,

> 2)  Irrespective of the CD/DVD drive being used, Brasero when recording CDs
> on recent ubuntu distros (1804 and 1604 tested) writes a bad block at the
> end of the data. This doesn't happen with DVDs or CDs recorded on very old
> systems (0710 and 1004 were tested).

Hehe. That's another one of my favorite Linux bugs.
It happens only with CD written with write type Track-At-Once (TAO) and
further depends on the reader drive and on the Linux kernel version.

Workaround would be to select Session-At-Once (SAO aka DAO) in Brasero.
(If i only knew where the option is hidden.)

If you use Xfburn instead of Brasero, make sure to have set "Write mode"
to "SAO", not "TAO". The default "Auto" is supposed to choose SAO. But
one never knows ...
See the "Write mode" selection menu in the middle of
[http://www.tuxarena.com/static/screenshots/tut01/xfburn03.png](http://www.tuxarena.com/static/screenshots/tut01/xfburn03.png)

TAO writes two non-data blocks (aka "Run-out") at the end of the CD track.
Most drives tell the track size including those blocks when being asked
by SCSI command READ CAPACITY. Those can trigger the Linux error, because
Linux tries to read up to the announced last block.

Modern Linux has some workaround which seems to help if the number of CD
blocks is divisible by 2, but not with odd numbers.
So we still see this problem frequently but often it also gets hidden by
a friendly drive or the Linux attempt to work around.

xorriso's -check_media assumes such a TAO end if the last two blocks of
the CD track are not readable as data. Then it reports them separately
as neither good nor bad ("0" instead of "+" or "-").
```

Media checks :        lba ,       size , quality
Media region :          0 ,     157154 , + good
Media region :     157154 ,          2 , 0 tao_end

```


> This doesn't happen with xorriso which writes clean in every test I've done

If you don't tell it to use TAO, then it will choose SAO if it knows
the size of the data job in advance. Only image burning from a pipe
will choose TAO and normally won't work with SAO. E.g.
```

tar czf - . | xorriso -as cdrecord -v dev=/dev/sr0 -waiti -eject -

```


> 3)  Xubuntu 18.04 recognises the bad block at the end of a CD read
>  (irrespective of application used) and sets the maximum speed to 4x
> (600KB/s) so that the next program reads slowly.

Ouchers ! That's stupid. Speed has nothing to do with read errors.
The drive would slow down and retry on its own, if the block was
marked as data block.

In any case the slowdown should be revoked after the tray moved out
for a potential media change.

(I still think that Brasero slows down too. But with a 10x CD-RW or
a 40x CD-R and maximum write speed this has not such a dramatic effect.)


> That can be fixed by using
> xorriso and cancelling it before the end of the disk.

You need to wait with cancelling until the first message
```

xorriso : UPDATE : X of Y blocks read in Z s , N.NxC

```
Else you risk that the SET CD SPEED command was not yet sent to the drive.

The minimal remedy without cancelling would be
```

xorriso -outdev /dev/sr0 -read_speed max -check_media use=outdev max_lba=0 --

```
Runtime 5 to 10 seconds without intervention. It stops as soon as it is
safe for your purpose.


> It's a great pity that xorriso is such a fantastic piece of software that it
> is too complex for routine daily use by a numpty such as myself.

There is also a complex GUI
  [https://screenshots.debian.net/screenshots/000/015/893/large.png](https://screenshots.debian.net/screenshots/000/015/893/large.png)

You could download
  [https://dev.lovelyhq.com/libburnia/libisoburn/raw/master/frontend/xorriso-tcltk](https://dev.lovelyhq.com/libburnia/libisoburn/raw/master/frontend/xorriso-tcltk)
give it x-permission, and run it by simply executing in a shell terminal while being in its
dowload directory
```

./xorriso-tcltk

```
Click on "Help" to the upper right, and right-click on any GUI element
in order to get a window with a help text.
(Another terminal window with "man xorriso" is helpful to learn details
 about the mentioned xorriso commands.)


> Question: are there any burners out there that have a simple GUI for
> handling CDs and DVDs (similar functionality to Brasero) but which have
> xorriso (or similar engine) as the back end?

I tried to persuade Xfburn and K3B. But both projects have no maintainer
who could make such a big change. Brasero is not even maintained enough
to get the burn speed setter fixed.

So i wrote xorriso-tctk as demo of a frontend program that cares for
user interaction but leaves the job of composition and burn settings
to xorriso. (6000 lines of Tcl code. About 3500 are comments and help
texts. It was about a week of work.)

Have a nice day :)

Thomas

---

### Post by jg1 on 2019-05-11
Thomas, that's brill.
Once upon a time (it may even have been in windows 3.1 when CDs were still quite a new thing) I'm sure Brasero had an option to write SAO and the default was TAO. There used to be lots of settings like buffer size and read-after-write checks etc.

Xfburn seems to do the trick and it's usable as an every day pgm - even for an old sausage fingers like me!  And even if I forget to set it to SAO, it seems to write clean CDs on Auto.  Not tried DVDs but I'm making the assumption that that bit works OK but I will check in due course.

I haven't tried your GUI yet but it's on the "to do" list.  Right now I have a whole heap of CDs that need rewriting...  'twas ever thus!

Tks again
jg

---

### Post by jg1 on 2019-05-11
**Interesting postscript ...**

Tried to recreate a Xubuntu 12.04.4 Live CD with a bad end block/run-out but the new image on repository has grown to 780MB - too big for a CD.  So used Brasero to create an ISO from the bad CD (using 1:1 disk copy) and it asked to install cdrdao so it could write "disk at once", aka SAO. It then creates a .toc image file that cdrdao uses to burn disk-at-once.  The result was clean, ie no bad block at the end.  Unfortunately it still doesn't provide the option to burn regular CDs disk-at-once!  

jg

---

### Post by scdbackup on 2019-05-11
Hi,

> Xfburn seems to do the trick and it's usable as an every day pgm

It's most obvious drawback is that cannot do multi-session.

Brasero can "import" a medium which was "left open" in a previous burn run.
It then can write an updated directory tree and new file data to the
remaining free space on the medium.

xorriso is able to do this for ISO 9660 filesystems even on DVD+RW, BD-RE,
and formatted DVD-RW media, which do not support multi-session by hardware.
(Commands -dev and -indev do this importing.)

K3B is similarly capable by help of growisofs.

> I'm sure Brasero had an option to write SAO and the default was TAO.
> There used to be lots of settings like buffer size and
> read-after-write checks etc.

I started my outdated copy of Brasero. 3.11.4. It mistakes a DVD+RW for
a DVD-RW and offers different burn options for it than for a blank CD-RW.
No option for TAO-or-SAO to see with either of the media.
(If it thinks it's a DVD-RW, then there should be the choice between
 DAO and Incremental write type.)

A code search in Debian's repo gives me the impression that SAO is
only enabled for audio CDs with CD-TEXT. Maybe there is also an opportunity
to use wodim as interpreter of .toc or .cue files. They describe a SAO run.

> cdrdao [...] disk-at-once

cdrdao's disk-at-once is the same write type as SAO.
(Actually Disk-At-Once is the term for DVD-R and unformatted DVD-RW.)

Have a nice day :)

Thomas

---

### Post by jg1 on 2019-05-11
Hi, Thomas
Yes the multi session thing is a pain, but not such a nuisance nowadays as it was 20 years ago when files were so much smaller.  Most of my current CD usage is for start-up/recovery disks, music and sending stuff in the mail, none of which encounter the need for multi-session recording.  In any case, I find USB sticks much more convenient for that sort of thing.
I'm afraid I don't have any of my really old Brasero.exe files but I still have a CD with an early copy of "Burning Nero" from around 1996 according to the copyright - no version number quoted and as I don't run Win3.1 any more, I'm not about to install Wine in the hope I can launch it!  DVDs hadn't been invented then, or if they had they weren't commercially available.
I'm going to draw stumps at that.
Tks again for your help and guidance.
vbw
jg

---

