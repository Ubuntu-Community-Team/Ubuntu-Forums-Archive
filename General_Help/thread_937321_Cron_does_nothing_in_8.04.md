---
title: "Cron does nothing in 8.04"
date: 2008-10-03
forum: General Help
---

### Post by adriandown on 2008-10-03
Hello,

I'm trying to get crontab to automate backup on my Ubuntu 8.04 box, but I can't get cron to run anything.  I've posted two scripts that I tried below, both of which work on their own but do nothing when part of a cron tab.

One thing that was interesting to me is that there was no cron log in /var/log.  I checked in /etc/syslog.conf, and the cron line was commented out (???).  I never touched (nor even heard of) this file, so it must have come this way by default in Ubuntu 8.04.

My suspicion is that cron is not running at all.  Check out the last script below.  It, too, produces no results nor any cron log.  I've tried adding cron tabs as both a user and root, but neither produce any results at all.

Any help is appreciated.  Let me know if there's any more information I can provide to help debug this problem, let me know.

Thanks,
Adrian

This is the script that I ultimately want to run with cron
```

#!/bin/bash

rsync --verbose --stats -x --archive --relative --delete --delete-excluded --delete-after --partial /work/adrian /mnt/cribsbiox/home/adown/backup

```
This is the crontab that I'm trying to use to run it.
```

15 15 * * * /work/adrian/scripts/backup/backup.sh

```
This is the test tab I tried just to see if cron was alive
```

* * * * * echo test > ~adrian/Desktop/tmp

```

---

### Post by mike2357 on 2008-10-03
Here are a few diagnostic steps you can take:

1.  Run the command "crontab -l"  This displays what is actually loaded in your crontab file.

2.  Run the command: "ps -eaf | grep cron"  This will show if the cron daemon is running.  Something like the following line should be displayed:
root      6365     1  0 05:42 ?        00:00:00 /usr/sbin/cron

3.  Do the files /etc/cron.allow or /etc/cron.deny exist?  If so, cron could be prevented from running for you.  Run "man crontab" for details.

If you see anything suspicious, post back what you find.

---

### Post by adriandown on 2008-10-04
Aha!  The cron daemon wasn't running.  The greppng the processes for cron returned nothing, so I did "sudo /etc/sbin/cron".  When the scheduled time for the crontab came around, it worked like a charm (finally!!!).  Okay, so now the questions become:
1) How do I set the cron daemon to run at startup?
2) Why isn't it running by default?  Lots of other people in my office use Ubuntu, and none of them have ever had any issues with cron.

Thanks again,
Adrian

---

### Post by adriandown on 2008-10-04
Hold on, I think I might know what's going on.  I'll have to wait till I get back to my office on Monday and reboot my machine to verify, but I think the sequence of events went as follows:
1) Originally, my crontab didn't work because the crontab file I was trying to use didn't terminate with an endline character.  Instead of printing some kind of useful message, cron just failed silently, which was pretty perplexing.
2) In the course of trying to figure out what was going on, before I realized the endline problem, I tried launching something like /usr/sbin/cron (although it might have been something else cron-related if there is anything, I don't exactly remember).  I got an error about a file lock: some other process was already monopolizing a necessary cron file.  Since the error message gave the PID of the offending process, I killed it and then tried launching cron manually.  This process was probably the cron daemon that was started when I booted the computer.  Since I still hadn't figured out the endline business and launching cron on my own didn't seem to solve the problem, I think I killed the cron process that I had initialized on my own.  My flawed reasoning, grasping for anything in the fog of confusion,  was that I didn't want to have a process running that might lock a file that cron would need if it ever decided to work.  I didn't realize at the time that I was launching and killing the necessary daemon, but it all makes sense now.
3) I finally found a post on an obscure internet forum where somebody with cron problems had found that adding an endline at the end of their crontab solved their problem.  I added an endline as well, but much to my dismay, cron continued to fail silently.  However, no the issue was that the cron daemon was dead, even though the file was formatted correctly.  The end result was that cron failed silently, at least from my perspective, and it appeared that the addition of the endline character had made no difference.

This is conjecture at this point, but my hunch is that cron will work fine when I reboot my desktop at work on Monday.  One more little question about cron: does my crontab file have to have any particular permissions?  I tried changing the permissions of both the crontab file and the script to be executed to 777 in desperation, and I'd like to change them back to something more reasonable if possible.

The moral of the long and stressful story: CRONTAB FILES NEED ENDLINES!!!  Maybe these characters are called newlines or something else, I'm not sure.  In any case, if in doubt, go to the end of your crontab file and hit enter.

I'm really glad this day-long ordeal is (hopefully) over, just in time for the weekend :D.

---

### Post by mike2357 on 2008-10-04
Great!  You solved your own problem.

In answer to your question about permissions on crontab files, it's something you should never have to worry about if you use crontab commmands.  To modify a crontab file, use "crontab -e", and crontab will figure out what permissions to make the crontab file.  Another advantage of "crontab -e" is that it will do some basic syntax checking when you save/exit and warn you of errors.  I suggest that you not directly modify the crontab files in /var/spool/cron/crontabs manually or set permissions on them.  The cron daemon runs as root so it will be able to access anything.  In fact, if you have changed permissions on a crontab file, I suggest you save/delete/reload as follows:

crontab -l > SAVE_CRON     (Note: this saves what's in cron)
crontab -r                 (Note: this deletes what's in cron)
crontab SAVE_CRON          (Note: this reloads cron)

Run "man 5 crontab" to get a lot of good information about cron.

---

### Post by adriandown on 2008-10-06
After rebooting the computer, cron is working normally.  So it was the endline after all.  Thanks for the debugging help :-).

---

### Post by directcharitycontribution on 2008-10-06
OP, perhaps you could mark as [SOLVED] using 'Thread Tools'.

---

