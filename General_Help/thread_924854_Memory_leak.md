---
title: "Memory leak"
date: 2008-09-20
forum: General Help
---

### Post by kb2001 on 2008-09-20
I believe I have a memory leak occurring.  When I reboot my computer and login, my memory usage is about 500MB.  The past 3 nights, I have rebooted, logged in, and left it alone.  When I come back to it the next night, the memory usage is about 1.9GB, and the swap has been accessed (between 20 and 40MB).

Can someone give me some tips on how to track down where this is occurring?  I've done top at regular intervals, sorted by memory usage %, but the heaviest processes haven't climbed at all, and I'm not sure how to view them all.

I am running 8.04, kernel is 2.6.24-19-generic.  I am current on updates.
2GB RAM, 1x80GB PATA drive, 2x250GB SATA drives, all formatted with ext3

Some apps that I run all the time:
mythtv-backend 0.21.0+fixes16838-0ubuntu3.1
mysql 5.0.51a-3ubuntu5.1
apache2 - max of 5 threads

My original install was 7.10.  I did the upgrade to 8.04 a few weeks ago.  I did not notice this behavior before the upgrade, but I wasn't looking either.  At that point in time, I was shutting the computer off at night, because I don't have air-conditioning and my wife and I were leaving everything off unless we were using it.

That's it, other than normal things.  Can anybody offer some tips on how I can track this down, or be able to view some better details on processes and their memory usage?

I appreciate any advice in this.  Tonight, I am going to reboot, kill myth-backend and see what I get tomorrow night.  Apache the next night, and both mythtv and mysql the following night.  I do not notice any slowdown while using the computer, and am really not sure where else I can go for more information.

---

### Post by Shazaam on 2008-09-20
For more info try htop. It's in the repos.

---

### Post by p_quarles on 2008-09-20
> **kb2001 said:**
> I believe I have a memory leak occurring.  When I reboot my computer and login, my memory usage is about 500MB.  The past 3 nights, I have rebooted, logged in, and left it alone.  When I come back to it the next night, the memory usage is about 1.9GB, and the swap has been accessed (between 20 and 40MB).
Whenever I see this, I wonder if that memory is really being used, or is simply cached. When the usage is high, run:
```
free -m
```
and post the results here.

---

### Post by kb2001 on 2008-09-20
Thanks for the tips.  I installed htop and checked it out.  I like that I can scroll through the processes, that is a huge help.  It's a bit deceiving though.  I started up FF, and it opened 4 processes, all with the me usage at 1.4%.  This seemed odd, so I added up the percentage usage of all processes and it came out to 122%.  Total mem usage was at 550MB.  I believe this is just the main proc total, with the LWP showing the same usage as the combined total of the main and LWP together.  Thank you Shaazam, this is very helpful

p_quarles- I saw your post after I had already rebooted so the usage is not high right now.  I'm on another computer now (so as not to taint my results) so I can't give the exact results of free -m.  I did notice that my total was at 610MB.  I started FF and it went to 628MB, though FF was using much more than that.  When I shut FF down, it went back to 610MB.  free -m showed the total at 610MB, and the buffer line was 2xx or so (I think? don't recall exactly).

I'll post back on this thread tomorrow/night.

Thank you again for the tips, it is appreciated.

---

### Post by Shazaam on 2008-09-20
If you look at the Firefox entries (or any other with multiple entries) while running htop you will notice each has a different PID.

---

### Post by kb2001 on 2008-09-20
I saw the different PIDs.  What I also noticed was that every firefox process had the same memory usage.  This is what I commented on before.  It seems that the LWP misreport on the memory usage for itself (themselves), and instead report the same mem usage as the parent, which reports as the cumulative total for all its processes (parent plus LWP).  This seemed odd, so I added up the percentages for ALL processes that htop reported, and the total came to 122%, when the mem usage total reported by top was 550MB out of 2GB, or about 27%.  Not 122%.  This is why I believe it to be deceptive.  It is still a very useful tool.  I am not being sarcastic at all.  I've already benefited from it.

I'm probably getting too picky.  At work, I've spent the past 4 weeks sorting through truss outputs and dtrace outputs trying to isolate a problem one of our apps is having.  This makes me hypersensitive to system specifics, and frustrated that I can't get the same visibility into my home computer as I can with our Solaris servers at work.  Well, maybe I can, I just don't know how to right now.

Again, the help is really appreciated.  I will update tomorrow night with more data, once I've let a cold reboot run for a day without the myth-backend running.

---

### Post by bingoUV on 2008-09-20
Read this to understand why the memory usage of processes doesn't add up and why the memory usage is what it is: [http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

So far, it seems most of your extra RAM usage is cache/buffers. Post the complete output of "free -m" after the PC has an uptime of a day or so.

---

### Post by kb2001 on 2008-09-20
It's been up for about 14 hours now.  I shutdown the mythtv-backend immediately after reboot last night.

According to top, my mem usage is ~580MB.  free -m produces this:

```

user@host:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026        578       1447          0         22        344
-/+ buffers/cache:        212       1814
Swap:         1953          0       1953

```

I read that article on how memory is utilized, along with the cache and the buffers, and it would explain a lot.  Given that, it makes sense that my usage would still be low now, since the computer wasn't doing anything actively.  I can believe that mythtv-backend WOULD be actively working, and would cause the usage to climb.  I'm going to reboot shortly, and leave mythtv-backend running, so I can check it with free -m when the mem usage is reported high again.  I hope it reveals good news.

Thank you again

---

### Post by kb2001 on 2008-09-22
I've had to use it a lot for work in this time, so I rebooted this morning and have left it alone since then, with mythtv-backend running.

top reports 105000kB in use.  Here is free -m:

```

user@host:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2026       1026        999          0         49        670
-/+ buffers/cache:        305       1720
Swap:         1953          0       1953

```

If I'm reading this correctly, it says 1026MB in use, but 670MB are cached.  So that means that it's really only using 356MB.  Am I reading this correctly?  And the buffers/cache line indicates that the applications are using 305MB.

So, the kernel is using about 50MB, my running applications are actively using 305MB, and I have an additional 670MB of data that is in cache, and can be replaced without paging.  Is this accurate?  If not, can someone please help me to understand this?  I believe I am understanding, but if what I have determined is incorrect, please set me straight.

Thanks

---

### Post by p_quarles on 2008-09-22
> **kb2001 said:**
> If I'm reading this correctly, it says 1026MB in use, but 670MB are cached.  So that means that it's really only using 356MB.  Am I reading this correctly?
Yep. There are no problems with those readings. Nearly all of the system's memory is available, so the kind of usage you are seeing is not something that is going to slow the system.

---

### Post by kb2001 on 2008-09-26
Thanks for everyone's help on this.  I appreciate it greatly.  It's been running for a few days now and the numbers show what is described in how it handles memory.  The one odd thing I noticed is that the swap space has 38MB used.  I imagine it operates in the same way by always holding on to it to make use of the resources.  Odd that it ever had to tap into it in the first place.  My actual used memory is still low.

Thanks again

---

### Post by p_quarles on 2008-09-26
Ubuntu is set by default to begin using swap space pretty early. You can change that (so that it will only use swap if absolutely needed) by running:
```
sudo echo 'vm.swappiness = 0' >> /etc/sysctl.conf
```
The default setting is 60.

---

