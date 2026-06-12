---
title: "[SOLVED] How to measure / track Firefox add-ons memory usage ?"
date: 2008-11-19
forum: General Help
---

### Post by alisonjo2786 on 2008-11-19
Anyone know of a way to figure out how much memory/CPU different Firefox add-ons use?  Maybe not exact numbers, but at least a general idea?

I have FF 3.04 (and the rest of my info is below in my signature) and even though just yesterday I doubled my memory, my processor isn't top-notch and I still only have ~1GB of RAM, so...  I'm trying to do what I can to minimize the "stress" I'm putting my computer under.

I've read in the forums that add-ons that are actually running any time FF is running will use more memory, which makes sense (as opposed to the add-ons that just gave me a "copy link text" option in my main context menu), so I've disabled a couple of add-ons, including Firebug and Tab Scope.

But, I'd like to have more info, y'know?  so I can make more intelligent/informed decisions about what add-ons to keep or trash.  So, any suggestions?

Thank you!

---

### Post by alisonjo2786 on 2008-11-20
bump

---

### Post by alisonjo2786 on 2008-11-21
(bump)

Does anyone maybe just have a suggestion for where I should post my question, if here is not an appropriate place?

---

### Post by alisonjo2786 on 2008-11-22
Does anyone maybe just have a suggestion for where I should post my question, if here is not an appropriate place?

---

### Post by clhsharky on 2008-11-22
I see that people are looking, but you are not having a problem so they move on. There are a lot of people with issues and trying to help as many as possible.

  Have you used-   top    -from a terminal, to monitor your ram.

A lot of the plug-ins don't get updated as often as ff. So not all play good with each update.

---

### Post by unutbu on 2008-11-22
Start up firefox with all add-ons disabled.
Open a terminal (Applications>Accessories>Terminal).
Type
```

pgrep firefox-bin

```
You will see a number, like 6133. This is the process id (PID) for firefox-bin.

Now type

```
top -p 6133 -d5
```

(substituting the number you see for 6133).

You will see output like this:
```

Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.2%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1034172k total,   444096k used,   590076k free,    13188k buffers
Swap:  3028212k total,        0k used,  3028212k free,   261112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                      
 6133 user      15   0  151m  42m  20m S   11  4.2   0:20.20 firefox-bin    
```              

The above example shows VIRT memory equals 151MB. VIRT memory is the amount of swap memory  plus the amount of physical RAM being used by firefox. The %CPU column gives you an estimate of how much of the CPU's clock cycles are being occupied running firefox.

The -d5 flag means that top will collect/update statistics every 5 seconds. The %CPU figure is valid for that 5 second interval.

Once you get a bearing on how much resources firefox is consuming without add-ons, you can enable the add-ons and see the difference.

---

### Post by alisonjo2786 on 2008-11-22
Thank you for the help, I will try that out in just a few minutes and report back *[consider this "stricken"--- *(just in case, like, anyone is curious about this in the future and has some of the same add-ons I have)* ---]*, and then I'll mark this as "SOLVED".

---

### Post by alisonjo2786 on 2008-11-22
I am all set, thanks so much for the advice!

And...
> **clhsharky said:**
> I see that people are looking, but you are not having a problem so they move on. There are a lot of people with issues and trying to help as many as possible.
Understood, makes sense.  Thank you for your reply, I appreciate it.

---

