---
title: "How to tell apart real and virtual cpu?"
date: 2010-04-25
forum: Hardware
---

### Post by Sepiraph on 2010-04-25
I was wondering if there is a way to tell apart the real and virtual cpu as a result of hyper-threading.  In this thread ([http://ubuntuforums.org/showthread.php?t=1312747&page=1](http://ubuntuforums.org/showthread.php?t=1312747&page=1)), specifically the last post 'guessed' that it can be deducted from dmesg.  However my own output shows slightly different result:

```
$ dmesg | egrep -i -e "Processor Core ID" -e "Initializing CPU" -e "Physical Processor ID"[    0.000000] Initializing CPU#0
[    0.009823] CPU: Physical Processor ID: 0
[    0.009823] CPU: Processor Core ID: 0
[    0.267446] Initializing CPU#1
[    0.416859] CPU: Physical Processor ID: 0
[    0.416860] CPU: Processor Core ID: 1
[    0.431592] Initializing CPU#2
[    0.576506] CPU: Physical Processor ID: 0
[    0.576507] CPU: Processor Core ID: 2
[    0.587970] Initializing CPU#3
[    0.736154] CPU: Physical Processor ID: 0
[    0.736155] CPU: Processor Core ID: 3
[    0.747651] Initializing CPU#4
[    0.895799] CPU: Physical Processor ID: 0
[    0.895800] CPU: Processor Core ID: 0
[    0.907142] Initializing CPU#5
[    1.055446] CPU: Physical Processor ID: 0
[    1.055447] CPU: Processor Core ID: 1
[    1.066870] Initializing CPU#6
[    1.215093] CPU: Physical Processor ID: 0
[    1.215093] CPU: Processor Core ID: 2
[    1.226492] Initializing CPU#7
[    1.374737] CPU: Physical Processor ID: 0
[    1.374738] CPU: Processor Core ID: 3

```

So I am wondering if it is something as simple as the 1st 4 are real or is there some specific way to find out?

---

