---
title: "Ubuntu is continously hanging"
date: 2009-07-29
forum: Hardware
---

### Post by threepwood960 on 2009-07-29
Hi, I didn't know where I should write this message. I have Ubuntu 9.04 with gnome, compiz and gnome-do. A month ago it is hanging all days several times. Always when I am a time working and open a new application it begins to go slower and slower, the application window gets to gray and the ubuntu doesn't work. Sometimes, with patience, I push ctrl+f1 and I get reboot or kill the last application. But normally I have to turn off the computer.
Yesterday I thought that it was for these messages in my logs:
> Jul 29 09:17:15 dellp kernel: [ 1005.279683] possible SYN flooding on port 4662. Sending cookies.

But I closed this port and it follow hanging. Now I think it is by the memory. When I write 'free' I obtain:
>              total       used       free     shared    buffers     cached
Mem:       2052308    1997524      54784          0      52956    1293876
-/+ buffers/cache:     650692    1401616
Swap:            0          0          0

And I don't understand why I haven't swap because I created this partition. And the most mysterious thing: when I start the sytem, the free memory begins to get low and low and low until approximately 50000 and it stops.

Another idea is when it hangs and I go to ctrl+F1, sometimes appears something like: 'virtualBox has been stopped' and the system is unblocked.

However it get hanging with virtualBox opened, or Wine, or aMule, compiz, etc, etc.

Please any idea? I'm hopeless.

---

### Post by AndyCee on 2009-07-29
Whoops, deleted my own post.

See if some of the following help:

To enable your swap:
```
sudo swapon -a -v
```

To check system processes to see what's eating up your memory & CPU time:
```
top
```

And for the heck of it:
```
nmap localhost
```

Don't post the last one on the internet. If you're receiving a SYN flooding attack, it might be worth checking to see what ports you've got open. Maybe even type "w" to make sure of your security.

One more - how is your disk usage? I encountered similar errors when my Ubuntu partition became full.

---

### Post by threepwood960 on 2009-07-29
Thanks AndyCee, 
I have tried 'sudo swapon -a -v' but it can't start:
> swapon en /dev/disk/by-uuid/b8b54be7-852f-4f34-965b-e82dad2b3813
swapon: no se pudo ejecutar 'stat' para /dev/disk/by-uuid/b8b54be7-852f-4f34-965


Could it be that I haven't this partition. It is strange. How could I check my partitions?

With 'top' I don't see nothing. All processes have between several Kb and 10-20 Mb. And CPU charge is low.

And with nmap:
> Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-29 16:42 CEST
Interesting ports on localhost (127.0.0.1):
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
990/tcp   open  ftps
5679/tcp  open  activesync
50001/tcp open  unknown

But it is strange: I have updated the kernel 2.6.28-14 (which I already had) and now when I use free the memory don't go down until 50.000 (only go down when I open a new process). I noticed that my virtualBox modules have also been updated. I will wait...

---

### Post by threepwood960 on 2009-07-29
Now, I'm sure it is memory. I have open 6-7 'heavy' applications and it hanged again. Again the memory stops of going down in approximately 50000 and with 2 or 3 more applications it is hanging.

In adittion, when the system start this is memory:
>             total       used       free     shared    buffers     cached
Mem:       2052332     713572    1338760          0      32680     394636
-/+ buffers/cache:     286256    1766076

It is very much, isn't it?

I don't understand, this one don't happens previously, and I am an Ubuntu user from the beginning.

---

### Post by lavinog on 2009-07-29
```

           total   used   free      shared buffers cached
Mem:       2052332 713572 1338760   0      32680   394636
-/+ buffers/cache: 286256 **1766076**

```
The number in bold is what you should look at which looks like you have about 1.7G of memory free.
a nicer way to use free is with thi -m switch
```

free -m
             total       used       free     shared    buffers     cached
Mem:          3386       2665        720          0        390       1394
-/+ buffers/cache:        880       2505
Swap:         1906          6       1899

```
this will give the results in megabytes

A good way to watch for memory leaks is to add the system monitor applet to the panel and configure it to watch memory:
right click the panel, click 'add to panel', start typing 'system monitor' in the find box until you see the system monitor, double click it. You should then have a bar graph showing cpu usage on your panel. Right click that bar graph, select preferences, under monitored resources, check memory and any other item you wish to monitor. If you are trying to watch for memory leaks, it helps to increase the system monitor update interval.

---

### Post by threepwood960 on 2009-07-29
Now I have swap memory. I 'rescued' it with swapon.
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1796        208          0         52       1274
-/+ buffers/cache:        468       1535
Swap:          956          0        956
```

But I don't think it will repair the problem because again the memory go down and I don't find any process from top.

---

### Post by lavinog on 2009-07-29
> **threepwood960 said:**
> Now I have swap memory. I 'rescued' it with swapon.
```
free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1796        208          0         52       1274
-/+ buffers/cache:        468       1535
Swap:          956          0        956
```

But I don't think it will repair the problem because again the memory go down and I don't find any process from top.

Free memory is considered wasted memory. Linux will use up as much memory as it can for disk cache to maximize performance, and reduce wear on your storage device.

If you are not seeing a process in top that is using up your memory, then I don't think the problem is caused by a memory leak. Besides the kernel will kill the process that uses the largest amount of memory if you do run out of memory before it will crash.

I think that SYN flooding message is a good start to find what the problem is.
How did you close the port?
are you getting any other messages now that it is closed?

---

### Post by lavinog on 2009-07-29
Does the computer hang if you disconnect the network cable/wireless?

Are you running any torrents or file sharing software?

---

### Post by threepwood960 on 2009-07-29
With my 1Gb Swap seem that it doesn't hang. I have run many applications and now there weren't problems. But I need test during a day.

When it hanged I tried to disconnect network and bluetooth (with the netbook button) but it followed hanged. I closed 4662 port in my adsl rooter and I opened a new one (5662) for amule, and SYN flooding appears in that new port. But I thing is not the problem, because in my log doesn't appear the 'SYN flooding' always.

---

### Post by threepwood960 on 2009-07-31
After 2 days everything is the same. Now I can open more applications thank to my Gb of swap and the computer hang after more time than before. The SYN flooding don't appear because I don't open amule, but I don't find the problem. Any new idea?

---

### Post by depaulmatthew on 2009-08-31
I have a problem with gnome-do. When the system boots, no program appears in the gnome-do list. then it hangs in a while. when I removed and installed gnome-do again. It worked fine. But after restarting the same problem. Its hanging again. Any cure for this?

---

