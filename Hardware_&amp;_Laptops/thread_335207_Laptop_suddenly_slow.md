---
title: "Laptop suddenly slow"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by sonoftheclayr on 2007-01-10
I have searched the forums but found nothing relevant to me.

My crappy 800MHz P3 satellite 1800 with 128MB RAM (I don't have all the specs at the moment) is running crappier than ever. Up until last night it was running fine and I had spent the day trying to get GRUB to boot SymphonyOS but to no avail.

As far as I can tell it only runs slow when I run Firefox or aMSN as they are the only ones I have tried to run before I get frustrated and cut the power.

First some information. I am running Edgy Eft with the Xfce Desktop Environment and so far have stopped Xfce loading the previous session when I log on as I thought it might have something to do with that.

Anyway, I clicked the Firefox button about 10 minutes ago. The button depressed and popped out again, the cursor changed to show it was busy, firefox-sh showed up in the task manager using only 10% of the CPU at top (the task manager uses more!???).

And that is all.

That was about 10 minutes ago and the only thing of note that has happened is the screensaver coming on and not doing anything, just remaining a black screen. I can't even get out of it! Last I checked firefox-sh was using a small amount of CPU (0.0% according to task manager) and still nothing happens. The furthest I got was without task-manager and the main window popped up with the Stumble upon toolbar neatly tucking itself away and the SU icon larger than the rest and making itself smaller as per usual.

The same happens with aMSN. It loads up shows a small window before it maximizes itself and only has half the screen initialized and stays that way.

I'm really desperate for any help and soon! I've nearly hit the laptop already (my big brother who I got the laptop off did that once and had to get the hard disk replaced).

---

### Post by SoggyCornflake on 2007-01-10
> **sonoftheclayr said:**
> My crappy 800MHz P3 satellite 1800 with 128MB RAM (I don't have all the specs at the moment) is running crappier than ever. Up until last night it was running fine and I had spent the day trying to get GRUB to boot SymphonyOS but to no avail.


Just a shot in the dark here, but maybe your memory is hitting the max amount and so the kernel is having to move stuff to the swap partition/file.  That would really slow down your laptop.  To check that try running a terminal session and running "top" (so some other memory monitoring program.  If you see a lot of swap disk activity when you start to notice the unit slowing down, then that would confirm that theory.  (Extra RAM is a PC/Laptop's best cure for slow response.)

By the way, I used to work at a company that made laptops.  They strongly discouraged screen savers since they chew up battery life and memory space.

---

### Post by sonoftheclayr on 2007-01-10
Okay here is what I got on the memory:

118076k total
93016k used
25032k free
2500k buffers

I obviously need some more

57 total running processes, 2 running and 55 sleeping.

I think I should mention this was at the kdm login screen and I was only running that and top.

Odd thing, though, I know there is swap space on the hard disk but I got 0k for total, used and free on the swap and 56010k cached. It would appear I have been using the swap and while I was meddling around yesterday I must have disabled it or wiped it or something.

That leaves the question: how do I get working again?

---

### Post by SoggyCornflake on 2007-01-10
> Odd thing, though, I know there is swap space on the hard disk but I got 0k for total, used and free on the swap and 56010k cached. It would appear I have been using the swap and while I was meddling around yesterday I must have disabled it or wiped it or something.

That leaves the question: how do I get working again?
Reply With Quote 
First check that your swap partition is mounted,   You can check it by typing 

```
cat /etc/fstab
```

Mine looks like this:> /dev/hda5 -- converted during upgrade to edgy
UUID=8ee4dc5e-2b14-4a12-9173-8c353cce8bfe none swap sw 0 0


---

### Post by sonoftheclayr on 2007-01-10
Mine says exactly the same only with a different UUID.
EDIT: I didn't notice this the first time *hits myself on the head** but there is a # before the entry

---

### Post by SoggyCornflake on 2007-01-10
> **sonoftheclayr said:**
> EDIT: I didn't notice this the first time *hits myself on the head** but there is a # before the entry

I think that a # is a character indicator.  Try deleting the character and rebooting.  then recheck your swap memory.

---

### Post by sonoftheclayr on 2007-01-10
I got my swap back by using mkswap and swapon but it required a bit of repartitioning to get it working and it wou't start up at boot. I know I should really write a startup script but if anyone has any ideas or if there is already one that I have to modify.

---

