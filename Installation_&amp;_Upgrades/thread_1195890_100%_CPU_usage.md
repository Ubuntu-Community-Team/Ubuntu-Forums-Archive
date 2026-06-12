---
title: "100% CPU usage"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by awam66 on 2009-06-24
Hi,
Yesterday I had a number of updates the most significant being to Kernel 2.6.28-13 and since then the cpu usage is constantly at 100%. Looking in System monitor there is nothing doing anything like that. Any ideas or has anyone else seen this. On my external USB disc I have xubuntu with the same kernel and no problems there.

Forgot to say it OS Jaunty Jackalope amd64 processor 1G memory

---

### Post by emeraldgirl08 on 2009-06-24
I had to disable three things in start-up for this problem: 

a)check for new hardware drivers, 
b)remote desktop, and 
c)update notifier. 

I figure I could do these manually anyway. I figured it had to do with something wireless after I turned off wireless and the spike went down. I did have the same symptoms such as a consistent 90+ CPU meter reading that would not go away! I also did not find anything in System Monitor that would cause this spike. Now I am staying at a fairly consistent sub 20% CPU reading :)

Hope it stays this way!

---

### Post by Therion on 2009-06-24
Had a very similar experience with one of my dual-cores being pegged at 100% -- 100% of the time.  I decided to let it go, but when I came back from class a couple hours later, same story.

When I looked I found it was a Firefox process that was running up the bill, even though there were no instances of Firefox open.  I killed the process and that solved the problem.  Odd though.

Running Karmic 64-bit.

---

### Post by emeraldgirl08 on 2009-06-24
Therion: What process was that? I had instances where my Firefox locked up the screen and I had to reboot. Hmmm.

---

### Post by awam66 on 2009-06-24
Still a puzzle,
I tried booting to the older kernel 2.6.28-11 but he problem remains. So looks like something other than the kernel.
Still investigating.

---

### Post by ssri on 2009-06-24
try running the terminal with the command "top" to see which processes are eating up your cpu.  Then you can type sudo kill -9 <process#> or sudo killall -9 <COMMAND>

---

### Post by awam66 on 2009-06-24
> **emeraldgirl08 said:**
> I had to disable three things in start-up for this problem: 

a)check for new hardware drivers, 
b)remote desktop, and 
c)update notifier. 

I figure I could do these manually anyway. I figured it had to do with something wireless after I turned off wireless and the spike went down. I did have the same symptoms such as a consistent 90+ CPU meter reading that would not go away! I also did not find anything in System Monitor that would cause this spike. Now I am staying at a fairly consistent sub 20% CPU reading :)

Hope it stays this way!

Hi emeraldgirl,
Just unchecked a) and b) above and that solved the problem.
Now which one is it?

---

### Post by Therion on 2009-06-24
> **emeraldgirl08 said:**
> Therion: What process was that? I had instances where my Firefox locked up the screen and I had to reboot. Hmmm.
It said something obvious, like "Firefox".  Just look for the process eating 99% of your CPU and force-quit it.  Or you can opt to *Kill it With Fire, like I did.








/*Killing with fire not recommended.

---

