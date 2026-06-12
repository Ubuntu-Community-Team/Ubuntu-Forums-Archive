---
title: "Empty root folder."
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-04-09
Suppose I specified all the necessary directories of Linux to different partitions, after this will I still need to specify the root partition?...if so what will be placed there?

Sorry for the frequent questions, but I cant find the answers online...and am getting confused...so this is the only way.

---

### Post by dandnsmith on 2009-04-09
One of the items which, if using manual positioning, you **must** specify (in fact, the only one in this category) is the root - all others are optional, and can be omitted if you've no clear reason for allocating them separately (the exception is swap, which has to go somewhere)

---

### Post by dE_logics on 2009-04-09
Ok...but what will be placed that in the case I specified?

---

### Post by dE_logics on 2009-04-09
Nothing?...if so can I make it in a like...1mb partition?

---

### Post by dandnsmith on 2009-04-09
All the stuff at root level which isn't in a separate directory which you have already allocated a separate partition/filesystem will go in the root directory, together with the mount points for the items you've allocated elsewhere.

If you're that unsure, then it might be sensible to do an install into one partition for root, and one for swap, and then look to see how mush goes where using the cli commands (look up du etc).

---

### Post by dE_logics on 2009-04-09
> All the stuff at root level which isn't in a separate directory which you have already allocated a separate partition/filesystem will go in the root directory,

Yes I know...but what if I have specified all the directories then what will be left in the root partition?

> together with the mount points for the items you've allocated elsewhere.

You mean they will be just 'displayed' in /...actually they will be somewhere else.

---

### Post by dandnsmith on 2009-04-09
> You mean they will be just 'displayed' in /...actually they will be somewhere else.

Exactly so - if you say, for example, that /usr is to be in a separate partition, it will still appear (when the system is up and running) to be under / in the usr directory, and it is only by consulting the 'mounted' list that you would see any different.
When you get used to it, it is so much more convenient than the other 'popular' way of doing it (with bits of one HDD appearing to be separate 'drives')

---

### Post by dE_logics on 2009-04-09
Thanks for confirming.

But one question still exists...if I've specified all directories to different partitions, then still I have to specify the root partition...in this case what will physically be put in this root partition that I've specified (not talking about the directories that appear, but about the actual data that's fed into the HDD)?

---

### Post by dE_logics on 2009-04-10
Can anyone pls answer this?[-o<

---

### Post by pbpersson on 2009-04-10
In my root directory I have 19 folders.

Can you create 19 mount points for all those folders?

Other than that I have 4 symlinks which take up no room at all.

The real question is, what will you be using this machine for and do you have any guarantees that some software will not want to add something to root?

Disk space is cheap - you can get a one terabyte drive for 100 USD

Why not make the root 1GB so you can sleep at night?

---

### Post by kevmitch on 2009-04-10
Every mounted partition must be mounted to an empty directory (well technically you can mount something on a non-empty directory, but I wouldn't recommend it!). If you managed to set things up how you describe, your root partition would contain no real "data", but a bunch of empty folders on which everything else is mounted. 

Technically however, the directories on which you are mounting are data (you have to at least store their names somewhere together with their permissions and as well as fact that they are directories  and not just regular files) so you NEED a root partition at least for this very small amount of directory data. 

This said, I suspect you may have trouble realising this ideal because I think /sbin and /bin need to actually be on the root partition. In fact, I think the presence of these directories (with their contents) is what defines the root partition because this is where the kernel needs to look to run /sbin/init after it has been loaded.

---

### Post by dE_logics on 2009-04-10
> The real question is, what will you be using this machine for and do you have any guarantees that some software will not want to add something to root?

Humm ok I see.


No problems with disc space...but I just wanna know.

So will it be empty?...if I specify all the 19 directories to different partitions?


BTW I'm on a lap...and you get 750GB at most in 2.5 inch HDD.

They'll be around 200 bucks...still not expensive for the size though.

---

### Post by dE_logics on 2009-04-10
And still very cheep.

---

### Post by pbpersson on 2009-04-10
Apparently no one on this forum knows because no one has gone down the path you are suggesting

---

### Post by dE_logics on 2009-04-10
Ok then...guess I'll drop the question, plenty more to ask.

---

### Post by dE_logics on 2012-01-13
:popcorn:

Yes I know.

You should consider what happens after the booting process gets out of the initramfs stage. The initramfs is supposed to execute init which's in /sbin/init. Whatever init (and the scripts it executes) depends on to run before mounting partitions in fstab should be placed in the root FS (as specified in the command line parameters root=/dev/sdXY).

This includes atleast the following - 

/lib* -- libraries for dynamically linked basic utilities required for boot.
/sbin -- Important programs like init, mount, switch_root etc...
/bin -- Some other utilities which init may require (depending on the init scripts) before mounting partitions in fstab.
/proc
/sys
/dev
The last 3 is used by the Linux kernel as a mount point to important virtual FS without which survival is impossible (for the record, /proc and /sys are mounted in the initramfs stage itself, and nowadays you can mount /dev too).

Pretty advanced question for a newbie :P:lol:

---

