---
title: "[SOLVED] Grub Error 25"
date: 2008-08-11
forum: General Help
---

### Post by stepanstas on 2008-08-11
I know there are a number of posts here about this, but I think my case is unique.

This all started when my computer just started running really slowing and was fading out my browser every few seconds.  So i did a reboot and since then got this or a similar error.

I got a Read Error, Error 25, Read Error at stage 1.5, and either 17 or 18, cant remember.

It also tried running a few tests by itselt (which took hours)

I couldn't understand what the tests ment and all the data was going through rather fast, so i could not remeber much, but i think it had a few errors.  And from what I read online, i have a hunch its a bad sector.

I tried using a live cd and doing find /boot/grub/stage1 and /menu.ls  and doing the root and setup thing, did not work.

It currently stands at error 25.

I heard something about a Linux Rescue included on the Live CD but i could not find any info about it.  I also was told that i could boot into my computer through the live cd.  Dont know how to do either of the 2.

Any help would be greatly appreciated.

P.S.  I do not dual boot.  I have 2 partitions/drives and only one has a Ubuntu install on it, the other is just data.

---

### Post by stepanstas on 2008-08-14
bump

---

### Post by Elfy on 2008-08-14
[http://ubuntu-rescue-remix.org/node/55](http://ubuntu-rescue-remix.org/node/55) is where the livecd is there is some documentation available

I would make sure that I got as much data of the disc as I needed, it would point a disc failure of some sort.

Not sure I can be of more help, which test did you run.

---

### Post by stepanstas on 2008-08-14
forestpixie, thanks for your reply.

What do you mean by "get as much data out of the disc as needed"
do you think I might never be able to get into Ubuntu again.
So you think this is a harddrive problem?

I don't know what tests I ran, they just loaded themselves up.  Took a really long time too.

---

### Post by Elfy on 2008-08-15
Yes I think that it's a hdd problem, I think you should run fsck - read the man page on it - [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

If you know the manufacturer of the hdd - if you don't open the case and have a look - I expect they have a test tool for it.


Edit Try running recovery mode and then I think the command should be, go to root prompt when you reach the menu

fsck /dev/sdax

check which partition it is 

fdsik -l will list partitions for you.

---

### Post by stepanstas on 2008-08-17
Thanks for all your help


I used the manufacturers disk check and found a lot of errors.

bad news for me

Thanks again.

---

### Post by stepanstas on 2008-08-18
Okay.

Last question before i mark this as solved.

This entire thing scared me a bit.

All this talk about bad secotors and stuff.

I used my manufacturers test and then fsck and that fixed it.  Now Ubuntu is running just as it was before.

Should I worry about this happening again and maybe this time I wont be able to recover it?

Should I back everything up and get a new drive?

---

### Post by Elfy on 2008-08-18
Well I'm glad that all was well evntually - there is always the chance of a drive dying and you should have backups; if it is going to break it could happen tommorrow, the day after, next week, mont, year :shrug:

I would though think that is it has problems it would be best to be ready for ity to go.

---

