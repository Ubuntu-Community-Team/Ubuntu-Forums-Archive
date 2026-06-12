---
title: "could a dead battery cause this problem...?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by dninja on 2006-03-25
I've got a laptop which was dontated to me by a friend. He gave up on it as it was regularly freezing on him, sometimes requiring turning off for 10-15 mins afterwards before restarting. A local repair shop could find nothing wrong with it.

He was running XP so I guessed it was probably just some bad driver and the not startup up thing was just him doing something wrong but now I'm getting the same problems. It isn't an OS thing as it does it in FreeBSD, gentoo, ubuntu, XP and even on the memory test kernel!

It isn't overheating as it sometimes does it after being on only a few minutes, sometimes after being on all day.

On some crashes I've seen reports of harddrive read errors, usb controller failures, sometimes the screen (X or command line) becomes corrupt but the mouse continues to work for a minute or so. Nothing to point to any one physical point of hardware failure.

The only thing I've noticed is that it seems to have the problem if it has been left without power for a few days, not doing anything, just sitting. When started up again, with or without power, that is when it is most likely to crash.

A local laptop repair centre says that power isn't likely to have anything to do with it but I'm wondering if it is something to do with the battery. Maybe the power levels drop and even when running on mains, if it still puts the charge through the battery and a weak battery is causing the problems. As I haven't had it from new I don't know if the battery was initially charged as recommended by the manufacturer.

What do people think? Could a faulty battery cause these problems or should I be looking at something else? If not the battery, can anyone suggest a good hardware testing program, doesn't matter about OS, I can dual boot into linux, bsd and XP.

---

### Post by ranf on 2006-03-25
I'd remove the battery and run it from power for a while.
If it still behaves that weird then it is not the battery.

---

### Post by John.Michael.Kane on 2006-03-25
Have you tried running the machine off the ac only no batt in it? also if you can get ahold of a spare drive to test to see if it gives the same panics as it does with the drive in it. from your post it could many things however power might not be the problem.


Edit:ranf beat me to it. lol

---

### Post by evilc on 2006-03-25
I would also double check the cooling fans, you say it can't be overheating but it can if the cpu fan is not working.

If you find out it's the battery loosing power quick you can connect a bulb to it and drain the power 2 or 3 times and recharge. Rechargable batteries tend to 1/2 charge if not done properly.

---

### Post by dninja on 2006-03-25
Seeing as most of the time it is running on my desktop I can try it with the battery out. The big problem is that it is intermittent. It happened for a while when I first got it then cleared up, not long after a fresh OS install so I assumed that I'd fixed it but it is doing it again on a new fresh install. It has ran for the last 2 months without any problems and it has been running hard. I'm doing wireless security audits so it has been running at 100% cpu cracking WEP keys, that is why I don't think it is overheating or similar as I've had it running full on for hours on end with no problems.

evilc, the battery will run fine from freshly fully charged, gives at least 2-3 hours and I've never ran out of battery, it seems to be losing power when left sitting doing nothing with no mains for a day or two. You seem to know a bit about batteries, is this normal? What bulb should I use, does it have to match the battery voltage or can it be anything upto that voltage?

---

### Post by dninja on 2006-03-25
Isn't the battery, I removed it and it just locked up on me again running under just AC. Should have tried that first  :oops: 

The only other easily removeable part is the harddrive. I can try removing that and booting a live CD.

---

### Post by evilc on 2006-03-26
From what you are saying it sounds maybe like a faulty hard drive they can fail intermittently. There is a program you can get from memory I think it's called Burnin, if there is anything wrong with system it will find it. (Only problem it can destroy it as well).
For the battery majority of them are around 14.8 v so use a bulb about 6-9v and leave it on, this only helps drain the battery quicker (just like leaving a torch on):) 
Can you try running it without cover on then you can see the fans, I have seen them stop start. 
The little gremlins are the worst kind to find ](*,)

---

### Post by dninja on 2006-03-26
Is this the [burnin]("http://www.micro2000.co.uk/products/microscope/burnin.htm") that you meant?

I may try to get the lid off but don't fancy making anything worse by messing anything up.

---

### Post by evilc on 2006-03-26
Yes that's the one, I would only use it at a last resort though it can (and does) tend to destroy faulty components, as the name implies.
Maybe if all else fails try to locate the manufacturers and if they are local try their tech dept, most seem to be helpfull.

---

### Post by dninja on 2006-03-26
[QUOTE=evilc]Maybe if all else fails try to locate the manufacturers and if they are local try their tech dept, most seem to be helpfull.[/QUOTE]

It was made in the UK by a company called Tiny who went bust not long after it was bought :-(

---

### Post by evilc on 2006-03-26
Looks like the phrase "your up the creek without the paddle". I think from what you have said I would be inclined to get the hard drive manufacturers disc format/repair disc (have a look on HD cover) and do a complete surface scan and reformat. If you can't find name use a commercial software program most work but manuf. one's are better.
As I said before Burnin willdo the job but could kill your unit completly.

---

### Post by dninja on 2006-03-27
I was given the laptop for that very reason. It won't cost me anything if I can't get it to stay up and running but it is a shame, it is a fairly high end amd64!

I'll scan the drive first and take it from there.

Thanks

---

