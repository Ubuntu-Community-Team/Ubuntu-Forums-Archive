---
title: "[SOLVED] Automatically Resume from Sleep/Standby/Suspend"
date: 2008-10-05
forum: General Help
---

### Post by Altay_H on 2008-10-05
I'm looking for a way to automatically resume from standby. I use crontab to use my computer as an alarm clock, and I'd like to be able to leave it in standby overnight. The problem is the task won't run if the computer is in standby. I've found a plethora of programs that offer this feature for Windows, but I can't find any way to accomplish this in Linux. I need a low-level program that will be able to resume the system from standby preferably at a specific time.

---

### Post by Altay_H on 2008-10-12
Bump.

Surely there must be *some* way to do this.

---

### Post by earthpigg on 2008-10-12
[http://manpages.ubuntu.com/manpages/intrepid/man1/apmsleep.html]("http://manpages.ubuntu.com/manpages/intrepid/man1/apmsleep.html")

ive never used it myself.

i have no idea if there is a graphical front-end for it.

---

### Post by earthpigg on 2008-10-12
again, i have not tried this (on a public windows computer ATM, so i cant try it right now)... but, in theory i think

```
apmsleep 05:30 -s
```

will immediately put your computer in suspend until 0530. -S will do standbye. you may have to put "sudo" in front of it.

the *easiest *way to have that wake you up, i guess, would be to turn your speakers up and pick the sound you want to be your alarm as your login sound.

---

### Post by Altay_H on 2008-10-12
Thanks. That's exactly what I was looking for. I prefer it without a graphical frontend. The only problem I have is that when I try to run it, the terminal informs me that:
```
apmsleep: Your kernel does not support APM.
apmsleep: Recompile kernel with APM and /dev/rtc support

```
Is there a guide to recompiling my kernel with APM and /dev/rtc support? I can imagine recompiling my kernel is no trivial task, but I'd really like to be able to use this. 

> **earthpigg said:**
> the *easiest *way to have that wake you up, i guess, would be to turn your speakers up and pick the sound you want to be your alarm as your login sound.
I'm not sure what you mean by this. I have my system set to automatically log in on resume, so crontab should run the process that wakes me up properly. All I need is to find a way to make apmsleep work.

---

### Post by earthpigg on 2008-10-12
recompiling your kernel is indeed no trivial task. way over my head. :)

and hey, look at [this]("https://bugs.launchpad.net/ubuntu/+bug/179613") bug report...

that being said, Ibex which is coming out on the 30th, will come with a new kernel version. i think.

so, maybe the problem will be solved for you at that point. we can hope.

edit: and ya, i wasn't thinking in my earler post about your login sound. :)

---

### Post by Altay_H on 2008-11-16
Just to update, Intrepid Ibex does come with a kernel update, which unfortunately not only breaks my volume buttons but also doesn't solve the apmsleep problem. I have found a possible solution though.

Apparently TuxOnIce is a kernel patch that adds functionality to sleeping. I'm not sure if patching my kernel with it will allow me to use apmsleep or not, but it's the best thing I've found so far. I might try it, but I'm reluctant to patch my kernel without knowing what it will do. Here's the link: [https://help.ubuntu.com/community/Suspend2Kernel](https://help.ubuntu.com/community/Suspend2Kernel)

I also found a way to enable apm on Ubuntu, but the guide is for version 4.10 (Warty Warthog), so I doubt it will actually work. Here's a link to that guide: [https://help.ubuntu.com/community/SuspendHowto](https://help.ubuntu.com/community/SuspendHowto)

If anyone has apmsleep working, please let me know how you did it.

---

### Post by Altay_H on 2008-11-19
I've made some progress in my search to enable apmsleep. I found this guide to recompiling a kernel:
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

Unfortunately, I don't know how to enable /dev/rtc and APM. I found APM under:
Power management options ---> <M> APM (Advanced Power Management) BIOS support

But there are six different options under that (see attachment). I have no idea which one(s) need to be enabled. Also, I can't find /dev/rtc at all. I found a website that suggested it was under General Setup, but it was an old website and I couldn't find it under General Setup.

If anyone has any idea how to set up the kernel to support apmsleep please respond.

---

### Post by Rodney9 on 2008-11-22
I too would love to get Ubuntu 8.10 to auto wake up from sleep at a set time, my old Mac did and I'm told Windows is easy to setup also. There must be some linux software to set it surely.
My bios has something called rtc alarm but nothing happens when I set it.

---

### Post by Rodney9 on 2008-11-23
How about rtcwake, how does it work, I tried  > sudo rtcwake -s 20 but it does not wake up ever.

---

### Post by Altay_H on 2008-11-24
Well, I made some more progress. I found that the default kernel does have support for rtc (it's under Device Drivers ---> Real Time Clock, if you're configuring your kernel), so if I could only figure out which APM options are necessary for apmsleep, I could recompile my kernel and (in theory) be able to use apmsleep. No progress figuring out which options are necessary though.

The program rtcwake looks promising. I'm going to give it a try and see if it works for me.


UPDATE:

I gave rtcwake a try, and it's behaving very strangely. What I expected was after I issued the command:
```
sudo rtcwake -s 1
```
My computer would put itself to sleep, then automatically resume 1 second later.

This is what actually happened:
```
:~$ date
Mon Nov 24 14:24:44 EST 2008
:~$ sudo rtcwake -s 1
rtcwake: wakeup from "standby" using /dev/rtc0 at Mon Nov 24 19:24:47 2008

```
It doesn't put my computer to sleep, but instead sets a wakeup time 5 hours and 1 second from now. I've tried it with different values, but it's always 5 hours off. I've tried the parameters -a, -l, and -u, but they don't change anything. Rodney9, is your rtcwake at least displaying a correct wakeup time?

---

