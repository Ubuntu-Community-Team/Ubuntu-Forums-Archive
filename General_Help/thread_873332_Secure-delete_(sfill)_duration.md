---
title: "Secure-delete (sfill) duration?"
date: 2008-07-28
forum: General Help
---

### Post by dontodd on 2008-07-28
Hardy.

I thought I'd try to wipe the free space on my /home using sfill from the secure-delete package. It's still running after 24 hours, and my /home is completely full. I probably had about 80 GB free when I started. sfill continues to eat 60-85% of CPU, though load average is still pretty low.

Is it normal for sfill to take so long to finish, or should I start getting concerned? What happens if I interrupt the process (ctrl-c)? Will my system revert to having the free space I had before I started?

I read about scrub creating a junk file. I looked for something similar with sfill but didn't find it. In fact, it's hard to find much on sfill at all.

Thanks,

Todd

---

### Post by dontodd on 2008-07-29
Just to follow up, the process finally completed. It took around 36 hours to wipe 30-odd GB of hard drive space. I didn't interrupt the process so I don't know what effect that would have had, but I've got my free space back now.

---

### Post by jaygo on 2008-08-19
thanks for the follow up. I'm waiting on it to finish a 750GB drive ... according to your results, It'll take about 35 days straight. What I don't get is that there's hardly any disk activity -- according to the HD light and the noise -- but CPU is constant at around 100% for one core.

I'm going to find a better/faster (windows) utility for now.

---

### Post by bsantos on 2008-08-29
Do you understand what sfill does? ;)

It creates a file that will occupy all your free space, fills it up with random data various times and then deletes the file (it will do so safely if you cancel the process in the middle).

I don't know how it acquires the default 38 passes (if they're done on the way or all the way, didn't research that) but writing data (even if random) 38 times on those disks will take the time it would take to write any data. So you have to calculate the time by knowing the writing speed of your disks and how much space they have left.

Check the docs:

[http://www.mirrors.wiretapped.net/security/host-security/secure-deletion/secure-delete/secure-delete-README.txt](http://www.mirrors.wiretapped.net/security/host-security/secure-deletion/secure-delete/secure-delete-README.txt)



Faster will mean less thorough, and in the end, less safe.

Cheers! :-)

---

### Post by jaygo on 2008-12-27
I found another way to handle the 750gb drive - using the inbuilt secure delete function (ATA spec). I wasn't able to access it from the boot CD that's floating around the web because it doesn't handle SATA drives, or most of them. However, from the good old linux console I found it using hdparm, and it only took about 1.5 hours to securely wipe that 750 gigs. 

Unfortunately, all four of my 320gb Seagates do NOT support the secure erase function that is supposed to be built into newer drives. So I'm going to have to pull them out of my RAID array and sfill them one at a time, for a couple of days each. 

I did sfill one of the 320gb Seagates a few months ago. I let it run for about 8 passes then ran some data recovery software on it. It found some files - I don't recall if they were genuine file names or random - but they were all unreadable and scrambled. The drive was previously formatted as ext3.

---

### Post by ptruchon on 2009-01-04
I started running the default 38 passes on my 5GB of free space:

```
sudo sfill /
```

and gave up halfway through.  The file /00000000.000 was only a few MB big while I had lost a few GB of free space by interrupting the process.  Was there another file written somewhere else?  I then reran sfill with only two passes

```
sudo sfill -l /
```

and all my free space came right back at the beginning of the process.  So it seems that interrupting doesn't recover the space, but restarting does.  So if one needed to interrupt the process, maybe rerunning it in insecure mode would recover the space?

```
sudo sfill -f /
```
(I didn't try that though)

---

### Post by dracayr on 2009-04-07
Well I interrupted it (using "killall sfill"), and it said something like "clean exit", and gave back the disk space.

dracayr

---

### Post by bsantos on 2009-04-07
> **dracayr said:**
> Well I interrupted it (using "killall sfill"), and it said something like "clean exit", and gave back the disk space.

dracayr

Yup, it dereferences the file it created for cleanup.

When the process is all done you also get the disk space back, it just takes too long. :-)

---

