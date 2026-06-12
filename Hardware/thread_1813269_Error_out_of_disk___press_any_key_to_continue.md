---
title: "Error: out of disk   press any key to continue"
date: 2011-07-27
forum: Hardware
---

### Post by hakonst on 2011-07-27
Hi
 
I just installed Ubuntu 11.04 on HP Compaq nc6320 laptop (the only OS). I like it but to make it great I am learning on it and clearing some errors out. I am new to UNIX/LINUX. 
 
One of my problems is that I get an error message at start up:
 
error: out of disk
press any key to continue
 
and then I can press any key and the OS starts up. Does anybody has a solution to that small error?
 
Thank you

---

### Post by jerrrys on 2011-07-28
open a terminal and enter:

df -Th

and please post the results

---

### Post by hakonst on 2011-07-28
Thanks for the response jerrye

hakonklara@hakonklara-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    456G  2.9G  430G   1% /
none      devtmpfs    743M  672K  743M   1% /dev
none         tmpfs    750M  1.4M  748M   1% /dev/shm
none         tmpfs    750M   96K  750M   1% /var/run
none         tmpfs    750M     0  750M   0% /var/lock
hakonklara@hakonklara-laptop:~$ 


My problem has changed a little since I posted the tread - I had to reinstall the OS, (2x), first I got a message Error: out of disk
Grub: rescue

and then I was stuck

I then installed again with small changes and now I get:
error: out of disk
error: no suitable mode found
error: no video mode activated

and then after a while the OS loads and it seams ok

but I still have the out of disk error and the results from the command df -Th is:

hakonklara@hakonklara-laptop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    456G  2.9G  430G   1% /
none      devtmpfs    743M  672K  743M   1% /dev
none         tmpfs    750M  1.4M  748M   1% /dev/shm
none         tmpfs    750M   96K  750M   1% /var/run
none         tmpfs    750M     0  750M   0% /var/lock
hakonklara@hakonklara-laptop:~$

what do you think?

thanks,
Hákon

---

### Post by jerrrys on 2011-07-28
i have ran across this type of behavior three time in the pass.

i once was trying to do an install on a dv6000 and kept ending up with unexplainable and changing errors.  come to find out this unit had a heat buildup problem and once it got hot (not hot enough to shutdown), it would install with errors (and not always the same errors).  i found out on this unit, that if i did the install as soon as i turned it on (while its cold), it would install without problem.  but if i tried ti do a dual install immediately after the first install, it would fail. 

another thing that will give you grief, is burning data disk at high speed (auto mode).  you can do a check disk at end of burn and you will get a green light, all is well, but its really not. i do my data burns at 4 to 6x and for me that works.

another thing is the cd itself.  i use cheap cd's.  50 for $8.00.  with cheap cd's you can end up with a bad batch and once again can give you weird results.  i still use cheap cd's.  i have not had a problem with "imation cd-r" (a brand name) and they cost $9.00 for 50 cd's.  they can be bought at "bestbuy"

and one last thought.  maybe your cd has a few scratches on it that could cause this behavior.

whats your thoughts on this?

EDIT:  forgot one thing. /dev/sda1     ext4    456G  2.9G  430G   1% /

those numbers don't add up.  while you have ubuntu up and running.  go to:

System>administration>disk utility and see what it says about sda1

---

### Post by hakonst on 2011-07-29
Thanks for the response

My laptop gets quite hot so that is maby a possibility, also my CD was burned ad high speed. 

I also was not shore what to set in the partition manager in the installation, but 2 times I used full automation in installation of Ubuntu, both times I got the error: out of disk - grub rescue, and then I was totally stop and had to reinstall.

I'm burining new installation CD which I will use to reinstall one more time...

I will post the results when done.

---

### Post by jerrrys on 2011-07-29
good luck

---

### Post by hakonst on 2011-07-29
Now I have gotten rid of the errors :)

I tried a new slow written CD and keeping the laptop cooler but that didn't work - in my first try the OS didnt load - it stopped on Error: out of disk - Grub: rescue

so I installed again and then I was able to load the OS but with the errors:
error: out of disk
error: no suitable mode found
error: no video mode activated

I recently replaced an older 80 GB hard drive with a 500 gig and when I did - I wasn't shore if it the computer would read it - but it did and I was able to install windows 7 - which crashed 2x (cracked version). I had read that the laptop would max take 120 gb hard drive so I was careful when I bought it that the computer would read it...

at least - I changed back to the 80 gig HD and then the errors were out of the history...
Which is good -but it is worse that I cant use the 500 gig HD... does anybody has a suggestion for that problem?

Thanks,
Hákon

---

### Post by jerrrys on 2011-07-29
pretty much all hdd's these day work on ubuntu.  what do you have?

---

### Post by hakonst on 2011-07-29
Its a Seagate Momentus 5400.6 500 GB...

---

### Post by jerrrys on 2011-07-29
did you have to change pin settings on the back of the 500G drive to master?

---

### Post by hakonst on 2011-07-29
Its a SATA drive- don't think I have the possibility do define it slave or master... is it?

---

### Post by jerrrys on 2011-07-29
my mistake, i wasn't thinking laptops

---

### Post by jerrrys on 2011-07-29
ok, this is more of a fishing trip, but is there any possibility of a needed change in BIOS.  and while you check it out im going to go google.

---

### Post by drs305 on 2011-07-29
Your BIOS may only recognizing the first 137GB of the drive. This is often the cause of Grub 2 'out of disk' errors on older computers.

You can check the reported drive size in your BIOS (enter setup during boot) and if it is either 8GB or 137GB (approximately) it means the BIOS is causing the problem.

Once a system boots, modern OS's can see the entire drive. But to boot, all your boot files must be within the part of the drive the BIOS can see.

Your options are to enable the large drive option in BIOS (if available), update the BIOS, or make sure your boot files are within the part of the drive seen by BIOS. You can do the latter by keeping the entire Ubuntu installation within the BIOS limit or create a separate /boot partition therein.

---

### Post by jerrrys on 2011-07-29
thank you drs305, i wasn't finding anything of value

---

### Post by thalant on 2011-12-06
I create an account just to reply the post number 14 to say that this is the explanation to the problem and bty the solutions also,
Brilliant,
Thank you very much
Seb

---

### Post by drs305 on 2011-12-06
> **thalant said:**
> I create an account just to reply the post number 14 to say that this is the explanation to the problem and bty the solutions also,
Brilliant,
Thank you very much
Seb

thalant,

Well thank you for joining the Ubuntu Forums. You can learn a lot from other members here. 

If you a are a new Ubuntu user, it won't be long before you will be able to help others with their problems.

Don't be a stranger!

Happy Ubuntu-ing !

---

