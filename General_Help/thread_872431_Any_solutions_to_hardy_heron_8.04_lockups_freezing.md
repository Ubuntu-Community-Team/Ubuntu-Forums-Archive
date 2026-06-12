---
title: "Any solutions to hardy heron 8.04 lockups freezing?"
date: 2008-07-28
forum: General Help
---

### Post by okos on 2008-07-28
Hi,
FYI, I never used (k)ubuntu until 8.04. Ive always used Slackware but really like the package manager for kubuntu.

Now to the point, I have had lots of problems with hardy heron locking up. Almost on a daily basis. It does not matter what I am doing it just happens. It has even happened after the screen saver started. ctrl+alt+del or backspace does not work. The only solution is push the off button ;(

It seem that LOTS of people are having the same problem. Including bug reports.  [Kernel lockup.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")

My questions is, has there been a resolution to this issue? Any suggestions on how to work around?

---

### Post by jimv on 2008-07-28
Installing the RT kernel worked for me.  If you're running the the generic kernel, then you can try this to.  (Type 'uname -r' to see what kernel you are running.)

To install the RT kernel, type this in a terminal:

sudo apt-get install linux-rt

---

### Post by okos on 2008-07-28
> **jimv said:**
> Installing the RT kernel worked for me.  If you're running the the generic kernel, then you can try this to.  (Type 'uname -r' to see what kernel you are running.)

To install the RT kernel, type this in a terminal:

sudo apt-get install linux-rt

That was EASY! Hopefully that will solve the problem.
Thank you.

---

### Post by okos on 2008-08-01
Ive had it! 
I cannot use a distro that keeps locking up.
I have a Dell Inspiron 5150. 
I upgraded the kernel as stated above. I upgraded my NVIDIA drivers.
Still, it locks up. Twice yesterday and once today.
I really like the Kubuntu features. It is far easier to use then Slackware.
However, Slackware has never locked up for me once, having used it for 1-1/2 years.
I cannot stick with Hardy Heron with this lockup problem.

I have two questions,
Would down grading to a previous version provide greater stability?
If so, is it still available. I can't seem to find the older versions.

---

### Post by edb66083 on 2008-08-10
I just started with ubuntu and kubuntu, and have lockup problems with both of them. I'm trying to restore a desktop pc whose hard drive died. I thought I would try a linux os as a fun (and cheap) alternative, but it has been very disappointing to say the least. I get a lockup every time I'm using it, no matter what I'm doing. I only takes about 5 minutes and I get frozen.

I'm going to try the previous version, Gutsy Gibbon, and see if that works better. I was able to find a download site here -> [http://releases.ubuntu.com/kubuntu/gutsy/](http://releases.ubuntu.com/kubuntu/gutsy/)

If you want the ubuntu 7.10 version, I would substitute that in the link above.

---

### Post by carusoswi on 2008-08-13
No solution to this problem, then, right?

---

