---
title: "Multiple atd processes causing headaches"
date: 2008-07-25
forum: General Help
---

### Post by gstuart on 2008-07-25
Hello - Often when I schedule a script to run (call to mencoder for television capture) from crontab, I get multiple (dozens? hundreds) of atd processes continually launching, locking up my computer.

This only appears to be a problem when my computer has been running for a long time, then my script is called up by cron, i.e. for a show that has been scheduled to record, days in advance.

In the shorter-term, this is not a problem - i.e. when I schedule recording for later that day, or the next day, ...

Any ideas / solutions?

Thanks, Greg  :-)

---

### Post by gstuart on 2008-07-28
Anyone?  Is this a bug, introduced by recent package updates?

Is no one else seeing this - multiple, uninterruptible atd processes (dozens, literally), frezzing up the computer.  I'm using Ubuntu 8.04 LTS; the problem arises when I call mencoder using crontab; it was working perfectly, until about a week (or less), ago.

grrrrrrrrrrrr ....................

---

### Post by gstuart on 2008-08-18
FYI - The solution is discussed in this thread - Greg  :-)

========================================================================

[http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes-2.html#post302226357](http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes-2.html#post302226357)

[http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes-printfriendly.html](http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes-printfriendly.html)

 The UNIX and Linux Forums  ([http://www.unix.com/index.php](http://www.unix.com/index.php))
-   UNIX for Advanced & Expert Users ([http://www.unix.com/unix-advanced-expert-users/](http://www.unix.com/unix-advanced-expert-users/))
-   -   Crontab spawning multiple at processes ([http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes.html](http://www.unix.com/unix-advanced-expert-users/77526-crontab-spawning-multiple-processes.html))

gstuart 	08-17-2008 02:22 PM

Crontab spawning multiple at processes
 
Hi - I need help. My user crontab is spawning multiple at processes (and multiple mencoder program starts, that exit, then restart, repeatedly), locking up my system.

For example I have this entry in my crontab:

$ sudo crontab -u victoria -e

* * * * * ~/recordings/pvr1
* * * * * ~/recordings/pvr2
[etc.]

where pvr1, pvr2, etc. are executable bash script files, e.g. pvr1 is:

#!/bin/sh
at -f ~/recordings/record_tv_1 12:58 pm Aug 17 2008
exit

As you can see, this calls my mencoder ecording file, record_tv_1:

tuner=/dev/video1 # or, /dev/video1 for the 2nd PVR-150 tuner in my Hauppauge PVR-4500 card
channel=70
duration=01:04:00 # hh:mm:ss
record_directory=/media/sdb1/recordings/UNPROCESED/
# record_directory=/home/victoria/temp/UNPROCESED/
file_name=Dog_Genius

ivtv-tune -c $channel -d $tuner

sleep 1

mencoder pvr:// -tv \
driver=v4l2:width=640:height=480:input=0:device=$t uner:norm=NTSC:chanlist=us-cable:outfmt=yuy2:adevice=/dev/dsp:audiorate=44100 \
-vf lavcdeint \
-ovc lavc \
-lavcopts vcodec=mpeg4:vbitrate=4500:keyint=3 \
-oac mp3lame \
-lameopts br=128:cbr:mode=3 \
-ffourcc divx \
-endpos $duration \
-quiet \
-o $record_directory$file_name"_"`date +%A_%B_%d_%Y_%I:%M_%p`.avi

The problem is that virtually every time the pvr script is called by crontab, it spawns (continuously) multiple/new at command processes (Process Viewer), and also several mencoder processes that continually start, stop, relaunch, that are multiply-present in Process Viewer at any one time. The recordings are all partial files (snips). This had been working properly, until about a month ago (Ubuntu updates, screwing things up?).

I'd appreciate it is someone could explain to me what the problem is. FYI: I am using Ubuntu 8.04 LTS -Hardy Heron.

Thanks, appreciated, Greg :-)

========================================================================

Annihilannic 	08-17-2008 08:43 PM

If you are calling these scripts from cron every minute, then it is no surprise that multiple at jobs are being scheduled... why do you need the crontab entries at all? Why don't you just schedule the programs directly through at?

========================================================================

vidyadhar85 	08-17-2008 10:29 PM

ya if you are using crontab to shedule why are you again using at command in your script??

========================================================================

gstuart 	08-17-2008 11:36 PM

Hi - Thank you for your replies ... I had intended to schedule the recordings from a script, avoiding the more tedious route via crontab itself. Regardless, since the bash scripts contain a single at command (scheduled time), I don't why cron is repeatedly spawning multiple processes (at commands, for the single, scheduled event).

That is, despite reading the file every minute, once this scheduled at command has been executed (at the appropriate time), shouldn't further calls to this bash file (with a now-expired at command start time) simply be ignored?

Or, it it the case that since the crontab-called file hasn't run it's course (completed, e.g for a scheduled recording of 1 hour), that cron thinks that the command hasn't executed, and tries to execute at the next available opportunity (here, every 1 minute)?

FYI, after I posted my original question, I had the idea (subsequently suggested, above), and directly called my record_tv_* scripts from crontab, which seems to be the solution - not quite what I had wanted, but so be it.

E.g.,

58 18 17 aug sun ~/recordings/record_tv_1

========================================================================

Annihilannic 	08-17-2008 11:59 PM

I agree that it sounds like something is going wrong there, and I'm not sure what's causing it. But what I don't understand is why you are using crontab at all. When you want to schedule a recording, just run the at command once, as you had in the bash script... job done? It will only run once, at the scheduled time, and then it will be forgotten about.

========================================================================

Vi-Curious 	08-18-2008 12:07 AM

When you set up your cron, you set it to call the script every minute. So, every minute, cron calls your script and your script schedules an at job. When that time arrives, the system will start running all of those queued up jobs scheduled by at.

Once you have passed the time specified in the at command, cron is still going to call your script (every minute) and it is going to try to schedule the at. Since the time is now passed, those at jobs should not be scheduled, but cron and the script are going to continue to run. How do you expect them to know that the time is expired? At will know the time is already expired and refuse to schedule a new job but everything leading up to that point is still going to happen.

========================================================================

gstuart 	08-18-2008 09:03 AM

Yes, I understand (fully) now ... thanks. Cron was the wrong approach - stick with "at," as suggested.

A related question: How can I delete those (100's, if not 1000's) of scheduled processes (at commands), a legacy from cron?

I know that I can remove specific job ids using atrm, but it won't accept wildcards. There are simply too many of these, to remove tyhem via atrm, one at a time.

Thanks again - Greg :-)

========================================================================

era  	08-18-2008 12:18 PM

Something like

Code:
atq | cut -f1 | xargs atrm

========================================================================

gstuart 	08-18-2008 06:10 PM

Quote:
Originally Posted by era (Post 302226180)

Something like

Code:
atq | cut -f1 | xargs atrm

Brilliant - this worked - thanks!! :-)

========================================================================

gstuart 	08-18-2008 06:49 PM

Update: Scheduling recordings via "at,"

at -f ~/recordings/record_tv_test 6:15 pm Aug 18 2008

where record_tv_test is an executable bash file (below) works fabulously (as did the command to delete all those 100's! of "un-needed" at commands, that accumulated via cron)!

Thanks again - you guys are great! Greg :-)

#!/bin/bash

tuner=/dev/video0
# or /dev/video1 for my 2nd Hauppauge PVR-500 card
channel=58
duration=00:05:00 # hh:mm:ss
record_directory=/media/sdb1/recordings/UNPROCESED/
file_name=test

ivtv-tune -c $channel -d $tuner

sleep 1

mencoder pvr:// -tv \
driver=v4l2:width=640:height=480:input=0:device=$tuner:norm=NTSC:chanlist=us-cable:outfmt=yuy2:adevice=/dev/dsp:audiorate=44100 \
-vf lavcdeint \
-ovc lavc \
-lavcopts vcodec=mpeg4:vbitrate=4500:keyint=3 \
-oac mp3lame \
-lameopts br=128:cbr:mode=3 \
-ffourcc divx \
-endpos $duration \
-quiet \
-o $record_directory$file_name"_"`date +%A_%B_%d_%Y_%I:%M_%p`.avi

========================================================================

---

