---
title: "T43 Suspend/Hibernate: Help me find a solution."
date: 2011-02-04
forum: Hardware
---

### Post by Cloudform on 2011-02-04
I found a solution.  See next post
[B]
tldr; is there any way to access a log to see what module/etc keeps waking my computer up from suspend?[/B]

Edit: I think (but am not completely certain) that the cause is a slightly faulty lid, which might signal that it is opening at random times.  I am going to test this tonight, but if I am correct--is there any way to disable the signal?

ok, so I am completely new to the forums, and relatively new to Ubuntu (4 months or so)

I've  running ubuntu solidly on a T43.  Everything works out of the box  except the suspend/hibernate.  They both suspend the machine... but then  will wake it up randomly.  I have googled solutions to this and have  tried... pretty much everything (including updating my BIOS), nothing  has worked.

Finally, I started looking into logs, to see if there  was some way to figure out what was causing the computer to wake up....  and as far as I can tell there is nothing.  See below:

(note, I am currently suspending using the command 'hibernate-ram'.  This works perfectly except it still randomly wakes up.)
This is from kern.log
> 

Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.472108] ACPI: Preparing to enter system sleep state S3
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.620189] PM: Saving platform NVS memory
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.621718] Disabling non-boot CPUs ...
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.621761] Extended CMOS year: 2000
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.621761] Back to C!
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.621761] PM: Restoring platform NVS memory
Feb  4 12:49:07 garrett-ThinkPad-T43 kernel: [10380.621761] Extended CMOS year: 2000
As you can see, there is no clues here (unless Extended CMOS year is waking it up???  This would explain the randomness, but what is it anyway?)

Something  I would like to point out is that it says it went to sleep and woke up  in the same second.  I assume this is because it has not yet loaded the  new time when it wakes up, so it gives a false timestamp.

If anyone knows of a way to find what is waking my computer up, let me know.  I would like to disable it.

---

### Post by Cloudform on 2011-02-06
After a little testing I found out the problem was due to a faulty lid, so after googled some, I found this solution.

Hopefully it helps people who have similar problems.

[https://bbs.archlinux.org/viewtopic.php?pid=558340](https://bbs.archlinux.org/viewtopic.php?pid=558340)

---

