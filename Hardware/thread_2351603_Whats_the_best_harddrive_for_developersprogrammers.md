---
title: "Whats the best harddrive for developers/programmers?"
date: 2017-02-05
forum: Hardware
---

### Post by horsebox2 on 2017-02-05
I have a Desktop PC with 12 Gb of RAM but the harddrive died on me. I got a new HP Envy laptop which was the biggest mistake I have ever made in buying computer related things. Its got this EUFI boot system which pretty much locks you into Windows 10, and as you probably know Windows is horrific for development (as well as security, CLI interaction, network administration, customisation and basically everything other than gaming and software availability). 

Its about time I get a new harddrive for the desktop PC. I was wondering what the best type of internal harddrive is for developers. Disk space isn't that important to me, 1Tb is more than enough, I can always use an external harddrive if I need more storage space. Looking into harddrives, I see there are 3 additional factors. For example, this drive:

```
[h=1][SIZE=3]WD Blue 3TB  Desktop Hard Disk Drive - 5400 RPM SATA 6 Gb/s 64MB Cache 3.5 Inch                                 [/SIZE][/h]
```

In addition to the 3TB storage space, it has:
[LIST]
[*] 5400 RPM (rotations per minute)
[*]6 Gb/s (I don't know what this means)
[*]64 MB Cache (not quite sure what this is either)
[/LIST]

To be honest, I don't know what any of it means. I'm guessing some of those contribute to read/write speed which is pretty important for development. Depending on the situation though I suppose. I do a lot of data scraping, and data manipulation jobs. I download large database dumps, run scripts through them to insert data and modify them, and various things like that. I do lots of database jobs with big data.

I'm not sure how important any of these things are for the average developer/programmer. Sometimes I'll work with huge CSV files and have to load lots of it into memory, so the speed at which I can read and write from data files like that is important. 

Which of these variables are important for development? What does RPM actually mean in terms of performance. Does harddrive cache affect your ability to deal with large data files? Like if I need to loop through an enormous 100,000 row CSV file, and write large chunks of data to it rapidly? I've got 8Gb RAM on this laptop but it doesn't seem to mean much as its always running out of memory and crashing, Windows eats up all the memory somehow. I see I could get a drive with 7200 RPM and 124 Mb cache, but would that really make a significant difference for development work?

---

### Post by QIII on 2017-02-05
Hello!

> and as you probably know Windows is horrific for development

I don't know about that.  It's great for developing Windows applications.  I make an obscene amount of money doing that.  (Just so you know, there are no brownie points given around here for dissing Windows.  As a matter of fact, it can get you into trouble.)

The disk is really of no consequence at all to your *development* - you could use a machine with an old IDE drive if you wanted to.  The disk you choose is more a matter of your budget.  Use that as your guide.  

For things to *work* quickly when you are finished with your development (that is operation, not development) or if you want to do performance testing of what you have done in an environment similar to your client's, the faster the better.

But for a desktop, if you go for an HDD:

7200 rpm
SATA Rev III (often referred to as SATA 3, SATA III or SATA 600)
64MB cache is pretty good.

> as its always running out of memory and crashing

It's the responsibility of the developer to make sure that doesn't happen!  ;)

---

### Post by horsebox2 on 2017-02-05
> **QIII said:**
> Hello!



I don't know about that.  It's great for developing Windows applications.  I make an obscene amount of money doing that.  (Just so you know, there are no brownie points given around here for dissing Windows.  As a matter of fact, it can get you into trouble.)
Yeah true, someone who uses Visual Basic, .NET, ASP, all that stuff will of course find Windows more useful. I don't use any of that, I'm experienced with bash scripting, PHP, perl and getting into python and django now, and have been through immense strife working around all the roadblocks with Windows. Its not Windows in itself I have a problem with. Its the fact that you have no option when you buy a new computer, they all come with Windows. That in itself isn't a big deal when you can install another OS on your machine (I usually dual boot or have at least a Windows VM), but I got a laptop with no CD drive which has a UEFI boot mechanism, and have spend days trying to get Ubuntu installed on a separate partition, I even managed to install it but can't boot into it. Thats what I have a problem with. Windows forcing users to use their commercial technology. It should be the other way around, computers should come with free open source operating systems, and paying for an expensive OS like Windows should be optional. I never had much of a problem with Windows until I got forced to use it as my primary OS.

Windows has some brilliant software so I always make sure I have access to Windows. Pycharm is amazing. And to be fair, Windows 10 is really a massive improvement to some of the older versions.

> **QIII said:**
> 
The disk is really of no consequence at all to your *development* - you could use a machine with an old IDE drive if you wanted to.  The disk you choose is more a matter of your budget.  Use that as your guide.  

For things to *work* quickly when you are finished with your development (that is operation, not development) or if you want to do performance testing of what you have done in an environment similar to your client's, the faster the better.

But for a desktop, if you go for an HDD:

7200 rpm
SATA Rev III (often referred to as SATA 3, SATA III or SATA 600)
64MB cache is pretty good.

Its more development I'm concerned with, testing and all that isn't an issue. I do huge data manipulation jobs on my local machine, but I'm not sure if the harddrive speed is an important factor for that, or whether thats mainly your computers RAM. With budget, there isn't a huge difference, an extra $20 can get you an extra 1Gb, or an extra 32MB cache. But still an extra $20 right now means the difference between whether I can afford it or not, so I'll go with your advice :) I think I'll go with those specs I listed, I'm just not sure which to put more emphasis on RPM or cache. Sometimes I have trouble with opening massive files, so if cache makes a difference to that, then thats pretty important. Thanks for the info, that gives me a better idea on what to do. I'm really looking forward to this, finally getting back to Ubuntu. 

> **QIII said:**
> 
It's the responsibility of the developer to make sure that doesn't happen!  ;)
My old laptop had 2Gb RAM and I didn't have this problem.


BTW what languages do you use for developing Windows software?

---

### Post by igdfpm on 2017-02-05
RPM is pretty irrelevant on modern hardware as it bares little relation to any kind of real-world speed boost - Would a 7200 rpm HDD transfer faster than a 5400 rpm equivalent? Yes but there would be nanoseconds difference... My only other vaguely useful comment would be that 7200 drives tend to go bang about 1800 rpm quicker than 5400 drives :P

Get the largest drive for the best price... not at lot more to say...

---

