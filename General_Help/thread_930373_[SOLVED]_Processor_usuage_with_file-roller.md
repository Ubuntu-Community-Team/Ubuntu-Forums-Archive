---
title: "[SOLVED] Processor usuage with file-roller"
date: 2008-09-26
forum: General Help
---

### Post by DeMus on 2008-09-26
Hi,
Whenever I want to extract files from a series of RAR files, I notice that my computer uses about 25% of the CPU, meaning 1 of the 4 cpu's of the Intel Q6600. I would think the other 3 are available for other duties but the system responds very slow to whatever I want to do at the same time. Isn't it so that when 1 cpu is taken by a process, the others are used when there is need for another process?
Is there a way to change that. I mean I have a nice computer but at times it is like I work on an old 386.

DeMus

---

### Post by DeMus on 2008-09-27
> **DeMus said:**
> Hi,
Whenever I want to extract files from a series of RAR files, I notice that my computer uses about 25% of the CPU, meaning 1 of the 4 cpu's of the Intel Q6600. I would think the other 3 are available for other duties but the system responds very slow to whatever I want to do at the same time. Isn't it so that when 1 cpu is taken by a process, the others are used when there is need for another process?
Is there a way to change that. I mean I have a nice computer but at times it is like I work on an old 386.

DeMus

Somebody, please help. Is there anything I can change in a setting somewhere to make the processor become more active?
Every help is appreciated.

DeMus

---

### Post by Zeedok on 2008-10-18
I've noticed this when creating archives as well.  Sorry I don't have a solution, but hopefully if people keep adding 'Me too' then a bright spark will offer a fix - or at least an explanation.

---

### Post by trazart on 2008-10-18
I dont have a dual core CPU, just Athlon XP and when i'm extracting a file it eats also about 25% of my CPU. But the system is extremely slow.

---

### Post by niteshifter on 2008-10-18
Hi,

The nice and renice commands can be used to adjust priority of a process from the command line:
```
man nice
man renice
```

You can also use the System Monitor application / applet: locate the task - for file-roller look for tar, unrar, bzip, etc. - in the Processes tab that's eating to much CPU, right click on Change Priority and give it a larger positive number to reduce the amount of CPU it's using.

---

### Post by Zeedok on 2008-10-18
Thanks for the suggestion. Changing priority from System monitor looks simple enough.

I guess I would need to enter System monitor (or go to the command line) every time I create an archive?

You don't happen to know _why_ fileroller uses up so much of the system resources?? Or how to always give it a lower priority (by default)?

Thanks again for your interest.

---

### Post by niteshifter on 2008-10-18
Hi,

You can place System Monitor on a GNOME panel: Right click on the desired panel, click on Add to Panel, int the dialog that appears scroll down to System and Hardware, click on System Monitor, click the Add button, click the Close button. Voila - System Monitor parked out where it's easily accessible for those once-in-a-while tasks that eat CPU. Or are hung and need to be ended (but be careful with that).

For something like file-roller which you know eats CPU, edit it's launcher:
System > Preferences > Main Menu. On my system it's in Accessories, named Archive Manager. Right click on that and click Properties. Edit the entry by the text **Command** to be:
```
nice -n 10 file-roller %U
```
and file-roller (and tar / zip / gzip / bzip2 / unrar - whatever "tool" file-roller is to use) will run at lower priority. Experiment a bit with this as the effects vary depending on hardware.

As to why: compression / expansion programs are what are called "compute bound" or "compute intensive", there's a considerable amount of math being performed on the data. This is what the CPU does - math. This is in contrast to the tar program, it's "I/O bound". tar - by itself - just (more-or-less) opens a file and copies the files supplied to it into that file (each file preceded by a header block), the CPU doesn't have all that much to do here. It's like recording to tape (sequential storage) - indeed "tar" is shorthand for **t**ape **ar**chive, the reason for it's creation way back last century ;)

So changing the "niceness" for tar - alone, no compression / expansion programs being run - will most likely not get you any system speedup: it's not the CPU that other processes are waiting on, it would be I/O but for the outstanding efficiency of the Linux kernel and device input-output methods like Direct Memory Access (DMA), PCI, and internal buffering RAM in modern disk drives.

---

### Post by Zeedok on 2008-10-18
> For something like file-roller which you know eats CPU, edit it's launcher:
System > Preferences > Main Menu. On my system it's in Accessories, named Archive Manager. Right click on that and click Properties. Edit the entry by the text Command to be:

Awesome.  Works brilliantly. Thanks.

Hey DeMus - Edit your first post with a SOLVED in the title, so others can find it easily.

---

### Post by DeMus on 2008-10-23
> **Zeedok said:**
> Awesome.  Works brilliantly. Thanks.

Hey DeMus - Edit your first post with a SOLVED in the title, so others can find it easily.

Well, it's not solved yet. I started this thread with the text that Fileroller uses about 25% of the CPU, leaving 75% free. Still the PC has become very slow even though 75% of the CPU is still available. It seems these 75% are not used at all.
Anybody an answer to this?

De Mus

---

### Post by trazart on 2008-10-25
I would say the problem is not the CPU but the hard drive. I think the use of the hard drive is so intensive that it is bottlenecking the whole system.

Unfortunately I dont know how to solve this.

---

