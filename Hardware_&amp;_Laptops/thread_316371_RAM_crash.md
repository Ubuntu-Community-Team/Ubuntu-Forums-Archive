---
title: "RAM crash"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by ScottMorris on 2006-12-10
Hey there, recently I have been experiencing memory management problems with random programs.  The problem is when I choose to do something it will start processing my command but then doesn't stop.  The OS gets very slow and after  what seems forever (between 10 min to 1 hr) it stops what it is doing with the program and kills it saying out of memory.  This has happened most with The Gimp and Wine.  In the Gimp, if I try to add an effect it starts on this memory filling loop and then the filter crashes.  With Wine, I try to open a program and it does the same thing (Wine always takes forever to negotiate out the problem) and the program I try to opens disappears.  In tty1 it has a message the explorer.exe and the program I was opening were killed due to memory usage.  This same thing has also happened with aMSN, Firefox, the System Monitor.  What can I do to remedy this problem?  Is it just a setting that has been corrupted and needs changing or is it more extreme?  Thanks for your help in advance.

---

### Post by zgornel on 2006-12-11
Have you tried memtest86 ? Try running it at boot and run some extensive tets. If it does report errors you know for sure that the memory is damaged and in this case the only solution is for it to be replaced. If it does not report and errors you might still be having memory problems. Rerun it 2-3 times to be sure. Also, try some windows games (in Windows :D ), or 3DMark - these usually fail if there are memory problems.

---

### Post by ScottMorris on 2006-12-11
I don't think its a RAM problem exactly, I think it has something to do with the software.  I have a tendency to open many programs in Windows and use all my RAM and there is no problems (except that Windows swap sucks) but it runs as Windows runs.  It seems that Ubuntu's memory management is having troubles managing and allowing the programs to leak.

---

### Post by zgornel on 2006-12-11
I seriously doubt that. Linux memory management is excellent and I never had problems with loads of things opened on a 512 mb system. Search the logs for abnormal messages.

---

### Post by ScottMorris on 2006-12-13
I believe that.  This is the first memory issue I have had with Linux (unlike Windows) and I do believe it is the programs that are causing the problem, but I don't understand why.  It is really weird.  I will look though the logs though :P

---

### Post by ScottMorris on 2006-12-16
I ran Memtest86+ and it found no hardware errors.  What kind of thing would I be looking for in the Log files that signify abnormal behavior?

---

### Post by stewakb on 2006-12-28
i am having the same issue.  Ubuntu is not freeing up memory after a program is closed and it slowly fills untill it errors and resets. This is happening on my server and i had to reinstall twice as the first two times it brought the system to a crawl. i have run memtest and nothing as this computer used to my xp box and ran games etc fine. it is now a server and i have the system monitor running watching how it does. Things started happening after i did the last batch of updates which included a kernel update.

Any suggestions would be appreciated.

Thanks

Kevin

---

### Post by ScottMorris on 2006-12-28
For your server are you using a GUI or a CUI?  What programs are you using at the time of the problem, maybe there is a common program that is doing this.  I have not updated my kernel to the latest so I'm not sure if it is that or not.  You say you reinstalled it twice, did you upgrade the Kernel each install or did it do it out of the box? What kind of server is it? SMB FTP HTTP etc.

---

