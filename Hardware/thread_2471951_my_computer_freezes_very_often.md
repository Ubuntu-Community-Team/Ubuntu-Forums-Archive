---
title: "my computer freezes very often"
date: 2022-02-14
forum: Hardware
---

### Post by ronjjjg8885 on 2022-02-14
lately my desktop computer freezes often.
then i've to restart.

i've been told it might be a memory problem
i've 7.7 GiB of memory

i've also heard that i need to make sure that "out of memory killer linux daemon" is enabled.

i'm really not advanced user and wonder what it might be and how to fix.

if you want to see the memory usage please let me also know how to i make some sort of report

thanks

i also want to mention that it occurs mostly when i'm on telegram desktop

but also while surfing the net in firefox

---

### Post by SeijiSensei on 2022-02-14
Do you have a swap file or a dedicated swap partition? If not, I'd start by creating a swap file using these instructions, then reboot.

[https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04/](https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04/)

---

### Post by ronjjjg8885 on 2022-02-15
if i did a regular automatic install should i've the swap partition?

here is a screenshot of my partitions[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290039&stc=1[/IMG]

---

### Post by SeijiSensei on 2022-02-15
Look in /etc/fstab and see if you have a line like this:
```
/swapfile        none            swap    sw       0 0
```
If so, a swapfile was created at installation.  It's unlikely you have a separate swap partition; you would have had to specify this during the installation by choosing the "manual" option during the disk partitioning phase.

You can also monitor your memory usage by opening a terminal window and running the command "top". 

```

top - 16:03:31 up 5 days, 2 min,  1 user,  load average: 0.58, 0.61, 0.58
Tasks: 226 total,   1 running, 225 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.0 us,  0.6 sy,  0.0 ni, 98.1 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15940.0 total,   6906.5 free,   3119.3 used,   5914.2 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.  12421.5 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                               
  72127 seiji     20   0 3783124 676888 214280 S   2.7   4.1  15:52.48 thunderbird                                                                           
  71592 root      20   0  398776  95196  64016 S   2.0   0.6   5:06.24 Xorg                                                                                  
  71913 seiji     20   0   12.7g 937364 267988 S   1.0   5.7  16:27.84 firefox                                                                               
  72133 seiji     20   0  813304 113928  92252 S   0.7   0.7   0:03.44 konsole                                                                               
  76180 seiji     20   0   13244   4232   3356 R   0.7   0.0   0:00.26 top                                                                                   
  [etc.]

```
Linux aggressively caches anything in memory. The available memory is approximately the sum of the free memory and the buff/cache number. Leave the window open as you do other tasks to see how the demands on your system change.

---

### Post by ronjjjg8885 on 2022-02-16
i will soon try to look at fstab
it is already a few days that the freezing didn't occurred but i want to check your suggestion so i will do it soon

i will try your other suggestion too....

thank you for the help

---

### Post by ronjjjg8885 on 2022-02-16
this is the content of fstab[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290044&stc=1[/IMG]


the 'top' command[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290045&stc=1[/IMG]

---

### Post by ronjjjg8885 on 2022-02-24
just to let you know
lately things are just fine with it

---

