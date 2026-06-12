---
title: "Toshiba satellite pro 4600"
date: 2013-02-18
forum: Hardware
---

### Post by Paulo Costa on 2013-02-18
Hi. I have a Toshiba satellite pro 4600 a vbery old laptop and it's the computer that i use on my vacations. i want to change the os to ubuntu because i think the computer will have a better performance. I«m a dummy in computers can you help me? will the ubuntu work in the computer?
thanks.

---

### Post by squakie on 2013-02-18
If it's the default configuration then no.
 
The Celeron 750mhz will run it, but probably slowly.
 
The default installed memory is 256mb - I believe Ubuntu requires 512mb minimum.  There are other Linux's out there that will run in that - one I've heard mention of on this forum is Damn Small Linux (DSL).
 
The default hard disk size is 10gb.  This also too small to be useful now.

---

### Post by mörgæs on 2013-02-18
These threads tend to get into a mish-mash of 'I have heard...'

To everyone posting here, please write only your actual experiences with similar hard- and software.

---

### Post by cetoka on 2013-02-18
I have a Toshiba Satellite A 200... 6 years old and Xubuntu is working fine.Suspend is working too.But I upgraded RAM to 2GB.

---

### Post by squakie on 2013-02-19
> **mörgæs said:**
> These threads tend to get into a mish-mash of 'I have heard...'
 
To everyone posting here, please write only your actual experiences with similar hard- and software.
 
Sorry - I didn't realize that the literally hundreds of posts I have seen on the forum recommending someone try things like DSL, Puppy, etc., could only be posted if you had experience with the actual hardware and software.  I was only trying to help the user.

---

### Post by varunendra on 2013-02-19
> **squakie said:**
> Sorry - I didn't realize that the literally hundreds of posts I have seen on the forum recommending someone try things like DSL, Puppy, etc., could only be posted if you had experience with the actual hardware and software.  I was only trying to help the user.

Well, I like the idea of actually testing before recommending, and for that I use VMs. Sure I can not 'downgrade' the CPU beyond assigning a single core, but I *think* the main bottlenecks are RAM and HDD space - both of which are scalable in VMs.

Having said that, I have personally used Linux Mint 9 (LXDE) on an old compaq presario 2100. It's dead now so can't confirm the exact CPU model, but was a pentium 4 and came with 256MB RAM by default. However, it was upgraded to an additional 512MB RAM when I tested it.

With 768 MB RAM, it could successfully run (in virtualbox) Win server 2003 (with 128 MB RAM assigned) + DSL (32 MB RAM assigned) on Mint 9 LXDE host simultaneously without any lagging.

As for DSL, it is very good for casual booting for basic emergency tasks or for system rescue / file recovery purpose, but is not suitable for regular desktop work. Slitaz with additional packages (available in Slitaz repos) can be more suitable.

