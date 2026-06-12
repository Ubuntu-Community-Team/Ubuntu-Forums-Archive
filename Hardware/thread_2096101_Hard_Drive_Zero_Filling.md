---
title: "Hard Drive Zero Filling"
date: 2012-12-19
forum: Hardware
---

### Post by swagatopablo on 2012-12-19
I was trying to install Ubuntu and there were some error with my hard drive. I decided to zero fill my hard drive while running Ubuntu 12.10 live from a USB stick. I entered the command
 ```

sudo dd if=/dev/zero of=/dev/sda bs=1M

```because this is what I found after some online searching. While I have absolutely no idea what individual parts of the code mean, I was under the impression that this will perform a low level formatting. The code didn't give any error, but it has been more than 12 hours, since it started. I don't know what's going on or how far it has progressed. Is it normal? I am relatively new to linux and will be grateful if answered in a non-technical way. I have Intel i5 processor, 4 GB DDR2 RAM and 500 Gig SATA HDD.

---

### Post by SlugSlug on 2012-12-19
dd is painfully slow and normally used to clone or destroy data (normally /dev/random not /dev/zero for security purposes).


For normal use / format  use the disk utility or gparted - it's much quicker ;)

---

### Post by hanzukun on 2012-12-19
If you look in the manual for dd, ('man dd' in the terminal), there is an example to get statistics while running. For your case, you should write: 
```

kill -USR1 PID

```
where you exchange PID to the process id of dd. That is, if you look in System Monitor or top (in terminal) you will see the pid.
You can also type ctrl+z in same terminal as you are running dd to pause it. Then type [FONT="Courier New"]ps[/FONT] to get the pids in the actual terminal window. Then you can continue by typing [FONT="Courier New"]bg[/FONT] (BackGround), which puts the process in the background. You now know the pid and you can run the command I typed at the top of this post.

For the other question, the meaning of your command is:
[FONT="Courier New"]sudo[/FONT] Run the following command as superuser (usually normal users are not allowed to modify the disks!)
[FONT="Courier New"]dd[/FONT] The program to run
[FONT="Courier New"]if=/dev/zero[/FONT] "if" stands for input file, in this case the special files that prints zeros
[FONT="Courier New"]of=/dev/sda[/FONT] "of" stands for output file
[FONT="Courier New"]bs=1M[/FONT] this option tells dd how many bytes it should read from "if" into memory before writing it to "of".

The parameter types of dd is quite different to other command programs, ie if=/dev/zero instead of more common -f /dev/zero or something like that.

---

### Post by Grenage on 2012-12-19
Top tip, you can also use *killall*, so you don't have to manually look for the PID:

```
killall -USR1 dd
```

Increasing the BS will also help speed things up, 4096 is a good number.

---

### Post by swagatopablo on 2012-12-19
Thank you everybody for the helps. I have used 
```

sudo killall -USR1 dd

```
since it was not working without invoking sudo and it says 189GB done out of 500 GB. That's pretty slow, I must say with more than 36 hours. But in any case, I was not able to resume the process or not sure whether my command killed the process entirely. So I have entered 
```

sudo dd if=/dev/zero of=/dev/sda bs=4096

```
and it started again. Now please tell me whether whatever was done in past 36 hours is wasted and this time it will begin from the scratch again?

---

### Post by ahallubuntu on 2012-12-19
~

---

### Post by Grenage on 2012-12-20
> **swagatopablo said:**
> and it started again. Now please tell me whether whatever was done in past 36 hours is wasted and this time it will begin from the scratch again?

Alas, it starts from the very beginning, unless you stipulate from where it should begin.  Bear in mind that the slower speeds are likely down to the existing drive errors you mentioned.

---

### Post by soori007 on 2013-06-01
Very Useful One.. I had two of my laptops zero filled with the sudo dd command. Thank You.

---

