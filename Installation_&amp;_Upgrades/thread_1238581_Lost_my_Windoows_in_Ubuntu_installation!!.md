---
title: "Lost my Windoows in Ubuntu installation!!"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by alkooheji on 2009-08-12
Hi,
 
I've tried ubuntu the CD and USB version until I've decided to install it on my windows laptop.
 
When I reached where to install the OS, I've selected "Entire Hard Disk", not knowing that it'll write on the existing OS. 
 
In the next page a warning message appeared telling me that the partition is not empty, but when I pressed "go back" button, a "Format" message appeared even I was reverted back to the previous page!
 
I've tried to stop everything and cancel the installation process, then restart the laptop, but it couldn't find the Windows telling me that there is no bootable sectors on my hard drive!
 
Now, does any one know what happened exactlly? And if I can get my Windows and files back as before!
 
Thank you

---

### Post by Atomic Fusion on 2009-08-12
If it did format, which I would have to assume it did, then yes, all of your hard drive, and everything in it is gone, and never coming back (unless you had a backup).

I'm sorry,
Stephen

---

### Post by lisati on 2009-08-12
If you're lucky just the MBR will have been altered. If you post the output of the following command from the Live CD, we'll be able to tell if Windows is still there and have some idea if it's recoverable:
```
sudo fdisk -l
```

---

### Post by alkooheji on 2009-08-13
Thank you all for your response

> **lisati said:**
> If you're lucky just the MBR will have been altered. If you post the output of the following command from the Live CD, we'll be able to tell if Windows is still there and have some idea if it's recoverable:
```
sudo fdisk -l
```

I've executed the command, and this is the output:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38162   306536233+  83  Linux
/dev/sda2           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris


```Could you please tell me what is going on?

Thank you

---

### Post by mostafa178 on 2009-08-13
I'm not familiar with the fdisk command. But I think that everything is deleted. Someone should confirm this though. Hopefully you have a back up. If not, I'm sorry.

---

### Post by Mark Phelps on 2009-08-14
Appears that MS Windows is gone. You will need to try to recover the files as best you can.  Your best bet (since you can't recover files from a partition to the same drive), is to remove this drive and hook it up to another PC as an external drive.

I'm sure Lisati will get back to you with the details ... as I've tried numerous times to recover MS Windows partitions using Linux utilities and never succeeded.

---

### Post by scottuss on 2009-08-14
Yes you have definitely lost Windows.

If you really really need data on there and you are not confident doing data recovery yourself (I would assume not, no offence!) turn the machine off and take it to a specialist straight away. They may be able to get some of the data back.

The more you use the machine, the less likely you are to retrieve anything.

---

### Post by stlsaint on 2009-08-14
dont worry almost all ppl on this forum have been there one way or another!!

---

### Post by Bucky Ball on 2009-08-14
You have wiped the drive. Always choose "Manual Partitioning" if you have an existing OS you want to keep. 

We live and learn. Sorry to hear of your loss. ;-(

---

### Post by alkooheji on 2009-08-17
I'd like to thank you all for your replays, even the ones were not useful! :P
 
Fortunately, I found an open source software called [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") that as the website says:
 
"help **recover lost partitions** and/or **make non-booting disks bootable again** *when* these symptoms are caused by *faulty software*, certain types of *viruses* or *human error* (such as *accidentally* deleting a Partition Table)."
 
Using this tool, I managed to retrieve the partition D which contains the most of my documents.
 
Regarding drive C, I've tried my best to make it working as before, but I failed. I was able to retrieve the data stored on it using another utility called [Active Boot Disk]("http://www.livecd.com"), it's a Windows based suite that boots from CD drive "like ubuntu live", and has utilities to retrieve files and partitions and many other tools.
 
I hope that you can help others who faces the same problem.

---

### Post by zkriesse on 2009-08-17
Sorry man for your loss of Windows...not that I like it but sorry. And remember....always always always choose manual partition!!!!!!!!!!

---

### Post by presence1960 on 2009-08-17
always back up data. Invest in an external hard disk and keep it powered off and unplugged from USB port except when backing up or restoring data. Always be prepared for the unexpected because at any moment anything can happen. If your data is valuable you will start a backup regimen immediately. 

I have images of all my partitions using PING. I use rsync to do incremental backups to my external hard disk every weekend, When I used windows only I used Norton Ghost. I did what you did the first install of Ubuntu and wiped my windows disk. But the difference was I had a backup scheme in place. 

Don't delay. Start backing up now and do it regularly.

---

### Post by mosgedm1 on 2011-01-16
> **alkooheji said:**
> Hi,I've tried ubuntu the CD and USB version until I've decided to install it on my windows laptop.When I reached where to install the OS, I've selected "Entire Hard Disk", not knowing that it'll write on the existing OS. In the next page a warning message appeared telling me that the partition is not empty, but when I pressed "go back" button, a "[[COLOR=#000000]Format[/COLOR]](http://www.powdershell.com/fr/science-and-technology/increasing-craze-for-online-computer-support.html)" message appeared even I was reverted back to the previous page!I've tried to stop everything and cancel the installation process, then restart the laptop, but it couldn't find the Windows telling me that there is no bootable sectors on my hard drive!Now, does any one know what happened exactlly? And if I can get my Windows and files back as before!Thank youI've got the same problem, It's long, Anybody can answer it?

---

### Post by wilee-nilee on 2011-01-16
> **mosgedm1 said:**
> I've got the same problem, It's long, Anybody can answer it?

So piggy backing on this thread will get you very little help. So start a thread state your problems and do this as well.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This is just common courtesy, if you want help you don't want it attached to another thread that seems similar.:)

---

