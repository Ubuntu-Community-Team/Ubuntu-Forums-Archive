---
title: "How to Control Fan on Old Laptop by CPU Usage"
date: 2008-08-11
forum: Hardware
---

### Post by grungedoobie on 2008-08-11
Hello, and thanks in advance for any advice.

I have a Toshiba Tecra 8000 with: Pentium II 366MHz (motherboard max), 256MB Ram, NeoMagic Integrated Video with 2.5MB Aperture, 80GB HDD, 2x DVD / 4x-CD-RW / 20x-CD-Rom Optical Drive.

I'm running Xubuntu Hardy Heron installed via the x86 Alternate Live-CD on it without any problems. (other than heat)

Does anyone know a simple command that can grab the CPU usage output of the "top" command and apply it to a variable which can then be used to control the output of a fan control script?  Because this thing runs pretty hot.

Here is the script I am using now, but it is inefficient at best.

## Begin
sudo toshset -fan on
sleep 3m
sudo toshset -fan off
## End

I then put an entry in "sudo crontab -e" to run this script every five minutes.

This script works well if I am just texting, or doing simple tasks, however, it isn't enough for gaming or graphics.  Light gaming needs to be on 4 of 5 mins, and multitasking needs 5 of 5 mins.

So, I'm thinking up to 33% CPU should be 3 of 5, 33% to 66% should be 4 of 5, and above 66% should be 5 of 5.

Is there a way to make a script work something like this?

## Begin
Grab CPU percentage = P%
If P% < 33 then T = 3
If P% > 33 then T = 4
If P% > 66 then T = 5
sudo toshset -fan on
if T = 5 then end
sleep Tm
sudo toshset -fan off
## End

Can this be done?  Or am I just dreaming.

I only have about two years of Linux including six successful installs under my belt, so, yes, I'm still a nuber.

---

### Post by grungedoobie on 2008-08-12
I know that what I am doing with my laptop will be considered by most to be extremely dangerous.  However, in my mind I see that letting the laptop run without a proper fan control system in place is all the more dangerous.

I have twice now run the battery to below 25% while gaming with the fan on at 4.5 of 5 mins and it ran comfortably.  (side note: When the battery gets below 50% the laptop is hardwired to drop the CPU from 366MHz to 300MHz, so the gaming experience looses some of its lustre, but it still runs.)  I also ran a CPU Monitor while gaming and sure enough that thing is churning out 100%.

I do lose a little battery time, but from what I've noticed, it's negligible (not a big deal).  However I guaranty that the processor running at 100% is eating up a lot more juice than the fan is.

I guess what I'm trying to say is, I accept all forms of ideas, even scripting in C++.  Say, that's not a bad idea.  I'll look around and see if I can get C++ to dump the "top" command output to a log file.  Read the log and grab the section of that log containing CPU usage.  Then equate that to the on off time.

Ugh, this thing gets more and more complicated every second.  But hey, maybe it'll work.  I'll give it a go.

Sorry you had to watch me talk to myself,

The Grunge

---

### Post by grungedoobie on 2009-03-23
This thread can be closed.

The safest way that I could find was to edit the cron entry to set the fan speed to high every 5 minutes.

Perhaps one day I'll be able to do more, but for now, this will do.


The Grunge :)

---

