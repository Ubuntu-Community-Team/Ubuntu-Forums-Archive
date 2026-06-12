---
title: "Memory eater"
date: 2005-11-11
forum: General Help
---

### Post by Gustav on 2005-11-11
Something is eating my memory :( 

When I start my computer it doesn't use much memory at all but after about 5-10 minutes a process called updatedb starts and it eats about 100 mb of my ram without ever returning it!!! (or it's something else that does it at the same time as updatedb runs)

Is there a solution for this or is it supposed to be like this?

---

### Post by codejunkie on 2005-11-11
[quote=Gustav]Something is eating my memory :( 

When I start my computer it doesn't use much memory at all but after about 5-10 minutes a process called updatedb starts and it eats about 100 mb of my ram without ever returning it!!!

Is there a solution for this or is it supposed to be like this?[/quote]
i dont know a solution for it but im suffering from the same thing, i have a gig of ram and the longer the pc stays up the more ram gets eaten up. for me it usually starts using up my swap file  after it reaches about 300mb of physical ram and with hoary i never noticed  any swap file usage.

---

### Post by LorenzoD on 2005-11-11
Updatedb runs as a daily cron job. It can take a while to complete, but it will complete and you should get your memory back.

You probably shouldn't disable it from running alltogether, but you may want to experiment with running it less frequently. If you care to know updatedb basically indexes files so that you can find them relatively quickly with locate.

---

### Post by Gustav on 2005-11-11
After a little searching I realize that it's probably not updatedb that is the bad guy but some other process run by cron.daily (they can be found in /etc/cron.daily)

Anyone have any ideas?

---

### Post by LorenzoD on 2005-11-11
Both updatedb and logrotate can get a bit heavy for me while they run. Depending on what I'm using the machine for, my solution sometimes is to move these out of cron.daily and into some other place like cron.weekly.

Of course, that will still make your system slow and barely usable, but this time only once a week and not once a day.

---

### Post by Gustav on 2005-11-11
It's not a problem that my computer is running slow while updatedb is running. The problem is that 100 mb of my memory mysteriusly disappear and isn't returned.

---

### Post by nagilum on 2005-11-11
[QUOTE=Gustav]After a little searching I realize that it's probably not updatedb that is the bad guy but some other process run by cron.daily (they can be found in /etc/cron.daily)

Anyone have any ideas?[/QUOTE]
I had the same problem, after a while the memory usage drastically increased and  it was indeed updatedb in my case that caused this. Don't have any other solution but to disable it though. Since I don't use locate (find is my friend) there are no drawbacks for me. Your situation might be different of course.

---

### Post by Gustav on 2005-11-11
[QUOTE=nagilum]I had the same problem, after a while the memory usage drastically increased and  it was indeed updatedb in my case that caused this. Don't have any other solution but to disable it though. Since I don't use locate (find is my friend) there are no drawbacks for me. Your situation might be different of course.[/QUOTE]
I don't use locate either so that seems to be the optimal solution

Thank you everybody!

---

### Post by earobinson on 2005-11-11
Im not sure but this might help you [http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/)

---

### Post by rwabel on 2005-11-13
I've the same problem. I don't care when all my memory is beeing used, but now also my SWAP is full. And I don't know a way to clear it. Furthermore the system also gets slower and slower and that can't be the sense behind it

---

### Post by kosmic on 2005-11-13
A radical way to clear the swap is to use as root the Swappoff e Swappon :cool: comands

---

### Post by nszabolcs on 2005-11-13
or you can use the system monitor to see which program uses too much memory and restart it. (Applications / System Tools / System Monitor)

---

### Post by rwabel on 2005-11-14
I've tried that already, but it only gives free a bit of the used memory! The only solution is either to restart X or reboot. Otherwise I only get about 5%-10% of my SWAP back

---

### Post by Gustav on 2005-11-16
For me, It was updatedb that ate my memory. If you are not using the 'locate' command you can disable it by doing this

```
cd /etc/cron.daily
sudo chmod slocate 644
```
For more info, look at [http://www.ubuntuforums.org/showthread.php?t=87497](http://www.ubuntuforums.org/showthread.php?t=87497)

---

