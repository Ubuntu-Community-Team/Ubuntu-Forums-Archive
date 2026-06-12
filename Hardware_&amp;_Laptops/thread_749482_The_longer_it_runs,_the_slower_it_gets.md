---
title: "The longer it runs, the slower it gets"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by ag65151 on 2008-04-08
The longer my laptop is running, the slower it gets. If I leave it on overnight, it is so slow it takes me 5 minutes just to shut it down. Once shut down and restarted, it runs fine and fast. I would not consider myself a n00b, but I can't figure what is consuming all the resources. When it slows down so much, top shows high percentages of %WA, which I am pretty sure means wait I/O. And the hard disk light is on constantly as well.

My question, is there a process that is known to use more and more I/O as the session time goes on. I have a feeling it is a memory leak that is causing huge swaps, but I am unsure as to where to look to confirm. Any help would be appreciated.



My specs:
HP-ZE5500 P4, 2.66GHZ laptop. 
ATI-IGP340M video
512 MB RAM
40GB hard drive
           / partition 5GB
           /home partition 33GB
           /swap 2GB
Ubuntu Gutsy 7.10 - all updates applied

---

### Post by ag65151 on 2008-04-11
Bump.

Am I the only one who has this problem?

---

### Post by sdennie on 2008-04-11
It does sound like a program with a memory leak.  You could check this theory by typing "top" in a terminal.  Once you have that up, you should be able to sort the processes based on memory usage by hitting 'F', 'n' and then Enter.

---

### Post by ag65151 on 2008-04-12
Thank you for the reply. 

The first two in top (F n) are FireFox and Xorg. I have already began closing FireFox when I am not using it and it seems to help a little bit.

The best solution I have is to shutdown my computer every night and start it back up in the morning. I remember when we used to post on these forums how long we had gone without a restart and now I have to do it daily. Kind of sad, really. 

Anyway, are there any known issues with FireFox or Xorg that they have memory leaks?

---

### Post by ZALMAN on 2008-04-12
You should not have to shut down your laptop to regain speed, I have machines that run for weeks and months before I do restarts. Have you tested you physical memory, might be bad mem, or have you upgraded your memory and its not running at its proper speed / or mismatch?

---

### Post by Saint Angeles on 2008-04-12
would this be firefox 2?

there is a known memory leak. it is fixed in firefox 3.

---

### Post by tgalati4 on 2008-04-12
>sudo apt-get install htop
>htop

---

### Post by ag65151 on 2008-04-12
Yes, it is Firefox 2.  I have tried Firefox 3 and it maxes out my CPU. Of course, that was a while ago. Have those issues been resolved? Is there a new version in the repos above what I have? I think I am on the bottom end of machines.

I haven't tested my memory, but I also have not changed anything with regard to hardware for at least 6 months. I also think it is Firefox 2.

Thanks for all the input.

By the way tgalati4: I am a bit paranoid, but what would htop get me that I don't have with just top?

---

### Post by sdennie on 2008-04-12
If you are using an older machine, it's possible that dma isn't enabled on your disk and so some disk intensive background program like updatedb is just taking forever to run and more or less bringing your computer to it's knees.  You may want to look into the hdparm command.  A possible fix would be to try:

```

sudo hdparm /dev/hda

```

But, I would google for information about hdparm before trying it out.

---

