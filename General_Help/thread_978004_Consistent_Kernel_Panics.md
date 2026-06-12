---
title: "Consistent Kernel Panics"
date: 2008-11-10
forum: General Help
---

### Post by ghindo on 2008-11-10
Hi, I'm using Ubuntu 8.10 Intrepid Ibex.

I've been experiencing pretty consistent kernel panics with my system.  The system freezes up, the caps and scroll lock lights blink, and I can't get out of it except for with a hard restart.  (Ctrl + atl + backspace doesn't work.)  

It's been happening with all the kernels I try, too.  2.6.27-4 through 2.6.27-7 all panic like this.

I've googled around and I can't find anything.  Anybody have any suggestions?

---

### Post by ghindo on 2008-11-17
Bump.

I'm keeping up-to-date with my updates, and have even installed kerneloops to try to help.  But, I'm still getting these panics.  Could this be a hardware problem?

---

### Post by ghindo on 2008-11-19
Bump.

It's still happening.  I ran a full Memtest86+ and it passed, so it's probably not a hardware problem.  What's going on here?  Anybody wanna help?

---

### Post by larnal29 on 2008-11-19
Hello!

I have exactly the same problem with my dell xps 1210 since I upgraded from hardy to ibex and can't find any info either.. It seems correlated with the wifi activity I think as it usually starts short after my wifi radar led starts blinking..

---

### Post by ghindo on 2008-11-19
> **larnal29 said:**
> Hello!

I have exactly the same problem with my dell xps 1210 since I upgraded from hardy to ibex and can't find any info either.. It seems correlated with the wifi activity I think as it usually starts short after my wifi radar led starts blinking..I'm also using a Dell laptop - an Inspiron 1420.  

I haven't noticed any correlation between the Wifi and the problem, although I also get a blinking Wifi LED when I think it should be a solid light.

---

### Post by larnal29 on 2008-11-19
Yes it is supposed to be constant lighting. I see quite a lot of wlan activity in my sys log that I think is suspicious, but it might simply be a side effect of some deeper instable process

---

### Post by philinux on 2008-11-19
Shut the machines down remove power cord and remove battery. Leave for 10 mins before powering back up.
This has been suggested before don't know for sure if it will work.

---

### Post by ghindo on 2008-11-19
> **larnal29 said:**
> Yes it is supposed to be constant lighting. I see quite a lot of wlan activity in my sys log that I think is suspicious, but it might simply be a side effect of some deeper instable processFrom looking around a little bit, it seems that the flashing LED is another thing entirely.  I found a bug report on LaunchPad that seems to confirm this.  

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211)

If you're registered with LaunchPad, please be sure to let the developers know that this issue affects you as well by toggling the "This bug does not affect me" option at the top of the page.> **philinux said:**
> Shut the machines down remove power cord and remove battery. Leave for 10 mins before powering back up.This seems to be a temporary solution more than anything.  I would like to find out what the root cause of this is.

---

### Post by philinux on 2008-11-19
Anything in dmesg to point the finger at?

---

### Post by larnal29 on 2008-11-19
I don't see anything in dmesg expect a lot of things related to wlan. Also I'm not a specialist in reading these stuff

---

### Post by snova on 2008-11-19
Knowing you're getting a kernel panic isn't much help if we don't know what it is! What's the panic about? Write down as much information you can. Where you doing anything or did it fail to boot at all?

Even if you don't understand the contents of dmesg (you aren't expected to, there are probably few that can make sense of the entire thing), somebody else here will, so attach it if you can.

Ctrl-Alt-Backspace won't work because that's an X thing (it causes it to restart), which clearly isn't running. :p

---

### Post by ghindo on 2008-11-19
> **snova said:**
> Knowing you're getting a kernel panic isn't much help if we don't know what it is! What's the panic about? Write down as much information you can. Where you doing anything or did it fail to boot at all?

Even if you don't understand the contents of dmesg (you aren't expected to, there are probably few that can make sense of the entire thing), somebody else here will, so attach it if you can.

Ctrl-Alt-Backspace won't work because that's an X thing (it causes it to restart), which clearly isn't running. :pI'm not exactly sure what the panic is about.  I've tried to include as much information as I can, but I'm not really sure what to look for.  The panics happen after boot, although I haven't ever noticed any consistency in terms of the programs I'm running, what I'm doing, etc.

I copy/pasted the dmesg output here:  [http://paste.ubuntu.com/74541/](http://paste.ubuntu.com/74541/)

I just included the Ctrl+Alt+Backspace thing to confirm it wasn't an X thing, and it was indeed a kernel panic.

Thank you everyone for your help :)

---

### Post by ulgor on 2008-11-20
I am experiencing the same problem since yesterday on my Dell XPS 1530. I upgraded from 8.04 to 8.10 a few weeks ago and did not have any problems with 8.10 so far...
I had to switch to Vista for 2 whole days because of this, and it didn´t crash - this is not a RAM/hardware issue!!

If I can somehow use a LiveCD to check the log files on my linux HD, which ones should I post here?

---

### Post by philinux on 2008-11-20
```
cat /var/log/messages > ~/Desktop/log.txt
```Then attach the file to reply.
Make sure you get your system log file and not the livecd's. Need to mount your drive first.

---

### Post by larnal29 on 2008-11-20
Here is my dmesg.

My laptop is usually running normally for a few minutes, firefox is usually open as well as open office and then, crash with blinking of the led indicators

---

### Post by ghindo on 2008-11-24
Bump.  Is there anybody who could help us decipher our dmesg/logs?

---

### Post by jerrykenny on 2008-11-24
If you suspect its a wifi problem, can you try running with your wifi modules unloaded manually ?

Just to see if the system will run smoothly in the absence of wifi.

Are you both running "updated" systems, maybe theres a deprecated kernel module running alongside the newer version? . . . . just thinking aloud, maybe have a look in /etc/modules and se if theres any extra stuff in there. . .

---

### Post by larnal29 on 2008-11-24
Here is what I get from my etc/modules

I'll try tonight to unload the wifi modules

---

### Post by damis648 on 2008-11-24
Curious: do you have a 4965AGN intel wireless card? Because I had the exact same issue with the kernel panics. (AFAIK, the flashing light for the wifi is a feature, not a bug. It flashes during activity.). Anyway, see my thread for a possible solution, installing the backports:
[http://ubuntuforums.org/showthread.php?t=964411](http://ubuntuforums.org/showthread.php?t=964411)

---

### Post by ghindo on 2008-11-24
> **damis648 said:**
> Curious: do you have a 4965AGN intel wireless card? Because I had the exact same issue with the kernel panics. (AFAIK, the flashing light for the wifi is a feature, not a bug. It flashes during activity.). Anyway, see my thread for a possible solution, installing the backports:
[http://ubuntuforums.org/showthread.php?t=964411](http://ubuntuforums.org/showthread.php?t=964411)I know I have an Intel wireless card, but I can't remember which, nor do I remember how to check.  The symptoms sound similar, although I already have backports enabled.  

I think I may just ride this bug out until Jaunty Alpha 2 or 3.  :(  Hopefully a new kernel will stop this from happening.

---

### Post by ghindo on 2008-12-01
Bump.  I reinstalled 8.10 for unrelated reasons and the kernel panics are still happening.  :(

---

### Post by karlr42 on 2008-12-01
I had the same issue on an Inspiron 1520, with an Intel Corporation PRO/Wireless 3945ABG card, running 8.10. I just reinstalled 8.04 instead.
FWIW, I think it's something to do with the new kernel.

---

