---
title: "Running out of disk space...but why?"
date: 2010-04-17
forum: Hardware
---

### Post by jtemple67 on 2010-04-17
Hi all!

I'm new to the forums but not new to Ubuntu.  I started with Ubuntu 8.10 on a Compaq Evo N800C about a year ago.  I upgraded to 9.04 and everything was peachy.  Then about a month ago I upgraded to 9.10.  That's when things didn't go so well.

After 5-10 minutes running email, internet, etc.  I get various messages about having no disk space left.  Sometimes the message says I have 0 bytes left and sometimes it has just small boxes in the dialog.  Whenever this happens the system becomes unstable and the only way to get it back is hard power off.  

In the past when I've had problems I just search the forums until I find the answer.  I've done the same here but can't find anyone with my exact problem.  When I run "df" I get:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            152051968   6821984 137566984   5% /
udev                    513224       244    512980   1% /dev
none                    513224       364    512860   1% /dev/shm
none                    513224        84    513140   1% /var/run
none                    513224         0    513224   0% /var/lock
none                    513224         0    513224   0% /lib/init/rw

As you can see from above, I've got plenty of space (150GB hard drive).  Nothing else is on the machine (no Windows junk, no dual partitions).  Disk Usage Analyzer shows a total of 145GB with 6.5GB used and 138.5GB available.  If I run "fdisk -l /" I get:

last_lba(): I don't know how to handle files with mode 40755

Again, no problems on 9.04.  I am also up to date on 9.10.  

Anyone have any ideas?  It would be greatly appreciated!

---

### Post by replica2010 on 2010-04-17
Have you looked at the permissions on files, in your home directory? Could be that until 5-10 minutes after using browser it goes to write out session information, and can't. 

Do your log files (tail -n 150 /var/log/messages for example) tell you anything more?

(I had a problem with Chrome suddenly just crashing because it couldn't write to one of the lock files.)

You might look for any weirdness in your /var/run directory?

All guesses, but maybe it'll point you somewhere until someone who knows what they're talking about replies. :-)

---

### Post by jtemple67 on 2010-04-17
Well, one thing for sure...it doesn't seem to have a rhyme or reason.  For example, I've been running the machine for about 30 minutes now with no problem.  One thing I have noticed is that it seems to happen faster if I have Thunderbird open.

I did the things you suggested.  All permissions in my home directory look OK.  I ran tail and not sure what I'm looking for.  I also looked in /var/run but again, not sure what to look for.

Thanks for the reply!

---

### Post by replica2010 on 2010-04-17
In your /var/log/messages, do you see any error messages about disk space?  

When you get a dialog saying you don't have any space left, what program's tossing it up?  Who owns the dialog box, in other words? Is it Firefox or Thunderbird, or gnome's disk utility/notifier app?

When you say you have to hard power off the system: have you tried CTRL-ALT-F1 to do a console login? (if you've not done that before, do it now; you can get back to your X session with ALT-F7 usually.  Note: *CTRL*-ALT-F1 (or F2-F6 if you haven't disabled the ttys) but only *ALT*-F7 to get back).  At console login when you get the message (assuming you can do so), what's df show?

Are you plugging in any flash drives?  Have you run a check on your file system recently?

Since everything was working prior to you upgrading, that would seem to me permissions, or something now configured to write to a device (perhaps a virtual one) with very little space.  Or, it could be that there's no problem with your space at all, but the application thinks there is, and hoses your session from there.  Interesting problem; please provide some more information as requested above.

---

### Post by 2hot6ft2 on 2010-04-17
[[SOLVED] Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

---

### Post by jtemple67 on 2010-04-18
> **replica2010 said:**
> In your /var/log/messages, do you see any error messages about disk space?  

When you get a dialog saying you don't have any space left, what program's tossing it up?  Who owns the dialog box, in other words? Is it Firefox or Thunderbird, or gnome's disk utility/notifier app?

When you say you have to hard power off the system: have you tried CTRL-ALT-F1 to do a console login? (if you've not done that before, do it now; you can get back to your X session with ALT-F7 usually.  Note: *CTRL*-ALT-F1 (or F2-F6 if you haven't disabled the ttys) but only *ALT*-F7 to get back).  At console login when you get the message (assuming you can do so), what's df show?

