---
title: "Only 4Gb of 6Gb RAM recognized ???"
date: 2010-06-11
forum: Hardware
---

### Post by akelsall on 2010-06-11
Just built a new PC with three 2-gig sticks of memory. BIOS shows 6 Gig, but when I boot into Ubuntu, it only shows 4.

I am running the 64-bit version of Ubuntu (and verified this via lshw - it shows 64-bit widht for the CPU). Why is Ubuntu not seeing the full 6 gig?

I'm using an ASUS P6X58D-E board and in i7 CPU.

Thanks,

Andy

---

### Post by akelsall on 2010-06-15
Son-of-a-biscuit. I guess a lot of people have this issue, but no fix (based on 55 views but no replies).  I really thought using 64-bit Ubuntu would help me avoid this issue, but it hasn't. It's disappointing to say the least.

---

### Post by Ranko Kohime on 2010-06-15
Could be a bad stick?  I've had bad sticks before and you just get zero memory out of them, as if they aren't there, even though the BIOS sometimes sees them.

Frustrated the hell out of me when I was trying to build a system years ago, and having only one 256mb stick, and wondering why the system just would not boot up, no matter what components I replaced.

---

### Post by akelsall on 2010-06-16
I guess I need to break down and test each stick individually to rule that out. I've read so many posts on the Internet about people not being able to recognize all their memory that I assumed it was something having to do with Linux. I'll re-post here once I've tested.


Thanks,

Andy

---

### Post by Yellow Pasque on 2010-06-16
> and verified this via lshw - it shows 64-bit width for the CPU
Does this really verify it or just report the hardware capability of the CPU?

Best way to verify would be:
```
uname -a
```
It should return x86_64 somewhere in the output.

---

### Post by cardmaverick on 2010-06-16
I'm having this same issue with 9.04 64bit. Here's what really makes me scratch my head though...

My 32 bit install of 9.04 can see 3 of my 4 gigs, which is what I expected to have happen, but....

the 64 bit version can only see 2.9 - thats even less! 

I think it might be a physical configuration issue on my mother boards DIMM slots. When I had both the old and new 1 gig sticks spread evenly across both CPU's I couldn't get the system to show me the BIOS Menue, this was solved by putting all the new sticks on one CPU and the old ones on the other. My BIOS says it can see 4 GB of memory.... I'll have to try out some funky configurations.

---

### Post by akelsall on 2010-06-17
Referring to my MOBO (ASUS) manual, I verified which slots three sticks of memory should be plugged into (and they were correct). Then, I began testing
each stick individually. My MOBO has mem slots labeled A1/A2, B1/B2, and C1/C2. 

I plugged my first stick into A1 and ran memtest for one pass. I then took that stick out, put the next stick into B1. Ran memtest. Took that stick out and put the last stick into C1. Ran memtest. 

In call cases, I ran memtest for just one pass and each one passed with no errors. Put all memory back, booted, and BAMM! I now see 5.8 GB. WTF

I'm now wondering if there's some "board/memory sensitivity", as it's pretty safe to say I didn't put the sticks back in their original positions (e.g. the stick that was in slot A1 may now be in slot B1). Has anyone ever heard of anything like this?

Thanks,

Andy

---

### Post by Ranko Kohime on 2010-06-17
Well now that I've never heard of before.  I've had USB peripherals be touchy about which port they get plugged into, but never memory.

---

### Post by jordilin on 2010-06-17
> **akelsall said:**
> Just built a new PC with three 2-gig sticks of memory. BIOS shows 6 Gig, but when I boot into Ubuntu, it only shows 4.

I am running the 64-bit version of Ubuntu (and verified this via lshw - it shows 64-bit widht for the CPU). Why is Ubuntu not seeing the full 6 gig?

I'm using an ASUS P6X58D-E board and in i7 CPU.

Thanks,

Andy

Could you open a Terminal and execute:
```
uname -a
```
as Temüjin has pointed out above and paste the output.

---

### Post by quadproc on 2010-06-17
> **akelsall said:**
> ...
I'm now wondering if there's some "board/memory sensitivity", as it's pretty safe to say I didn't put the sticks back in their original positions (e.g. the stick that was in slot A1 may now be in slot B1). Has anyone ever heard of anything like this?

It is possible that the combination of mother board and memory does not work correctly due to something like a timing or level problem between a particular socket location and a particular memory stick but this is pretty unlikely.

More likely, there was a contact problem between one of the contacts on one memory stick and the particular socket that it was plugged into.  Often, unplugging and replugging will eliminate such contact problems, at least temporarily, because such problems are frequently due to a bit of junk on the surface of the metal and that junk gets pushed off by the plugging action.

If you have reason to remove the memory stick(s) again then I suggest using a magnifying glass to inspect the socket contacts while the memory is removed.  If you see any bent or broken pins then you will know why there was a problem.

quadproc

---

### Post by Yellow Pasque on 2010-06-17
> **akelsall said:**
>  Has anyone ever heard of anything like this?
Most likely, you didn't install the RAM correctly initially (probably didn't push one of the sticks hard enough based on the fact that you saw 4GB). RAM can be a real pain sometimes :\.

---

### Post by akelsall on 2010-06-17
Ya know, you're probably right (about the sticks not being seated properly). Although, they did feel snug when I popped each one out.  It does make more sense than some memory/MOBO slot sensitivity lol

---

### Post by lyall on 2010-06-17
I alway try to clean the slots before installing the memory, and check the the memory contracts before installing them

---

### Post by akelsall on 2010-06-18
lyall, how do you go about cleaning the slots? It seems like it would be difficult to do so.

---