### Post by Altay_H on 2008-11-24
After some further investigation, it turns out it's actually off by exactly 5 hours and 1 second, and it looks like there's nothing I can do about it. Here's an example to illustrate:
```

:~$ date
Mon Nov 24 14:44:50 EST 2008
:~$ date -d 14:50:00 +%s
1227556200
:~$ sudo rtcwake -t 1227556200
rtcwake: wakeup from "standby" using /dev/rtc0 at Mon Nov 24 19:50:01 2008

:~$ date -d 9:50:00 +%s
1227538200
:~$ sudo rtcwake -t 1227538200
rtcwake: time doesn't go backward to Mon Nov 24 14:50:00 2008

```
It's 14:44:50 and I want to set it to wake up at 14:50:00. When I set it to wake up at that time, it says it's set to wake up 5 hours and 1 second after that time. If I attempt to set it back 5 hours to correct the discrepency, it says it can't go backward in time. Maybe it's just the output that's incorrect and it would actually wake my computer up correctly if I suspended it. I'll give that a try just in case.

---

### Post by frigaut on 2008-11-27
it's because the time it prints out is UTC.
I did exactly the same on my machine (with -s 100), and it printed out a time 3 hours and 100 seconds from now. But the thing went to sleep and woke up 100 seconds later.
what I found:

1) I understand you want to test quickly, but I wouldn't use too low a number of seconds. the machine will take some time to go to sleep, so I wouldn't use -s X with X<30 or so...

2) use -m mem  (mem mode, see rtcwake manpage). This should put your conputer to sleep

3) so I used
sudo rtcwake -u -s 200 -m mem
and it did put my machine to sleep (took 6 to 8 seconds or so) and it *did* wake it up after 200 seconds, but the problem is that it killed my gnome session. When I came back, I was presented with a loggin screen. But it did not just reboot. My uptime is still over one day (which is the last time I rebooted, yesterday).

hope it helps.

---

### Post by frigaut on 2008-11-27
Success!

ok, I got it to work.
I tried again with -m mem and watched what was happening during wakeup. he issue seems to be with the framebuffer that's all messed up after the resume. Hence another X session is started and gnome restart a gdm (login screen).
This is actually mentionned in the manpage of rtcwake
> NOTES
       Some  PC  systems  can’t  currently exit sleep states such as mem using
       only the kernel code accessed by this  driver.   They  need  help  from
       userspace code to make the framebuffer work again.

So I tried with "-m disk", which also resumed but gave me the same framebuffer issue.

Finally, I tried "-m on", 

sudo rtcwake -u -s 120 -m on

which means, "do not suspend" and did the regular suspend-through-the-gnome-menu. And it worked! The computer woke up at the exact requested time (from the time it got the rtcwake command, not of course from the time I suspended, so give it enough time otherwise the wake up is supposed to occur *before* you suspend), with all my session still on, as if I had open the lid or pressed the wakeup button.

Thanks to attract my attention to rtcwake. I was also looking for something similar for a while.

---

### Post by frigaut on 2008-11-27
I just wrote this script that works like a charm (of course, your mileage may vary, e.g. your BIOS settings might not allow rtc wake, or pm-suspend might need quirks):

```
#!/bin/sh
# alarmtest script
# example:
# alarmtest "Nov 28, 2008 00:16:00"
# will wake up the computer from suspend or hibernate
# and execute a task (here, play a mp3)
t=`date --date "$1" +%s`
# to get sudo hand before the executing the 
#   rtcwake in background:
sudo /bin/true
sudo rtcwake -u -t $t -m on &
# give rtcwake some time to make its stuff:
sleep 2
# then suspend
sudo pm-suspend
# when it wakes up, it will pick up from here
vlc ~/pop.mp3

```

---

### Post by frigaut on 2008-12-01
Suspend and rtcwake in ibex (at least on my machine) seem to be exceptionally stable. I wrote a little script that automatically suspend and wakes up the machine (suspend for 30 seconds, then wake up and stay awake for 100 seconds, then suspend again, etc..). I let it run for the whole night and it went flawlessly through 129 cycles! I just stopped it the next morning as the demonstration was successful enough...
Talk of stability! Everything was still functional after these 129 cycles: network, all drivers, etc... Ubuntu has made great progress since I started using it a couple of years back. 
Thanks Canonical and developers!

---

### Post by MeisterLampe1 on 2008-12-03
Thanks for the script, frigaut, it's exactly what I was looking for. I think I found a minor bug, at least on my configuration: the -u switch overrides the system settings of the clock, so it is off by 2 hours: when I type

alarmtest "21:30"

it wakes at 19:30 (well I like to sleep long ;) removing the -u switch solves the problem..

---

### Post by frigaut on 2008-12-04
MeisterLampe1:
Yes. I believe this must be because you hardware clock is set to local (mine is set to UTC).
Glad to have been helpful.

---

### Post by Altay_H on 2008-12-11
Frigaut, thank you for your script. It works perfectly the first time I run it after rebooting. When I run the script, giving it a time to wake up it returns something like:

rtcwake: wakeup from "on" using /dev/rtc0 at Thu Dec 11 20:49:00 2008

However, if after resuming from suspend I attempt to run the script again, it returns:

/dev/rtc0: Device or resource busy

Then the script puts my computer to sleep, and it won't wake up automatically because the rtcwake failed.

Do you have any idea why /dev/rtc0 is busy after running the script the first time?

---

### Post by Altay_H on 2008-12-21
Bump.
It's been over a week.

Does no one know why I can only set 1 rtcwake per boot?
Am I the only one having this problem?

---

### Post by frigaut on 2008-12-23
Hi Altay_H,

I get what you describe when I wake up the computer before the rtcwake wakes it up itself.
Basically, you'll get the error you describe if rtc is still alive.
Just do a
ps auxc | grep rtcwake
if this list a rtcwake process, something is weird. You can however kill it with sudo kill -9 [your rtcwake process number]
and then you should be clear for another rtcwake call

---

