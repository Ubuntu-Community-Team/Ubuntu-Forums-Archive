---
title: "smartctl monitoring - the basics."
date: 2018-01-29
forum: Hardware
---

### Post by david503 on 2018-01-29
Hello I'm running smartctl on four drives (one at a time haha), some simple questions:

How do I make it run in a way that I can see the progress on the command line? 

Also where are the logs saved for smartctl?  Should I just more them now and then?

These seem like easy questions to google for, but either they're not, or I'm just bad at finding them.  

(Oh and I can just simultaneously run it on other drives connected here and that doesn't conflict, right? Or will the logs be a conflated mess?)

thanks,

d

---

### Post by TheFu on 2018-01-29
I'm not an expert on SMART, but here's what I know.

There is the testing part and the reporting part.  For testing, I use "short" mode when I'm in a hurry and schedule "long" mode for weekly updates.  The reporting part just reads the information that the other testing modes write to the drive firmware.  Reporting is fast - just send the reports to text files via normal redirection.

I run the tests sequentially, but I suppose they could be run in parallel. It isn't been an issue.

---

### Post by david503 on 2018-01-29
> **TheFu said:**
> I'm not an expert on SMART, but here's what I know.

There is the testing part and the reporting part.  For testing, I use "short" mode when I'm in a hurry and schedule "long" mode for weekly updates.  The reporting part just reads the information that the other testing modes write to the drive firmware.  Reporting is fast - just send the reports to text files via normal redirection.

I run the tests sequentially, but I suppose they could be run in parallel. It isn't been an issue.


Yep as of writing my question I figured a lot out:

If you have partitions, like /dev/sda1 /dev/sda2, etc, you can run it on individual partitions, but that's lame right, I want to test the entire drive all at once, so what you can do is just run the tests on /dev/sda  (without specifying the 1's, see).  I had to figure that out;

smartctl -t long /dev/sda

And then it doesn't display anything while it's running but you know it is because you hear your drive crunching (if it's local to you and not a server.) 

And while it's running, and after, you can go

smartctl -a /dev/sda

After it's done, in there's you'll see "completed no errors" somewhere in the -a results.  Or you'll see it give up.  

I don't know where the logs are stored.  I'm running this in a knoppix live disc so I don't know if even stores them anywhere in knoppix.  

I don't think normal | redirection will work... 

In my case I ran it on two drives at the same time, it had no problem doing that.  It's more time efficient too!

And as I suspected, one drive test immediately stopped after 10 seconds and I ran the -a command on it and sure enough, the drive was broken, it detailed reported the errors. (I didn't care what they were, I was just like "yep!" that drive is toast.  I knew it would be, it had been flakey for months, that's why I figured this whold smart test stuff out.) 

Other good command to know-

To kill a test:  

smartctl -X /dev/sda

Basically that's all I know so far- I haven't gotten into making it a cron with smartd or whatever, but that's probably what I'll do in later days.

good luck,

d

---

### Post by TheFu on 2018-01-30
I'm positive that redirection works.

Sometimes, more options are necessary for devices connected with non-standard controllers like USB3, Marvell, etc.  SMART produces a bunch of data, but IME, only 3-4 elements are useful.  Some of those need to be watched over time for comparison.  If you can hear the HDDs, then I suspect you have a different issue (or only 1 disk).  I cannot hear the SMART tests running in my setup.  But there are 20+ disks spinning in the room already.

I'm used to scheduling things and prefer to have the computer do things so results are finished and waiting for me. I guess we all have different ways of working. ;)

---

### Post by david503 on 2018-01-30
Yea we might be talking about different things when it comes to redirection.  

In any case, I start it and have the lan server running next to me on my desk so I'm not, y'know, just sitting there for an hour while it runs.  

And yea, like I said above, I haven't gotten in to running sshd like ever week or whatever, but I plan to.

---

