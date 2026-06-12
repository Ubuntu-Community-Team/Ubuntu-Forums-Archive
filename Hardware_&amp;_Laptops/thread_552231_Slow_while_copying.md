---
title: "Slow while copying??"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by nesh87 on 2007-09-16
Hey guys,
im not a hardware expert neither am i an OS expert. Im not sure if its supposed to be this way, but when i copy files, large amount of size, my laptop gets really sluggish and slow. It takes a while for it to respond to normal things like launching firefox, and even typing in emesene. Im copying files from my external hard drive onto my laptop (over 10GB i think) and its getting really slow. Oh if it matters im running compiz fusion and AWN.

These are my specs:
Hp Pavilion dv1000
Memory: 1002.5 Mb
Processor: Intel(R) Pentium(R) M processor 2GHz 

with my basic knowledge i think my specs are not bad..

Thanks,
Mohd.

---

### Post by kidders on 2007-09-18
Hi there,

This is one of the things I've always been a little dubious about in Linux ... the almost disproportionately high priority given to I/O. Linux seems to like to perform I/O operations as quickly as possible, which can, in the right circumstances, essentially lock up your machine.

I'm sure you're familiar with the idea that, when asked to do several things at the same time, your computer slices up each task, and interleaves the various processes in a long, linear chain. Your box then performs all the tasks simultaneously, by rapidly switching control of your CPU between them. Now, suppose you are using a calculator (process #1), while copying a 5GiB file from one disk to another (process #2). So, you might end up with something like...[LIST]
[*]Process #1: Multiply 9 by 5.
[*]Process #2: Read 8MiB of data into a buffer.
[*]Process #1: Fetch the answer to "9 times 5", and add 6.
[*]Process #2: Empty a buffer onto a disk.
[*]...
[*]...[/LIST]It should be clear that process #2's slices are far more demanding, since they involve disk I/O, which is extremely slow (at least when compared to the speed with which your processor can access CPU registers). You can see this delay for yourself...[LIST=1]
[*]Run "top" & set the update frequency to something short (eg 1 second) by hitting 'S'.
[*]Do something like **cp ~/a_big_file /tmp**
[*]Keep an eye on the "%wa" figure in top's window.[/LIST]"%wa" is an indication of the amount of CPU time wasted while waiting on I/O operations to complete. Your compiz, for example, may suddenly want to read a setting out of a configuration file. If you're copying something at the same time, your disk buffers will constantly be flushing, which means compiz will actually have to access your hard disk to do it ... which means that no matter when it tries to access its files, it will almost certainly have to wait for a free time slice.

Anyhow, solutions...[LIST]
[*]**If you have multiple disks, use them.** For example, if you are copying a file from a USB device to /home, simultaneously accessing a file in /usr will take longer, if /usr and /home are on the same physical disk. If people *can*, they often like to spread an OS over multiple disks for performance reasons (in part).
[*]**Be mindful of swapping.** Copy operations essentially involve reading chunks of data into RAM, and dumping them back out again. If the RAM being used to do this is, in fact, *virtual* RAM (ie swap space), you will pay a serious performance penalty. Similarly, if something like compiz is swapping while you are copying, and the swap space is on one of the physical devices involved in the copy operation, you will notice performance issues. If your computer does a lot of swapping, you may need to buy more RAM, or re-think your usage habits.
[*]**Don't be afraid of playing with process priorities.** This one requires a little explanation...[/LIST]A process' priority controls the probability that it will have control of the CPU at any given moment. Linux provides utilities (eg "nice" and "renice") to let you manipulate it. When doing so, please bear in mind you should _only ever make small changes_ to a process' priority, unless you really know what you're doing. Large changes very often adversely impact performance.

_**One approach**_
Instead of typing **cp ~/a_big_file /media/usbdisk**, you could try **nice cp ~/a_big_file /media/usbdisk**, thereby lowering the priority of "cp" (adding 10 to it), and any processes it spawns. Although it's certainly worth a try, I don't tend to find this makes a big difference, since copying isn't exactly a CPU guzzler ... it's the I/O that takes up all the time.

[U][B]Another option
[/B][/U]You could try the "Apple" approach. OSX's user interface can take a hell of a lot of punishment before it gets sluggish & starts stuttering. Part of the reason for this is that it always runs with a slightly higher priority than everything else. The result is a performance trade-off between the UI and the rest of the system. Similarly, you may find that your compiz can put up with a little more disk bashing without getting jumpy if you **renice -n -10 compiz**. I *have* found that launching something like compiz with an elevated (ie negative) priority makes it more fluid.

Anyhow, sorry this post is so long-winded. I guess the short version is...[LIST]
[*]Always set your Linux box up well ... something that often requires a little thought.
[*]If you're running complex applications, be sure your computer can handle them. While swapping is a good thing in general, *undesired* swapping is a killer.
[*]_Read the manual first_, and see if you can squeeze a little extra juice out of your box by trying to de-prioritise copying. After all, does it really matter if a copy operation that *could* have been completed in 60 seconds takes 75 instead?[/LIST]I hope something in here helps!

[SIZE=1]**Edit:**

Additional things I forgot to mention ... just for the sake of completion:

The speed of disk I/O is very important, since it essentially dictates how quickly your box can get one process slice out of the way, and move on to the next one. Disk tuning (eg with sdparm or hdparm) may help this happen sooner. Other issues worth consideration are the quality of your motherboard's I/O bus, the size of your disk caches & hardware compatibility.[/SIZE]

---