### Post by Altay_H on 2008-12-24
> **frigaut said:**
> Just do a
ps auxc | grep rtcwake
if this list a rtcwake process, something is weird. You can however kill it with sudo kill -9 [your rtcwake process number]
and then you should be clear for another rtcwake call
For some reason, for me "something is weird" every time I use the script. I guess rtcwake doesn't clean up after itself on my computer for whatever reason. Thanks for letting me know how to kill it though. That's much easier than needing to reboot. I'll probably modify my version of the script to kill the rtcwake process number when I figure out how.


After messing around a bit I wrote a script that works. It's probably not the cleanest solution, but the script works. I'll post it below in case anyone is curious/interested.
```

#!/bin/bash

# Set var equal to the process information of rtcwake
var=`ps auxc | grep rtcwake`;

# Extract the second term from var
n=0;
for i in $var;
	do	
		if [ $n -eq 1 ]
			then	pid=$i;
		fi
	n=$(($n + 1 ));
done

# Kill the process with the given number
sudo kill -9 $pid;

```


Lol, I just realized I could use:
```

sudo killall rtcwake

```
instead of the complicated script I have above. Is there any difference at all between what killall and kill -9 do?


I figured out the difference between killall and kill -9. Killall tells the program to close itself, whereas kill -9 simply terminates the program without giving it a chance to do whatever it wants to do. Since killall and kill -9 both work in my case, I guess it doesn't make any difference.

---

### Post by blntechie on 2008-12-28
> **frigaut said:**
> 

```
#!/bin/sh
# alarmtest script
# example:
# alarmtest "Nov 28, 2008 00:16:00"
# will wake up the computer from suspend or hibernate
# and execute a task (here, play a mp3)
t=`date --date "$1" +%s`
# to get sudo hand before the executing the 
#   rtcwake in background:
sudo /bin/true
sudo rtcwake -u -t $t -m on &
# give rtcwake some time to make its stuff:
sleep 2
# then suspend
sudo pm-suspend
# when it wakes up, it will pick up from here
vlc ~/pop.mp3

```

I love it frigaut. Great.Thanks.
I want exactly this. I have not tried it yet. Hope this works or anyway it will make me understand the working in ubuntu better even if it does not work.

---

### Post by parvata on 2009-01-05
Hi,

Your solution to kill the rtcwake process resolved the same problem (device or resource busy error on subsequent calls to rtcwake) that I was having too. Thanks for the solution.

---

### Post by RedgeOnline on 2009-08-28
> **Altay_H said:**
> 
```

#!/bin/bash

# Set var equal to the process information of rtcwake
var=`ps auxc | grep rtcwake`;

# Extract the second term from var
n=0;
for i in $var;
	do	
		if [ $n -eq 1 ]
			then	pid=$i;
		fi
	n=$(($n + 1 ));
done

# Kill the process with the given number
sudo kill -9 $pid;

```



Absolute times don't seem to work for me: might be timezone related. Anyway: I created a script that uses relative timing. Called like: suspend_for 1 hour 30 minutes

```
#!/bin/sh

# Auto suspend and wake-up script

# Puts the computer on standby and automatically wakes it up after specified period

# How to use: download this script and place it on you computer.
# Call the script like this:
# suspend_for 1
# suspend_for 1 hour
# suspend_for 2 hours
# suspend_for 1 minute
# suspend_for 60 minutes
# suspend_for 1 hour 30 minutes
# suspend_for 2 hours 1 minute

# Original version courtesy of http://ubuntuforums.org/member.php?u=130449
# from thread http://ubuntuforums.org/showthread.php?t=938533&page=2
# Edited by Romke van der Meulen <redge.online@gmail.com>

# ------------------------------------------------------
# Argument check
MINARGS=1
MAXARGS=4
E_BADARGS=65

if [ $# -lt "$MINARGS" ] || [ $# -gt "$MAXARGS" ]; then
  echo "Usage: `basename $0` [[number] hours/h] [[number] minutes/m]"
  echo "E.G.: `basename $0` 2 hours"
  echo "E.G.: `basename $0` 30 minutes"
  echo "E.G.: `basename $0` 2 hours 30 minutes"
  echo "E.G.: `basename $0` 2 h 30 m"
  exit $E_BADARGS
fi
# ------------------------------------------------------

# Get root
sudo /bin/true

# Determine sleep interval
hours=0
minutes=0
multiply=0
total=0

# Check for first argument set, default hours
multiply=3600
if [ $# -gt 1 ]; then
	if [ "$2" = "minutes" ] || [ "$2" = "minute" ] || [ "$2" = "m" ]; then
		multiply=60
		minutes=$1
	else
		multiply=3600	
		hours=$1
	fi
fi

# Add time from first argument set
total=`expr $1 \* $multiply`

# Check for second argument set, default minutes
multiply=0
if [ $# -gt 2 ]; then	
	if [ "$4" = "hours" ] || [ "$4" = "hour" ] || [ "$4" = "h" ]; then
		multiply=3600
		hours=`expr $3 + $hours`
	else
		multiply=60	
		minutes=`expr $3 + $minutes`
	fi
	
	# Add time from second argument set
	total=`echo "$total + ($3 * $multiply)" | bc`
fi

# Let user know what we're going to do
echo "Going to suspend for $hours hours $minutes minutes ($total seconds)"
echo "To cancel, press Ctrl+c within the next 5 seconds."
sleep 5

# Set wake up time,
sudo rtcwake -u -s $total -m on &

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend

# Wake up with monitor disabled
xset dpms force off

# and console cleared
clear

# Any commands you want to launch after resume
# can be placed here
# Remember: sudo may have expired by now
echo "Good morning!"

```

\EDIT: I updated the script so that it can handle both hours and minutes.
\EDIT: Put down the latest version of the script while I'm here again

---

### Post by sindhu_sundar on 2009-09-21
> **frigaut said:**
> Success!

