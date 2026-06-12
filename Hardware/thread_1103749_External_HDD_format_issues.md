---
title: "External HDD format issues"
date: 2009-03-23
forum: Hardware
---

### Post by therickster2 on 2009-03-23
Okay. So where to begin.

A couple months ago I purchased a Seagate free-agent desktop 1.5TB external Hard drive. It had some on and off issues with clicking and freezing up during file transfers, Which I surmised were overheating issues. So I went through various trials to see if that was the case. Indeed it was. Well one day about a week ago, I had the thing on my laptop's cooler pad. This had been a good method to keep it cool. So I'm transfering a file sized around 8 gigs, and it froze up. I tried to safely disconnect, but that wouldn't work. So I pulled the power cord out. This problem kept reoccuring over and over again, until my computer didn't even register that the drive was there any more.

Next after a few tests I figure out that the file system had corrupted and become RAW. So the obvious thing seemed to just format it. Well there's the problem. It won't format. I've tried going to disk manager and right clicking it in windows. Oh btw windows can see the drive, but this is vista, and in vista a bar shows up under a drive to tell you how much used/free space is on that drive. Well that bar isn't there with the Freeagent. So I've tried everything I could get my hands on in windows to format it. Doesn't work.

So I think, it's time to boot into Ubuntu and format it. So I go into Intrepid Ibex and run gparted. And it seems to be at least trying. Well after letting it try, it was obviously not getting anywhere, (I was trying to format it into fat32) I canceled the operation. Well now gparted doesn't even recognise the thing is there, but I can open the drive, where as earlier I could not. So inside the drive I see all these odd names like %.c and some symbols that look like a block with four binary numbers or letters in them.

Oh btw I opened the thing up and it has a seagate 1.5tb barracuda 3.5" sata hard drive in it. So I've ordered a sata cable and am going to try a direct connection and see if that allows for a format.

So besides that I'm at a loss as to what to do. Any suggestions? Or help? Or someone want to point out something noobish I've done?

---

