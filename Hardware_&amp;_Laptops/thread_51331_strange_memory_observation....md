---
title: "strange memory observation..."
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by ephman on 2005-07-23
hi,

ok this is pretty strange and am wondering if anybody else has noticed this or can give me a bit of an explanation.  first off everything seems to be running totally fine on my machine, no problems from what i can notice:

for the past couple months i've notice that after everything was booted up and running i was pretty much maxing out my physical memory.  all of a sudden the other day after zero changes to my machine, things have changed.  now after i've booted up i'm only using about 50% of my physical memory.

has anybody ever noticed anything like that before?

thanks,
ephman

---

### Post by Lunde on 2005-07-23
How much memory do you have? and did it change after an update?

---

### Post by ephman on 2005-07-23
i have 384 mb.  and no changes that i'm aware of were made.  it's so strange.  i'm not worried about it much, just very curious.  there has been no change to my system.  its so strange.  i wish i could go back in time and see what's using what amount of memory and then check so see what's doing what now.  people i am not crazy!  it's so funny.

ciao!
ephman

---

### Post by Lunde on 2005-07-23
You could check if there are any messages related to this in your /var(log/syslog.X.gz (where X is changed to the number on days you want to go back, 1 week max)

---

### Post by az on 2005-07-23
From what I have opbserved, given a ton of memory, an out-of-the-box Hoary install will consume just about 128 megs of ram at startup.  If your machine does a job, like runnning the update-notifier, that could change.  Could this be what is happening?

---

### Post by ephman on 2005-07-24
i think i just figured out what my problem was.  it was a gdesklet memory app that i was relying on to tell me what my memory was.  let's just say it wasn't accurate.  i should have known.  silly me.

thanks,
ephman

---

### Post by Lunde on 2005-07-24
Good to hear, 
What was the name of it, in case there are people with similar problems?

And.. Azz, do you know what's an accurate "memory usage" program? 
The System Monitor is not showing correct i think.

---

### Post by az on 2005-07-24
"And.. Azz, do you know what's an accurate "memory usage" program?
The System Monitor is not showing correct i think."

I use 

cat /proc/meminfo

or

free

from a terminal.  Is the system monitor not working properly?


If the system monitor or any other desktop system monitor gives you different results, please file a bug report about it (if there is not already one filed)  

bugzilla.ubuntu.com

---

### Post by Lunde on 2005-07-25
Thanks Azz!
My system works perfect, but I'm not sure if it shows correct memory use. I feel like I have to set myself more into the "problem" before I post a bug report.

---

### Post by kb00heda on 2005-07-26
I will make an addition (?) to this thread, which resembles something that has occured to me.

After boot, my system, running Hoary, WDM and Fluxbox, cosumes about 65 MB of RAM. Then, after launching a couple of applications, like Eterm, Skype, Gaim, Epiphany, Sylpheed and Emacs, this number naturally rises. But upon closing them all, following a bit of browsing, sometimes the memory usage does not decrease (or at least not as much as I had expected).

I am using "free" to check the memory consumption, and "top" just to get an idea how much RAM ought to be used (by summing up the MEM% column). On these occasions the numbers do not add up at all, the one given in "free" being way larger.

It seems to me that somehow allocated memory is not freed upon closing the causing application. At first I thought this to Firefox, or maybe one of my KDE related programs, but after testing another browser and getting rid of my K stuff, the problem still persists. But I am far from being anything of an expert in these matters --- perhaps anyone else could assist me?

---

### Post by az on 2005-07-26
It does not free up the memory because it has no reason to.  If run another application which needs more memory, it will do the right thing.   If something is cached, but not being used and the kernel has to chose between overwriting those unused libraries or using swap space, it will dump the unsed stuff.

---

### Post by kb00heda on 2005-07-26
I always look at the "used" column when executing, e.g., "free -m", i.e., the second row excluding buffers and cache. 

Correct me if I misunderstood, but then it may appear as if more RAM is being used, for the simple reason it has yet to be freed? On the other hand, most often it do look like this RAM is released instantly, upon closing applications. This can't be happening by chance, can it?

(Pardon me if I'm missing the point!)

---

### Post by doclivingston on 2005-07-27
A reaonable approximation of how much memory an application is using is "RSS - Shared". You may have to enable the RSS and Shared memory columns though.

---

### Post by mike'o on 2005-08-05
Remember that Linux also uses RAM as your hard drive buffer. The more you browse through the directories, the consumption increases. Of course there is a limit to this, but I don't know what it is, or how to set it.

Another thing: 

Has anyone else noticed that gdesklet is eating up memory?
There is a memory leak either in the daemon itself, or at the SideStripes desklet.
The initial memory usage is about 70+ MB, but when I let it run for a while, it will increase at a rate of maybe 0,1 MB tice a minute (or something).
This one has used up my memory to a point when I couldn't launch another application, but had to log out from Gnome.

I haven't filed a bug report yet, because I don't know if this is a SideStripes problem or a more general gdesklet problem.

Mikko

---

### Post by doclivingston on 2005-08-05
From what I've heard on the forums, and saw during the short time I tried gdesklets, I think that it does leak memory - or at least one (or more) of the common desklets do.

---

### Post by kkass on 2005-08-10
Speaking of strange memory observations, Ubuntu does not seem to recognize all of my RAM.  When I check my memory it shows that I have just under 1GB of RAM.  I know That I have 1.5GB of RAM installed.

I even ran memtest86 to see if there was a hardware problem.  (I detected the 1.5GB and tested out OK.)

Below is the meminfo output.  I am open to suggestions.

```
$cat /proc/meminfo
**MemTotal:       906656 kB**
MemFree:        209780 kB
Buffers:         27196 kB
Cached:         412356 kB
SwapCached:          0 kB
Active:         318948 kB
Inactive:       337472 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       906656 kB
LowFree:        209780 kB
SwapTotal:     2634620 kB
SwapFree:      2634620 kB
Dirty:              56 kB
Writeback:           0 kB
Mapped:         304940 kB
Slab:            22916 kB
CommitLimit:   3087948 kB
Committed_AS:   471940 kB
PageTables:       2320 kB
VmallocTotal:   122800 kB
VmallocUsed:     26200 kB
VmallocChunk:    95148 kB

```

---

### Post by doclivingston on 2005-08-10
The reason is that the 386 kernel doesn't have support build in for that much memory. The solution is to install either the 686 (intel) or k7 (amd) kernels: linux-686 or linux-k7

---

### Post by kkass on 2005-08-10
Interesting.  I will have to try the 686 kernel again.  I tried it once before, but it hung during boot up.

---

