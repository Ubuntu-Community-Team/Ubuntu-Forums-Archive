---
title: "System Monitor vs Top  show memory usage diffence"
date: 2008-11-24
forum: Hardware
---

### Post by alekons on 2008-11-24
Hello,

I was trying to find out the memory usage in my system through System monitor applet. The strange thing is that the total amount of memory is 2.4 GB although my system has 4GB or ram. 

As i was not sure i check the top command and there i found a huge difference. 

The amount of memory was the same but the usage was much higher.
Monitor system show : 2.4GB total and the usage is 981.9 MB 
Top : 2.55 GB total memory and the usage is 2.47 GB 

(see attached image )


Why this huge difference ?


Ubuntu 8.10

Thanks
Alexis

---

### Post by iggykoopa on 2008-11-24
If you are using 32 bit ubuntu that could explain why not all your memory is showing...if you install the server kernel or reinstall with 64-bit the rest of your ram should show up. The memory usage shows that way because ubuntu is caching stuff..on the system monitor the difference shows(with the default colors) light green for cache and dark green for system useage, it's nothing to worry about unless your swap is being used.

edit: when i was talking about the colors its with the system monitor applet...

---

### Post by linux_tech on 2008-11-24
To monitor the memory you may want to check out [http://manpages.ubuntu.com/manpages/...an1/asmem.html](http://manpages.ubuntu.com/manpages/...an1/asmem.html)

64-bit normally supports more memory than 32-bit.

If your focus is to utilize more memory and have higher maximum limits, then I would use 64-bit server OS. Server versions usually support more memory than the workstation versions.

If you are running a 32-bit system and you want to maximize RAM limits, then you will need to run server, and compile a kernal with PAE. The kernel of the server version of Ubuntu has support for PAE (Physical Address Extension), to make a 32-bit system be able to use up to 64 GB RAM more info here-http://en.wikipedia.or/wiki/Physical_Address_Extension

---

### Post by alekons on 2008-11-25
Thanks for the reply.
My wonder was why is so big differences between this 2 tools System monitor & TOP. 

As for the memory i read that the 32 bit systems recognize 3 to 3,5 GB but the issue here is that my laptop see only 2.4GB.
for that reason i opened a couple of days ago another thread asking only this but the answer was confusing.

The other thread is here: [http://ubuntuforums.org/showthread.php?t=983418]("http://ubuntuforums.org/showthread.php?t=983418")
Thanks
Alexis

---

### Post by binbash on 2008-11-25
Google > Linux Ram management.Linux's ram management is different then Windows.$free and check +/- buffers.

---

### Post by jjtest on 2008-12-07
As far as why the gui gnome system monitor in Intrepid yields wildly different results than the command-line top command... I ask the same question, but may be able to offer some insight.

It appeared to me, from a side-by-side comparison of "top" and the gui system monitor processes, that the gdm system monitor is completely ignoring the Xorg process itself, which from my top results seems to command a relatively large amount of system resources.

Wondering about that, I looked into some settings for the System Monitor and noticed that, by default, it was only showing My Processes, or the processes spawned by my login... I figured that was the problem so while on the Processes tab, I clicked View and changed My Processes to All Processes. Xorg... and many other processes did show up, but I then clicked on the Resources tab... and it still reports only half the memory being used that "top" does... which is still a mystery to me. 

Unlike the original poster, my System Monitor *does* report the correct amount of total system memory.

I will default to trusting top, as I have been using it for years, and consider a lingering bug or undocumented user error is causing the discrepancy.

---

### Post by amathewk on 2011-10-29
I know this thread is old but it showed up high for me in my search results. This page explains the linux memory usage and disparity you may be seeing in memory monitoring tools.
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Davez69gto on 2012-02-08
Thanks for that last reply.  I was watching top last night while doing processes to spec out an atom board and got a little scared.  I feel much better now, thx!! :D

---

