---
title: "Changing CPU without reinstalling"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by Fenboy on 2009-09-13
Hi all,
My motherboard is capable of running a more powerful processor than the Athlon 64 x2 5000 which came bundled with it.  I'm thinking of replacing it with a Phenom x4 9650 (it's about as much as I can afford) and should be noticeably quicker.

My question is: Am I right to think that I can do this simple swap without the need to reinstall Jaunty?  I'm pretty sure I couldn't get away with this with Windows.

Thanks

---

### Post by sanderj on 2009-09-13
Yes, I'm quite sure you're right and you can just replace the CPU.

The only problems I know of when replacing hardware:
- replacing the video card with the old video card still configured in Linux
- putting in a new mother board on which the installed Ubuntu does not run at all, for example because the motherboard needs newer kernel/drivers than available in the installed Ubuntu.

Replacing a CPU seems like a harmless thing to do.

---

### Post by Fenboy on 2009-09-13
Thanks for the reply.  Other threads suggest that this is probably the case. I'll report back what happens when I make the switch; probably in the course of this week.

---

### Post by rob-ward on 2009-09-13
I have swapped a CPU in a ubuntu computer in the past with no problems so you should be OK

---

### Post by Fenboy on 2009-09-20
Just to wrap this thread up I can report that the CPU change went almost without a hitch.
The bios and Ubuntu system monitor picked up the change with no problem.  But strangely when I restarted I got the "ignoring home/.dmrc" message.

I've seen this before so it was easily fixed by the following:

sudo chown -R username /home/username 
chmod 755 /home/username
chmod 644 /home/username/.dmrc

Disappointingly the change doesn't seem to have made much difference to the overall speed of the machine but I guess the change from a dual to quad core will help it cope better with multi-tasking.

Thanks for your help guys.

---