ok, I got it to work.
I tried again with -m mem and watched what was happening during wakeup. he issue seems to be with the framebuffer that's all messed up after the resume. Hence another X session is started and gnome restart a gdm (login screen).
This is actually mentionned in the manpage of rtcwake


So I tried with "-m disk", which also resumed but gave me the same framebuffer issue.

Finally, I tried "-m on", 

sudo rtcwake -u -s 120 -m on

which means, "do not suspend" and did the regular suspend-through-the-gnome-menu. And it worked! The computer woke up at the exact requested time (from the time it got the rtcwake command, not of course from the time I suspended, so give it enough time otherwise the wake up is supposed to occur *before* you suspend), with all my session still on, as if I had open the lid or pressed the wakeup button.

This worked for me too! Thanks a lot for posting it here :D

I added this to my /etc/rc.local so my computer wakes up at 2 every morning and executes a few cronjobs 

but what happens at the next time the job is supposed to happen if I dont suspend the eee? ie am still using the computer?

also what happens if i shutdown my system?

---

### Post by sindhu_sundar on 2009-09-21
> **frigaut said:**
> MeisterLampe1:
Yes. I believe this must be because you hardware clock is set to local (mine is set to UTC).
Glad to have been helpful.

You can add "-a" switch to make it auto decided between UTC and local time.

"-a | --auto
              Reads the clock mode (whether the hardware clock is set to UTC or local time) from /etc/adjtime.  That’s  the
              location where the hwclock stores that information."

---

### Post by hostilejosh on 2010-01-04
these seem great scripts, being a bit of a n00b, how do i use them? just copy into a terminal and replace 0's next to```
hours=0
minutes=0
multiply=0
total=0

```

with numbers?

---

### Post by RedgeOnline on 2010-01-04
> **hostilejosh said:**
> these seem great scripts, being a bit of a n00b, how do i use them? just copy into a terminal and replace 0's next to```
hours=0
minutes=0
multiply=0
total=0

```

with numbers?

No, you can simply save the script as suspend_for (or something) and then call it like this:
# suspend_for 1
# suspend_for 1 hour
# suspend_for 2 hours
# suspend_for 1 minute
# suspend_for 60 minutes
# suspend_for 2 hours 30 minutes

Specially for n00bs let me present my 8 step plan:
 1 Copy the script from the original post
 2 Open an editor (gedit or something)
 3 Paste the code
 4 Save in your home directory as "suspend_for" (no quotes, no extention)
 5 Open a terminal
 6 excute this command (without the quotes): "~/suspend_for 1 hour 30 minutes" (replace numbers as needed)
 7 It will ask for your password
 8 Wait a few seconds, then your computer will suspend

Disclaimer: even if this doesn't work, it shouldn't mess up your computer. But if something goes wrong with your computer, though I'll be glad to help, don't hold me responsible.

---

### Post by markp1989 on 2010-01-18
> **frigaut said:**
> I just wrote this script that works like a charm (of course, your mileage may vary, e.g. your BIOS settings might not allow rtc wake, or pm-suspend might need quirks):

```
#!/bin/sh
# alarmtest script
# example:
# alarmtest "Nov 28, 2008 00:16:00"
# will wake up the computer from suspend or hibernate
# and execute a task (here, play a mp3)
t=`date --date "$1" +%s`
# to get sudo hand before the executing the 
#   rtcwake in background:
sudo /bin/true
sudo rtcwake -u -t $t -m on &
# give rtcwake some time to make its stuff:
sleep 2
# then suspend
sudo pm-suspend
# when it wakes up, it will pick up from here
vlc ~/pop.mp3

```

this is cool, does 1 feature i was looking for,

idealy i would like it to resume, run flexget to see if there are any new shows, if there are stay on till rtorrent finishes that torrent, if there are no new shows go back to sleep again.

---

### Post by Rodney9 on 2010-02-01
> **RedgeOnline said:**
> Absolute times don't seem to work for me: might be timezone related. Anyway: I created a script that uses relative timing. Called like: suspend_for 1 hour 30 minutes

```
#!/bin/sh

# Auto suspend and wake-up script

# Puts the computer on standby and automatically wakes it up after specified period

# How to use: download this script and place it on you computer.
# Call the script like this:
# suspend_for 1
# suspend_for 1 hour
# suspend_for 2 hours
# suspend_for 1 minute
# suspend_for 60 minutes
# suspend_for 1 hour 30 minutes
# suspend_for 2 hours 1 minute

# Original version courtesy of http://ubuntuforums.org/member.php?u=130449
# from thread http://ubuntuforums.org/showthread.php?t=938533&page=2
# Edited by Romke van der Meulen <redge.online@gmail.com>

# ------------------------------------------------------
# Argument check
MINARGS=1
MAXARGS=4
E_BADARGS=65