### Post by Tankerdog2002 on 2009-07-05
What to do after secure-delete corrupts your drive?

I used this secure-delete command on a New Dell Vostro with a 140 GB drive running hardy: 

sudo sfill -v / 

After three days I only had 15 passes...we had a power outage and after that my machine would not boot. Got the GRUB but nothing after that.

I solved this by using the "fsck" command, under root in read-only mode. This corrected all bad sectors and inodes. Everything is fixed and running fine now.

Please remember that once you start the process, don't interrupt it. 

Hope this helps someone.

Tank

---

### Post by bsantos on 2009-07-05
> **Tankerdog2002 said:**
> What to do after secure-delete corrupts your drive?

I used this secure-delete command on a New Dell Vostro with a 140 GB drive running hardy: 

sudo sfill -v / 

After three days I only had 15 passes...we had a power outage and after that my machine would not boot. Got the GRUB but nothing after that.

I solved this by using the "fsck" command, under root in read-only mode. This corrected all bad sectors and inodes. Everything is fixed and running fine now.

Please remember that once you start the process, don't interrupt it. 

Hope this helps someone.

Tank

Hi Tank, I'd say that 15 passes is overkill, unless you're preparing drives with sensible data to sell or give away. I've read a couple of discussions on recoverability of data after 1 or 2 passes and it is very difficult and requires very advanced equipment to recover data after those, so you'd be safe with it.

The failure you had would probably leave your partition full (all inodes referenced) and some inconsistency between written data and referenced inodes. You may have stuff in lost+found that resulted from the work of fsck, probably data from the sfill files.

If you interrupt it correctly it shouldn't make any damage, maybe leave the data files behind. The problem you had was because the power failure left data in the disk cache/buffer that wasn't written to the platters or something like that. That doesn't happen if you interrupt the program. The operating system will be able to finish writting data to the disk or delete the files normally and the file system should continue to be sane.

Hope you didn't lose any file though!

---

### Post by desmane on 2009-07-11
after completely overwrite your data once it gets super difficult to recover any data.. sfill -l does two times and should be alright. The 38x overwriting thing is a myth. 

> [...]The study concludes that after a single overwrite of hard drive data, the likelihood of being able to reconstruct a single byte is 0.97 percent.  The odds of recovering multiple sequential bytes of data (such as a password or document) are significantly less and would require exact knowledge of where on the hard drive the sensitive data is located.

[http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)




--

another thing, "sfill /" will erase free disk space on every mounted device, right?

i got like a lot of drives and partitions, my home is on sdb2 and so on and need to be sure that it will work? thx

---

### Post by bsantos on 2009-07-11
> **desmane said:**
> after completely overwrite your data once it gets super difficult to recover any data.. sfill -l does two times and should be alright. The 38x overwriting thing is a myth.

Yup



> **desmane said:**
>  another thing, "sfill /" will erase free disk space on every mounted device, right?

i got like a lot of drives and partitions, my home is on sdb2 and so on and need to be sure that it will work? thx

I assume it only works on the /  partition. You'd have to run it on a directory belonging to each partition you want to wipe. Since sfill works by creating a file and writing data in it, it will fill the current partition, just like it would happen when you create any file in any partition that won't fill the space of your other partitions.

In Windows each partition has a logical drive associated with it. In unix based OSs you can associate a file system directory to a partition, making it easier to organize your files and making it more seamless than using different logical drives (you can mount a partition under your home folder just for your photos or videos, for example).

As an example, using zfs (or one of the new file systems coming to Linux that I haven't yet read about their features) you can add all your drives to a pool of disk space and partition that pool as needed. The kernel will manage the disk space to those partitions regarding some rules but in a transparent way to the user. In this example, using sfill on one of the virtual partitions, if it was configured to be able to allocate 100% available disk space, you'd fill all the disks in the pool seamlessly. That also makes it easier to manage disk space among partitions, and I believe it also supports mirroring or at least some kind of way to support hard drive failures, but I don't know much about it.

Cheers! :-)

---

### Post by desmane on 2009-07-11
> I assume it only works on the / partition. You'd have to run it on a directory belonging to [...] won't fill the space of your other partitions.

