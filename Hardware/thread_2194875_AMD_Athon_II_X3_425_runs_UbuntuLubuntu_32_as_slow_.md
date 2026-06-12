---
title: "AMD Athon II X3 425 runs Ubuntu/Lubuntu 32 as slow as a slug In a minefield"
date: 2013-12-21
forum: Hardware
---

### Post by Langney on 2013-12-21
Right, I Installed Ubuntu 13.10 on my rig but for some reason It literally runs software at snails pace. I could try and load up Firefox or Chromium, Libre office and so forth but It takes around 15-20 seconds for them to even start. I know technology Is evolving all the time and higher system specs are needed but I'm running a machine that was made In 09. Surely that can't be the cause as I was running Ubuntu fine on an 06 machine (Core2Duo 2.7ghz) Up until recently. 

I even tried Lubuntu, you know the lightweight brother of Ubuntu 32-bit but to my surprise. It was the same Issue. If there a fault In the AMD II X3 435 processor somewhere that stops It from running at It's peak. Overall creating an unusable OS at this point. Currently I'm back on Windows (Unfortunate I know) as It don't seem to affect any of my programs and they boot up just like that.

Any help on the matter would be great at to be honest as I would really like to get back to using Ubuntu. Shame I gave my old mobo away. 

Here are the current specs of my machine

 Processor: AMD Athlon(tm) II X3 425 Processor (3 CPUs), ~2.7GHz
             Memory: 3072MB RAM
Available OS Memory: 3072MB RAM
Card name: NVIDIA GeForce GTX 260
       Manufacturer: NVIDIA
          Chip type: GeForce GTX 260

---

### Post by sanderj on 2013-12-21
What is the CPU load according to System Monitor (press Superkey, then type "System Monitor"). And while you're there: what is memory and swap usage & availablity?

---

### Post by Langney on 2013-12-21
> **sanderj said:**
> What is the CPU load according to System Monitor (press Superkey, then type "System Monitor"). And while you're there: what is memory and swap usage & availablity?


Hi there. Thanks for the reply. Here is a screenshot of my system monitor. I hope this helps.  [IMG]http://img.photobucket.com/albums/v512/djplayuk/Screenshotfrom2013-12-21095619_zpsd0418a20.png[/IMG]

---

### Post by sanderj on 2013-12-21
Low CPU load, low memory load (but much memory available) ... just looks good. Strange.

You have install Lubuntu to a harddisk built in your system, right? Not a USB stick/drive or something else?

---

### Post by Langney on 2013-12-21
> **sanderj said:**
> Low CPU load, low memory load (but much memory available) ... just looks good. Strange.

You have install Lubuntu to a harddisk built in your system, right? Not a USB stick/drive or something else?

Nope all Installed on a hard drive. All I could think really Is possible broken hard drive?

---

### Post by sanderj on 2013-12-21
> **Langney said:**
> Nope all Installed on a hard drive. All I could think really Is possible broken hard drive?

Something with the hard drive is my idea too: broken hard drive, or 'just' some misconfiguration.

You could measure how long it takes to write and then read a 1GB file. 


```
time dd if=/dev/zero of=test.img bs=1M count=1000
time dd if=test.img of=/dev/null

```


On my laptop with SSD it takes 7 resp 3 seconds, but my laptop has a SSD

```
sander@flappie:~$ time dd if=/dev/zero of=test.img bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1,0 GB) copied, 7,65376 s, 137 MB/s

real	0m7.838s
user	0m0.005s
sys	0m1.267s
sander@flappie:~$ ll test.img 
-rw-r--r-- 1 sander sander 1048576000 dec 21 11:39 test.img
sander@flappie:~$time dd if=/dev/zero of=test.img bs=1M count=1000


sander@flappie:~$ time dd if=test.img of=/dev/null
2048000+0 records in
2048000+0 records out
1048576000 bytes (1,0 GB) copied, 3,73035 s, 281 MB/s

real	0m3.736s
user	0m0.474s
sys	0m2.623s
sander@flappie:~$

```

---

### Post by Langney on 2013-12-21
> **sanderj said:**
> Something with the hard drive is my idea too: broken hard drive, or 'just' some misconfiguration.

You could measure how long it takes to write and then read a 1GB file. 


```
time dd if=/dev/zero of=test.img bs=1M count=1000
time dd if=test.img of=/dev/null

```


On my laptop with SSD it takes 7 resp 3 seconds, but my laptop has a SSD

```
sander@flappie:~$ time dd if=/dev/zero of=test.img bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1,0 GB) copied, 7,65376 s, 137 MB/s

real    0m7.838s
user    0m0.005s
sys    0m1.267s
sander@flappie:~$ ll test.img 
-rw-r--r-- 1 sander sander 1048576000 dec 21 11:39 test.img
sander@flappie:~$time dd if=/dev/zero of=test.img bs=1M count=1000


sander@flappie:~$ time dd if=test.img of=/dev/null
2048000+0 records in
2048000+0 records out
1048576000 bytes (1,0 GB) copied, 3,73035 s, 281 MB/s

real    0m3.736s
user    0m0.474s
sys    0m2.623s
sander@flappie:~$

```


Here are my readings 
```

1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 9.2752 s, 113 MB/s


real	0m9.432s
user	0m0.020s
sys	0m3.540s
craig@craig-VG241AA-ABU-p6206uk:~$ time dd if=test.img of=/dev/null
2048000+0 records in
2048000+0 records out
1048576000 bytes (1.0 GB) copied, 1.90244 s, 551 MB/s


real	0m1.905s
user	0m0.380s
sys	0m1.524s
craig@craig-VG241AA-ABU-p6206uk:~$ 



```

---

### Post by Langney on 2013-12-23
I managed to sort out my Issue with my computer regarding how slow It was going. I thought I'd try and put 12.04 LTS on my machine and low and behold. It works perfectly ;). No slowdowns or anything. I'm now thinking there Is a regression somewhere In the 13.10 version. What do you think?

---

### Post by sanderj on 2013-12-23
Good it works now.

As we have not found anything as high CPU load or slow harddisk IO, it might be indeed something in the kernel: 12.04 and 13.10 use different kernels. You could try 13.04, and you could interpolate kernels.

Or ... just keep using 12.04 ... :-)

---

### Post by mörgæs on 2013-12-23
It would be interesting to know how 14.04 works. It will be the next long term support release, so finding bugs at an early stage would be a great help.

---

### Post by sanderj on 2013-12-23
> **mörgæs said:**
> It would be interesting to know how 14.04 works. It will be the next long term support release, so finding bugs at an early stage would be a great help.

**If** the OP wants to do that, the daily is here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) ...

---

### Post by Langney on 2013-12-23
> **sanderj said:**
> **If** the OP wants to do that, the daily is here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) ...

I really don't mind to be honest. If It helps with others experiences with Ubuntu then I'm all for It :)

---