if [ $# -lt "$MINARGS" ] || [ $# -gt "$MAXARGS" ]; then
  echo "Usage: `basename $0` [[number] hours/h] [[number] minutes/m]"
  echo "E.G.: `basename $0` 2 hours"
  echo "E.G.: `basename $0` 30 minutes"
  echo "E.G.: `basename $0` 2 hours 30 minutes"
  echo "E.G.: `basename $0` 2 h 30 m"
  exit $E_BADARGS
fi
# ------------------------------------------------------

# Get root
sudo /bin/true

# Determine sleep interval
hours=0
minutes=0
multiply=0
total=0

# Check for first argument set, default hours
multiply=3600
if [ $# -gt 1 ]; then
	if [ "$2" = "minutes" ] || [ "$2" = "minute" ] || [ "$2" = "m" ]; then
		multiply=60
		minutes=$1
	else
		multiply=3600	
		hours=$1
	fi
fi

# Add time from first argument set
total=`expr $1 \* $multiply`

# Check for second argument set, default minutes
multiply=0
if [ $# -gt 2 ]; then	
	if [ "$4" = "hours" ] || [ "$4" = "hour" ] || [ "$4" = "h" ]; then
		multiply=3600
		hours=`expr $3 + $hours`
	else
		multiply=60	
		minutes=`expr $3 + $minutes`
	fi
	
	# Add time from second argument set
	total=`echo "$total + ($3 * $multiply)" | bc`
fi

# Let user know what we're going to do
echo "Going to suspend for $hours hours $minutes minutes ($total seconds)"
echo "To cancel, press Ctrl+c within the next 5 seconds."
sleep 5

# Set wake up time,
sudo rtcwake -u -s $total -m on &

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend

# Wake up with monitor disabled
xset dpms force off

# and console cleared
clear

# Any commands you want to launch after resume
# can be placed here
# Remember: sudo may have expired by now
echo "Good morning!"

```

\EDIT: I updated the script so that it can handle both hours and minutes.
\EDIT: Put down the latest version of the script while I'm here again

Thank You, this is great ! works well.

---

### Post by Rodney9 on 2010-02-22
I try this in Mint 8 64bit and I always get incorrect times like these copied examples -

> $ ~/suspend_for 7 hour 39 minute

Going to suspend for 7 hours 74 minutes (27540 seconds)

> $ ~/suspend_for 1 minute

Going to suspend for 7 hours 1 minutes (60 seconds)


> $ ~/suspend_for 7 hour
Going to suspend for 7 hours 35 minutes (25200 seconds)


What is going wrong ?

---

### Post by RedgeOnline on 2010-03-01
> **Rodney9 said:**
> I try this in Mint 8 64bit and I always get incorrect times like these copied examples -


What is going wrong ?

Did you copy the entire script correctly?

---

### Post by Rodney9 on 2010-03-01
> **RedgeOnline said:**
> Did you copy the entire script correctly?

I'm sorry I should have responded before now , you are correct , I did not copy it correctly.

It is now working perfectly.

---

### Post by layr on 2011-05-29
Nice script! Though it would be nice if someone knew how to upgrade the script so the wakeup time could be entered also as time, eg. 'suspend_until 14:45'.
(no dates, just plain 24-h computer clock (not UTC))

PS i'd recommend changing line
```
if [ "$2" = "minutes" ] || [ "$2" = "minute" ] || [ "$2" = "m" ]; then
```
to
```
if [ "$2" = "minutes" ] || [ "$2" = "minute" ] || [ "$2" = "m" ]** || [ "$2" = "min" ]**; then
```
otherwise 'min' value might get defined as hour.

PS2 Why is the rtcwake kept loaded in memory after wakeup so it has to be killed every time?

---

### Post by RedgeOnline on 2011-05-29
> **layr said:**
> Nice script! Though it would be nice if someone knew how to upgrade the script so the wakeup time could be entered also as time, eg. 'suspend_until 14:45'.
(no dates, just plain 24-h computer clock (not UTC))


Your wish is my command. Does this work?

```

#!/bin/bash

# Auto suspend and wake-up script
#
# Puts the computer on standby and automatically wakes it up at specified time
#
# Written by Romke van der Meulen <redge.online@gmail.com>
#
# Takes a 24hour time HH:MM as its argument
# Example:
# suspend_untill 9:30
# suspend_untill 18:45

# ------------------------------------------------------
# Argument check
if [ $# -lt 1 ]; then
	echo "Usage: suspend_untill HH:MM"
fi

# Check whether specified time today or tomorrow
DESIRED=$((`date +%s -d "$1"`))
NOW=$((`date +%s`))
if [ $DESIRED -lt $NOW ]; then
	DESIRED=$((`date +%s -d "$1"` + 24*60*60))
fi

# Kill rtcwake if already running
sudo killall rtcwake

# Set RTC wakeup time
sudo rtcwake -l -m on -t $DESIRED &

# feedback
echo "Suspending..."

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend

# Any commands you want to launch after wakeup can be placed here
# Remember: sudo may have expired by now

# Wake up with monitor disabled
xset dpms force off

# and a fresh console
clear
echo "Good morning!"

```

> **layr said:**
> 
PS2 Why is the rtcwake kept loaded in memory after wakeup so it has to be killed every time?


I have no idea. Annoying, isn't it?

---

### Post by layr on 2011-05-29
Thanks a lot RedgeOnline! Works like a charm (Y)
PS i hope you won't mind if i share this script in Estonian linux forum. Many could use this awesome script :)

---

### Post by RedgeOnline on 2011-05-31
> **layr said:**
> Thanks a lot RedgeOnline! Works like a charm (Y)
PS i hope you won't mind if i share this script in Estonian linux forum. Many could use this awesome script :)

Go right ahead.

---

### Post by layr on 2011-06-01
Added the 'going to suspend for X' line again + few alsa-mixer lines, to make sure volume is up and unmuted (learned the hard way :P)
PS your system might have different alsamixer configuration (for instance the '0' in the amixer line is my sound card, your's might be different).


```
#!/bin/bash

# Auto suspend and wake-up script
#
# Puts the computer on standby and automatically wakes it up at specified time
#
# Written by Romke van der Meulen <redge.online@gmail.com>
#
# Takes a 24hour time HH:MM as its argument
# Example:
# suspend_until 9:30
# suspend_until 18:45
# suspend_until 0325
# suspend_until 515

# (just drag the scriptfile into terminal window and add time to the line)

# ------------------------------------------------------
# Argument check
if [ $# -lt 1 ]; then
	echo "Usage: suspend_until HH:MM"
fi

# Check whether specified time today or tomorrow
DESIRED=$((`date +%s -d "$1"`))
NOW=$((`date +%s`))
if [ $DESIRED -lt $NOW ]; then
	DESIRED=$((`date +%s -d "$1"` + 24*60*60))
fi


# Define hours/mins/sec to wake-up (for printing purposes only):
hours=$(((DESIRED-NOW)/3600))
minutes=$((  ((DESIRED-NOW)-(hours*3600))/60  ))
seconds=$(( ((DESIRED-NOW)-((hours*3600)+(minutes*60)))  ))

# Kill rtcwake if already running
sudo killall rtcwake

# Let user know what we're going to do
echo "Going to suspend for $hours h $minutes min"

echo "To cancel, press Ctrl+c within the next 10 seconds."
sleep 10

# Set RTC wakeup time
sudo rtcwake -l -m on -t $DESIRED &

# feedback
echo "Suspending..."

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend
# -------------------------------------------------------------------------------------
# Any commands you want to launch after wakeup can be placed here
# Remember: sudo may have expired by now

# Wake up with monitor disabled
# xset dpms force off

# Set volume level and (just in case) unmute system
amixer -c 0 set Master 80% unmute
amixer -c 0 set PCM 70% unmute

# echo "Good morning"

# Open VLC (vlc + path to your audio/video file)
vlc '/home/USER/Music/audiofile.mp3'

# Unload rtcwake if it's running, otherwise next time computer won't wake up from sleep
SERVICE='rtcwake'
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE running, killing process..."
    sudo killall rtcwake
else
    echo "$SERVICE is not running, no action taken."
fi
```
Makes a damn good alarm-clock :)

---

### Post by Rebelli0us on 2011-06-01
Linux has the equivalent of Windows' "Task Scheduler" (I forget what they call it), which may also have the ability to "wake up computer to run a task". In windows it runs the named task at the time set and then goes back to S3 suspend. If you figure out how it works in Linux I'd like to know as well.

---

### Post by IlbiStarz on 2011-07-05
For some reason it isn't working for me. When I do:

sudo rtcwake -m disk -s 60

It says it'll wake in 60 seconds but it doesn't, my computer stays off. I  have to actually boot it up again and then it wakes up from the  hibernation. Any help?

---

### Post by layr on 2011-09-24
Update (as of 27.03.12)
Another usage option added, as described in the script. Improved argument check.
Added the ability to postpone alert.

Note you have to edit optional pre-suspend and post-suspend commands; I left mine for example purposes.
```
#!/bin/bash

# Auto suspend and wake-up script. It's intended to act as an alarm-clock.
#
# Puts the computer on standby (after pre-defined time) and automatically wakes it up and executes commands at specified time or
# executes commands after given sleep period.
#
# Written by Romke van der Meulen <redge.online at gmail>
# Edited by Laur Aliste <laur.aliste at gmail>
#
# -----------------------------------------------------
# If you want the script to work without typing any passwords, you have to edit sudoers file:
# sudo visudo
# go to the last line and enter this line (without the '# ' at the beginning!) and save:
# username    ALL=NOPASSWD: /usr/sbin/rtcwake
#
# !!! This step is only needed if you're going to use (long) pre-suspend sleep periods; if so, sudo might 
# expire before 'sudo rtcwake' command is executed and system won't suspend !!!
# -----------------------------------------------------
##### USAGE #####
#
# 3 usage methods:
#    1. Suspending to RAM:
#        Example: suspend_script 930 15        - suspends system after 15 min and wakes up at  9:30
#             suspend_script 1845 10        - suspends system after 10 min and wakes up at 18:45
#             suspend_script 0325 2        - suspends system after  2 min and wakes up at 03:25
#             suspend_script 515        - If the second argument (pre-suspend sleep time) is missing as it is in this example,
#                               the default value is 10 sec, so the system suspends after 10 sec
#                                and wakes up at 05:15
#    2. Sleeping until predefined time:
#        Example: suspend_script 930 sleep    - executes pre-defined commands at 9:30
#
#    3. Sleeping for given time:
#        Example: suspend_script sleep 31    - executes pre-defined commands after sleeping for 31 minutes
#             suspend_script sleep        - If the second argument (sleep time) is missing as it is in this example,
#                               the default value is 10 min, so the system executes pre-defined commands
#                                after sleeping for 10 minutes
#
#
# - You can place this file (suspend_script) into /usr/local/bin. When you want to use the script, open terminal
# and type "suspend_script TIMEVALUE SLEEPVALUE" or 
# - simply drag the scriptfile (located anywhere) into terminal window and add those two values to the end of command line.
#
# Don't forget to make this file executable!
# ------------------------------------------------------
# Default values; do not change:
standalone_sleep=0
suspend=1
# Argument check:
if [[ $# > 2 ]]; then
    echo "==============================================================================="
    echo "      Error: too many arguments;"
    echo "      only wake-up time and/or sleep arguments are accepted"
    echo "==============================================================================="; exit 1
fi
if [[ $# < 1 ]]; then
    echo "====================================================="
    echo "      Wake-up time (HHMM) or \"sleep\" needed"
    echo "====================================================="; exit 1
fi
if [[ "$1" == "sleep" ]] ; then
    standalone_sleep=1
    suspend=0
    if ! [[ -z $2 ]]; then
        if ! [[ "$2" =~ ^[0-9]+$ ]] ; then
        echo "========================================================================="
         echo "      Error: sleep value (MM) has to be numerical."
        echo "             eg. 10; 200; 5"
        echo "========================================================================="; exit 1
        fi
    fi
elif ! [[ "$1" =~ ^[0-9]+$ ]]; then
     echo "=============================================================="
    echo "    Error: first argument has to be either numerical (HHMM)"
    echo "           eg. 1000; 900; 1830;  or \"sleep\""
    echo "=============================================================="; exit 1
elif ! [[ -z $2 ]]; then
    if [[ "$2" == "sleep" ]] ; then
        suspend=0
    elif ! [[ "$2" =~ ^[0-9]+$ ]] ; then
        echo "========================================================================="
         echo "      Error: second argument has to be either numerical (MM)"
        echo "             eg. 10; 200; 5;  or \"sleep\""
        echo "========================================================================="; exit 1
    fi
fi

# Check whether specified time is today or tomorrow and define suspend period:
if [[ $standalone_sleep == 0 ]]; then
    TARGET1=$((`date +%s -d "$1"`))
    NOW=$((`date +%s`))
    if [ $TARGET1 -lt $NOW ]; then
        TARGET1=$((`date +%s -d "$1"` + 24*60*60))
    fi
    TARGET=$(($TARGET1-$NOW))
fi
# Define hours/mins/sec until wake-up:
hours=$(($TARGET/3600))
minutes=$((  ($TARGET-($hours*3600))/60  ))
seconds=$(( $TARGET-(($hours*3600)+($minutes*60))  ))

# Check whether entered wake-up time makes any sense:
if [[ "$1" =~ ^[0-9]+$ ]] ; then
    if (( $hours < 0 )); then
        echo "======================================================"
        echo "       Error: please re-check the wake-up time"
        echo "======================================================"; exit 1
    fi
fi

# Decide whether to sleep or suspend; define pre-suspend sleep durance if necessary:
if [[ $suspend == 1 ]]; then
                #-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
#-------------------------------#-#             SUSPEND SCRIPT              #-#--------------------------------#
                #-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
    killall rtcwake > /dev/null 2>&1
    if [[ $2 > 0 ]];then
    sleep_value=$(( $2*60 ))
    else
    sleep_value=10
    fi

    # Print countdown feedback:
    while [ $sleep_value -gt 0 ]; do
        clear
        # Let user know what we're going to do
        echo "Going to suspend for $hours h $minutes min"
        let sleep_value=$sleep_value-1  
        hours2=$(( $sleep_value/3600 ))
        minutes2=$((  ($sleep_value-$hours2*3600)/60  ))
        seconds2=$(( $sleep_value-($hours2*3600+$minutes2*60)  ))
        echo "----------------------------------------------------------" 
        if [[ $hours2 > 0 ]] ;then
            echo "To cancel, press Ctrl+c within the next $hours2 h $minutes2 min $seconds2 sec"
        elif [[ $minutes2 > 0 ]] ;then
            echo "To cancel, press Ctrl+c within the next $minutes2 min $seconds2 sec"
        else
            echo "To cancel, press Ctrl+c within the next $seconds2 sec"
        fi
        sleep 1 
    done

    #################################################################################################
    #################################################################################################
    # Between these double octothorpe (#) lines go optional commands
    # which are to be executed BEFORE suspension:
    #------------------------------------------------------------------------------------------------
    # Kill conky:
    #pkill -9 -f conky > /dev/null 2>&1

    #################################################################################################
    #################################################################################################

    # Feedback again:
    echo "Suspending..."
    sleep 1
    # Set RTC wakeup time and suspend to RAM:
    sudo rtcwake -m mem -s $TARGET
    # Buffer time...
    sleep 2
    #################################################################################################
    #################################################################################################
    # Between these double octothorpe (#) lines go optional commands
    # which are to be executed AFTER suspension:
    #------------------------------------------------------------------------------------------------
    # Wake up with monitor disabled:
    # xset dpms force off

    # Clear the terminal window:
    clear

    # Set volume level and (just in case) unmute system:
    amixer -c 0 set Master 80% unmute > /dev/null 2>&1
    amixer -c 0 set PCM 80% unmute > /dev/null 2>&1

    # Start conky:
    #conky -c /home/laur/.conkyrc > /dev/null 2>&1
    #conky -c /home/laur/.conkyrc_banshee > /dev/null 2>&1

    echo "
    Good morning

    "

    # Start ncmpcpp:
    ncmpcpp play > /dev/null 2>&1
    # Postpone? :
    echo -n "Want to sleep some more? (y/n) "
    read postpone
    if [[ "$postpone" == "y" ]]; then
        while [[ "$postpone" == "y" ]]; do
            ncmpcpp pause > /dev/null 2>&1
            echo -n "Enter time in minutes (leave blank for 10min): "
            read sleep_value
            if ! [[ -z $sleep_value ]]; then
                if ! [[ "$sleep_value" =~ ^[0-9]+$ ]] ; then
                    echo "========================================================================="
                     echo "      Error: sleep time (MM) has to be numerical."
                    echo "             eg. 10; 20; 5"
                    echo "========================================================================="; exit 1
                fi
            fi
            if [[ $sleep_value > 0 ]];then
                sleep_value=$(( $sleep_value*60 ))
            else
                sleep_value=600
            fi
            # Define hours/mins/sec until wake-up:
            hours=$(( $sleep_value/3600 ))
            minutes=$((  ($sleep_value-$hours*3600)/60  ))
            seconds=$(( $sleep_value-($hours*3600+$minutes*60)  ))
            while [ $sleep_value -gt 0 ]; do
                clear
                # Let user know what we're going to do
                if [[ $hours > 0 ]] ;then
                    echo "Going to sleep for $hours h $minutes min"
                else
                    echo "Going to sleep for $minutes min"
                fi
                let sleep_value=$sleep_value-1  
            hours2=$(( $sleep_value/3600 ))
            minutes2=$((  ($sleep_value-$hours2*3600)/60  ))
            seconds2=$(( $sleep_value-($hours2*3600+$minutes2*60)  ))
                echo "----------------------------------------------------------" 
                if [[ $hours2 > 0 ]] ;then
                    echo "Waking up in... $hours2 h $minutes2 min $seconds2 sec"
                elif [[ $minutes2 > 0 ]] ;then
                    echo "Waking up in... $minutes2 min $seconds2 sec"
                else
                    echo "Waking up in... $seconds2 sec"
                fi
                sleep 1 
            done
            amixer -c 0 set Master 80% unmute > /dev/null 2>&1
            amixer -c 0 set PCM 80% unmute > /dev/null 2>&1
            ncmpcpp play > /dev/null 2>&1
            echo -n "Want to sleep some more? (y/n) "
            read postpone
        done
    fi
    #################################################################################################
    #################################################################################################

    # Unload rtcwake if it's running, otherwise next time computer won't wake up from sleep:
    killall rtcwake > /dev/null 2>&1
    exit 1
fi


                #-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
#-------------------------------#-#              SLEEP SCRIPT               #-#--------------------------------#
                #-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#

    #################################################################################################
    #################################################################################################
    # Between these double octothorpe (#) lines go optional commands
    # which are to be executed BEFORE system sleep:
    #------------------------------------------------------------------------------------------------


    #################################################################################################
    #################################################################################################
if [[ "$standalone_sleep" == "1" ]]; then

    if [[ $2 > 0 ]];then
    sleep_value=$(( $2*60 ))
    else
    sleep_value=600
    fi

    # Define hours/mins/sec until wake-up:
    hours=$(( $sleep_value/3600 ))
    minutes=$((  ($sleep_value-$hours*3600)/60  ))
    seconds=$(( $sleep_value-($hours*3600+$minutes*60)  ))
    while [ $sleep_value -gt 0 ]; do
        clear
        # Let user know what we're going to do
        if [[ $hours > 0 ]] ;then
            echo "Going to sleep for $hours h $minutes min"
        else
            echo "Going to sleep for $minutes min"
        fi
        let sleep_value=$sleep_value-1  
    hours2=$(( $sleep_value/3600 ))
    minutes2=$((  ($sleep_value-$hours2*3600)/60  ))
    seconds2=$(( $sleep_value-($hours2*3600+$minutes2*60)  ))
        echo "----------------------------------------------------------" 
        if [[ $hours2 > 0 ]] ;then
            echo "Waking up in... $hours2 h $minutes2 min $seconds2 sec"
        elif [[ $minutes2 > 0 ]] ;then
            echo "Waking up in... $minutes2 min $seconds2 sec"
        else
            echo "Waking up in... $seconds2 sec"
        fi
        sleep 1 
    done
else
    sleep_value=$TARGET
    while [ $sleep_value -gt 0 ]; do
        clear
        # Let user know what we're going to do
        if [[ $hours > 0 ]] ;then
            echo "Going to sleep for $hours h $minutes min $seconds s"
        elif [[ $minutes > 0 ]] ;then
            echo "Going to sleep for $minutes min $seconds s"
        else
            echo "Going to sleep for $seconds s"
        fi
        let sleep_value=$sleep_value-1  
    hours2=$(( $sleep_value/3600 ))
    minutes2=$((  ($sleep_value-$hours2*3600)/60  ))
    seconds2=$(( $sleep_value-($hours2*3600+$minutes2*60)  ))
        echo "----------------------------------------------------------" 
        if [[ $hours2 > 0 ]] ;then
            echo "Waking up in... $hours2 h $minutes2 min $seconds2 sec"
        elif [[ $minutes2 > 0 ]] ;then
            echo "Waking up in... $minutes2 min $seconds2 sec"
        else
            echo "Waking up in... $seconds2 sec"
        fi
        sleep 1 
    done
fi

    #################################################################################################
    #################################################################################################
    # Between these double octothorpe (#) lines go optional commands
    # which are to be executed AFTER system sleep:
    #------------------------------------------------------------------------------------------------
    clear

    # Set volume level and (just in case) unmute system:
    amixer -c 0 set Master 80% unmute > /dev/null 2>&1
    amixer -c 0 set PCM 80% unmute > /dev/null 2>&1

    # Start conky:
    #conky -c /home/laur/.conkyrc > /dev/null 2>&1
    #conky -c /home/laur/.conkyrc_banshee > /dev/null 2>&1

    echo "
    Wakey-wakey


    "

    #Start ncmpcpp:
    ncmpcpp play > /dev/null 2>&1
    # Postpone? :
    echo -n "Want to sleep some more? (y/n) "
    read postpone
    if [[ "$postpone" == "y" ]]; then
        while [[ "$postpone" == "y" ]]; do
            ncmpcpp pause > /dev/null 2>&1
            echo -n "Enter time in minutes (leave blank for 10min): "
            read sleep_value
            if ! [[ -z $sleep_value ]]; then
                if ! [[ "$sleep_value" =~ ^[0-9]+$ ]] ; then
                    echo "========================================================================="
                     echo "      Error: sleep time (MM) has to be numerical."
                    echo "             eg. 10; 20; 5"
                    echo "========================================================================="; exit 1
                fi
            fi
            if [[ $sleep_value > 0 ]];then
                sleep_value=$(( $sleep_value*60 ))
            else
                sleep_value=600
            fi
            # Define hours/mins/sec until wake-up:
            hours=$(( $sleep_value/3600 ))
            minutes=$((  ($sleep_value-$hours*3600)/60  ))
            seconds=$(( $sleep_value-($hours*3600+$minutes*60)  ))
            while [ $sleep_value -gt 0 ]; do
                clear
                # Let user know what we're going to do
                if [[ $hours > 0 ]] ;then
                    echo "Going to sleep for $hours h $minutes min"
                else
                    echo "Going to sleep for $minutes min"
                fi
                let sleep_value=$sleep_value-1  
            hours2=$(( $sleep_value/3600 ))
            minutes2=$((  ($sleep_value-$hours2*3600)/60  ))
            seconds2=$(( $sleep_value-($hours2*3600+$minutes2*60)  ))
                echo "----------------------------------------------------------" 
                if [[ $hours2 > 0 ]] ;then
                    echo "Waking up in... $hours2 h $minutes2 min $seconds2 sec"
                elif [[ $minutes2 > 0 ]] ;then
                    echo "Waking up in... $minutes2 min $seconds2 sec"
                else
                    echo "Waking up in... $seconds2 sec"
                fi
                sleep 1 
            done
            amixer -c 0 set Master 80% unmute > /dev/null 2>&1
            amixer -c 0 set PCM 80% unmute > /dev/null 2>&1
            ncmpcpp play > /dev/null 2>&1
            echo -n "Want to sleep some more? (y/n) "
            read postpone
        done
    fi
    #################################################################################################
    #################################################################################################
exit 1
```

---