Well, that makes sense! I'll do sfill for any individual partition then. It's quite fast. Thanks for your explanation.

zfs sounds a bit like a software raid.. sounds great. nice feature. but. well. no ;-)

---

### Post by bsantos on 2009-07-11
> **desmane said:**
> Well, that makes sense! I'll do sfill for any individual partition then. It's quite fast. Thanks for your explanation.

zfs sounds a bit like a software raid.. sounds great. nice feature. but. well. no ;-)

No problem! ;)

zfs is much more than that. It's a file system that works like an abstraction layer above disks. I think you can attach disks outside your machine (NAS and disk arrays using other technologies) to that pool and everything, It has performance monitoring and much more than I know about. I saw a lecture from a SUN developer some years ago about it and it is pretty cool. It must do much more by now and in a more stable way. Too bad it isn't available on Linux IIRC due too licensing or patent issues. :roll:

Cheers! :-)

---

### Post by Tankerdog2002 on 2009-08-15
Hey there bsantos!

Thanks for the tip buddy.

Can I stop the process after about 7 runs with the "killall sfill" command and still maintain the integrity of that 7-wipe process?

Sorry.....I'm a Noob in regards to Secure-Delete sfill. Never used it before.....but I glad we have such nice programs for Ubuntu.

Tank

---

### Post by michy99 on 2009-08-15
You can stop sfill with Ctrl+C and it will make a clean exit.

---

### Post by bsantos on 2009-08-15
Yes, using Ctrl-C is preferable, but killall sends a SIGTERM signal by default and sfill does a clean exit when receiving it. So either way will work. :-)

---

### Post by matteorinaudo on 2010-01-18
> **bsantos said:**
> Yup, it dereferences the file it created for cleanup.

When the process is all done you also get the disk space back, it just takes too long. :-)
That is correct, `*killall*' is the way to go. Here's my output:

[B]# sfill -v -z /
Using /dev/urandom for random input.
Wipe mode is secure (38 special passes)
Wiping now ...
Creating /oooooooo.ooo ... *
[/B][*on another root console: # killall sfill*]
[B]Terminated by signal. Clean exit.
#
[/B]
After a few minutes, the huge file previously created will be all dereferenced.

---

### Post by no.human.being on 2010-11-11
Obviously, "sfill" creates a file named "oooooooo.ooo" and writes loads of "ff ff ff ..." bytes into it (you can verify this by typing "tail oooooooo.ooo | hexdump" into the shell, while "sfill" is running). However, it takes **several hours** of time for writing a few hundred megabytes to the disk (you can monitor the size of the "oooooooo.ooo" file using "ls -l" on the shell).

When I do something like "dd if=/dev/urandom of=somefile" on the console, it writes about 10 gigabytes per hour on average. When the partition is empty, it starts out with about 20 gigabytes per second, but gets slower as space on the file system gets scarce and the last few gigabytes take like forever. This is on an encrypted partition, so the system will actually have to encrypt the random numbers "dd" is writing before they actually reach the disk. The "dd" method is hundreds of times faster than "sfill", but produces significantly lower hard drive activity (when using "dd", the hard drive is hardly ever working, while it will be very busy while "sfill" is working).

Now the question is: What's so special about "sfill" and why is it **that** slow? Why would one need such a utility if every GNU/Linux system comes with "dd"? Is the "dd"ing method less secure than a single pass of "sfill"? If so, why? Where can I get the source code of "sfill", if I want to investigate this further?

Thanks in advance for your information.

**EDIT:** If you are using the options "oflag=dsync" and "bs=4M", your overwrite will be more secure (because of the "flag=dsync", which will cause the disk to cause an immediate write without buffering the data in a cache, so you can guarantee that data actually reaches the disk - I guess the use without dsync doesn't make it THAT much less secure since the write cache of the disk will usually be only a few KB or MB and data will eventually reach the disk, at least when the cache is full - and since it cannot hold very much data, it will usually become full very quick) and much faster (because of the "bs=4M", which will cause dd to write the data in 4 MB blocks rather than individual bytes). So now the dd method is much much faster than it already was. Where's the purpose in sfill and why is it rediculously slow?

---