Are you plugging in any flash drives?  Have you run a check on your file system recently?

Since everything was working prior to you upgrading, that would seem to me permissions, or something now configured to write to a device (perhaps a virtual one) with very little space.  Or, it could be that there's no problem with your space at all, but the application thinks there is, and hoses your session from there.  Interesting problem; please provide some more information as requested above.

Thanks for the reply! 

I opened the messages file and don't see any error messages about disk space.

As far as who owns the dialog box, I'm not sure.  It happens when Firefox and Thunderbird is not open so I assume it's a Gnome window.

The last time that the system became unresponsive I did try Ctl+Alt+F1 and could not get a console window.  Another time I tried the same and I got a window with some garbled characters and could not exit the terminal.  In both cases I had to hard power off the system to get it back.

Yesterday I decided to uninstall Chrome because I noticed in Disk Usage Analyzer that the Chrome cache was almost up to a GB.  I tried to clear the cache with Chrome but it didn't work.  When I rebooted I was presented a recovery console and suggested I run fsck.  I did so and got pages and pages of requests to fix things it found wrong.  I rebooted and got the desktop back but the system still hangs.  I also am now getting an error from Package Manager and attempting to run system update results in an error (Error opening cache).

I'm starting to think that a wipe and reload may be in order.  Is that too drastic?

Thanks!

---

### Post by cguy on 2010-04-18
I've had this happen twice.
It were the log files which got out of control.
I learned my lesson and now I always, ALWAYS create a /var/log partition.

I never figured out why they grew uncontrollably. I was too busy for that, so I just reinstalled Ubuntu - 20 minutes. (did I mention that I have a /home partition, so I didn't lose any files or settings?)

---

### Post by drs305 on 2010-04-18
Logs, undeleted trash and backups to the wrong partition are the usual suspects. This post details ways to check your disk space and perhaps find out what is causing your free space to disappear:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Cracauer on 2010-04-18
> **drs305 said:**
> Logs, undeleted trash and backups to the wrong partition are the usual suspects. This post details ways to check your disk space and perhaps find out what is causing your free space to disappear:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

How would he fill up his almost 150 GB in a couple of seconds? I don't think he has an actual disk full problem here.

I want to see the actual error message cut'n'pasted. If it is a klickbunti program a screenshot.

In general, problems like these often result from people having a separate /tmp mount (on a memory-backed filesystem) and then some program might run out of space there, although there is space in the other filesystems. But from your df output (thanks for posting it) we can see that you don't have one.

---

### Post by replica2010 on 2010-04-19
If fdisk is grumbling... say, wouldn't he be out of disk space if partitions were unmounted to avoid further corruption? Just wondering...

That the console's garbled... sounds like memory corruption? Definitely something weird.  

Directed to OP: if you do a reinstall, and it's a hardware issue, then you'll have wasted a fair shake of time.  It's possible that upgrading to 9.10 stressed disk or memory just enough to push borderline components over; when you're using Firefox/Thunderbird (both individually enough to make even more than modest hardware scream in agony and fear) you're also stressing it.

Actually, silly question, but have you ruled out heat issues?

Second silly question: What happens if you use a LiveCD to do the activities that are causing this? (ie, browsing, obviously not checking email)

2a: If your system's fine using a LiveCD + Firefox, what happens if you then mount your drives (via LiveCD) and run Firefox / Thunderbird off your hdds?

That way, you can at least try to narrow it down a bit. If all that's hunkey dorey (say, you get a couple HOURS browsing 'net / checking email) then you can breathe a little easier that it's some braindeadness elsewhere...

Very very odd that you can't get to a console, though...

---

### Post by jtemple67 on 2010-04-19
Okay...so things were getting weirder and weirder.  I decided that a clean install was called for.  I ruled out bad disk and memory as I've replaced both in the not too distant past.  So I backed up the few things that I needed then ran a fresh install.  On first reboot I had a problem with a hard drive GUID on the grub script.  I deleted that line (based on another post I read) and the system booted and has been running without problems.  AAMOF, the system has been on all day (ran updates after the reload) with no errors.  So it seems the reload fixed the problem...for the moment.

---

