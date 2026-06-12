---
title: "Ubuntu not loading... now grub4dos?"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by dpawl31 on 2009-08-26
Ok guys, been running Ubuntu (started as 7.04, upgraded as came out) on an HP. Mainly because XP got infected with some virus that corrupted IE and firefox, and I can't get it out. It is also on my other work PC which I am on right now, and pissing me off to no end lol.

Anyway, we lost power the other day. My food prep manager is the owner of the HP w/ ubuntu.

He's not PC - literate so he MAY have done something himself to cause this.
Basically, when came in that day - he said he got into Ubuntu and put in his name/password and something 'didn't work right'
and he couldn't get in. Then he tried XP, and it worked, but still virus'd out.

When I select UBUNTU in the GRUB loader, it goes to GRUB4DOS. No idea what to do there. Am I screwed? There's a lot of important food/inventory logs and files on there we need to get. 

I figure I can probably use a LIVECD to get that stuff right? But can I just fix this instead?

---

### Post by esalnoj on 2009-08-26
Have you done the grub reinstall routine from liveCD? How did GRUB4DOS get on there anyway?

Do you have an external hard-drive?

If so, copy the files to it when the drive is mounted from live CD first.

How much time would it take to get the system updated from a fresh install to current state? Could this be accomplished when the restaurant isn't open?

Have you made a recent backup of your system? This would decrease the time required to reset the system to current state.

---

### Post by dpawl31 on 2009-08-26
So I can reinstall grub from the livecd?

And I have NO IDEA how grub4dos got there. NO IDEA.

How do I go about reinstalling GRUB from the CD?

---

### Post by esalnoj on 2009-08-26
For setting up grub from liveCD:

1. Open terminal, then run following text:

```
sudo grub
find /boot/grub/stage1
```
This gives location in hd(number:number) (your ubuntu partition)

```
root hd(number:number)
setup hd(number:number)
quit
```

If that doesn't solve it, consider the other questions I asked.

---

### Post by dpawl31 on 2009-08-26
Hope that works, will try when I get the liveCD back here to the office.
Thanks, hopefully tomorrow I'll get it going again.

-Doug

Oh and yes - I do have an external hard drive as well as 8GB thumb drive.
If need be, I'll fresh install.

---

### Post by dpawl31 on 2009-08-26
How do I get the two numbers?

*edit*
duh, you said that haha... whoops.

---

### Post by dpawl31 on 2009-08-26
When I do find /boot/grub/stage1 
I get file not found.

I assume I have to somehow use the livecd to run a terminal 
IN my hard drive directory, but I don't get that part.

---

### Post by esalnoj on 2009-08-27
try cd'ing into /media/"your hard drive" before running the grub commands.

---

### Post by dpawl31 on 2009-08-27
> **esalnoj said:**
> try cd'ing into /media/"your hard drive" before running the grub commands.


Do I need to use SUDO?
Also, by "your hard drive" do you mean sda1 hda1 sda0 that kind of thing?
I don't know how to figure out my hard drive name like that off the live CD.

In my full install I have a hard drive partition manager that tells me the names.

This is  what I tried.

```
cd /media/"hda1"

cd /media
```

I tried all variations of hdo0 hda1 sda0 sda1, no luck.
I tried into just media, and that worked.

On another note, not sure how to access my files to back them up.
When on the liveCD I have these for options:

69.3 Media <-- hard drive
CD Drive <-- duh
Filesystem <-- LIVECD filesystem, correct?

Under the hard drive, it's all Windows Junk, plus an
ubuntu folder that only has docs, install and winboot. 
I MAY have done a Windows install of Ubuntu, not sure.
But now I don't know how to get TO my files, so it
looks like fixing GRUB itself is my only option...

Thanks for the help by the way, I can always count on
people on forums to help me out. I may be new to this forum, 
but I have ~5000 technical posts on computer building forums.

I'm pretty good with windows too... but programming/working with
ubuntu is tough, aside from compiz hehe... :)

Thanks again man, hope you can help me get this fixed. 
Once I get it fixed - I am flushing the drive, no more XP dual boot etc.
Going straight Ubuntu, and backing up to thumb drive DAILY.

-Doug

---

### Post by esalnoj on 2009-08-27
Are your logs inside the hard drive->ubuntu->docs?

Try recovering from there.

As per the cd command, open the filesytem on the live CD, go to media, then see what your hard drive's folder is called. Should be something along the lines of "disk".

Then run:
```
cd /media/"disk"
```

Try googling "wubi jaunty grub reinstall"

And see what you find. I have not experienced a wubi grub recovery yet.

---

