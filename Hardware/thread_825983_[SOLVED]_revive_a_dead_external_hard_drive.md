---
title: "[SOLVED] revive a dead external hard drive"
date: 2008-06-11
forum: Hardware
---

### Post by moore.bryan on 2008-06-11
long story short, my wonderfully well-functioning western digital usb external hard drive was having some issues which i now know were warning signs of impending doom. most of my life is on that disk and, of course, there is no complete backup; just fragments here and there, scattered around the internet, floppies, cd's, etc.

so, here's one for the community... what are our experiences with recovering data from a drive that won't even be recognized, so no viable software data recovery solution can be utilized? miraculous successes, catastrophic failures, etc...

oh, and just to put it out there, i'm in the process of acquiring another external and am trying the "freezer trick."

---

### Post by stchman on 2008-06-11
> **moore.bryan said:**
> long story short, my wonderfully well-functioning western digital usb external hard drive was having some issues which i now know were warning signs of impending doom. most of my life is on that disk and, of course, there is no complete backup; just fragments here and there, scattered around the internet, floppies, cd's, etc.

so, here's one for the community... what are our experiences with recovering data from a drive that won't even be recognized, so no viable software data recovery solution can be utilized? miraculous successes, catastrophic failures, etc...

oh, and just to put it out there, i'm in the process of acquiring another external and am trying the "freezer trick."

Data recovery on a non working hdd is both difficult and expensive.  You might look at removing the hdd from it's enclosure to see if the interface (USB, Firewire, or eSATA) is messed up.  If that is the case then installing the hdd in a new external case would be an inexpensive option.

If the drive is indeed bad it is probably lost forever.  I recommend periodic backups.

---

### Post by moore.bryan on 2008-06-11
> **stchman said:**
> Data recovery on a non working hdd is both difficult and expensive.
yeah, this is something i figured-out really quickly through initial research.
> You might look at removing the hdd from it's enclosure to see if the interface (USB, Firewire, or eSATA) is messed up.  If that is the case then installing the hdd in a new external case would be an inexpensive option.
from what i've read, the sounds i've been hearing are either an unreadable block or a stuck r/w head, so i don't think it's the usb interface... unless experience has told you it might be?
> If the drive is indeed bad it is probably lost forever.  I recommend periodic backups.
very true; hind-sight is 20/20.

---

### Post by stchman on 2008-06-11
> **moore.bryan said:**
> yeah, this is something i figured-out really quickly through initial research.

from what i've read, the sounds i've been hearing are either an unreadable block or a stuck r/w head, so i don't think it's the usb interface... unless experience has told you it might be?

very true; hind-sight is 20/20.

The USB interface is probably OK, but it is worth a try.  Is the hdd 2.5 or 3.5?  A new enclosure for either form is pretty inexpensive.

---

### Post by moore.bryan on 2008-06-12
3.5"... i think if my freezer trick doesn't work, your suggestion will be the next step. thanks for the input; have you ever had a similar problem?

what about others out there?

---

### Post by shrimphead on 2008-06-12
I've had something similar happen to me in the past, and unfortunately I managed to lose quite a lot of work. I really hope you don't end up in the same boat.

I now pretty much live my life by this: [http://jwz.livejournal.com/801607.html](http://jwz.livejournal.com/801607.html)

EDIT: Option 2 that is ;)

---

### Post by moore.bryan on 2008-06-12
> **shrimphead said:**
> I really hope you don't end up in the same boat.
thanks... i appreciate any hopes/prayers/spells/charms i get right now...
> I now pretty much live my life by this: [http://jwz.livejournal.com/801607.html](http://jwz.livejournal.com/801607.html)
EDIT: Option 2 that is ;)
i was hoping you didn't go for #1! it'll teach me a lesson about western digital... seems most posts criticize them as being not 100% reliable.

---

### Post by moore.bryan on 2008-06-17
just wanted to let everyone know what happened with the freezing; in short, it worked amazingly well. i was able to salvage 100% of my data from the dead drive and put it on my new 500gb lacie. 

a question now arises, however; what is the best file system for a 500gb external hd mainly used for backups and media? will some give longer life than others? the lacie i purchased came formatted, interestingly enough, fat32.

---

### Post by Odrodzona-Sarmacja on 2008-06-18
Fat32 never gets old for storage purposes. :D
Other file systems are good for running operative systems, but for data storage... nothing beats fat32 really. :D
I got myself a Lacie too. A smart purchase. :D

---

### Post by moore.bryan on 2008-06-18
yeah, i did my homework this time and found lacie to be the most commonly recommended. it somewhat surprises me fat32 hasn't been "bested" by some other file system.

---

### Post by moore.bryan on 2008-06-21
there's a new rub to this very "solved" issue... the drive isn't dead. in fact, it's working just as well now after it's been reformatted and checked. not a single issue; i.e. not one problem. could it have been the ext3 file system causing the issue? could it be a "bad block" at the point of the drive i finally reached?

---

### Post by deamon_knight on 2008-06-21
If there is a SINGLE or Very Few bad blocks (physically bad spot on the drive), and you repartition the drive, they system should map around that bad spot. HOWEVER, this should happen automatically through interactions between the Drive itself and the file system, and should not become a problem to the user. Since it has become a problem, its likely a sign of a deeper, physical failure on that Hard Drive. You may be able to continue using it, however I would advise against it.

---

### Post by moore.bryan on 2008-06-22
> **deamon_knight said:**
> If there is a SINGLE or Very Few bad blocks (physically bad spot on the drive), and you repartition the drive, they system should map around that bad spot. HOWEVER, this should happen automatically through interactions between the Drive itself and the file system, and should not become a problem to the user. Since it has become a problem, its likely a sign of a deeper, physical failure on that Hard Drive. You may be able to continue using it, however I would advise against it.
yeah, i figured the same. strange that the "badblocks" cli tool didn't return any errors, though.

---

### Post by Odrodzona-Sarmacja on 2008-06-22
There is last few years a well known kernel bug on linux distros. On some hardware configurations it causes linux to corrupt files on ext3 partitions.
You can read more on ext3 coruptions with Ubuntu in particular at
"https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102"

---

### Post by moore.bryan on 2008-06-23
> **Odrodzona-Sarmacja said:**
> There is last few years a well known kernel bug on linux distros. On some hardware configurations it causes linux to corrupt files on ext3 partitions.
You can read more on ext3 coruptions with Ubuntu in particular at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/53102)
interesting read... i find it exceedingly strange the main/default fs choice of ubuntu could be so unpredictable.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
> **moore.bryan said:**
> interesting read... i find it exceedingly strange the main/default fs choice of ubuntu could be so unpredictable.

It is also quite volatile subject on Linux forums. Discussions gets closed and locked. Better not talk much about it from my experience. However Linus, creator of the Linux kernel knows about this bug already few years and there is still no solution on horizon. The known solution is to get some other hardware configuration, which the bug-less majority of Linux users use.

---

### Post by moore.bryan on 2008-06-23
is ext4 supposed to solve any of these "issues?"

---