But for any serious desktop usage, it is strongly recommended to get at least 512MB or more memory for that laptop, then install any dedicated desktop OS. Xubuntu or Lubuntu are my favourite (although there may be better ones I haven't tested personally).

---

### Post by squakie on 2013-02-19
How would I set up a VM to emulate that hardware?  The only things I've ever done, and the only things I *thought* possible, was to run an OS.  I do use virtualbox, but not having their exact hardware I didn't know how I could possibly emulate it.
 
Didn't know DSL was only for recovery.  In the ABS of the forum I have seen it mentioned many times, along with Puppy and many others, as a distro to try with restricted hardware.
 
I do know that with the default memory (256mb) the OP can't run straight Ubuntu.  I also recall that it takes more than the default disk size (10gb) to install and actually use productively straight Ubuntu.
 
That's all I was trying to tell the OP - no, their hardware wouldn't run Ubuntu (since most people refer to that as the Ubuntu you would download from Ubuntu.com).  I mentioned DSL because it has been recommended so many times.  I know that Puppy is also recommended.  Both cases because of the restricted hardware the OP has.
 
So, unless there is a way to emulate and exact hardware platform - in this case the OP's Satellite Pro 4600, it won't matter how much testing you do in a VM.  That will only prove that a given OS can run within the memory restrictions unless you also force the virtual disk to a fixed size (in this case 10gb).  Even then it's still not the hardware model.
 
If it is that important, next time before I try to help someone, following what is already in the forums, I'll set up a VM within the given memory and disk constraints, install the OS(s) in question and see what happens.  It still is not emulating the hardware - just the OS.  I *thought* things like DSL, Puppy, etc., had been proven enough to run within those specs as to not try to confuse the OP.
 
My mistake.
 
BUT......back to the OP's question to begin with:  I stand by my comment.  You can search these forums and/or the net for other lightweight Linux distributions.  Right now the important thing is to review the minimum specs (processor, memory, disk) that the distribution requires and get one that fits within your PC's parameters.  I threw DSL out there because it is a very common response to many, many other posts like this.  I mention Puppy Linux for the same reason.  There are others as well.  Have I tried to run them within the specs of your PC?  No.  Perhaps that invalidates my reply.

---

### Post by varunendra on 2013-02-20
> **squakie said:**
> My mistake.
Not at all! I just shared my opinion as you shared yours, that's all.

I quoted your comment only to express that it is not always necessary to own a specific hardware to test an OS. I'm sorry if it seemed offending to you, but I certainly don't mean to.
 
> Didn't know DSL was only for recovery.  In the ABS of the forum I have seen it mentioned many times, along with Puppy and many others, as a distro to try with restricted hardware.
About a few hundred of those recommendations would be mine :)
I often recommend it to those who can not upgrade hardware and want to just somehow use their old computer.

In fact I once posted [a thread]("http://ubuntuforums.org/showthread.php?t=1711228") on how to boot it in VBox (although it was focussed towards setting up a VM, you can get the idea how much I am obsessed with DSL;))

*[Oh, and digging up that thread also made me realize that I actually had 512 MB RAM on the laptop that I mentioned earlier (had pulled out 256 MB to test performance within those constraints).]*

I have also heard many times about puppy and gentoo, and by the descriptions from others, it seems maybe puppy is more advanced than DSL for any practical (but casual) desktop usage (is often recommended as a live USB), but I have never tried it myself, so never talk about it as I have no idea of how usable it really is.
 
> If it is that important, next time before I try to help someone, following what is already in the forums, I'll set up a VM within the given memory and disk constraints, install the OS(s) in question and see what happens.
I would certainly not recommend doing so. It is not even feasible for most users who are volunteering their skills here and may not have time for all those experiments. But it is also undeniable that we can offer much better help on something which we have first hand experience with.

One more thing, not to argue, but just for sake of newbies who might come across this thread -
> **squakie said:**
> How would I set up a VM to emulate that hardware?...I do use virtualbox, but not having their exact hardware I didn't know how I could possibly emulate it.
No, we certainly can't.
But a hardware as old as the OP mentioned is very close to the legacy hadware that a typical VBox or VMware VM emulates. So in my experience (which is not very extensive though) hardware variation does not make much difference. The only things that matter (RAM & HDD space) are both scalable in VMs.

Obviously, the story is different for modern hardware.

---

### Post by squakie on 2013-02-20
Thank you so much for explaining!  I'm sorry I got a little upset - I've been a little touchy since another matter and guess I carried it over to here.  Have a good one! ;)

---

### Post by mörgæs on 2013-02-20
> **varunendra said:**
> 
I have also heard many times about puppy and gentoo, and by the descriptions from others, it seems maybe puppy is more advanced than DSL for any practical (but casual) desktop usage (is often recommended as a live USB), but I have never tried it myself, so never talk about it as I have no idea of how usable it really is.
 


I have tested both Damn Small Linux and Puppy on various old hardware, and I would not recommend the former. It has been dormant for quite some time and is only slowly getting up to speed. Most applications are dated and need an update.

Puppy (especially Precise Puppy) is a better choice, but again: More RAM is needed.

---

